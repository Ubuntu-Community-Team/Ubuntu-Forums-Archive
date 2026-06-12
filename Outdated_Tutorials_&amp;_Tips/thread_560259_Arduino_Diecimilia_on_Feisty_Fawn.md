---
title: "Arduino Diecimilia on Feisty Fawn"
date: 2007-09-26
forum: Outdated Tutorials &amp; Tips
---

### Post by sedition on 2007-09-26
.: ubuntu Diecimila :.

This howto was written using Ubuntu Feisty Fawn 32-bit and arduino-0009.

* Open Synaptic and install the following:
sun-java5-bin
sun-java5-jdk
avr-libc
gcc-avr
librxtx-java

* REMOVE brltty (will cause conflicts)

*** NOTE: removing brltty will possibly break your accessibility options if utilized

* Download the arduino software: [http://www.arduino.cc/en/Main/Software](http://www.arduino.cc/en/Main/Software)
* Enter the extracted arduino folder, gedit and replace the launcher (arduino)

* rename these files within arduino-0009/lib/ (they cause conflicts with  librxtx-java):
RXTXcomm.jar
librxtxSerial.so
---to---
RXTXcomm.jar.BAK
librxtxSerial.so.BAK

* Open your arduino launcher with the text editor and replace the contents with the following (resolves conflicts with  librxtx-java):

```
 #!/bin/sh

# Original: CLASSPATH=java/lib/rt.jar:lib:lib/build:lib/pde.jar:lib/core.jar:lib/antlr.jar:lib/oro.jar:lib/registry.jar:lib/mrj.jar:lib/RXTXcomm.jar
CLASSPATH=java/lib/rt.jar:lib:lib/build:lib/pde.jar:lib/core.jar:lib/antlr.jar:lib/oro.jar:lib/registry.jar:lib/mrj.jar:/usr/share/java/RXTXcomm.jar
export CLASSPATH

# put the directory where this file lives in the front of the path, because
# that directory also contains jikes, which we will need at runtime.
#
PATH=`pwd`/tools:${PATH}
export PATH

# put the directory with the native RXTX libs in the library path
# Original: LD_LIBRARY_PATH=`pwd`/lib:${LD_LIBRARY_PATH}
LD_LIBRARY_PATH=/usr/lib:${LD_LIBRARY_PATH}
export LD_LIBRARY_PATH

java processing.app.Base
```Open a terminal and type "sudo update-alternatives --config java" and press enter. Type the number of the option which has "java-1.5.0-sun" in it and press enter.
***NOTE: In order to get started programming, be sure to select in the arduino program: Tools -> Serial Port and select /dev/ttyUSB0

References:
[http://www.arduino.cc/playground/Linux/Ubuntu](http://www.arduino.cc/playground/Linux/Ubuntu)
[http://www.arduino.cc/en/Main/Software](http://www.arduino.cc/en/Main/Software)

---

### Post by Godzig on 2007-10-28
Thanks, 
This tutorial also worked with gutsy and java 1.6.0_03

---

### Post by 23meg on 2007-11-14
Gutsy has brltty disabled by default.

---

### Post by lucasrossi on 2007-11-15
It was useful! It' working!
Let me say that arduino didn't work with 64 bit version.. I installed the 64 bit but I prefferred  reinstalling 32 rather than becoming crazy once again:( .. Already enough problems on my computer
Bye

---

### Post by regomodo on 2007-11-20
sorry didn't work for me. It is not seeing my Arduino that is plugged in.
lsusb sees it and so does kinfocenter. I've looked in /dev/ for a probable port but i can't see one.

---

### Post by BlueSun on 2007-11-24
[FONT="Verdana"]
**Arduino-0010 Installed and Running on 7.10 Gutsy AMD64**

I just followed the above instructions *to the letter* on my new Kubuntu Gutsy 64-bit installation.  Everything is functioning properly and I've compiled and installed a test sketch on my Arduino NG.  No software tweaks were necessary -- I think you just need to make sure you get the 64-bit version of the Java 1.5 JRE.

To get the Arduino IDE running once everything is installed and configured, simply open a terminal in your "arduino-0010" directory and type:

```

./arduino

```

[/FONT]

---

### Post by Kabatwa on 2007-12-07
Thanks for this. I kind of got my arduinoBT working under Feisty. I could compile thanks to your tutorial but I couldn't upload for some reason. I think it's something to do with it being serial, bluetooth. I found a way around it by uploading via CLI using uisp which is in tools folder of the arduino folder. Haven't tried under Gutsy yet.
Thanks once again, Tim

---

### Post by ktheking on 2008-02-07
Ubuntu 7.10 Alternate - command line version (No GUI) + arduino ( ATMEGA168 ) USB

This is how I get it working (with step by step instructions in detail) : [http://www.arduino.cc/cgi-bin/yabb2/YaBB.pl?num=1202054885](http://www.arduino.cc/cgi-bin/yabb2/YaBB.pl?num=1202054885) (reply nr 9)


Advantage is that you end up installing Ubuntu with the least of possible options ,so Ubuntu can run a less powerfull system.
Also there is no need to install java with this setup.

---

### Post by TheOther1 on 2008-05-04
Seditions instructions worked on my Hardy Heron 64-bit install.  I used arduino-0011.  Works great!

---

### Post by cmdowns on 2008-05-05
Hello, I'm a Linux noob and a new Ubuntu user working with Gutsy Gibbon. I'm attempting to install the Arduino IDE on my laptop. I'm trying to follow the instruction in the first post in this thread, but my knowledge fails me when I get to this part:
> **sedition said:**
> 
* Enter the extracted arduino folder, gedit and replace the launcher (arduino)


I'm sure this is something incredibly basic, but I'm at a loss. I have downloaded and extracted the arduino app, but I don't really understand what the OP means by "gedit and replace the launcher (arduino)". Could some benevolent guru spell this out for me please? I will repay you with praise and eternal gratitude (I know, what a deal!).

---

### Post by xolot1 on 2008-05-12
i just installed arduino 0011 on hardy.
i installed the packages suggested, but i did not need to edit the launcher script. i could immediately run it:

```
./arduino
```

---

### Post by Keen101 on 2008-06-07
I'm not a linux guru, but i got the Arduino software to run on my 8.04 Heron system the other day. 

[http://www.arduino.cc/playground/Learning/Linux](http://www.arduino.cc/playground/Learning/Linux)

Step one: get  java runtime (jre. I searched for "jre" in synaptic package manager, and installed the "openjdk-6-jre" packages. Works great.

Step two: install the "gcc-avr" tools. also, the "binutils-avr", and the "avrdude" packages from the repositories. also the "acr-libc" package.

Step three:  searched for the "brltty" package in synaptic, and removed it just in case.

Step four: copy and extract the arduino software to my desktop. Open the folder. And double click on the "arduino" script file. When prompted what to do click "run"

hope that helps.

-Andrew
-keen101

---

