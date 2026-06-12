---
title: "Wimba Classroom - errors on Chrome on Ubuntu 12.04 and Firefox on Wine"
date: 2012-08-10
forum: New to Ubuntu
---

### Post by Qianling on 2012-08-10
Hi, I'm running Ubuntu 12.04 with Cinnamon Desktop. I've been trying to access Wimba Classroom on a university website and have not been successful. 




I've tried two ways so far:


1) Via Chrome installed on Ubuntu

I've managed to enter the classroom successfully, the plugins have loaded but I get a JSecure door error.

As you can see in this image below, I've managed to type something into the main room, but errors persist.

[IMG]http://i.imgur.com/dDJkk.png[/IMG]


This pic shows the Java version that Chrome is running.

[IMG]http://i.imgur.com/x67jt.png[/IMG]




2) Via Firefox installed on Wine

I uninstalled Firefox from Ubuntu, installed Firefox on Wine and tried to access the class again.

As you can see, Firefox is missing the Java plugin.

[IMG]http://i.imgur.com/onLJl.png[/IMG]


These are the plugins that Firefox has.

[IMG]http://i.imgur.com/2SC4f.png[/IMG]



These are the messages I get regarding Java on Firefox on Wine.

[IMG]http://i.imgur.com/WOsCt.png[/IMG]

[IMG]http://i.imgur.com/LPr3L.png[/IMG]

[IMG]http://i.imgur.com/6hP40.png[/IMG] 




I like to find out how I can either:

a)  get rid of the errors in Chrome, or 

b) install Java version 7 update 4 in Firefox on Wine, so I can test if that helps me get into the classroom without errors.


I got rid of Windows Vista and installed Ubuntu on my laptop recently. It runs so much faster and much more smoothly than before, I would _really_ regret having to go back to Windows because of this. ;)


Your help and assistance will be greatly appreciated, and many thanks in advance!

--
Qianling

---

### Post by PhantomTurtle on 2012-08-11
Hmmm, so it doesn't work at all with the linux version of firefox? This thread [here]("http://www.wimba.com/forum/viewthread/169/#296") says that there is no linux support for wimba classroom. This is from 2010 but I see the problem has not been fixed yet. You said you had Windows vista before, you could install that in a virtual machine. Just install virtualbox from the Software Center. Then get your copy of vista and install it. You can also dual-boot if you prefer.

Java in Wine
Not sure if this will work or how it will even work with the linux version of java already installed. A virtual machine is the best option in my opinion.

---

### Post by Qianling on 2012-08-11
Thanks.

I found a very old thread here which gives a workaround for an older version of Java and Ubuntu.

[http://ubuntuforums.org/showpost.php?p=11617121&postcount=17](http://ubuntuforums.org/showpost.php?p=11617121&postcount=17)


I would like to try this, but the thing is that I don't understand the instructions very well.

> goto Java SE Runtime Environment 6u20

download the bin to desktop
jre-6u20-linux-i586.bin

I unpacked the file with

cd Desktop
then ran chmod -x jre-6u20-linux-i586.bin
then ran ./jre-6u20-linux-i586.bin

then I went to the directory /usr/lib/xulrunner-addons/plugins

from there i ran sudo ln -s /home/ubuntu/Desktop/jre1.6.0_20/plugin/i386/ns7/libjavaplugin_oji.so

I don't know how it just worked all of a sudden I tried several java versions and this is the only one that worked. 

I am thinking it has something to do with this part

There are 4 alternatives which provide `java'.

Selection Alternative
-----------------------------------------------
1 /usr/bin/gij-4.2
2 /usr/bin/gij-4.1
* 3 /usr/bin/cacao
+ 4 /usr/lib/jvm/java-gcj/jre/bin/java





How does one run "./jre-6u20-linux-i586.bin" ? Tried this in Terminal and got 

```
bash: ./jre-6u33-linux-i586.bin: No such file or directory
```


I appreciate it if someone could decipher this and give specific instructions for what I should be typing into my terminal.

I hope this will give me a fix, 'cos I suspect that Wimba Voice is causing the problems in Wimba Classroom.

Many thanks in advance.

--
Qianling

---

### Post by Qianling on 2012-08-11
Hi, I'm still hoping someone will see this and help me with the instructions. Thanks.

---

### Post by flurospar on 2012-08-11
Uninstall all previous versions of Java plugin. We will not use Wine for the purpose, we will use Firefox/Chrome + Java (natively):

Get the required file for Ubuntu from [http://www.oracle.com/technetwork/java/javase/downloads/java-se-jre-7-download-432155.html](http://www.oracle.com/technetwork/java/javase/downloads/java-se-jre-7-download-432155.html) .

You most probably want [http://download.oracle.com/otn-pub/java/jdk/7/jre-7-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7/jre-7-linux-i586.tar.gz) (assuming a 32-bit machine) so go ahead and download the file in your home folder.

Make sure you have no folder with name starting with "jre"

After downloading the file open up the terminal and run:

```
tar -xf jre-7u*<version>*-linux-i586.tar.gz && cd jre* && chmod +x -R *
```After that type
```
ls
```and paste the output here so that I can see what is inside the archive, since I am unsure what is inside the archive (and my connection is too slow to download that 33MB thing).

After you paste the output of ls, I can help you further.

---

### Post by Qianling on 2012-08-19
Hi, I'm sorry for the delay in replying. I've had to do a clean reinstall of Ubuntu 'cos it was freezing/hanging more often than Windows Vista ever did. 

I tried to uninstall Java following this site: [http://akbarahmed.com/2012/06/24/uninstall-java-from-ubuntu-linux/](http://akbarahmed.com/2012/06/24/uninstall-java-from-ubuntu-linux/) but failed! I changed the version number too. 


```


joan@Lenni:~$ sudo update-alternatives --display java
[sudo] password for joan: 
java - auto mode
  link currently points to /usr/lib/jvm/java-7-oracle/jre/bin/java
/usr/lib/jvm/java-7-oracle/jre/bin/java - priority 1
  slave java.1.gz: /usr/lib/jvm/java-7-oracle/man/man1/java.1.gz
Current 'best' version is '/usr/lib/jvm/java-7-oracle/jre/bin/java'.
joan@Lenni:~$ sudo update-alternatives --remove "java" "/usr/lib/jvm/jdk1.7.0_04/bin/java"
joan@Lenni:~$ sudo update-alternatives --remove "javac" "/usr/lib/jvm/jdk1.7.0_04/bin/javac"
joan@Lenni:~$ sudo update-alternatives --remove "javaws" "/usr/lib/jvm/jdk1.7.0_04/bin/javaws"
joan@Lenni:~$ java -version
java version "1.7.0_06"
Java(TM) SE Runtime Environment (build 1.7.0_06-b24)
Java HotSpot(TM) Server VM (build 23.2-b09, mixed mode)
joan@Lenni:~$ javac -version
javac 1.7.0_06
joan@Lenni:~$ sudo update-alternatives --remove "java" "/usr/lib/jvm/jdk1.7.0_06/bin/java"
joan@Lenni:~$ sudo update-alternatives --remove "javac" "/usr/lib/jvm/jdk1.7.0_06/bin/javac"
joan@Lenni:~$ sudo update-alternatives --remove "javaws" "/usr/lib/jvm/jdk1.7.0_06/bin/javaws"
joan@Lenni:~$ java -version
java version "1.7.0_06"
Java(TM) SE Runtime Environment (build 1.7.0_06-b24)
Java HotSpot(TM) Server VM (build 23.2-b09, mixed mode)
joan@Lenni:~$ 
joan@Lenni:~$ java -version
java version "1.7.0_06"
Java(TM) SE Runtime Environment (build 1.7.0_06-b24)
Java HotSpot(TM) Server VM (build 23.2-b09, mixed mode)
joan@Lenni:~$ 
joan@Lenni:~$ sudo update-alternatives --display java
java - auto mode
  link currently points to /usr/lib/jvm/java-7-oracle/jre/bin/java
/usr/lib/jvm/java-7-oracle/jre/bin/java - priority 1
  slave java.1.gz: /usr/lib/jvm/java-7-oracle/man/man1/java.1.gz
Current 'best' version is '/usr/lib/jvm/java-7-oracle/jre/bin/java'.


```

So I am stuck at "uninstall Java". Can someone give pointers please?

Thanks muchly.

---

### Post by PJSingh5000 on 2012-09-08
I am using Ubuntu 12.04 x64.  I am using Firefox 15.0.
I have installed Oracle's JDK Java SE 7u7 (from jdk-7u7-linux-x64.tar.gz).
I have configured Firefox to use the Java Plug-in 1.7.0_07 from this JDK installation.

When I run the Wimba Wizard, here is the error from the Wimba log window.  (You can see the log file from the Wimba Options button in the Wizard).  (Note I replaced my home folder with <user_name>, below).

```

[SIZE="1"]Sat Sep 08 16:10:06 EDT 2012 - [warn] DoorController.run(), unable to launch agent
java.lang.Exception: java.io.IOException: Cannot run program "/home/<user_name>/.horizonwimba/JSecureDoor/horizonmedia_2.3.2/data/horizonmedia" (in directory "/home/<user_name>/.horizonwimba/JSecureDoor/horizonmedia_2.3.2/data"): error=2, No such file or directory
	at com.hw.client.util.n.<init>(SourceFile:34)
	at com.hw.client.util.b.a(SourceFile:119)
	at com.hw.client.util.b.b(SourceFile:64)
	at WC_JS.bw.run(SourceFile:252)
	at java.lang.Thread.run(Thread.java:722)[/SIZE]

```

Because the error says "No such file or directory," I verified that the following file does exist:
/home/<user_name>/.horizonwimba/JSecureDoor/horizonmedia_2.3.2/data/horizonmedia

This file has executable permissions.  If I try to run the file directly from the commandline, I get the following error:
```

$ cd ~/.horizonwimba/JSecureDoor/horizonmedia_2.3.2/data
$ ./horizonmedia 
bash: ./horizonmedia: No such file or directory

```

I then checked if this file is compiled for x64 bit architectures...
```

$ file horizonmedia 
horizonmedia: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.8, not stripped

```

Obviously it is for 32-bit architectures, AND an older Linux kernel!

For comparison, here is my machines architecture...
```

$ uname -a
Linux Computer-1000 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

This may not be the same issue others are experiencing.  There are other errors in the logfile.  I have attached the full log file (replacing my home directory with <user_name>.  Maybe the output will help someone figure out a work-around.

I will see if I can get this 32 bit program to run on my x64 machine. I will post more if I make any progress.

Finally, I would like to make one comment:  It is deplorable that a company creating software for online courses offered by a university has not built a client that works on Linux/Unix!  Most universities rely on Linux/Unix heavily!  It's just unbelieveable!

---

### Post by PJSingh5000 on 2012-09-08
OK, I got the 32 bit horizonmedia program to run on my x64 machine.  I simply installed the x32bit compatability libraries:
```

$ sudo apt-get install ia32-libs

```

Now the Wimba Control Bar actually loads in the Setup Wizard...
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=223892&stc=1&d=1347138113[/IMG]

However, I am now getting a few more errors...
```

[SIZE="1"]Sat Sep 08 16:51:17 EDT 2012 - [debug] IAX_ERR Expression 'SetApproximateSampleRate( pcm, hwParams, sr )' failed in '/home/buildbot/ct-ubuntu-7.10/coretech-trunk-ubuntu-7.10/build/portaudio/src/hostapi/alsa/pa_linux_alsa.c', line: 1305
Sat Sep 08 16:51:17 EDT 2012 - [debug] IAX_OUT iaxc_ev_call_state	0	38	wizard-recording	guest@stevenslive.wimba.com:4569/wizard-recording	Not Available	default
Sat Sep 08 16:51:17 EDT 2012 - [debug] IAX_ERR Expression 'PaAlsaStreamComponent_InitialConfigure( &self->capture, inParams, self->primeBuffers, hwParamsCapture, &realSr )' failed in '/home/buildbot/ct-ubuntu-7.10/coretech-trunk-ubuntu-7.10/build/portaudio/src/hostapi/alsa/pa_linux_alsa.c', line: 1876
Sat Sep 08 16:51:17 EDT 2012 - [debug] IAX_OUT iaxc_ev_text	-1	1	Call 0 accepted
Sat Sep 08 16:51:17 EDT 2012 - [debug] IAX_OUT iaxc_ev_text	-1	2	failed to service audio
Sat Sep 08 16:51:17 EDT 2012 - [debug] IAX_ERR Expression 'PaAlsaStream_Configure( stream, inputParameters, outputParameters, sampleRate, framesPerBuffer, &inputLatency, &outputLatency, &hostBufferSizeMode )' failed in '/home/buildbot/ct-ubuntu-7.10/coretech-trunk-ubuntu-7.10/build/portaudio/src/hostapi/alsa/pa_linux_alsa.c', line: 2000
Sat Sep 08 16:51:17 EDT 2012 - [debug] IAX_ERR PortAudio error at Unable to open streams: Invalid error code (value greater than zero)
Sat Sep 08 16:51:17 EDT 2012 - [debug] IAX_ERR IAXCLIENT: Call 0 accepted
Sat Sep 08 16:51:17 EDT 2012 - [debug] IAX_ERR IAXCLIENT: failed to service audio
Sat Sep 08 16:51:17 EDT 2012 - [debug] processHWEvent(), state => 38
Sat Sep 08 16:51:17 EDT 2012 - [info] call status update, state => outgoing
Sat Sep 08 16:51:17 EDT 2012 - [debug] changing call state, state => connecting
Sat Sep 08 16:51:17 EDT 2012 - [debug] setCallState(), state => connecting
Sat Sep 08 16:51:17 EDT 2012 - [info] iax status, msg => Call 0 accepted
Sat Sep 08 16:51:17 EDT 2012 - [info] iax notice, msg => failed to service audio
Sat Sep 08 16:51:17 EDT 2012 - [debug] IAX_OUT iaxc_ev_text	-1	2	failed to service audio[/SIZE]

```

The full log file is attached.

This looks like the linux audio driver "ALSA" is not working. I think Ubuntu 12.04 uses PulseAudio instead of ALSA.

I will continue to work on this.  If anyone has input/suggestions, please post.

---

### Post by Kamallo on 2012-10-17
It seems to be an issue in PortAudio rather than in Wimba, depending on the audio card you have.
In my Ubuntu 12.04 (64 bit) I got it fixed by running this:

```
export PA_ALSA_PLUGHW=1
```

before running Firefox or Chrome from the terminal / command line.
After this, both audio playing and recording worked fine in Wimba.

Good luck!

-- 
Kamal

---

