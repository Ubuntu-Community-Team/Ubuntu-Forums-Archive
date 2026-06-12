---
title: "how to perform a stress test and see the ongoing performance?"
date: 2013-03-19
forum: New to Ubuntu
---

### Post by goliah88 on 2013-03-19
Hi all,

I just installed Ubuntu 12.10, and therefore i registered here to get some help with it hopefully.

I need to create a script that will test my router or any other ip, i need to load test it and see the details on another window, like cpu usage, ram, etcc.

I deed some research on the net, Ping command, and 
sudo sh stresstest.sh -h 192.168.0.1 -40

But it tells me can´t open stresstest.sh

I Am i going the right way or? i would appreciate any kind of advice. Thanks guys:P

---

### Post by Kopkins on 2013-03-19
Did you download a script for stresstest.sh? Why do you need all the details about your connection? What details are you specifically looking for. Your post seems kind of vague.

If you want to see system info like cpu ram and stuff like that, you can use conky. 
Conky can display lots if system info. Just search around for conky.

---

### Post by coldraven on 2013-03-19
GUI way
You could try in Nautilus right click stresstest.sh then Properties>Permissions>Check "Execute"
Then double click the file > Run in terminal

Terminal way
Also to run a script that is in the current folder you need to put ./ in front of it.

So if the script was in /home/joe/mytest
```
pwd
``` will tell you the present working directory
```
cd /home/joe/mytest
```change to where the script is
```
./stresstest.sh
```should run it

---

### Post by goliah88 on 2013-03-20
> **Kopkins said:**
> Did you download a script for stresstest.sh? Why do you need all the details about your connection? What details are you specifically looking for. Your post seems kind of vague.

If you want to see system info like cpu ram and stuff like that, you can use conky. 
Conky can display lots if system info. Just search around for conky.

I apply for a job as Software tester, i am gonna start a learning contract of 6 months, but before starting i need to show some basic skills, they asked me to focus on these things:

This is the kind of prodcuts that you will be asked to test:
equipment such as satellite modulators, modems and
demodulators, frequency converters and combiners, data
processors and redundancy switches.

The goal is to perform load tests on modulators / demodulators via
linux using command line Interface or snmp (Simple Network Management
Protocol).
you should be able to write some basic scripts in Linux. 
you should be able to interconnect devices to perform tests.

so how do i start please? i just need the direction and i will get to study, ps i newer had ubuntu, but i have some basics.

---

### Post by goliah88 on 2013-03-20
do you have any idea on how to perform those tasks?

---

### Post by matt_symes on 2013-03-20
Hi
> 
The goal is to perform load tests on modulators / demodulators via
linux using command line Interface or snmp (Simple Network Management
Protocol).
you should be able to write some basic scripts in Linux. 
you should be able to interconnect devices to perform tests.

Can you be more specific about what you are modulating / demodulating ?

Is it a standard modem (PPP connection) with Ethernet traffic going over it ? If so, have you checked out

```
iperf
```

Used to perform throughput tests.

```
sudo apt-get install iperf
```

then read the man pages to start with.

You'll have to be more specific as to the requirements though for a better answer from forum members.

EDIT:

Have a read of this...

[http://www.midcoast.com/~jp/snmp.html](http://www.midcoast.com/~jp/snmp.html)

Also...

```
matthew-S206:/home/matthew % apt-cache search snmpget
snmp-mibs-downloader - Install and manage Management Information Base (MIB) files
matthew-S206:/home/matthew % 
```

Kind regards

---

### Post by tgalati4 on 2013-03-20
Check out *phoronix-test-suite*.  It's a test manager that installs, runs, and uploads test data to a website.  It contains many of the standard computing performance test routines.

```
sudo apt-get install phoronix-test-suite
man phoronix-test-suite
phoronix-test-suite interactive
```

These are the categories:  (There are many tests in each category.  Enough to spend a year just running tests.)

1:  pts/audio-encoding
2:  pts/chess
3:  pts/compilation
4:  pts/compiler
5:  pts/compression
6:  pts/computational
7:  pts/computational-biology
8:  pts/cpu
9:  pts/cryptography
10: pts/daily-kernel-tracker
11: pts/daily-system-tracker
12: pts/database
13: pts/desktop-graphics
14: pts/disk
15: pts/encoding
16: pts/favorites
17: pts/gaming
18: pts/gaming-closed
19: pts/gaming-free
20: pts/gui-toolkits
21: pts/ioquake3-games
22: pts/iqc
23: pts/java
24: pts/java-opengl
25: pts/kernel
26: pts/linux-system
27: pts/memory
28: pts/mesa
29: pts/motherboard
30: pts/multicore
31: pts/netbook
32: pts/network
33: pts/nevada
34: pts/opencl
35: pts/opengl-demos
36: pts/opengl-workstation
37: pts/pts-desktop-live
38: pts/ray-tracing
39: pts/server
40: pts/unigine
41: pts/universe
42: pts/universe-cli
43: pts/universe-x
44: pts/video-encoding
45: pts/workstation
46: pts/workstation-graphics
47: pts/xrender
48: pts/system
49: pts/processor
50: pts/disk
51: pts/graphics
52: pts/memory
53: pts/network
54: pts/other

---

### Post by goliah88 on 2013-03-21
Love you guys! I know i am not really specific, but i dont know aswell what i am gonna test so i am gonna try this way and see if they accept it.
Today is my appointment, wil keep posted if i past or not :p 
thanks xx

---

### Post by matt_symes on 2013-03-21
Good luck :KS

---

