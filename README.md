# FDSE

FDSE :-
---------

FDSE is an automated test input generation tool based on symbolic execution.
Collect path constraints using LLVM Pass instrumentation and solve path constraints using Z3 solver.

FDSE can support parallel analysis and is designed based on a master-slave framework.
The master node controls the exploration of path constraint trees, while the slave node 
performs symbol execution and collects path constraints. Both pass input for execution and 
serialized path constraints through sockets.

NOTE :-
Local network ports need to be opened for use.


Author :-
---------
Guofeng Z, Ziqi S, Kelin M, Kunlin L, Zhenbang C, and Ji W.


SYSTEM REQUIREMENTS :-
---------------------
0) Ubuntu 22.04
1) >= python 3.6.1


DOWNLOAD :-
---------------
https://zenodo.org/records/10203198
 
 
Third Party Components Used :-
----------------------------

a) LLVM 10.0.1 (for compile)
   TOOL URL : https://github.com/llvm-project/llvm
   LICENSE  : https://github.com/llvm-project/llvm/blob/master/LICENSE.TXT
	
b) symcc (for instrumentation)
   TOOL URL : https://github.com/eurecom-s3/symcc
   LICENSE  : https://github.com/eurecom-s3/symcc/blob/master/LICENSE

c) Z3 SMT Solver 4.8.10 (for constraints solving)
   TOOL URL : https://github.com/Z3Prover/z3
   LICENSE  : https://github.com/Z3Prover/z3/blob/master/LICENSE.txt

d) Protocol Buffers 3.14.0 (for data serialization and deserialization)
   TOOL URL : https://github.com/protocolbuffers/protobuf
   LICENSE  : https://github.com/protocolbuffers/protobuf/master/LICENSE.txt
   
e) json-c   (for create json file)
   TOOL URL : https://github.com/json-c/json-c
   LICENSE  : https://github.com/json-c/json-c/blob/master/COPYING

f) KLEE (for DSE)
   TOOL URL : http://klee.github.io/
   LICENSE  : klee/LICENSE

USAGE :-
--------
./fdse --testcomp --property-file <.prp file> --output /home/xxx/output -sf CFILE

eg. ./fdse --testcomp --property-file ~/sv-benchmarks-master/c/properties/unreach-call.prp
--arch 64  --output /home/aaa/output -sf ~/sv-bencmarks-master/c/eca-rers2012/Problem01_label20.c


The package provides run_test.sh script is used to demonstrate the FDSE usage
eg. ./run_test.sh


OUTPUT :-
---------
All generated test inputs are output in XML format to $fdse_output/test-suite
