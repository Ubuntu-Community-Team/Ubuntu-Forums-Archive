---
title: "Howto: Driver installation for Asrock motherboad integrated realtek AC'97 soundcard"
date: 2005-07-22
forum: Outdated Tutorials &amp; Tips
---

### Post by linuxeiro on 2005-07-22
Hello. I explain here how to install a driver for realtek AC'97 soundcard, since Ubuntu has some problems recognizing this sound card when it is integrated in the motherboard Asrock K8 upgrade 760GX. First of all, you have to download the driver from 
[http://www.realtek.com.tw/downloads/dlac97-2.aspx?lineid=5&famid=12&series=8&Software=True#8Unix%20(Linux](http://www.realtek.com.tw/downloads/dlac97-2.aspx?lineid=5&famid=12&series=8&Software=True#8Unix%20(Linux))
	
Once you have downloaded the linux_r32.zip file, you have to unzip it. One of the unzipped files is azx.tar.bz2 . Unzip this file too, and you will get a directory called alsa-driver-1.0.9rc4a. 

Before compiling and installing, you will probable to get some applications with Synaptic. Open Synaptic and search for "gcc" , "linux-source" and "linux-headers" and install them.  Don't forget to update Ubuntu before doing this. Once you have this packages installed, you can go on: open a root terminal and write the following commands. After rebooting Ubuntu, your integrated ac'97 soundcard will be working. 

 ./configure

 make

 make install

 ./snddevices

---

### Post by PAM on 2005-07-24
[QUOTE=linuxeiro]Hello. I explain here how to install a driver for realtek AC'97 soundcard, since Ubuntu has some problems recognizing this sound card when it is integrated in the motherboard Asrock K8 upgrade 760GX. First of all, you have to download the driver from 
[http://www.realtek.com.tw/downloads/dlac97-2.aspx?lineid=5&famid=12&series=8&Software=True#8Unix%20(Linux](http://www.realtek.com.tw/downloads/dlac97-2.aspx?lineid=5&famid=12&series=8&Software=True#8Unix%20(Linux))
	
Once you have downloaded the linux_r32.zip file, you have to unzip it. One of the unzipped files is azx.tar.bz2 . Unzip this file too, and you will get a directory called alsa-driver-1.0.9rc4a. 

Before compiling and installing, you will probable to get some applications with Synaptic. Open Synaptic and search for "gcc" , "linux-source" and "linux-headers" and install them.  Don't forget to update Ubuntu before doing this. Once you have this packages installed, you can go on: open a root terminal and write the following commands. After rebooting Ubuntu, your integrated ac'97 soundcard will be working. 

 ./configure

 make

 make install

 ./snddevices[/QUOTE]
 
Linuxeiro, 

I have exactly this problem and am looking forward to trying your solution. My question is:

Where should the various files and directories wind up after they are uzipped?

I look forward to your reply.

Thanks and Enjoy,

PAM

---

### Post by storkur on 2005-11-07
Have this same problem on Kubuntu. Can you tell me how to fix it, does not work the same way as with ubuntu.


Thanks

---

### Post by TFleck on 2005-12-04
Im having this problem, but i cant get it working.

when execute the configure script i get this error:

```

checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

Someone know how to solve it?

---

### Post by eZtaR on 2005-12-25
[QUOTE=TFleck]Im having this problem, but i cant get it working.

when execute the configure script i get this error:

```

checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

Someone know how to solve it?[/QUOTE]


A sudo apt-get install gcc should do the job :)

---

