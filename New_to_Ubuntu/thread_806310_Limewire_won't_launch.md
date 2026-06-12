---
title: "Limewire won't launch"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by suomalainen on 2008-05-24
Hello Ubunteros!

I installed Limewire months ago and each time I wanted to use it it launched without dely. BUT TODAY... it doesn't even want to launch.

What can I do?

Thank you!

---

### Post by tjwoosta on 2008-05-24
open a terminal (Applications-Accessories-Terminal)

type
```
limewire
```

then post whatever it says

---

### Post by CloudFX on 2008-05-24
You need to update java.  See [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java).

To install:
> sudo apt-get update
sudo apt-get upgrade
sudo apt-get install java-common

---

### Post by suomalainen on 2008-05-25
THIS IS WHAT I GET WHEN I TYPE "LIMEWIRE"

Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.7.0]
Configuring environment...
Loading LimeWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b928f130e11, pid=6891, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /tmp/hs_err_pid6891.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
./runLime.sh: line 124:  6891 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar LimeWire.jar $ARGUMENTS

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.5+)
The version of Java in your PATH is:
java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b21)
IcedTea 64-Bit Server VM (build 1.7.0-b21, mixed mode)

---

### Post by tjwoosta on 2008-05-26
hmm..  looks like there might be something wrong with your java

did you try what was posted above?

did you just recently install icedtea?

last time i tried installing icedtea the same thing happened to my limewire (i ended up just removing icedtea and installing openjdk)

---

