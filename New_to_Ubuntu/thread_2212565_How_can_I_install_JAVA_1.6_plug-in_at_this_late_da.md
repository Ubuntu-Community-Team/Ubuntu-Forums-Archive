---
title: "How can I install JAVA 1.6 plug-in at this late date?"
date: 2014-03-21
forum: New to Ubuntu
---

### Post by AbleTassie on 2014-03-21
[SIZE=3]I need to install the JAVA 1.6 plug-in at this late date, even though it is now old and archived. The reason I need to do this is explained in my previous post at [http://ubuntuforums.org/showthread.php?t=2211752](http://ubuntuforums.org/showthread.php?t=2211752) and below. Basically WebEx only supports older versions of Linux with JAVA 1.6 for WebEx meetings with a large govt organization (LGO), (see info at previous post and under my name below). 
[U][B]
I had thought I had solved this problem[/B][/U] by running a simulated "dry run" meeting with WebEx tech support using CentOS 6.5 as suggested on this forum. I had installed a later form of JAVA, jre-7u51-linux-i586. _**The first dry run worked.**_ But when I double checked with a later "dry run" simulation that showed the LGO's actual WebEx meeting webpage (using CentOs 6.5, the same later JAVA plugin with WebEx tech support), it did not work. I got an error message related to JAVA. **_I still appreciate very much the advice I got on this forum;_** I think It is entirely possible this error is related to the newer JAVA, not Centos 6.5.

So I installed Ubuntu 11.10 (I know this is a security risk, it's archived, etc., but it is supported by WebEx for use with the LGO) and I installed JAVA 10.51.2 (I think this is JAVA 1.70_51). And I tried yet another dry run with WebEx tech support with Ubuntu 11.10 & JAVA 10.51.2. Again, it did not work. I got an error message related to JAVA. [U][B]

So at this point I only have two options: use MS WIndows XP SP3 or an older Linux (e.g., Ubuntu 11.10) with JAVA 1.6.[/B][/U] (I could also buy a new computer or a new operating system, but I don't want to do that). _**I only plan to use the old operating system (whether Linux or WIndows XP) for this one activity.**_ And I'll use Ubuntu 12.04 LTS, which I like a lot, for everything else--I'll dual boot.
    
QUESTION: How can I install JAVA 1.6 plug-in at this late date?

Thanks,

R.[U][B]

Summary of WebEx crossplatform support for use with the LGO (Large Govt Organization):[/B][/U]
[/SIZE][TABLE="class: cms_table_body, width: 100%"]
[TR="bgcolor: #efefef"]
[TD="width: 12%, align: center"][SIZE=3]
[/SIZE][/TD]
[TD="width: 14%, align: center"][SIZE=3]
[/SIZE][/TD]
[/TR]
[TR="bgcolor: #ffffff"]
[TD="align: left"][SIZE=3]**Operating          Systems**[/SIZE][/TD]
[TD="class: cms_table_bodySmall"][SIZE=3][B]Windows
[/B]XP SP3, 2003 Server,         
        Vista 32-bit/64-bit, 
       Windows 7 32-bit/64-bit,
     Windows 8 32-bit/64-bit[/SIZE][/TD]
[TD="class: cms_table_bodySmall"][SIZE=3]**Mac OS X* **10.5, 10.6, 10.7, 10.8, 10.9
[/SIZE][/TD]
[TD="class: cms_table_bodySmall"][SIZE=3][B]Linux

[/B]Ubuntu   10x and 11x (Gnome),
        Red Hat 5, 6, 
        Open SuSE 11.4
        Fedora 15, 16 (all   32-bit)[/SIZE][/TD]
[/TR]
[/TABLE]

[SIZE=3]**Notes**: 

 WebEx       will support any Linux distribution as long as it meets the following       requirements:
 
[/SIZE]
[LIST]
[*][SIZE=3]Kernel:        2.6 or later[/SIZE] 
[*][SIZE=3]X        Lib: X11R6 or later compatible[/SIZE] 
[*][SIZE=3] C++        Lib: libstdc++ 6[/SIZE] 
[*][SIZE=3]Desktop        Environment: XFce 4.0 or later, KDE, Ximian, Gnome[/SIZE] 
[*][SIZE=3]GDK/GTK+        version: 2.0 or later[/SIZE] 
[*][SIZE=3]Glib:        2.0 or later[/SIZE] 
[*][SIZE=3]_**Java 1.6 **_
[/SIZE] 
[/LIST]

---

### Post by AbleTassie on 2014-03-21
[SIZE=3]BTW, I know OpenJDK Java 6 Runtime may be in the software center for download, but I am not sure this will work for WebEx with the LGO site. I think only the actual official archived JAVA 1.6 from Oracle is officially supported. So I am wondering about downloading and installing the official archived JAVA 1.6.

Thanks,

R.
[/SIZE]

---

### Post by QIII on 2014-03-21
Hello!

You can still download 1.6 [here]("http://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase6-419409.html").

The installation instruction [here]("https://sites.google.com/site/easylinuxtipsproject/java") should work, but remember to use the correct file names.

Please keep in mind that this is a *dangerous *move and you should change your alternative back to the most recent Oracle Java 7 release when you are not using this for WebEx.

---

### Post by 1clue on 2014-03-21
OK it's a pain to do this, but here's how I did it to support legacy code from a VM which has no Internet connectivity:

[LIST=1]
[*]Download the java you want from oracle's java site.
[*]Unzip it into some directory, I use: **/opt/java6/jdk-<version>** and then **ln -s jdk-<version> current** from the /opt/java6 directory so I can upgrade minor version number and not have to change environment variables.
[*]If webex has a wrapper script which sets up the environment, then use that for step 5.
[*]If there is no wrapper script then make one.
[*]In the wrapper script, **export** **JAVA_HOME****=****/opt/java6/current**.
[*]Also in the wrapper script, put **$JAVA_HOME/bin** into the **$PATH ***IN FRONT OF the rest of the PATH!*
[*]Start the webex wrapper script.
[/LIST]

This is off the top of my head, but it's pretty much what I do.

I deal with systems where we build a product which goes to a specific customer, and then we are contractually required to support that exact setup for so many years.  Using a PPA version of one of the critical tools is not an option, because an upgrade will destroy the environment and break our contract.

That said, you need to be really careful to not accidentally use that Java for some random thing on the Internet.  There are some really good reasons why Java6 is no longer supported.  I strongly recommend that if you're using Java6 you should minimize your risk as much as possible.  For example:
[LIST=1]
[*]Install a VM
[*]Follow the instructions above and make webex work
[*]Shut the VM down.
[*]Copy it/back it up completely.
[*]Use the VM when you need webex.
[*]If you get a problem, just restore your backup and start again.
[/LIST]

This avoids damage to a system you might need by avoiding an old Java on your good system.

---

### Post by AbleTassie on 2014-03-22
> **QIII said:**
> Hello!

You can still download 1.6 [here]("http://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase6-419409.html").

The installation instruction [here]("https://sites.google.com/site/easylinuxtipsproject/java") should work, but remember to use the correct file names.

Please keep in mind that this is a *dangerous *move and you should change your alternative back to the most recent Oracle Java 7 release when you are not using this for WebEx.

Thanks QIII (Moderator),

The installation instructions [here]("https://sites.google.com/site/easylinuxtipsproject/java") say: *"For 32 bit you want **Linux**; the name of this file ends on [COLOR=#0000FF].tar.gz[/COLOR]. You don't want** Linux RPM**, of which the file name ends on [COLOR=#0000FF]i586.rpm[/COLOR] Because RPM is not built for Ubuntu and Linux Mint, but for other Linux distro's."* 

But the only files for downloading 1.6  [here]("http://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase6-419409.html") that I seem to be able to find that I think are 32 bit Linux are labelled ".bin" and the only .tar.gz files are 64 bit. My PC is 32 bit.

QUESTION: Do you have any comments about this?  

R.

---

### Post by AbleTassie on 2014-03-22
> **1clue said:**
> OK it's a pain to do this, but here's how I did it to support legacy code from a VM which has no Internet connectivity:

[LIST=1]
[*]Download ... 
[/LIST]

This is off the top of my head, but it's pretty much what I do.

  For example:
[LIST=1]
[*]Install a VM 
[/LIST]
 This avoids damage to a system you might need by avoiding an old Java on your good system.

1clue,

Thanks for your advice -- I appreciate it. I am not sophisticated enough, at least not yet, to do the programming you suggest. I have been studying terminal commands recently. I did some computer programming years ago in Fortran, in C, in C++ and Pascal. I think the Terminal programming language for Ubuntu is similar to C, isn't it? I was pretty good at, and liked, the programming I did years ago.

I only have 2 GB of RAM, so a virtual machine (VM) is not a real option for me.

Thanks,

R.

---

### Post by 1clue on 2014-03-22
RMcGinnis,

The default shell for Ubuntu and most Linux distributions is bash.  It's not really like C.  There are alternative shells you can use, including csh which is a lot like C.

You're going to have to learn to set your PATH fairly soon I think.  If you want Java6 you will almost certainly need to do it manually.

Good luck.

---

### Post by AbleTassie on 2014-03-23
Thanks, I'll see it I can find a manual of terminal commands.

R.

---

### Post by 1clue on 2014-03-23
Search on "bash tutorial" and that's a good place to get started.  And if you need help, don't hesitate to post a thread with specific details, there is a lot of expertise on this forum.

---

### Post by AbleTassie on 2014-03-24
> **1clue said:**
> Search on "bash tutorial" and that's a good place to get started.  And if you need help, don't hesitate to post a thread with specific details, there is a lot of expertise on this forum.

Thanks so much 1clue. Here are some links regarding bash tutorial I turned up just from searching these forums:

[http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)

**An A-Z Index of the Bash command line for Linux.**
[http://shafordesigns.com/CISC_323/A-...or%20Linux.pdf]("http://shafordesigns.com/CISC_323/A-Z%20Index%20of%20the%20Bash%20command%20line%20for%20Linux.pdf")

the advanced bash scripting guide:

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

mywiki.wooledge.org/BashGuide

[http://www.linuxcommand.org/writing_shell_scripts.php](http://www.linuxcommand.org/writing_shell_scripts.php)

linuxcommand.org/tlcl.php

[www.tldp.org/LDP/abs/html/index.html](www.tldp.org/LDP/abs/html/index.html)


[http://www.faqs.org/docs/Linux-HOWTO...tro-HOWTO.html]("http://www.faqs.org/docs/Linux-HOWTO/Bash-Prog-Intro-HOWTO.html")

R.

---

### Post by 1clue on 2014-03-24
That top one is the place I would start.

If you're going to administer a Linux box, sooner or later you'll have to dive into scripting.  Sorry for pushing you into that, but if you don't do it you'll cripple yourself.  Lots of people here, including me, will be glad to help with specific questions.

---

