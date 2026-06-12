---
title: "Spring Project Compilation issues"
date: 2010-02-12
forum: Packaging and Compiling Programs
---

### Post by Soldred on 2010-02-12
I've been trying to compile the most recent version of the Spring RTS. Most of the dependencies I've been able to resolve, however I keep getting this error: 

warning: No Java includes found!
warning: Java AI Interface will not be built!

I've tried installing many different Java development packages, but I'm obviously missing something. I'd appreciate any ideas. 
Thanks in advance.

---

### Post by SevenMachines on 2010-02-13
do you have default-jdk installed?
bear in mind, i believe spring has a ppa with prebuilt binaries for versions of ubuntu (its included in ubuntu as of lucid, the next release)

---

### Post by Soldred on 2010-02-13
Thanks for the help, all the dependencies seem to be solved however I am still getting this error after it starts building:

sh: Syntax error: "(" unexpected
os.chdir('AI/Interfaces/Java/bin')
awk -v SPRING_SOURCE_DIR=/home/evan/Desktop/spring_0.81.1.3 (2) -v INTERFACE_SOURCE_DIR=/home/evan/Desktop/spring_0.81.1.3 (2)/AI/Interfaces/Java/src/main/java -v GENERATED_SOURCE_DIR=/home/evan/Desktop/spring_0.81.1.3 (2)/build/AI/Interfaces/Java/src-generated/main/java -f jna_wrappCallback.awk -f /home/evan/Desktop/spring_0.81.1.3 (2)/AI/Wrappers/CUtils/bin/common.awk -f /home/evan/Desktop/spring_0.81.1.3 (2)/AI/Wrappers/CUtils/bin/commonDoc.awk /home/evan/Desktop/spring_0.81.1.3 (2)/rts/ExternalAI/Interface/SSkirmishAICallback.h
sh: Syntax error: "(" unexpected
os.chdir('/home/evan/Desktop/spring_0.81.1.3 (2)')
scons: *** [build/AI/Interfaces/Java/src-generated/main/java/com/springrts/ai/AICallback.java] Error 2
scons: building terminated because of errors.



And to answer your question, I have not been able to find any 64 bit debian packages for the newest spring engine.

---

### Post by SevenMachines on 2010-02-13
spring has its own [ubuntu ppa]("https://launchpad.net/%7Espring/+archive/ppa/+packages") that includes amd64 builds 

the compiling error looks like a sh/bash/dash incompatibility i'd guess, i dont get it myself.
you could try altering the Makefile,
SHELL = /bin/sh

to use either of bash or dash and see if that helps if you still need to compile it

---

### Post by Soldred on 2010-02-13
Great! The repository had just what I needed. I might try your suggestion about compiling just to see if it works. Thanks

---

