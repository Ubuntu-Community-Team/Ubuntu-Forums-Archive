---
title: "Java is unusable on Ubuntu"
date: 2006-08-16
forum: Programming Talk
---

### Post by coconut on 2006-08-16
Is anyone having problem with Java on Ubuntu, or am I the only one?

We have different distros, running Tomcat/Jboss/Eclipse, and the only distro which is causing nasty problem has been Ubuntu. On Ubuntu, Java (the JVM) crashed all day long. We are running the same version of Java applications, along with the same version of JRE/JDK on different distros, other distros are just fine, but JVM keeps on crashing on Ubuntu. 

Our application server (JBoss) on Fedora has logged an uptime of 279 days without any problem, and that's quite a busy server. On Ubuntu, no Java app can run more than a few hours without crashing. 

I'm running Ubuntu 6.06, with a few security patches, no kernel upgrade or anything like that. Java 1.4.2_11, 1.5.0_06, 1.5.0_07, 1.5.0._08, all crash on Ubuntu.

I like the Ubuntu desktop, it's my main desktop and development station, but it's unusable for developing Java software.

Since we use the same version of Java software everywhere, and the only place where it crashed is on Ubuntu, I'm suspecting the libraries on Ubuntu are somewhat incompatible with Java.

Anyone has experience anything similar? Any solution for that? I'm having the Sun JVM crash reporting page open constantly on my desktop, with 20 reports per day, so many that I'm tired of reporting now. Ubuntu 5.10 also had the same problem. I've been using Ubuntu since 4.06, the whole line of Ubuntu has had problem with Java all along. But because I had other desktop for Java dev, it wasn't so bad, now that I use Ubuntu only, this is so nasty that I'm thinking of dropping Ubuntu now.

Anyone with any experience, please help.

thanks

---

### Post by virtual_void on 2006-08-17
My experience is that the java VM included in Ubuntu is quite unstable. Download either IBM:s or Sun:s java environment. I'm running Kubuntu 6.06 for the x86_64 architecture and no java enabled website worked as it should with the included JVM, they all work fine now with the 1.5.0 JVM from IBM.

---

### Post by LordHunter317 on 2006-08-17
He said he's running the Sun JVM.  Expecting the GNU stuff to be crappy is normal.

However, no one can tell you what's up because you haven't posted the bloody crashes.

---

### Post by chonger on 2006-08-17
First, how to debug java issues

[http://java.sun.com/j2se/1.5/pdf/jdk50_ts_guide.pdf](http://java.sun.com/j2se/1.5/pdf/jdk50_ts_guide.pdf) 

I am sure this is not a problem caused by Ubuntu. I'm about to set up a pretty complicated Java application on an Ubuntu box. I will definitely share my experiences with you.

What kind of crashses are you seeing? Do you get Hotspot errors? Or do you get some kind of error like OutOfMemoryError? Have you tried changing the compiler (running as -client instead of -server)? 

When people talk about Java crashing, they sometimes refer to a Hotspot error when the process actually dies. Other times, they refer to an error that causes the application to fail, but the Java process is still running. 

In a Hotspot error, you should be getting a hs_err_pid%p.log file, which you can use to examine the error (and find out what's the cause).

If not a Hotspot error you can do some useful debugging.

I hope you don't give up Ubuntu because of this. There must be some way to get Java to work on Ubuntu. Maybe the cause is in default system configuration. Maybe something in /etc/security/limits.conf needs to be raised.

---

### Post by BreddS on 2006-08-18
"I don't know how I can execute an event of Javascript into a link in a program in Perl. 
This event of JavaScript have executed a function that return a HTML page. 
Anybody know how I can it? 

Is it possible do it this?: 
$datos=$datos.""<a href='"" . $me . ""?C=OFERTAS2&EMPRESA="".$empresa_param.""&NREF="".$nref.""' onMouseOver=""linkFTecnica(nref2)"">""; 

What is bad in this code? 

Thank you very much. "

---

### Post by yaaarrrgg on 2006-08-18
> **BreddS said:**
> "I don't know how I can execute an event of Javascript into a link in a program in Perl. 
This event of JavaScript have executed a function that return a HTML page. 
Anybody know how I can it? 

Is it possible do it this?: 
$datos=$datos.""<a href='"" . $me . ""?C=OFERTAS2&EMPRESA="".$empresa_param.""&NREF="".$nref.""' onMouseOver=""linkFTecnica(nref2)"">""; 

What is bad in this code? 

Thank you very much. "

Why are you using double double quotes?  
also, if nref2 is a string, you will need to wrap it in single quotes. 
also, i suppose you are closing the <a> tag somewhere else?

Something like this should work:

```

$datos="$datos <a href=\"$me?C=OFERTAS2&EMPRESA=$empresa_param&NREF=$nref\" onMouseOver=\"linkFTecnica('nref2')\">"; 

```

btw... you should always start a new thread for a new question.      :)

edit: also if nref2 is a perl variable, you need the $, for example $nref2

---

### Post by coconut on 2006-08-19
> **LordHunter317 said:**
> However, no one can tell you what's up because you haven't posted the bloody crashes.

I didn't put in the hs_err_pid***.log file coz I'm not sure if it is of any help to anyone, besides Sun's folks who work on the jvm itself. 

If anyone can help figure out the problem based on those files, I'd be glad to provide 20 to 30 of these on a daily basis, and I'd be the first one to volunteer to help testing. I submit about 20 crash reports to Sun per day, but I'm not sure this is going anywhere, since I've been doing this for quite a long time (actually since I started switching to Ubuntu).

Another reason I didn't post is, I don't think this forum allows to post anything as long as a hs_err_pid***.log file.

---

### Post by coconut on 2006-08-19
Anyways, I'm cutting up the hs_err_pid***.log file into pieces, and post them here one by one to get around the post length limit:

Part 1:

> 
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb147d9a1, pid=5130, tid=2215979952
#
# Java VM: Java HotSpot(TM) Server VM (1.5.0_08-b03 mixed mode)
# Problematic frame:
# v  ~BufferBlob::vtable chunks
#

---------------  T H R E A D  ---------------

Current thread (0x081d6f68):  JavaThread "ModalContext" [_thread_in_Java, id=11277]

siginfo:si_signo=11, si_errno=0, si_code=1, si_addr=0x00740089

Registers:
EAX=0x00740049, EBX=0x8e0e0bb8, ECX=0x92138390, EDX=0x9210df98
ESP=0x84151d14, EBP=0x8e0cbee0, ESI=0xaef2faa4, EDI=0x00000000
EIP=0xb147d9a1, CR2=0x00740089, EFLAGS=0x00210297

Top of Stack: (sp=0x84151d14)
0x84151d14:   b1a03c80 92138390 8e0cbe40 8e0dcaa0
0x84151d24:   00001042 84151d70 afd2ce48 000000b4
0x84151d34:   b14810c3 84151d70 afd2ce48 84151d70
0x84151d44:   84151d48 b143ca13 92138390 8e0cbee0
0x84151d54:   84151d54 aef2faa4 84151dbc aef321a8
0x84151d64:   afd2ce48 aef2ffc8 84151db8 84151ddc
0x84151d74:   b143cb6b 92138390 00000007 00000003
0x84151d84:   92173158 00000029 00000018 93726e08 

Instructions: (pc=0xb147d9a1)
0xb147d991:   00 00 00 09 00 00 00 8b 41 04 8b 80 24 01 00 00
0xb147d9a1:   8b 58 40 ff e3 00 00 00 00 00 00 00 00 00 00 09 

Stack: [0x840d2000,0x84153000),  sp=0x84151d14,  free space=511k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
v  ~BufferBlob::vtable chunks


---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
=>0x081d6f68 JavaThread "ModalContext" [_thread_in_Java, id=11277]
  0x0812c100 JavaThread "Worker-60" [_thread_blocked, id=10377]
  0x09960600 JavaThread "Worker-52" [_thread_blocked, id=9782]
  0x094f4bb0 JavaThread "Java indexing" daemon [_thread_blocked, id=5155]
  0x08216ee0 JavaThread "Start Level Event Dispatcher" daemon [_thread_blocked, id=5145]
  0x083d4ec0 JavaThread "Framework Event Dispatcher" daemon [_thread_blocked, id=5144]
  0x083d4638 JavaThread "State Data Manager" daemon [_thread_blocked, id=5143]
  0x0810c440 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=5138]
  0x0810afb8 JavaThread "CompilerThread1" daemon [_thread_in_native, id=5137]
  0x08109f58 JavaThread "CompilerThread0" daemon [_thread_blocked, id=5136]
  0x08108e28 JavaThread "AdapterThread" daemon [_thread_blocked, id=5135]
  0x08107ff0 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=5134]
  0x080e8ac0 JavaThread "Finalizer" daemon [_thread_blocked, id=5133]
  0x080e85d0 JavaThread "Reference Handler" daemon [_thread_blocked, id=5132]
  0x0805cc90 JavaThread "main" [_thread_in_native, id=5130]

Other Threads:
  0x080e6118 VMThread [id=5131]
  0x0810d8e0 WatcherThread [id=5139]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 26304K, used 14414K [0x8d370000, 0x8eff0000, 0x90c50000)
  eden space 23424K,  58% used [0x8d370000, 0x8e0eae70, 0x8ea50000)
  from space 2880K,  21% used [0x8ed20000, 0x8edb8a80, 0x8eff0000)
  to   space 2880K,   0% used [0x8ea50000, 0x8ea50000, 0x8ed20000)
 tenured generation   total 233024K, used 89927K [0x90c50000, 0x9efe0000, 0xad370000)
   the space 233024K,  38% used [0x90c50000, 0x96421e90, 0x96422000, 0x9efe0000)
 compacting perm gen  total 43776K, used 42740K [0xad370000, 0xafe30000, 0xb1370000)
   the space 43776K,  97% used [0xad370000, 0xafd2d2a0, 0xafd2d400, 0xafe30000)
No shared spaces configured.



---

### Post by coconut on 2006-08-19
Part 2:

> 
Dynamic libraries:
08048000-08057000 r-xp 00000000 03:01 1034150    /home/csp/bin/jdk1.5.0_08/bin/java
08057000-08059000 rwxp 0000e000 03:01 1034150    /home/csp/bin/jdk1.5.0_08/bin/java
08059000-09fb6000 rwxp 08059000 00:00 0          [heap]
7e000000-7e0fc000 rwxp 7e000000 00:00 0 
7e0fc000-7e100000 ---p 7e0fc000 00:00 0 
7e100000-7e121000 rwxp 7e100000 00:00 0 
7e121000-7e200000 ---p 7e121000 00:00 0 
7e200000-7e2f3000 rwxp 7e200000 00:00 0 
7e2f3000-7e300000 ---p 7e2f3000 00:00 0 
7e300000-7e3f7000 rwxp 7e300000 00:00 0 
7e3f7000-7e400000 ---p 7e3f7000 00:00 0 
7e400000-7e4f1000 rwxp 7e400000 00:00 0 
7e4f1000-7e500000 ---p 7e4f1000 00:00 0 
7e500000-7e5ff000 rwxp 7e500000 00:00 0 
7e5ff000-7e600000 ---p 7e5ff000 00:00 0 
7e600000-7e6fd000 rwxp 7e600000 00:00 0 
7e6fd000-7e700000 ---p 7e6fd000 00:00 0 
7e800000-7e8fb000 rwxp 7e800000 00:00 0 
7e8fb000-7e900000 ---p 7e8fb000 00:00 0 
7ea00000-7eafa000 rwxp 7ea00000 00:00 0 
7eafa000-7eb00000 ---p 7eafa000 00:00 0 
83500000-835f9000 rwxp 83500000 00:00 0 
835f9000-83600000 ---p 835f9000 00:00 0 
83600000-83669000 rwxp 83600000 00:00 0 
83669000-83700000 ---p 83669000 00:00 0 
83700000-837f9000 rwxp 83700000 00:00 0 
837f9000-83800000 ---p 837f9000 00:00 0 
83800000-838f9000 rwxp 83800000 00:00 0 
838f9000-83900000 ---p 838f9000 00:00 0 
83900000-839f9000 rwxp 83900000 00:00 0 
839f9000-83a00000 ---p 839f9000 00:00 0 
83a00000-83af9000 rwxp 83a00000 00:00 0 
83af9000-83b00000 ---p 83af9000 00:00 0 
83b00000-83bf9000 rwxp 83b00000 00:00 0 
83bf9000-83c00000 ---p 83bf9000 00:00 0 
83c49000-83c4c000 rwxp 83c49000 00:00 0 
83c4c000-83cca000 rwxp 83c4c000 00:00 0 
83cca000-83ccd000 rwxp 83cca000 00:00 0 
83ccd000-83d4b000 rwxp 83ccd000 00:00 0 
83d4b000-83d4e000 rwxp 83d4b000 00:00 0 
83d4e000-83dcc000 rwxp 83d4e000 00:00 0 
83dcc000-83dcf000 rwxp 83dcc000 00:00 0 
83dcf000-83e4d000 rwxp 83dcf000 00:00 0 
83e4d000-83e50000 rwxp 83e4d000 00:00 0 
83e50000-83ece000 rwxp 83e50000 00:00 0 
83ece000-83ed1000 rwxp 83ece000 00:00 0 
83ed1000-83f4f000 rwxp 83ed1000 00:00 0 
83f4f000-83f52000 rwxp 83f4f000 00:00 0 
83f52000-83fd0000 rwxp 83f52000 00:00 0 
83fd0000-83fd3000 rwxp 83fd0000 00:00 0 
83fd3000-84051000 rwxp 83fd3000 00:00 0 
84051000-84054000 rwxp 84051000 00:00 0 
84054000-840d2000 rwxp 84054000 00:00 0 
840d2000-840d5000 ---p 840d2000 00:00 0 
840d5000-84153000 rwxp 840d5000 00:00 0 
84153000-84156000 rwxp 84153000 00:00 0 
84156000-841d4000 rwxp 84156000 00:00 0 
841d4000-841d7000 rwxp 841d4000 00:00 0 
841d7000-84255000 rwxp 841d7000 00:00 0 
84255000-84258000 rwxp 84255000 00:00 0 
84258000-842d6000 rwxp 84258000 00:00 0 
842d6000-842d9000 ---p 842d6000 00:00 0 
842d9000-84357000 rwxp 842d9000 00:00 0 
84357000-8435a000 ---p 84357000 00:00 0 
8435a000-843d8000 rwxp 8435a000 00:00 0 
843d8000-857aa000 r-xp 00000000 03:01 249557     /usr/share/fonts/truetype/arphic/uming.ttf
857aa000-85f14000 r-xp 00000000 03:01 249577     /usr/share/fonts/truetype/kochi/kochi-gothic-subst.ttf
85f14000-867fa000 r-xp 00000000 03:01 328097     /usr/share/icons/gnome/icon-theme.cache
867fa000-8696f000 r-xp 00000000 03:01 332093     /usr/share/icons/Tango/icon-theme.cache
8696f000-869c0000 r-xp 00000000 03:01 332091     /usr/share/icons/Tangerine/icon-theme.cache
869c0000-86b00000 r-xp 00000000 03:01 332079     /usr/share/icons/Human/icon-theme.cache
86b00000-86bf6000 rwxp 86b00000 00:00 0 
86bf6000-86c00000 ---p 86bf6000 00:00 0 
86c7d000-86c80000 rwxp 86c7d000 00:00 0 
86c80000-86cfe000 rwxp 86c80000 00:00 0 
86cfe000-86d01000 rwxp 86cfe000 00:00 0 
86d01000-86d7f000 rwxp 86d01000 00:00 0 
86d7f000-86d82000 rwxp 86d7f000 00:00 0 
86d82000-86ef9000 rwxp 86d82000 00:00 0 
86ef9000-86f00000 ---p 86ef9000 00:00 0 
86f7f000-86f82000 rwxp 86f7f000 00:00 0 
86f82000-87200000 rwxp 86f82000 00:00 0 
87200000-873fd000 rwxp 87200000 00:00 0 
873fd000-87400000 ---p 873fd000 00:00 0 
87473000-87476000 rwxp 87473000 00:00 0 
87476000-874f4000 rwxp 87476000 00:00 0 
87500000-875fd000 rwxp 87500000 00:00 0 
875fd000-87600000 ---p 875fd000 00:00 0 
8762b000-8762e000 rwxp 8762b000 00:00 0 
8762e000-876ac000 rwxp 8762e000 00:00 0 
876ac000-876af000 rwxp 876ac000 00:00 0 
876af000-8772d000 rwxp 876af000 00:00 0 
8772d000-87750000 r-xs 00000000 03:01 6489106    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.ltk.ui.refactoring_3.1.1.jar
87750000-87755000 r-xp 00000000 03:01 396998     /usr/share/locale-langpack/en_GB/LC_MESSAGES/file-roller.mo
87755000-877be000 r-xs 00000000 03:01 6489066    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.compare_3.1.1.jar
877be000-878e4000 r-xs 00000000 03:01 6488684    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.team.cvs.ui_3.1.1.jar
878e4000-878eb000 r-xp 00000000 03:01 397092     /usr/share/locale-langpack/en_GB/LC_MESSAGES/totem.mo
878eb000-87901000 r-xs 00000000 03:01 6489083    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.ant.core_3.1.1.jar
87901000-881e7000 r-xp 00000000 03:01 328097     /usr/share/icons/gnome/icon-theme.cache
881e7000-8835c000 r-xp 00000000 03:01 332093     /usr/share/icons/Tango/icon-theme.cache
8835c000-883ad000 r-xp 00000000 03:01 332091     /usr/share/icons/Tangerine/icon-theme.cache
883ad000-884ed000 r-xp 00000000 03:01 332079     /usr/share/icons/Human/icon-theme.cache
884ed000-884fc000 r-xp 00000000 03:01 397006     /usr/share/locale-langpack/en_GB/LC_MESSAGES/gedit.mo
884fc000-88503000 r-xp 00000000 03:01 34397      /usr/lib/libfam.so.0.0.0
88503000-88504000 rwxp 00006000 03:01 34397      /usr/lib/libfam.so.0.0.0
88507000-8850b000 r-xp 00000000 03:01 1559674    /lib/tls/i686/cmov/libnss_dns-2.3.6.so
8850b000-8850c000 rwxp 00003000 03:01 1559674    /lib/tls/i686/cmov/libnss_dns-2.3.6.so
8850c000-88510000 r-xp 00000000 03:01 397014     /usr/share/locale-langpack/en_GB/LC_MESSAGES/glib20.mo
88510000-885c0000 r-xp 00000000 03:01 34272      /usr/lib/libasound.so.2.0.0
885c0000-885c5000 rwxp 000af000 03:01 34272      /usr/lib/libasound.so.2.0.0
885c5000-885fb000 r-xp 00000000 03:01 34340      /usr/lib/libdbus-1.so.2.0.0
885fb000-885fc000 rwxp 00036000 03:01 34340      /usr/lib/libdbus-1.so.2.0.0
885fc000-885ff000 r-xp 00000000 03:01 34550      /usr/lib/libgpg-error.so.0.1.4
885ff000-88600000 rwxp 00002000 03:01 34550      /usr/lib/libgpg-error.so.0.1.4
88600000-88647000 r-xp 00000000 03:01 34430      /usr/lib/libgcrypt.so.11.2.1
88647000-8864c000 rwxp 00047000 03:01 34430      /usr/lib/libgcrypt.so.11.2.1
8864c000-8865b000 r-xp 00000000 03:01 34888      /usr/lib/libtasn1.so.2.0.17
8865b000-8865c000 rwxp 0000f000 03:01 34888      /usr/lib/libtasn1.so.2.0.17
8865c000-88671000 r-xp 00000000 03:01 34183      /usr/lib/libICE.so.6.3.0
88671000-88672000 rwxp 00014000 03:01 34183      /usr/lib/libICE.so.6.3.0
88672000-88674000 rwxp 88672000 00:00 0 


---

### Post by coconut on 2006-08-19
Part 3:

> 
88674000-8867b000 r-xp 00000000 03:01 34199      /usr/lib/libSM.so.6.0.0
8867b000-8867c000 rwxp 00007000 03:01 34199      /usr/lib/libSM.so.6.0.0
8867c000-8869a000 r-xp 00000000 03:01 34672      /usr/lib/libjpeg.so.62.0.0
8869a000-8869b000 rwxp 0001d000 03:01 34672      /usr/lib/libjpeg.so.62.0.0
8869b000-886a5000 r-xp 00000000 03:01 34512      /usr/lib/libgnome-keyring.so.0.0.1
886a5000-886a6000 rwxp 00009000 03:01 34512      /usr/lib/libgnome-keyring.so.0.0.1
886a6000-886fd000 r-xp 00000000 03:01 34307      /usr/lib/libbonoboui-2.so.0.0.0
886fd000-88700000 rwxp 00056000 03:01 34307      /usr/lib/libbonoboui-2.so.0.0.0
88700000-887fa000 rwxp 88700000 00:00 0 
887fa000-88800000 ---p 887fa000 00:00 0 
88800000-88900000 rwxp 88800000 00:00 0 
88901000-88904000 r-xp 00000000 03:01 34195      /usr/lib/libORBitCosNaming-2.so.0.1.0
88904000-88905000 rwxp 00003000 03:01 34195      /usr/lib/libORBitCosNaming-2.so.0.1.0
88905000-88919000 r-xp 00000000 03:01 34270      /usr/lib/libart_lgpl_2.so.2.3.17
88919000-8891a000 rwxp 00013000 03:01 34270      /usr/lib/libart_lgpl_2.so.2.3.17
8891a000-88942000 r-xp 00000000 03:01 34526      /usr/lib/libgnomecanvas-2.so.0.1400.0
88942000-88943000 rwxp 00028000 03:01 34526      /usr/lib/libgnomecanvas-2.so.0.1400.0
88943000-8894a000 r-xp 00000000 03:01 1556586    /lib/libpopt.so.0.0.0
8894a000-8894b000 rwxp 00006000 03:01 1556586    /lib/libpopt.so.0.0.0
8894b000-88969000 r-xp 00000000 03:01 34287      /usr/lib/libaudiofile.so.0.0.2
88969000-8896b000 rwxp 0001e000 03:01 34287      /usr/lib/libaudiofile.so.0.0.2
8896b000-88974000 r-xp 00000000 03:01 34380      /usr/lib/libesd.so.0.2.36
88974000-88975000 rwxp 00008000 03:01 34380      /usr/lib/libesd.so.0.2.36
88975000-88985000 r-xp 00000000 03:01 1559687    /lib/tls/i686/cmov/libresolv-2.3.6.so
88985000-88986000 rwxp 00010000 03:01 1559687    /lib/tls/i686/cmov/libresolv-2.3.6.so
88986000-88988000 rwxp 88986000 00:00 0 
88988000-88996000 r-xp 00000000 03:01 34289      /usr/lib/libavahi-client.so.3.1.2
88996000-88997000 rwxp 0000d000 03:01 34289      /usr/lib/libavahi-client.so.3.1.2
88997000-889fa000 r-xp 00000000 03:01 34546      /usr/lib/libgnutls.so.12.3.6
889fa000-88a00000 rwxp 00062000 03:01 34546      /usr/lib/libgnutls.so.12.3.6
88a00000-88c00000 rwxp 88a00000 00:00 0 
88c00000-88e00000 rwxp 88c00000 00:00 0 
88e00000-88f00000 rwxp 88e00000 00:00 0 
88f01000-88f0a000 r-xp 00000000 03:01 34291      /usr/lib/libavahi-common.so.3.4.0
88f0a000-88f0b000 rwxp 00009000 03:01 34291      /usr/lib/libavahi-common.so.3.4.0
88f0b000-89014000 r-xp 00000000 03:01 34931      /usr/lib/libxml2.so.2.6.24
89014000-8901a000 rwxp 00108000 03:01 34931      /usr/lib/libxml2.so.2.6.24
8901a000-8905f000 r-xp 00000000 03:01 34191      /usr/lib/libORBit-2.so.0.1.0
8905f000-8906b000 rwxp 00044000 03:01 34191      /usr/lib/libORBit-2.so.0.1.0
8906b000-8907c000 r-xp 00000000 03:01 34305      /usr/lib/libbonobo-activation.so.4.0.0
8907c000-8907f000 rwxp 00010000 03:01 34305      /usr/lib/libbonobo-activation.so.4.0.0
8907f000-890cc000 r-xp 00000000 03:01 34303      /usr/lib/libbonobo-2.so.0.0.0
890cc000-890d6000 rwxp 0004c000 03:01 34303      /usr/lib/libbonobo-2.so.0.0.0
890d6000-89103000 r-xp 00000000 03:01 34428      /usr/lib/libgconf-2.so.4.1.0
89103000-89106000 rwxp 0002d000 03:01 34428      /usr/lib/libgconf-2.so.4.1.0
89106000-89187000 r-xp 00000000 03:01 34538      /usr/lib/libgnomeui-2.so.0.1401.0
89187000-8918b000 rwxp 00080000 03:01 34538      /usr/lib/libgnomeui-2.so.0.1401.0
8918b000-8919e000 r-xp 00000000 03:01 34508      /usr/lib/libgnome-2.so.0.1401.0
8919e000-8919f000 rwxp 00013000 03:01 34508      /usr/lib/libgnome-2.so.0.1401.0
8919f000-891f5000 r-xp 00000000 03:01 34540      /usr/lib/libgnomevfs-2.so.0.1400.1
891f5000-891fa000 rwxp 00056000 03:01 34540      /usr/lib/libgnomevfs-2.so.0.1400.1
891fb000-89205000 r-xp 00000000 03:01 36397      /usr/lib/gnome-vfs-2.0/modules/libfile.so
89205000-89206000 rwxp 00009000 03:01 36397      /usr/lib/gnome-vfs-2.0/modules/libfile.so
89206000-89209000 r-xp 00000000 03:01 7013197    /home/csp/bin/eclipse-3.1.2/configuration/org.eclipse.osgi/bundles/90/1/.cp/libswt-gnome-gtk-3139.so
89209000-8920a000 rwxp 00002000 03:01 7013197    /home/csp/bin/eclipse-3.1.2/configuration/org.eclipse.osgi/bundles/90/1/.cp/libswt-gnome-gtk-3139.so
8920a000-8922a000 r-xs 00000000 03:01 6489031    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.ltk.core.refactoring_3.1.0.jar
8922a000-8924b000 r-xs 00000000 03:01 6489071    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.ui.console_3.1.2.jar
8924b000-8927c000 r-xs 00000000 03:01 6489094    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.jdt.launching_3.1.0.jar
8927c000-8927f000 rwxp 8927c000 00:00 0 
8927f000-892fd000 rwxp 8927f000 00:00 0 
892fd000-893ba000 r-xs 00000000 03:01 6520840    /home/csp/bin/eclipse-3.1.2/plugins/org.tigris.subversion.subclipse.core_1.0.2/lib/javasvn.jar
893ba000-893e2000 r-xs 00000000 03:01 6520839    /home/csp/bin/eclipse-3.1.2/plugins/org.tigris.subversion.subclipse.core_1.0.2/lib/ganymed.jar
893e2000-893e5000 rwxp 893e2000 00:00 0 
893e5000-89463000 rwxp 893e5000 00:00 0 
89463000-8946e000 r-xs 00000000 03:01 6520842    /home/csp/bin/eclipse-3.1.2/plugins/org.tigris.subversion.subclipse.core_1.0.2/lib/svnjavahl.jar
8946e000-89474000 r-xs 00000000 03:01 6489087    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.update.scheduler_3.1.0.jar
89474000-89476000 r-xp 00000000 03:01 1559693    /lib/tls/i686/cmov/libutil-2.3.6.so
89476000-89477000 rwxp 00001000 03:01 1559693    /lib/tls/i686/cmov/libutil-2.3.6.so
89477000-8947a000 rwxp 89477000 00:00 0 
8947a000-894f8000 rwxp 8947a000 00:00 0 
894f8000-89596000 r-xs 00000000 03:01 6489086    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.team.ui_3.1.1.jar
89596000-895b9000 r-xs 00000000 03:01 6520841    /home/csp/bin/eclipse-3.1.2/plugins/org.tigris.subversion.subclipse.core_1.0.2/lib/svnClientAdapter.jar
895b9000-895f2000 r-xs 00000000 03:01 6520836    /home/csp/bin/eclipse-3.1.2/plugins/org.tigris.subversion.subclipse.core_1.0.2/SVNPluginCore.jar
895f2000-895f5000 rwxp 895f2000 00:00 0 
895f5000-89673000 rwxp 895f5000 00:00 0 
89673000-8978b000 r-xs 00000000 03:01 6520852    /home/csp/bin/eclipse-3.1.2/plugins/org.tigris.subversion.subclipse.ui_1.0.2/SVNPluginUI.jar
8978b000-8983e000 r-xs 00000000 03:01 6489033    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.jdt.debug_3.1.1/jdimodel.jar
8983e000-8984b000 r-xs 00000000 03:01 6489034    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.jdt.debug_3.1.1/jdi.jar
8984b000-89ad7000 r-xs 00000000 03:01 6489080    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.pde.ui_3.1.2.jar
89ad7000-89bcd000 r-xs 00000000 03:01 6488683    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.ant.ui_3.1.2.jar
89bcd000-89c07000 r-xs 00000000 03:01 6489089    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.debug.core_3.1.2.jar
89c07000-89d0f000 r-xs 00000000 03:01 6489062    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.jdt.debug.ui_3.1.2.jar
89d0f000-89d2d000 r-xs 00000000 03:01 6489084    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.ui.externaltools_3.1.1.jar
89d2d000-89d30000 rwxp 89d2d000 00:00 0 
89d30000-89dae000 rwxp 89d30000 00:00 0 
89dae000-8a116000 r-xs 00000000 03:01 6489098    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.jdt.core_3.1.2.jar
8a116000-8a13b000 r-xs 00000000 03:01 6918685    /home/csp/bin/eclipse-3.1.2/plugins/com.objfac.xmleditor_2.0.75/xml-apis.jar
8a13b000-8a147000 r-xs 00000000 03:01 6918682    /home/csp/bin/eclipse-3.1.2/plugins/com.objfac.xmleditor_2.0.75/validate.jar
8a147000-8a14a000 ---p 8a147000 00:00 0 
8a14a000-8a1c8000 rwxp 8a14a000 00:00 0 
8a1c8000-8a1cb000 rwxp 8a1c8000 00:00 0 
8a1cb000-8a249000 rwxp 8a1cb000 00:00 0 
8a249000-8a26f000 r-xp 00000000 03:01 249676     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono-BoldOblique.ttf
8a26f000-8a297000 r-xp 00000000 03:01 249677     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono-Oblique.ttf
8a297000-8a2bb000 r-xp 00000000 03:01 249675     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono-Bold.ttf
8a2bb000-8a2e1000 r-xp 00000000 03:01 249678     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
8a2e1000-8a33d000 r-xp 00000000 03:01 249667     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-BoldOblique.ttf
8a33d000-8a396000 r-xp 00000000 03:01 249669     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Oblique.ttf
8a396000-8a4dc000 r-xs 00000000 03:01 6489090    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.debug.ui_3.1.2.jar
8a4dc000-8a53a000 r-xs 00000000 03:01 6488810    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.search_3.1.2.jar
8a53a000-8a550000 r-xs 00000000 03:01 6489073    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.core.filebuffers_3.1.2.jar
8a550000-8a586000 r-xs 00000000 03:01 6489091    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.team.core_3.1.1.jar
8a586000-8a596000 r-xs 00000000 03:01 6489078    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.ui.views_3.1.1.jar
8a596000-8a600000 r-xs 00000000 03:01 6489077    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.ui.workbench.texteditor_3.1.2.jar
8a600000-8a6a4000 r-xs 00000000 03:01 6489076    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.jface.text_3.1.2.jar
8a6a4000-8a6d1000 r-xs 00000000 03:01 6489079    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.text_3.1.1.jar
8a6d1000-8a7bf000 r-xs 00000000 03:01 6918687    /home/csp/bin/eclipse-3.1.2/plugins/com.objfac.xmleditor_2.0.75/xmleditor.jar
8a7bf000-8a7e3000 r-xs 00000000 03:01 6918686    /home/csp/bin/eclipse-3.1.2/plugins/com.objfac.xmleditor_2.0.75/xml.jar
8a7e3000-8a8cd000 r-xs 00000000 03:01 6918684    /home/csp/bin/eclipse-3.1.2/plugins/com.objfac.xmleditor_2.0.75/xerces.jar
8a8cd000-8a8cf000 r-xs 00000000 03:01 6918683    /home/csp/bin/eclipse-3.1.2/plugins/com.objfac.xmleditor_2.0.75/walker.jar
8a8cf000-8a8e9000 r-xs 00000000 03:01 6918681    /home/csp/bin/eclipse-3.1.2/plugins/com.objfac.xmleditor_2.0.75/util.jar
8a8e9000-8a8ea000 r-xs 00000000 03:01 6918680    /home/csp/bin/eclipse-3.1.2/plugins/com.objfac.xmleditor_2.0.75/trangutils.jar
8a8ea000-8a963000 r-xs 00000000 03:01 6918679    /home/csp/bin/eclipse-3.1.2/plugins/com.objfac.xmleditor_2.0.75/trang.jar
8a963000-8a968000 r-xs 00000000 03:01 6918677    /home/csp/bin/eclipse-3.1.2/plugins/com.objfac.xmleditor_2.0.75/saxpath.jar
8a968000-8aa91000 r-xs 00000000 03:01 6918676    /home/csp/bin/eclipse-3.1.2/plugins/com.objfac.xmleditor_2.0.75/saxon.jar
8aa91000-8ab2b000 r-xs 00000000 03:01 6918670    /home/csp/bin/eclipse-3.1.2/plugins/com.objfac.xmleditor_2.0.75/jing.jar
8ab2b000-8ab4c000 r-xs 00000000 03:01 6918669    /home/csp/bin/eclipse-3.1.2/plugins/com.objfac.xmleditor_2.0.75/jaxen.jar
8ab4c000-8ab5c000 r-xs 00000000 03:01 6918668    /home/csp/bin/eclipse-3.1.2/plugins/com.objfac.xmleditor_2.0.75/isorelax.jar
8ab5c000-8ab5e000 r-xs 00000000 03:01 6918672    /home/csp/bin/eclipse-3.1.2/plugins/com.objfac.xmleditor_2.0.75/moved.jar
8ab5e000-8b1f5000 r-xs 00000000 03:01 6489095    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.jdt.ui_3.1.2.jar
8b1f5000-8b25c000 r-xs 00000000 03:01 6489074    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.ui.editors_3.1.1.jar
8b25c000-8b26d000 r-xs 00000000 03:01 6489072    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.help_3.1.0.jar
8b26d000-8b2cd000 rwxs 00000000 00:07 1015831    /SYSV00000000 (deleted)
8b2cd000-8b2d0000 rwxp 8b2cd000 00:00 0 
8b2d0000-8b34e000 rwxp 8b2d0000 00:00 0 
8b34e000-8b36a000 r-xs 00000000 03:01 6488963    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.core.resources.compatibility_3.1.0.jar
8b36a000-8b435000 r-xp 00000000 03:01 34883      /usr/lib/libstdc++.so.6.0.7
8b435000-8b43a000 rwxp 000cb000 03:01 34883      /usr/lib/libstdc++.so.6.0.7
8b43a000-8b43f000 rwxp 8b43a000 00:00 0 
8b43f000-8b4a0000 r-xp 00000000 03:01 249666     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
8b4a0000-8b500000 rwxs 00000000 00:07 950293     /SYSV00000000 (deleted)
8b500000-8b5fb000 rwxp 8b500000 00:00 0 
8b5fb000-8b600000 ---p 8b5fb000 00:00 0 


---

### Post by coconut on 2006-08-19
Part 4:

> 
8b601000-8b603000 r-xp 00000000 03:01 34293      /usr/lib/libavahi-glib.so.1.0.0
8b603000-8b604000 rwxp 00001000 03:01 34293      /usr/lib/libavahi-glib.so.1.0.0
8b604000-8b606000 r-xp 00000000 03:01 118196     /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
8b606000-8b607000 rwxp 00001000 03:01 118196     /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
8b607000-8b66c000 r-xp 00000000 03:01 249670     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
8b66c000-8b69f000 r-xp 00000000 03:01 82566      /usr/lib/locale/zh_SG.utf8/LC_CTYPE
8b69f000-8b6d2000 r-xp 00000000 03:01 82566      /usr/lib/locale/zh_HK.utf8/LC_CTYPE
8b6d2000-8b706000 r-xp 00000000 03:01 98335      /usr/lib/locale/zh_TW.utf8/LC_CTYPE
8b706000-8b73a000 r-xp 00000000 03:01 98335      /usr/lib/locale/zh_CN.utf8/LC_CTYPE
8b73a000-8b751000 r-xs 00000000 03:01 6489063    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.ui.presentations.r21_3.1.0.jar
8b751000-8b754000 rwxs 00000000 00:07 983062     /SYSV00000000 (deleted)
8b754000-8b75b000 r-xs 00000000 03:01 6488682    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.core.resources.linux_3.1.0.jar
8b75b000-8b7f1000 r-xs 00000000 03:01 6489101    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.core.resources_3.1.2.jar
8b7f1000-8b801000 r-xp 00000000 03:01 180355     /usr/lib/scim-1.0/1.4.0/IMEngine/socket.so
8b801000-8b802000 rwxp 0000f000 03:01 180355     /usr/lib/scim-1.0/1.4.0/IMEngine/socket.so
8b802000-8b80b000 r-xp 00000000 03:01 1556549    /lib/libgcc_s.so.1
8b80b000-8b80c000 rwxp 00009000 03:01 1556549    /lib/libgcc_s.so.1
8b80c000-8b80e000 r-xp 00000000 03:01 34847      /usr/lib/libscim-x11utils-1.0.so.8.1.0
8b80e000-8b80f000 rwxp 00001000 03:01 34847      /usr/lib/libscim-x11utils-1.0.so.8.1.0
8b80f000-8b8de000 r-xp 00000000 03:01 34843      /usr/lib/libscim-1.0.so.8.1.0
8b8de000-8b8ed000 rwxp 000ce000 03:01 34843      /usr/lib/libscim-1.0.so.8.1.0
8b8ef000-8b8f1000 r-xp 00000000 03:01 7013679    /home/csp/bin/eclipse-3.1.2/configuration/org.eclipse.osgi/bundles/4/1/.cp/os/linux/x86/libcore_3_1_0.so
8b8f1000-8b8f2000 rwxp 00001000 03:01 7013679    /home/csp/bin/eclipse-3.1.2/configuration/org.eclipse.osgi/bundles/4/1/.cp/os/linux/x86/libcore_3_1_0.so
8b8f2000-8b8f8000 r-xp 00000000 03:01 180349     /usr/lib/scim-1.0/1.4.0/Config/socket.so
8b8f8000-8b8f9000 rwxp 00005000 03:01 180349     /usr/lib/scim-1.0/1.4.0/Config/socket.so
8b8f9000-8b91a000 r-xp 00000000 03:01 36625      /usr/lib/gtk-2.0/2.4.0/immodules/im-scim.so
8b91a000-8b91b000 rwxp 00021000 03:01 36625      /usr/lib/gtk-2.0/2.4.0/immodules/im-scim.so
8b91b000-8b928000 r-xs 00000000 03:01 6488962    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.core.expressions_3.1.0.jar
8b928000-8b939000 r-xs 00000000 03:01 6489064    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.core.commands_3.1.0.jar
8b939000-8b94a000 r-xp 00000000 03:01 36618      /usr/lib/gtk-2.0/2.4.0/engines/libubuntulooks.so
8b94a000-8b94b000 rwxp 00011000 03:01 36618      /usr/lib/gtk-2.0/2.4.0/engines/libubuntulooks.so
8b94b000-8b971000 r-xp 00000000 03:01 7013120    /home/csp/bin/eclipse-3.1.2/configuration/org.eclipse.osgi/bundles/90/1/.cp/libswt-gtk-3139.so
8b971000-8b973000 rwxp 00025000 03:01 7013120    /home/csp/bin/eclipse-3.1.2/configuration/org.eclipse.osgi/bundles/90/1/.cp/libswt-gtk-3139.so
8b973000-8b974000 rwxp 8b973000 00:00 0 
8b974000-8b98e000 r-xp 00000000 03:01 397052     /usr/share/locale-langpack/en_GB/LC_MESSAGES/gtk20-properties.mo
8b98e000-8b997000 r-xp 00000000 03:01 397053     /usr/share/locale-langpack/en_GB/LC_MESSAGES/gtk20.mo
8b997000-8ba6e000 r-xp 00000000 03:01 82109      /usr/lib/locale/en_US.utf8/LC_COLLATE
8ba6e000-8ba8a000 r-xp 00000000 03:01 34393      /usr/lib/libexpat.so.1.0.0
8ba8a000-8ba8d000 rwxp 0001c000 03:01 34393      /usr/lib/libexpat.so.1.0.0
8ba8d000-8baaf000 r-xp 00000000 03:01 34803      /usr/lib/libpng12.so.0.1.2.8
8baaf000-8bab0000 rwxp 00022000 03:01 34803      /usr/lib/libpng12.so.0.1.2.8
8bab0000-8bab2000 r-xp 00000000 03:01 34209      /usr/lib/libXau.so.6.0.0
8bab2000-8bab3000 rwxp 00001000 03:01 34209      /usr/lib/libXau.so.6.0.0
8bab3000-8bac6000 r-xp 00000000 03:01 34943      /usr/lib/libz.so.1.2.3
8bac6000-8bac7000 rwxp 00012000 03:01 34943      /usr/lib/libz.so.1.2.3
8bac7000-8bb2d000 r-xp 00000000 03:01 33015      /usr/lib/libfreetype.so.6.3.8
8bb2d000-8bb30000 rwxp 00066000 03:01 33015      /usr/lib/libfreetype.so.6.3.8
8bb30000-8bb53000 r-xp 00000000 03:01 34781      /usr/lib/libpangoft2-1.0.so.0.1200.2
8bb53000-8bb54000 rwxp 00022000 03:01 34781      /usr/lib/libpangoft2-1.0.so.0.1200.2
8bb54000-8bb57000 r-xp 00000000 03:01 34222      /usr/lib/libXfixes.so.3.0.0
8bb57000-8bb58000 rwxp 00003000 03:01 34222      /usr/lib/libXfixes.so.3.0.0
8bb58000-8bb60000 r-xp 00000000 03:01 34214      /usr/lib/libXcursor.so.1.0.2
8bb60000-8bb61000 rwxp 00007000 03:01 34214      /usr/lib/libXcursor.so.1.0.2
8bb61000-8bb63000 r-xp 00000000 03:01 34240      /usr/lib/libXrandr.so.2.0.0
8bb63000-8bb64000 rwxp 00002000 03:01 34240      /usr/lib/libXrandr.so.2.0.0
8bb64000-8bb6b000 r-xp 00000000 03:01 34228      /usr/lib/libXi.so.6.0.0
8bb6b000-8bb6c000 rwxp 00006000 03:01 34228      /usr/lib/libXi.so.6.0.0
8bb6c000-8bb6e000 r-xp 00000000 03:01 34230      /usr/lib/libXinerama.so.1.0.0
8bb6e000-8bb6f000 rwxp 00001000 03:01 34230      /usr/lib/libXinerama.so.1.0.0
8bb6f000-8bb76000 r-xp 00000000 03:01 34242      /usr/lib/libXrender.so.1.3.0
8bb76000-8bb77000 rwxp 00006000 03:01 34242      /usr/lib/libXrender.so.1.3.0
8bb77000-8bb9f000 r-xp 00000000 03:01 34402      /usr/lib/libfontconfig.so.1.0.4
8bb9f000-8bba4000 rwxp 00027000 03:01 34402      /usr/lib/libfontconfig.so.1.0.4
8bba4000-8bba5000 rwxp 8bba4000 00:00 0 
8bba5000-8bbb1000 r-xp 00000000 03:01 34220      /usr/lib/libXext.so.6.4.0
8bbb1000-8bbb2000 rwxp 0000c000 03:01 34220      /usr/lib/libXext.so.6.4.0
8bbb2000-8bbf7000 r-xp 00000000 03:01 34311      /usr/lib/libcairo.so.2.2.4
8bbf7000-8bbf8000 rwxp 00045000 03:01 34311      /usr/lib/libcairo.so.2.2.4
8bbf8000-8bc7b000 r-xp 00000000 03:01 32887      /usr/lib/libglib-2.0.so.0.1000.3
8bc7b000-8bc7c000 rwxp 00082000 03:01 32887      /usr/lib/libglib-2.0.so.0.1000.3
8bc7c000-8bc7e000 r-xp 00000000 03:01 33213      /usr/lib/libgmodule-2.0.so.0.1000.3
8bc7e000-8bc7f000 rwxp 00002000 03:01 33213      /usr/lib/libgmodule-2.0.so.0.1000.3
8bc7f000-8bcb6000 r-xp 00000000 03:01 33013      /usr/lib/libgobject-2.0.so.0.1000.3
8bcb6000-8bcb7000 rwxp 00037000 03:01 33013      /usr/lib/libgobject-2.0.so.0.1000.3
8bcb7000-8bcce000 r-xp 00000000 03:01 34281      /usr/lib/libatk-1.0.so.0.1114.0
8bcce000-8bcd0000 rwxp 00016000 03:01 34281      /usr/lib/libatk-1.0.so.0.1114.0
8bcd0000-8bdb1000 r-xp 00000000 03:01 34203      /usr/lib/libX11.so.6.2.0
8bdb1000-8bdb5000 rwxp 000e1000 03:01 34203      /usr/lib/libX11.so.6.2.0
8bdb5000-8bdb6000 rwxp 8bdb5000 00:00 0 
8bdb6000-8bdec000 r-xp 00000000 03:01 34777      /usr/lib/libpango-1.0.so.0.1200.2
8bdec000-8bdee000 rwxp 00035000 03:01 34777      /usr/lib/libpango-1.0.so.0.1200.2
8bdee000-8bdf5000 r-xp 00000000 03:01 34779      /usr/lib/libpangocairo-1.0.so.0.1200.2
8bdf5000-8bdf6000 rwxp 00006000 03:01 34779      /usr/lib/libpangocairo-1.0.so.0.1200.2
8bdf6000-8be70000 r-xp 00000000 03:01 34449      /usr/lib/libgdk-x11-2.0.so.0.800.17
8be70000-8be73000 rwxp 0007a000 03:01 34449      /usr/lib/libgdk-x11-2.0.so.0.800.17
8be73000-8be87000 r-xp 00000000 03:01 34451      /usr/lib/libgdk_pixbuf-2.0.so.0.800.17
8be87000-8be88000 rwxp 00014000 03:01 34451      /usr/lib/libgdk_pixbuf-2.0.so.0.800.17
8be88000-8be8c000 r-xp 00000000 03:01 34248      /usr/lib/libXtst.so.6.1.0
8be8c000-8be8d000 rwxp 00003000 03:01 34248      /usr/lib/libXtst.so.6.1.0
8be8d000-8c156000 r-xp 00000000 03:01 34601      /usr/lib/libgtk-x11-2.0.so.0.800.17
8c156000-8c15e000 rwxp 002c8000 03:01 34601      /usr/lib/libgtk-x11-2.0.so.0.800.17
8c15e000-8c162000 rwxp 8c15e000 00:00 0 
8c163000-8c164000 r-xp 8c163000 00:00 0 
8c164000-8c165000 r-xp 00000000 03:01 397064     /usr/share/locale-langpack/en_GB/LC_MESSAGES/libc.mo
8c165000-8c166000 r-xp 00000000 03:01 36016      /usr/lib/gconv/ISO8859-1.so
8c166000-8c167000 rwxp 00001000 03:01 36016      /usr/lib/gconv/ISO8859-1.so
8c167000-8c168000 r-xp 00000000 03:01 82115      /usr/lib/locale/en_US.utf8/LC_NUMERIC
8c168000-8c169000 r-xp 00000000 03:01 82687      /usr/lib/locale/en_US.utf8/LC_TIME
8c169000-8c16a000 r-xp 00000000 03:01 82686      /usr/lib/locale/en_US.utf8/LC_MONETARY
8c16a000-8c16b000 r-xp 00000000 03:01 82132      /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
8c16b000-8c16c000 r-xp 00000000 03:01 82594      /usr/lib/locale/en_US.utf8/LC_PAPER
8c16c000-8c16d000 r-xp 00000000 03:01 82690      /usr/lib/locale/en_US.utf8/LC_NAME
8c16d000-8c16e000 r-xp 00000000 03:01 82685      /usr/lib/locale/en_US.utf8/LC_ADDRESS
8c16e000-8c1b0000 r-xp 00000000 03:01 7013119    /home/csp/bin/eclipse-3.1.2/configuration/org.eclipse.osgi/bundles/90/1/.cp/libswt-pi-gtk-3139.so
8c1b0000-8c1b2000 rwxp 00042000 03:01 7013119    /home/csp/bin/eclipse-3.1.2/configuration/org.eclipse.osgi/bundles/90/1/.cp/libswt-pi-gtk-3139.so
8c1b2000-8c1d0000 r-xs 00000000 03:01 6489081    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.ui_3.1.2.jar
8c1d0000-8c323000 r-xs 00000000 03:01 6489108    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.swt.gtk.linux.x86_3.1.1.jar
8c323000-8c324000 r-xs 00000000 03:01 6489105    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.swt_3.1.0.jar
8c324000-8c3c8000 r-xs 00000000 03:01 6489030    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.jface_3.1.1.jar
8c3c8000-8c3c9000 r-xs 00000000 03:01 6619265    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.ui.workbench.compatibility_3.1.0/compatibility.jar
8c3c9000-8c688000 r-xs 00000000 03:01 6488809    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.ui.workbench_3.1.2.jar
8c688000-8c800000 r-xs 00000000 03:01 6489092    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.ui.ide_3.1.1.jar
8c800000-8c817000 r-xs 00000000 03:01 6488961    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.update.configurator_3.1.0.jar
8c817000-8c82c000 r-xs 00000000 03:01 6489102    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.core.runtime.compatibility_3.1.0.jar
8c82c000-8c89b000 r-xs 00000000 03:01 6489104    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.core.runtime_3.1.2.jar
8c89b000-8c89e000 ---p 8c89b000 00:00 0 
8c89e000-8c91c000 rwxp 8c89e000 00:00 0 
8c91c000-8c91f000 ---p 8c91c000 00:00 0 
8c91f000-8c99d000 rwxp 8c91f000 00:00 0 
8c99d000-8c9a0000 ---p 8c99d000 00:00 0 
8c9a0000-8ca1e000 rwxp 8c9a0000 00:00 0 
8ca1e000-8ca24000 r-xp 00000000 03:01 1033489    /home/csp/bin/jdk1.5.0_08/jre/lib/i386/libnio.so
8ca24000-8ca25000 rwxp 00005000 03:01 1033489    /home/csp/bin/jdk1.5.0_08/jre/lib/i386/libnio.so
8ca25000-8ca36000 r-xp 00000000 03:01 1033488    /home/csp/bin/jdk1.5.0_08/jre/lib/i386/libnet.so
8ca36000-8ca37000 rwxp 00011000 03:01 1033488    /home/csp/bin/jdk1.5.0_08/jre/lib/i386/libnet.so
8ca37000-8caef000 r-xs 00000000 03:01 6489065    /home/csp/bin/eclipse-3.1.2/plugins/org.eclipse.osgi_3.1.2.jar
8caef000-8caf2000 rwxp 8caef000 00:00 0 
8caf2000-8cb70000 rwxp 8caf2000 00:00 0 
8cb70000-8cb78000 r-xs 00000000 03:01 6489111    /home/csp/bin/eclipse-3.1.2/startup.jar
8cb78000-8cc3c000 r-xs 00000000 03:01 1033525    /home/csp/bin/jdk1.5.0_08/jre/lib/ext/localedata.jar
8cc3c000-8cc67000 r-xs 00000000 03:01 1033523    /home/csp/bin/jdk1.5.0_08/jre/lib/ext/sunpkcs11.jar
8cc67000-8cc8e000 r-xs 00000000 03:01 1033522    /home/csp/bin/jdk1.5.0_08/jre/lib/ext/sunjce_provider.jar
8cc8e000-8cc8f000 ---p 8cc8e000 00:00 0 
8cc8f000-8cd0f000 rwxp 8cc8f000 00:00 0 
8cd0f000-8cd12000 ---p 8cd0f000 00:00 0 
8cd12000-8cd90000 rwxp 8cd12000 00:00 0 
8cd90000-8cd93000 ---p 8cd90000 00:00 0 
8cd93000-8ce11000 rwxp 8cd93000 00:00 0 
8ce11000-8ce14000 ---p 8ce11000 00:00 0 
8ce14000-8ce92000 rwxp 8ce14000 00:00 0 
8ce92000-8ce95000 ---p 8ce92000 00:00 0 
8ce95000-8cf13000 rwxp 8ce95000 00:00 0 
8cf13000-8cf16000 ---p 8cf13000 00:00 0 
8cf16000-8cf94000 rwxp 8cf16000 00:00 0 
8cf94000-8cfc7000 r-xp 00000000 03:01 82110      /usr/lib/locale/en_US.utf8/LC_CTYPE
8cfc7000-8cfca000 ---p 8cfc7000 00:00 0 
8cfca000-8d048000 rwxp 8cfca000 00:00 0 
8d048000-8d04b000 ---p 8d048000 00:00 0 
8d04b000-8d0c9000 rwxp 8d04b000 00:00 0 
8d0c9000-8d0ca000 ---p 8d0c9000 00:00 0 
8d0ca000-8d160000 rwxp 8d0ca000 00:00 0 
8d160000-8d16b000 rwxp 8d160000 00:00 0 
8d16b000-8d1dd000 rwxp 8d16b000 00:00 0 
8d1dd000-8d24f000 rwxp 8d1dd000 00:00 0 
8d24f000-8d25e000 rwxp 8d24f000 00:00 0 
8d25e000-8d26b000 rwxp 8d25e000 00:00 0 
8d26b000-8d2de000 rwxp 8d26b000 00:00 0 
8d2de000-8d34f000 rwxp 8d2de000 00:00 0 
8d34f000-8d365000 rwxp 8d34f000 00:00 0 
8d365000-8d36f000 rwxp 8d365000 00:00 0 
8d36f000-8eff0000 rwxp 8d36f000 00:00 0 
8eff0000-90c50000 rwxp 8eff0000 00:00 0 
90c50000-9efe0000 rwxp 90c50000 00:00 0 
9efe0000-ad370000 rwxp 9efe0000 00:00 0 
ad370000-afe30000 rwxp ad370000 00:00 0 
afe30000-b1370000 rwxp afe30000 00:00 0 
b1370000-b1371000 r-xp 00000000 03:01 82691      /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b1371000-b1372000 r-xp 00000000 03:01 82887      /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b1372000-b137a000 r-xs 00000000 03:01 6489111    /home/csp/bin/eclipse-3.1.2/startup.jar
b137a000-b13a6000 rwxp b137a000 00:00 0 
b13a6000-b143a000 rwxp b13a6000 00:00 0 
b143a000-b1f1a000 rwxp b143a000 00:00 0 
b1f1a000-b443a000 rwxp b1f1a000 00:00 0 


---

### Post by coconut on 2006-08-19
Part 5:

> 
b443a000-b4caa000 r-xs 00000000 03:01 1034118    /home/csp/bin/jdk1.5.0_08/jre/lib/charsets.jar
b4caa000-b4cbf000 r-xs 00000000 03:01 1033526    /home/csp/bin/jdk1.5.0_08/jre/lib/jce.jar
b4cbf000-b4d44000 r-xs 00000000 03:01 1034062    /home/csp/bin/jdk1.5.0_08/jre/lib/jsse.jar
b4d44000-b4dad000 rwxp b4d44000 00:00 0 
b4dad000-b73c3000 r-xs 00000000 03:01 1034120    /home/csp/bin/jdk1.5.0_08/jre/lib/rt.jar
b73c3000-b73d2000 r-xp 00000000 03:01 1033485    /home/csp/bin/jdk1.5.0_08/jre/lib/i386/libzip.so
b73d2000-b73d4000 rwxp 0000e000 03:01 1033485    /home/csp/bin/jdk1.5.0_08/jre/lib/i386/libzip.so
b73d4000-b73f5000 r-xp 00000000 03:01 1033483    /home/csp/bin/jdk1.5.0_08/jre/lib/i386/libjava.so
b73f5000-b73f7000 rwxp 00020000 03:01 1033483    /home/csp/bin/jdk1.5.0_08/jre/lib/i386/libjava.so
b73f7000-b7402000 r-xp 00000000 03:01 1033482    /home/csp/bin/jdk1.5.0_08/jre/lib/i386/libverify.so
b7402000-b7403000 rwxp 0000b000 03:01 1033482    /home/csp/bin/jdk1.5.0_08/jre/lib/i386/libverify.so
b7403000-b740c000 r-xp 00000000 03:01 1559676    /lib/tls/i686/cmov/libnss_files-2.3.6.so
b740c000-b740d000 rwxp 00008000 03:01 1559676    /lib/tls/i686/cmov/libnss_files-2.3.6.so
b740d000-b7415000 r-xp 00000000 03:01 1559680    /lib/tls/i686/cmov/libnss_nis-2.3.6.so
b7415000-b7416000 rwxp 00007000 03:01 1559680    /lib/tls/i686/cmov/libnss_nis-2.3.6.so
b7416000-b741e000 r-xp 00000000 03:01 1559672    /lib/tls/i686/cmov/libnss_compat-2.3.6.so
b741e000-b741f000 rwxp 00007000 03:01 1559672    /lib/tls/i686/cmov/libnss_compat-2.3.6.so
b741f000-b7431000 r-xp 00000000 03:01 1559670    /lib/tls/i686/cmov/libnsl-2.3.6.so
b7431000-b7432000 rwxp 00012000 03:01 1559670    /lib/tls/i686/cmov/libnsl-2.3.6.so
b7432000-b7434000 rwxp b7432000 00:00 0 
b7434000-b7437000 r-xp 00000000 03:01 33367      /usr/lib/libgthread-2.0.so.0.1000.3
b7437000-b7438000 rwxp 00002000 03:01 33367      /usr/lib/libgthread-2.0.so.0.1000.3
b7438000-b7440000 rwxs 00000000 03:01 7556924    /tmp/hsperfdata_csp/5130
b7440000-b7461000 r-xp 00000000 03:01 1559667    /lib/tls/i686/cmov/libm-2.3.6.so
b7461000-b7462000 rwxp 00020000 03:01 1559667    /lib/tls/i686/cmov/libm-2.3.6.so
b7462000-b79bc000 r-xp 00000000 03:01 1033472    /home/csp/bin/jdk1.5.0_08/jre/lib/i386/server/libjvm.so
b79bc000-b7a1f000 rwxp 0055a000 03:01 1033472    /home/csp/bin/jdk1.5.0_08/jre/lib/i386/server/libjvm.so
b7a1f000-b7e37000 rwxp b7a1f000 00:00 0 
b7e37000-b7f5c000 r-xp 00000000 03:01 1559659    /lib/tls/i686/cmov/libc-2.3.6.so
b7f5c000-b7f63000 rwxp 00125000 03:01 1559659    /lib/tls/i686/cmov/libc-2.3.6.so
b7f63000-b7f66000 rwxp b7f63000 00:00 0 
b7f66000-b7f68000 r-xp 00000000 03:01 1559665    /lib/tls/i686/cmov/libdl-2.3.6.so
b7f68000-b7f69000 rwxp 00001000 03:01 1559665    /lib/tls/i686/cmov/libdl-2.3.6.so
b7f69000-b7f6a000 rwxp b7f69000 00:00 0 
b7f6a000-b7f79000 r-xp 00000000 03:01 1559685    /lib/tls/i686/cmov/libpthread-2.3.6.so
b7f79000-b7f7a000 rwxp 0000e000 03:01 1559685    /lib/tls/i686/cmov/libpthread-2.3.6.so
b7f7a000-b7f7c000 rwxp b7f7a000 00:00 0 
b7f7c000-b7f7d000 r-xp 00000000 03:01 82688      /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f7d000-b7f7f000 r-xs 00000000 03:01 1033524    /home/csp/bin/jdk1.5.0_08/jre/lib/ext/dnsns.jar
b7f7f000-b7f85000 r-xp 00000000 03:01 1033470    /home/csp/bin/jdk1.5.0_08/jre/lib/i386/native_threads/libhpi.so
b7f85000-b7f86000 rwxp 00006000 03:01 1033470    /home/csp/bin/jdk1.5.0_08/jre/lib/i386/native_threads/libhpi.so
b7f86000-b7f87000 rwxp b7f86000 00:00 0 
b7f87000-b7f88000 r-xp b7f87000 00:00 0 
b7f88000-b7f8b000 rwxp b7f88000 00:00 0 
b7f8b000-b7fa0000 r-xp 00000000 03:01 1556502    /lib/ld-2.3.6.so
b7fa0000-b7fa1000 rwxp 00014000 03:01 1556502    /lib/ld-2.3.6.so
bfba0000-bfba3000 ---p bfba0000 00:00 0 
bfba3000-bfda0000 rwxp bfba3000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]

VM Arguments:
jvm_args: -Xms256m -Xmx512m
java_command: /home/csp/bin/eclipse/startup.jar -os linux -ws gtk -arch x86 -launcher /home/csp/bin/eclipse/eclipse -name Eclipse -showsplash 600 -exitdata d8013 -vm /home/csp/bin/java/bin/java -vmargs -Xms256m -Xmx512m -server -jar /home/csp/bin/eclipse/startup.jar
Launcher Type: SUN_STANDARD

Environment Variables:
JAVA_HOME=/home/csp/bin/java
PATH=/home/csp/bin:/home/csp/bin/java/bin:/home/csp/bin/eclipse:/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
USERNAME=csp
LD_LIBRARY_PATH=/home/csp/bin/jdk1.5.0_08/jre/lib/i386/server:/home/csp/bin/jdk1.5.0_08/jre/lib/i386:/home/csp/bin/jdk1.5.0_08/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x508860], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x508860], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x42cac0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00001000, sa_flags=0x10000000
SIGILL: [libjvm.so+0x42cac0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x42ef10], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x42e940], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: SIG_IGN, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGQUIT: [libjvm.so+0x42e940], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x42e940], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:testing/unstable

uname:Linux 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686
libc:glibc 2.3.6 NPTL 2.3.6 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:15.70 9.97 4.37

CPU:total 1 (cores per cpu 1, threads per core 1) family 15 model 2 stepping 7, cmov, cx8, fxsr, mmx, sse, sse2

Memory: 4k page, physical 1036096k(10656k free), swap 3036244k(2619296k free)

vm_info: Java HotSpot(TM) Server VM (1.5.0_08-b03) for linux-x86, built on Jun 28 2006 00:27:00 by java_re with gcc 3.2.1-7a (J2SE release)


So, here you go, sorry for the messy stuff!

---

### Post by coconut on 2006-08-19
> **chonger said:**
> I am sure this is not a problem caused by Ubuntu. I'm about to set up a pretty complicated Java application on an Ubuntu box. I will definitely share my experiences with you.

What kind of crashses are you seeing? Do you get Hotspot errors? Or do you get some kind of error like OutOfMemoryError? Have you tried changing the compiler (running as -client instead of -server)? 



It's definitely a Hotspot problem, not because of lack of memory. A machine with 2GB of memory should run Eclipse just fine, I think. Besides, no matter how much I set the Xmx__m option, it still dies.

I also tried the -server vs -client options, but that didn't help either.

What I suspect most is that the jvm is compiled with an old version of gcc, and most probably with some old versions of libraries too, while Ubuntu was built with newer version of gcc.

I tried to use the JDK from the Ubuntu multiverse repo, hoping that it would be better, but no, it's not. And every single version of JDKs I have on my machine has the same issues.

I just threw the issue here, hoping that this is a lone case, or someone knows what's going on. Never had so bad experience with good old Fedora (and RH and Mandrake) before. Our production machines on Fedora 8, Fedora 9 and RHEL 4 are running Java apps rock solid. Working with java on Ubuntu makes me want to run...](*,) 

Hope to hear about your experience.

---

### Post by coconut on 2006-08-19
Changing to IBM JVM is not helping either. Eclipse can't even finish checking a project from Subversion (with Subclipse plugin) before jvm dies. This is a fairly big project, rougly 15K files to check out. 

On smaller projects, it just hangs in the middle, doing nothing. No error, no output, no message, whatsoever. It just hangs. I had  to "kill -9" to get out of it.

Here's the error message from the crash:

> 
Type=Segmentation error vmState=0x00020002
Target=2_30_20060501_06428_lHdSMR (Linux 2.6.15-23-386)
CPU=x86 (1 logical CPUs) (0x3f3d0000 RAM)
J9Generic_Signal_Number=00000004 Signal_Number=0000000b Error_Value=00000000 Signal_Code=00000001
Handler1=B7D7C13F Handler2=B7D4642E InaccessibleAddress=00000000
EDI=A1D1A0BC ESI=08084D54 EAX=080D1270 EBX=080D1274
ECX=A1D1A0BC EDX=00000000
EIP=B78ACB15 ES=C010007B DS=0000007B ESP=96AE6C78
EFlags=00010212 CS=00000073 SS=0000007B EBP=96AE6CB0
Module=/home/csp/bin/ibm-java2-i386-50/jre/bin/libj9gc23.so
Module_base_address=B7885000
JVMDUMP006I Processing Dump Event "gpf", detail "" - Please Wait.
JVMDUMP007I JVM Requesting System Dump using '/home/csp/core.20060819.174148.28859.dmp'
JVMDUMP010I System Dump written to /home/csp/core.20060819.174148.28859.dmp
JVMDUMP007I JVM Requesting Snap Dump using '/home/csp/Snap0001.20060819.174148.28859.trc'
JVMDUMP010I Snap Dump written to /home/csp/Snap0001.20060819.174148.28859.trc
JVMDUMP007I JVM Requesting Java Dump using '/home/csp/javacore.20060819.174148.28859.txt'
JVMDUMP010I Java Dump written to /home/csp/javacore.20060819.174148.28859.txt
JVMDUMP013I Processed Dump Event "gpf", detail "".


It left behind a core dump file and trace file. In the one hour I tried to use IBM Java, it crashed twice, hanged 3 times. So I'd say, not a better record. 

I just don't know what to do with Ubuntu now, definitely not for running Java (for me!). Need to move to something more stable now, wasting too much time on this.

---

### Post by chonger on 2006-08-19
It sounds like you've made an honest effort to debug this, which makes this more complicated. I'll suggest a few things which may help you. I'll also keep this thread updated with my experience for your reference.

1. If an app hangs but does not crash, you may use jstack or kill -3 to find out what's happening in the JBM. The jmap command can help you examine memory usage. They both come with a 1.5 JDK.

2. It seems that your perm gen is at 97% usage. Perhaps you're using .intern() or some other issues that's using up the perm gen. Try increasing that too. The perm generation space does not automatically scale with -Xmx. Try -XX:MaxPermGen=128m.

3. If you suspect that the way the jvm is compiled is the issue. I think blackdown java allows you to compile the JVM yourself.

4. Try running something like Azureus for a while to see if it crashes. Do all Java apps crash, or does it happen under specific circumstances?

---

### Post by chonger on 2006-08-19
Sorry about the double post, but I just saw your comment about the log file (probably) not being useful. It's useful in a couple of senses:

1. You can indicate that it is a hotspot error, and the error type. 

2. You can show that the error occured while executing Eclipse/SWT code, not while executing your code (although it is possible that the true cause came from else where).

3. You can show the JVM args - It seems you are running Eclipse in server mode, which is kind of weird. But I doubt this is the cause of your problems.

---

### Post by LordHunter317 on 2006-08-20
ARe you using hte eclipse packages in the Ubuntu repositories or eclipse from source?

---

### Post by coconut on 2006-08-20
> **LordHunter317 said:**
> ARe you using hte eclipse packages in the Ubuntu repositories or eclipse from source?

It does not really matter which one I use, I get the same crash. I was hoping that the packages from Ubuntu repo would do better, so I've used it for a month or so (mainly Eclipse 3.1.0 and 3.1.2), but that's not helping either. I got basically the same problem, rouglhy 20 crashes a day.

---

### Post by coconut on 2006-08-20
> **chonger said:**
> 
4. Try running something like Azureus for a while to see if it crashes. Do all Java apps crash, or does it happen under specific circumstances?

Sorry, no torrent stuff at work. But it crashes Eclipse, it crashes Tomcat, it crashes JBoss, it crashes XXE (XMLMind editor), it crashes ant, it crashes its own javac (run on the command line),...
so I'd say it crashes all Java apps (at least all the Java apps that we are using).

Sometimes, it even crashed before ant had a chance to start up and load some libraries. The worst case was when I wrote a hello-world one-file program, and compile it manually with javac just for the heck of it, and it also crashed. Not reproducible evertyime, of course, but it did happened once, and that's too much already.

That's more than I can swallow. I still run Ubuntu at home, but I  definitely would not recommend anyone to do any Java stuff on this distro. Had been doing Java stuff on Linux since 1999, Ubuntu has been the worst of all in that area. Sad to say that, otherwise, it is a nice distro.

---

### Post by LordHunter317 on 2006-08-21
Have we verified the hardware is really good?  Does the box memtest86 and mprime clean for 24 hours?

---

### Post by chonger on 2006-08-23
I've been running Apache Cocoon for a while now. It is a full web-based Java+XML publishing application and no errors yet. I don't know if it is necessary to run memtest86 for a full 24 hours, but I think LordHunter's right; it might be a hardware issue.

---

### Post by LordHunter317 on 2006-08-23
Unless an error occurs, a minimum run is probably 24 hours.  Sometimes longer may be necessary.

---

### Post by kfjethro on 2006-08-26
We've had problems with the SUN JDK 1.5 as well. We kept getting hotspot errors. Using the -client option fixes the problem for us.

---

### Post by chonger on 2006-08-26
Note that I have seen similar issues on a Red Hat Enterpise 3 server as well. So this JVM problems is not unique to Ubuntu.

---

### Post by fredybiehl on 2006-08-28
Hello people,

Nice thing I found this thread. It feels like i´m not alone...
anyways, Im running a Ubuntu(6.06) server now for 3 weeks. It hosts a webapp witch runs on top of a Tomcat 5.5.12 and Sun´s jvm 1.5.0_07-b03.

By now I noticed 3 jvm crashes. When that happens I just run tomcat again and everything goes normal. Only at the second crash I noticed something really strange. All locale formating information on the app was appearing wrong (I mean dates and numbers). I restarted all the system and runned the app again: Back to normal (!?!).

All the hs_err_pid*** files states the following:

# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb795a049, pid=7517, tid=2992389040
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_07-b03 mixed mode, sharing)
# Problematic frame:
# V  [libjvm.so+0x264049]
#

(...) lots of info here (...) and ends like:

---------------  S Y S T E M  ---------------

OS:testing/unstable

uname:Linux 2.6.15-23-server #1 SMP Tue May 23 15:10:35 UTC 2006 i686
libc:glibc 2.3.6 NPTL 2.3.6 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:0.02 0.01 0.00

CPU:total 2 family 15, cmov, cx8, fxsr, mmx, sse, sse2, ht

Memory: 4k page, physical 2075220k(1546776k free), swap 979832k(979832k free)

vm_info: Java HotSpot(TM) Client VM (1.5.0_07-b03) for linux-x86, built on May  3 2006 01:46:28 by java_re with gcc 3.2.1-7a (J2SE release)
---------------------------------------------

Well, Im not an expert on jvm debuggin and Im not really sure what all that means. Should I just move to another distro and see how it goes? Could id be hardware?

I´ll be gald to hear any directions
Thanks, regards.

---

### Post by blaamann on 2006-09-05
Same problem with myself. I have tried various jdk's and they all crash and spit out that same error message:

#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb1ad1e5d, pid=30019, tid=2974362544
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x2ae5d]
#


I get this crash when I use Firefox (and the java plugin) trying to access an applet irc client.

I've tried to access the same applet on another distro (Mandriva) and it works without any problems so it is an Ubuntu issue indeed.

---

### Post by blaamann on 2006-09-05
apt-get remove ttf-gujarati-fonts fixed my problem that was FONT related.

---

### Post by spacepluk on 2006-09-05
I know it doesn't help, but I'm running fine with Eclipse and Ubuntu on my machine.

Saludosss

---

### Post by deenuy on 2008-10-16
Hello all,

 

 

I have requirement of accessing [http://localhost:8080/tc/webclient](http://localhost:8080/tc/webclient) using Domain server name say [www.tc.emerson.com](www.tc.emerson.com). Domain Name has been already configured in etc\host.

 

tc ear has been deployed in jboss-4.0.1sp1. 

 

I'm using Apache2 to virtual host for my jboss-4.0.1sp1 Application Server.  

 

Issue is, when I run [www.tc.emerson.com](www.tc.emerson.com) in browser, it is redirecting to jboss jmx-console page, instead of redirecting to [http://localhost:8080/tc/webclient](http://localhost:8080/tc/webclient)

 

Please can anyone help me out from this issue? It is bit urgent. It would be greatly appreciable.

 

Here is part of the Apache config:
Config of httpd.conf:
```

#Include mod_jk configuration file

Include conf/mod-jk.conf
```
 

 

Config of Mod-jk.conf:

```
LoadModule jk_module modules/mod_jk.so

 

#Where to find workers.properties

#Where to put jk shared memory

#Where to put jk logs

#Set the jk log level [debug/error/info]

#Select the timestamp log format

#JkOptions indicates to send SSK KEY SIZE

 

JkWorkersFile conf/workers.properties

JkShmFile        "D:/Apps/ApacheWebServer2.0/Apache2/logs/mod_jk.shm"

JkLogFile          "D:/Apps/ApacheWebServer2.0/Apache2/logs/mod_jk.log"

JkLogLevel        debug

 

JkLogStampFormat "[%a %b %d %H:%M:%S %Y]"

JkOptions +ForwardKeySize +ForwardURICompatUnparsed -ForwardDirectories

 

<VirtualHost *:80>

    ServerName               www.tc.emerson.com

    ServerAdmin Deenanath.Yadav@emerson.com    

    LogLevel warn

    CustomLog                logs/ tc.emerson.com.access.log combined

    ErrorLog                    logs/ tc.emerson.com.error.log

    ServerSignature Off

            

    JkAutoAlias               /tc/webclient

    JkMountFile               conf/uriworkermap.properties

</VirtualHost>
```
 

 

Config of workers.properties:

```
# Define list of workers that will be used

# for mapping requests

# The configuration directives are valid

# for the mod_jk version 1.2.18 and later

#

 

worker.list=worker1

worker.worker1.type=ajp13

worker.worker1.host= localhost

worker.worker1.port=8009

worker.worker1.lbfactor=1
```
 

 

Config of uriworkermap.properties:

```
/tc/webclient/*=worker1 

/tc/webclient=worker1 

/*=worker1
```
 

 

Here is part of the Jboss config:

JBoss Configuration:

 

Config of Server.xml:
```

<Engine name="jboss.web" defaultHost="localhost" jvmroute="worker1">

<Logger className="org.jboss.web.tomcat.Log4jLogger"

            verbosityLevel="WARNING"

            category="org.jboss.web.localhost.Engine"/>

 

         <Host name="localhost"

            autoDeploy="false" deployOnStartup="false" deployXML="false">

                                    <Alias>www.tc.emerson.com</Alias>

                                    <Alias>tc.emerson.com</Alias>

<Valve className="org.apache.catalina.valves.AccessLogValve"

                prefix=" tc.emerson.com _log." suffix=".log"

                pattern="common" directory="${jboss.server.home.dir}/log"/>
```
 

 

Config of jboss-web.xml:

```
<jboss-web>

    <context-root>/</context-root>

    <virtual-host>www.tc.emerson.com</virtual-host>   

</jboss-web>
```
 

 

Am I missing anything in configuration? I couldn’t find any clue thru googling.  Can anyone help me out form this issue.


Any suggestions are greatly appreciated.

 

Waiting for reply with anticipation.

 

Thanks,

Deenu

---

### Post by jespdj on 2008-10-16
Deenu, why are you adding a completely unrelated question to a thread that is more than two years old? Start a new thread with your question.

---

