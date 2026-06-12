---
title: "Java install but not in sh"
date: 2014-08-11
forum: New to Ubuntu
---

### Post by duongthaiha on 2014-08-11
Hi 
I installed java both open and set default to openjdk. I can access java and javac anywhere in terminal. However if i use  sh then i got 
/bin/sh: 1: /usr/lib/jvm/java-7-openjdk-amd64/bin/javac: not found

```

java -version
java version "1.7.0_55"
OpenJDK Runtime Environment (IcedTea 2.4.7) (7u55-2.4.7-1ubuntu1)
OpenJDK 64-Bit Server VM (build 24.51-b03, mixed mode)

```

Can you please help show me what I have done wrong?
Thanks

---

### Post by redrumrogue on 2014-08-11
Would need to see some of your script.  What is the first line of your script (does it start with "#! /bin/bash" ?) and what line in your script calls for "/usr/lib/jvm/java-7-openjdk-amd64/bin/javac"?

---

### Post by nerdtron on 2014-08-11
```
whereis java
```

Then put the correct path of java on your script.

---

### Post by duongthaiha on 2014-08-11
Thank you very much for your replies:
What i was trying to do is to follow intruction of building google or tool then this error happen during a make file.
I run 
```

make DEBUG=-g all

```
and this is the error when i run it

```

/usr/lib/jvm/java-7-openjdk-amd64/bin/javac -d objs src/com/google/ortools/constraintsolver/*.java src/gen/com/google/ortools/constraintsolver/*.java src/gen/com/google/ortools/algorithms/*.java src/gen/com/google/ortools/graph/*.java src/gen/com/google/ortools/linearsolver/*.java
/bin/sh: 1: /usr/lib/jvm/java-6-openjdk-amd64/bin/javac: not found
make: *** [lib/com.google.ortools.jar] Error 127

```

I am not familiar with make file(hopefully not yet) and found this is the only place in the make file contain javac command

```


$(LIB_DIR)/com.google.ortools.jar: \
	$(GEN_DIR)/constraint_solver/constraint_solver_java_wrap.cc \
	$(GEN_DIR)/algorithms/knapsack_solver_java_wrap.cc \
	$(GEN_DIR)/graph/graph_java_wrap.cc \
	$(GEN_DIR)/linear_solver/linear_solver_java_wrap.cc
	$(JAVAC_BIN) -d $(OBJ_DIR) $(SRC_DIR)$Scom$Sgoogle$Sortools$Sconstraintsolver$S*.java $(GEN_DIR)$Scom$Sgoogle$Sortools$Sconstraintsolver$S*.java $(GEN_DIR)$Scom$Sgoogle$Sortools$Salgorithms$S*.java $(GEN_DIR)$Scom$Sgoogle$Sortools$Sgraph$S*.java $(GEN_DIR)$Scom$Sgoogle$Sortools$Slinearsolver$S*.java
	$(JAR_BIN) cf $(LIB_DIR)$Scom.google.ortools.jar -C $(OBJ_DIR) com$Sgoogle$Sortools$S

```
Any iread please help. 
Thanks

---

### Post by steeldriver on 2014-08-11
Was the makefile created by a ./configure script? if so, there may be a ./configure option like '--with-javac=' that lets you write the correct value - try './configure --help' 

Alternatively if you can find where JAVAC_BIN is defined in the makefile you can simply edit it (although it will likely be reverted if you run ./configure again)

Either way, you should also be able to override the JAVAC_BIN variable on the make command line like

```

make DEBUG=-g JAVAC_BIN="path/to/actual/javac" all

```

or possibly
```

make DEBUG=-g JAVAC_BIN="$(which javac)" all

```

---

