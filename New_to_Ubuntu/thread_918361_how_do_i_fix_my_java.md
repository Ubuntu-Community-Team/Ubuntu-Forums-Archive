---
title: "how do i fix my java"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by imgkg on 2008-09-12
my java intallation has messed up any ideas how to fix it any java application i try to run it gives me error > :~$ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_07]
Configuring environment...
Loading LimeWire:
./runLime.sh: line 124: 7689 Segmentation fault ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons .logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar LimeWire.jar $ARGUMENTS

************************************************** ****************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.5+)
The version of Java in your PATH is:
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

:~$ 

---

### Post by jamesstansell on 2008-09-12
That output looks perfect, except for the "Segmentation fault" message.

Is there a logfile that has more information?  If not then perhaps you can enable it?

You have similar problems with other java programs?

I assume it's only Java where you see crashes like this?

"java -version" does run correctly, right?

---

### Post by imgkg on 2008-09-13
yes its only with java i am trying to detect with other java applications have been trying to install and remove from past 12 hours lime wire crashing ,frost wire crashing, i dont know from where to get the log file

---

