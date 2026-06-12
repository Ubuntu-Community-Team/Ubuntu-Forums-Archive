---
title: "[EclipseME]: Debugger crashes"
date: 2008-09-22
forum: Programming Talk
---

### Post by pete78 on 2008-09-22
In Eclipse 3.2.2 with EclipseME 1.7.9 I develop MIDlets under Ubuntu. My problem is, that debugging does not work. After it says "Connection received." it pauses and crashes with the error "received signal SIGSEGV" followed by native stacks. The error log of the native stacks is different on every crash.
Please give me some help.

Thanks and regards
Pete

Example console output:
Connecting to 127.0.0.1 on port 2800
Waiting for debugger on port 58104
Waiting for KVM...
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-wenquanyi-wenquanyi zenhei-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-sazanami-gothic-medium-r-normal--*-140-*-*-c-*-jisx0208.1983-0" to type FontStruct
Warning: Cannot convert string "-baekmuk-gulim-medium-r-normal--*-140-*-*-c-*-ksc5601.1987-0" to type FontStruct
Connection received.
Running with storage root /home/pete/j2mewtk/2.5.2/appdb/DefaultColorPhone
Running with locale: de_CH.UTF-8
Running in the maximum security domain
Connected to KVM
received signal SIGSEGV
Method............: b7ae7874 'com/sun/midp/midletsuite/ManifestProperties$UTF8ManifestStream.read (virtual)' 
Stack Chunk.......: b51cc634
Frame Pointer.....: b51cc720
Bytecode..........: b7cffe78
Previous Frame....: b51cc6f4
Previous IP.......: b7ce0722 (offset -1211234654)
Frame size........: 3 (1 arguments, 2 local variables)
Argument[0].......: 61
Local[1]..........: 61
Local[2]..........: 0

---

### Post by tinny on 2008-09-22
Hi

Ive had problems like this before.

Did you follow the EclipseME setup guide? 

The debug config specifically:

[http://eclipseme.org/docs/configuring.html#step4](http://eclipseme.org/docs/configuring.html#step4)

Also what Java runtime / JDK are you using?

```

java -version
javac -version

```

Also what Java runtime is Eclipse setup to use? 

“Window” > “Preferences” > “Installed JREs”

---

### Post by pete78 on 2008-09-22
Hi tinny

Thank you for your help :-) .
Yes, I followed the setup guide and did the settings in step4.

Versions:
$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)
$ javac -version
javac 1.6.0_06

Eclipse:
JRE type: Standard VM
JRE name: java-6-sun-1.6.0.06
JRE home directory: /usr/lib/jvm/java-6-sun-1.6.0.06

Does this give you hints regarding the problem?

---

### Post by tinny on 2008-09-22
> **pete78 said:**
> Hi tinny

Thank you for your help :-) .
Yes, I followed the setup guide and did the settings in step4.

Versions:
$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)
$ javac -version
javac 1.6.0_06

Eclipse:
JRE type: Standard VM
JRE name: java-6-sun-1.6.0.06
JRE home directory: /usr/lib/jvm/java-6-sun-1.6.0.06

Does this give you hints regarding the problem?

Hmmmm, no that looks fine to me.

Quick question, have you installed Frostwore or Limewire lately? (May be related...)

---

### Post by tinny on 2008-09-22
Also...

Id try reinstalling the Java environment (Purging it).

```

sudo apt-get remove --purge sun-java6*
sudo apt-get install sun-java6*

```

---

### Post by pete78 on 2008-09-23
Hi tinny

Thank you! I reinstalled Java and also Eclipse and EclipseME and now it works :).

Kind regards
Pete

---

### Post by pinturic on 2008-09-24
Hi,

I have had the same problem; I solved it at the same manner, i.e., uninstalling and reinstalling. Now after some days I am having the same problem again; reinstalling eclipse+java+j2me every two weeks is not feasible.
Did anyone find a solution for this problem?

---

