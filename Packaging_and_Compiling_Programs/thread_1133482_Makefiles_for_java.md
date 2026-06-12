---
title: "Makefiles for java"
date: 2009-04-23
forum: Packaging and Compiling Programs
---

### Post by chiefbutz on 2009-04-23
I am currently working to use a Makefile to compile a project I created in Java. The makefile works and it compiles, however when I run the file only the first of the commands that is dependent upon the line for my executable is shown as running.

This is my make file:
```
JFLAGS = -nowarn
JC = javac
.SUFFIXES: .java .class
.java.class:
	$(JC) $(JFLAGS) $*.java

CLASSES = ALU.class \
			bit_16.class \
			bit_8.class \
			bit_flags.class \
			bit.class \
			Condition.class \
			Control.class \
			GLOBAL.class \
			InstrDecoder.class \
			Main.class \
			Register.class 
			
8085a : $(CLASSES)
	gcj -o 8085a --main=Main $(CLASSES)

ALU.class : ALU.java
	$(JC) $(JFLAGS) ALU.java

bit_16.class : bit_16.java
	$(JC) $(JFLAGS) bit_16.java

bit_8.class : bit_8.java
	$(JC) $(JFLAGS) bit_8.java

bit_flags.class : bit_flags.java
	$(JC) $(JFLAGS) bit_flags.java

bit.class : bit.java
	$(JC) $(JFLAGS) bit.java

Condition.class : Condition.java
	$(JC) $(JFLAGS) Condition.class

Control.class : Control.java
	$(JC) $(JFLAGS) -nowarn Control.java

GLOBAL.class : GLOBAL.java
	$(JC) $(JFLAGS) GLOBAL.java

InstrDecoder.class : InstrDecoder.java
	$(JC) $(JFLAGS) InstrDecoder.java

Main.class : Main.java
	$(JC) $(JFLAGS) Main.java

Register.class : Register.java
	$(JC) $(JFLAGS) Register.java
```

When I run it I get this:
> javac -nowarn ALU.java
gcj -o 8085a --main=Main ALU.class bit_16.class bit_8.class bit_flags.class bit.class Condition.class Control.class GLOBAL.class InstrDecoder.class Main.class Register.class

I know I am being a little picky, but I remember when I would do this for C++ the make file would output a lot more and it is nice to see what all it is outputting. Thanks for the help.

---

