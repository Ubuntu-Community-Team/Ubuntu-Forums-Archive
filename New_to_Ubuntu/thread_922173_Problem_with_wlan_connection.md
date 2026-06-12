---
title: "Problem with wlan connection"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by matthew_1 on 2008-09-17
Hi,

I have lately installed Xubuntu 7.x on an old hardware (Compaq Armada 700 MHz, 312 MB RAM, 9,5 GB HDD). Everything looks fine so far, except for the network connection. The only option I can connect to the network is over wifi, and the computer has the "external" USB wlan adapter Linksys WUSB54GC. The computer recognises the adapter, shows the name of my home network, asks for WEP key, I enter the key and it is trying to connect for about a minute, but then asks for the network key again. Once it connected yesterday and I could browse a few web pages in Firefox, but then the connection was lost and it started asking for the network key again. The key I type is absolutely correct, I have checked it over and over several times. I am beginning to lose hope already.... 

I would highly appreciate any ideas-suggestions!

---

### Post by lemmy999 on 2008-09-17
Having had a similar problem with a recent Xubuntu install on an old laptop I can recommend the "how to" here [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495).

Make sure you also do a eth0 down as well ( thats what got me)

---

### Post by matthew_1 on 2008-09-18
Tried a few hours yesterday, but with no success. Most installations guides refer to downloading ndiswrapper and the driver via terminal, but I do not have any connection available. I have ndiswrapper and WUSB54GC driver downloaded from another computer and on the flash stick. Is there any way to manage without the terminal? I don't know anything about the terminal tasks in Linux. 

Sorry for the questions obviously funny for people familiar with Linux. This is my first trial with Ubuntu, and Linux OS in general. And it is all way too different from the Windows/Mac world I've lived in so far.... I do hope to find a way for solving this issue and getting Ubuntu running as it should; there's no way back to XP anymore:)

---

### Post by lemmy999 on 2008-09-18
My understanding is that if your PC is showing the ESSID of your WAP then the driver is installed. You shouldn't need ndiswrapper etc!

Have you tried the link I posted?

---

### Post by matthew_1 on 2008-09-18
I was wondering, could I try installing Ubuntu 8.04 (should be more "plug-and-play" than previous versions)? Is the old laptop's hardware configuration sufficient? That was my son's computer until he got iMac, now the old laptop is free for testing and learning Linux distros. It is well worth trying.

---

### Post by blazemore on 2008-09-18
Definately install 8.04. It has a much better (more recent anyway) kernel, with better plug-n-play support. Or, wait a few weeks for 8.10, and do a clean reinstall of that. I found that 8.10 (alpha) detected my wireless hardware out the box, whereas earlier versions required hours of tweaking ndiswrapper.

---

