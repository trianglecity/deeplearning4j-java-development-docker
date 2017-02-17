##
## This work is based on 
## [1] the work of https://docs.docker.com/opensource/project/set-up-dev-env/
## [2] https://github.com/bytedeco/javacpp-presets (for OpenBLAS)
##

The deeplearning4j developement environment is implemented using Docker.
This source code includes 
	javacpp
	javacpp-presets (for OpenBLAS)
	libnd4j
	nd4j
	datavec
	deeplearning4j
	MNIST (mnist data)
	exmaples (mnist java example code)
	
NOTICE: Do NOT change included pom.xml files	

Please follow the instructions below to run the mnist java example.

[1] download (or git clone) this source code folder

[2] cd downloaded-source-code-folder

[3] sudo make BIND_DIR=. shell

	wait ... wait ... then a bash shell will be ready (root@f01e1dc38daa:/#)

[4] root@f01e1dc38daa:/# cd /root/deeplearning/

[5] root@f01e1dc38daa:~/deeplearning# cd javacpp

[6] root@f01e1dc38daa:~/deeplearning/javacpp# mvn clean install

[7] root@f01e1dc38daa:~/deeplearning/javacpp# cd ..

[8] root@f01e1dc38daa:~/deeplearning# cd javacpp-presets

[9] root@f01e1dc38daa:~/deeplearning/javacpp-presets# ./cppbuild.sh

[10] root@f01e1dc38daa:~/deeplearning/javacpp-presets# mvn clean install

[11] root@f01e1dc38daa:~/deeplearning/javacpp-presets# cd ..

[12] root@f01e1dc38daa:~/deeplearning# cd libnd4j

[13] root@f01e1dc38daa:~/deeplearning/libnd4j# ./buildnativeoperations.sh

[14] root@f01e1dc38daa:~/deeplearning/libnd4j# export LIBND4J_HOME=`pwd`

[15] root@f01e1dc38daa:~/deeplearning/libnd4j# cd ..

[16] root@f01e1dc38daa:~/deeplearning# cd nd4j

[17] root@f01e1dc38daa:~/deeplearning/nd4j# mvn clean install -DskipTests -Dmaven.javadoc.skip=true -pl '!:nd4j-cuda-8.0,!:nd4j-cuda-8.0-platform,!:nd4j-tests'

[18] root@f01e1dc38daa:~/deeplearning/nd4j# cd ..

[19] root@f01e1dc38daa:~/deeplearning# cp -rp ./nd4j/ /usr/local/lib/

[20] root@f01e1dc38daa:~/deeplearning# cd datavec

[21] root@f01e1dc38daa:~/deeplearning/datavec# bash buildmultiplescalaversions.sh clean install -DskipTests -Dmaven.javadoc.skip=true

[22] root@f01e1dc38daa:~/deeplearning/datavec# cd .. 

[23] root@f01e1dc38daa:~/deeplearning# cd deeplearning4j

[24] root@f01e1dc38daa:~/deeplearning/deeplearning4j# mvn clean install -DskipTests -Dmaven.javadoc.skip=true -pl '!:deeplearning4j-cuda-8.0'
	

[25] root@f01e1dc38daa:~/deeplearning/deeplearning4j# cd ..

[26] root@f01e1dc38daa:~/deeplearning# cd examples

[27] root@f01e1dc38daa:~/deeplearning/examples# cd mnist

[28] root@f01e1dc38daa:~/deeplearning/examples/mnist# mvn clean compile

[29] root@f01e1dc38daa:~/deeplearning/examples/mnist# mvn clean package 

[30] root@f01e1dc38daa:~/deeplearning/examples/mnist# java -Djava.library.path=/usr/lib/:/usr/lib/gcc/x86_64-linux-gnu/5/:/usr/local/lib/nd4j/nd4j-backends/nd4j-backend-impls/nd4j-native/target/classes/org/nd4j/nativeblas/linux-x86_64:/root/deeplearning/nd4j/nd4j-backends/nd4j-backend-impls/nd4j-native/target/classes/org/nd4j/nativeblas/linux-x86_64:/root/deeplearning/javacpp-presets/openblas/target/classes/org/bytedeco/javacpp/linux-x86_64/ -cp /root/.m2/repository/org/slf4j/slf4j-api/1.7.12/slf4j-api-1.7.12.jar:/root.m2/repository/org/slf4j/slf4j-simple/1.7.12/slf4j-simple-1.7.12.jar:/root/.m2/repository/org/nd4j/nd4j-common/0.7.3-SNAPSHOT/nd4j-common-0.7.3-SNAPSHOT.jar:/root/.m2/repository/org/nd4j/nd4j-context/0.7.3-SNAPSHOT/nd4j-context-0.7.3-SNAPSHOT.jar:/root/.m2/repository/org/nd4j/nd4j-buffer/0.7.3-SNAPSHOT/nd4j-buffer-0.7.3-SNAPSHOT.jar:/root/.m2/repository/org/nd4j/nd4j-api/0.7.3-SNAPSHOT/nd4j-api-0.7.3-SNAPSHOT.jar:/root/.m2/repository/org/deeplearning4j/deeplearning4j-core/0.7.3-SNAPSHOT/deeplearning4j-core-0.7.3-SNAPSHOT.jar:/root/.m2/repository/org/deeplearning4j/deeplearning4j-nn/0.7.3-SNAPSHOT/deeplearning4j-nn-0.7.3-SNAPSHOT.jar:/root/.m2/repository/org/deeplearning4j/deeplearning4j-nlp/0.7.3-SNAPSHOT/deeplearning4j-nlp-0.7.3-SNAPSHOT.jar::/root/.m2/repository/org/nd4j/nd4j-native-platform/0.7.3-SNAPSHOT/nd4j-native-platform-0.7.3-SNAPSHOT.jar:/root/.m2/repository/org/nd4j/nd4j-native/0.7.3-SNAPSHOT/nd4j-native-0.7.3-SNAPSHOT.jar:/root/.m2/repository/commons-lang/commons-lang/2.6/commons-lang-2.6.jar::/root/.m2/repository/commons-io/commons-io/1.3.2/commons-io-1.3.2.jar:/root/.m2/repository/org/apache/commons/commons-compress/1.8/commons-compress-1.8.jar::/root/.m2/repository/org/apache/commons/commons-math3/3.6/commons-math3-3.6.jar:/root/.m2/repository/org/nd4j/nd4j-native-api/0.7.3-SNAPSHOT/nd4j-native-api-0.7.3-SNAPSHOT.jar:/root/.m2/repository/com/google/collections/google-collections/1.0/google-collections-1.0.jar:/root/.m2/repository/org/reflections/reflections/0.9.10/reflections-0.9.10.jar:/root/.m2/repository/org/bytedeco/javacpp/1.3/javacpp-1.3.jar::/root/.m2/repository/commons-codec/commons-codec/1.10/commons-codec-1.10.jar:/root/.m2/repository/org/bytedeco/javacpp-presets/openblas/0.2.19-1.3/openblas-0.2.19-1.3.jar:/root/.m2/repository/org/bytedeco/javacpp-presets/1.3/javacpp-presets-1.3.jar:/root/deeplearning/nd4j/nd4j-shade/jackson/target/jackson-0.7.3-SNAPSHOT.jar:/root/.m2/repository/org/apache/commons/commons-lang3/3.5/commons-lang3-3.5.jar:/root/.m2/repository/commons-io/commons-io/2.5/commons-io-2.5.jar:/root/.m2/repository/com/google/guava/guava/21.0/guava-21.0.jar:/root/.m2/repository/org/apache/commons/commons-math3/3.6.1/commons-math3-3.6.1.jar:/root/.m2/repository/javassist/javassist/3.12.1.GA/javassist-3.12.1.GA.jar:/root/deeplearning/examples/mnist/target/mnist-1.0-SNAPSHOT.jar com.example.mnist.App


[31] the output looks like 

	SLF4J: Failed to load class "org.slf4j.impl.StaticLoggerBinder".
	SLF4J: Defaulting to no-operation (NOP) logger implementation
	SLF4J: See http://www.slf4j.org/codes.html#StaticLoggerBinder for further details.

	... dl4j:mnist ...

	/root/deeplearning/MNIST/
	.. the file exists ...
	... all the MNIST data are in the /root/deeplearning/MNIST ... 


	/root/deeplearning/MNIST/
	.. the file exists ...
	... all the MNIST data are in the /root/deeplearning/MNIST ... 


	epoch = 0
	epoch = 1
	epoch = 2
	epoch = 3
	epoch = 4
	... in evaluation process ...
	... in evaluation process ...
	
	... in evaluation process ...
	... in evaluation process ...

	Examples labeled as 0 classified by model as 0: 965 times
	
	Examples labeled as 1 classified by model as 1: 1118 times
	
	Examples labeled as 2 classified by model as 2: 976 times
	
	Examples labeled as 3 classified by model as 3: 965 times
	
	Examples labeled as 4 classified by model as 4: 927 times
	
	Examples labeled as 5 classified by model as 5: 825 times
	
	Examples labeled as 6 classified by model as 6: 924 times
	
	Examples labeled as 7 classified by model as 7: 971 times
	
	Examples labeled as 8 classified by model as 8: 908 times
	
	Examples labeled as 9 classified by model as 9: 947 times


	==========================Scores========================================
 	Accuracy:        0.9526
 	Precision:       0.9524
 	Recall:          0.952
 	F1 Score:        0.9522
	========================================================================

[32] to disable the message that says "... in evaluation process ...", we can edit  downloaded-source-code-folder/deeplearning4j/deeplearning4j-nn/src/main/java/org/deeplearning4j/eval/Evaluation.java in the local machine (or in the docker).
	
	line # 193: System.out.println("... in evaluation process ...");


[33] repeat steps from [25] through [30] to see the modified output. 

