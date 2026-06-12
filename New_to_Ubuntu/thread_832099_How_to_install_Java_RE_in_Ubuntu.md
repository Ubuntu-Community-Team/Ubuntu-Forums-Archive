---
title: "How to install Java RE in Ubuntu"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by sajackson on 2008-06-17
Hi, although the first operating system I used was Unix on a Sun workstation I have been using Windows exclusively for many years now. The main reason why I have decided to try Linux is because Windows Vista is so bad I really don't like the idea of finally being forced to use it!! I decided to try Ubuntu because I heard that DELL is now distributing it with some of its computers and when I mentioned it to a friend who is a Linux administrator he said it would be ideal for me.

I built myself another computer with parts I had in my various spares boxes: AMD Duron 1.3Ghz, 512Mb DDR, nVidia MX-440-8X 64Mb, 160Gb HDD, DVD writer. I did a default install and let Ubuntu partition the disk and everything else. I have downloaded and installed all the updates and installed the flash plugin for Firefox.

All seems to be working very nicely and I only had to install the nVidia graphics accelerator driver which was downloaded and installed for me anyway. I am using it now to write this. I must admit I am very impressed and am liking Ubuntu more and more as I am using it!:)

One thing (for now) I am a bit confused about is this: I am not sure if any form of Java Runtime Environment is installed.... which version to install.... what the installation file is called and where to download it.... how to install it.... how to test if it is working OK.

If anyone can help me that would be great.

Anyway, hi to all and expect to be getting many more questions from me as I learn.

---

### Post by stchman on 2008-06-17
> **sajackson said:**
> Hi, although the first operating system I used was Unix on a Sun workstation I have been using Windows exclusively for many years now. The main reason why I have decided to try Linux is because Windows Vista is so bad I really don't like the idea of finally being forced to use it!! I decided to try Ubuntu because I heard that DELL is now distributing it with some of its computers and when I mentioned it to a friend who is a Linux administrator he said it would be ideal for me.

I built myself another computer with parts I had in my various spares boxes: AMD Duron 1.3Ghz, 512Mb DDR, nVidia MX-440-8X 64Mb, 160Gb HDD, DVD writer. I did a default install and let Ubuntu partition the disk and everything else. I have downloaded and installed all the updates and installed the flash plugin for Firefox.

All seems to be working very nicely and I only had to install the nVidia graphics accelerator driver which was downloaded and installed for me anyway. I am using it now to write this. I must admit I am very impressed and am liking Ubuntu more and more as I am using it!:)

One thing (for now) I am a bit confused about is this: I am not sure if any form of Java Runtime Environment is installed.... which version to install.... what the installation file is called and where to download it.... how to install it.... how to test if it is working OK.

If anyone can help me that would be great.

Anyway, hi to all and expect to be getting many more questions from me as I learn.

For 32 bit use the following.
```
sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```

For 64 bit use the following.
```
sudo apt-get install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin
```

The SUN JRE is more compatible, but they don't make a 64 bit plugin as of yet.

---

### Post by Pjotr123 on 2008-06-17
This is even easier and gives you 100 % multimedia support:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---

### Post by Nepherte on 2008-06-17
I always prefer to use the sun packages when possible. When you have a 32bit system, there's no problem. When you have a 64bit system, there's no browser plugin so for the browser I use the openjdk, for the rest sun.

---

### Post by sajackson on 2008-06-17
Hi again, Thanks for the replies. This may sound like a really dumb question but how do I know which version of Ubuntu I am running? 32 or 64 bit? I installed from a copy of a DVD I got from a friend.:-k

---

### Post by kalesh7 on 2008-06-17
> **sajackson said:**
> Hi again, Thanks for the replies. This may sound like a really dumb question but how do I know which version of Ubuntu I am running? 32 or 64 bit? I installed from a copy of a DVD I got from a friend.:-k
```
file /bin/bash | cut -d' ' -f3
```

---

### Post by Abu_Dayya on 2008-06-17
java6 didn't install correctly for me. I'm using java5

---

### Post by sajackson on 2008-06-18
Thanks, kalesh7, that worked fine - it is 32bit as I suspected.

Another couple of things I am a bit confused about:-

1. My network icon at the top of the screen has an exclamation mark on it (!) and says "No network connection". The thing is I am using it now and connected to the internet fine (DHCP via router and cable modem). Also I can connect to the shared folders on my Windows machines and download files, etc. :confused:

2. Each time I start Firefox it starts in "Work Offline" mode and I have to untick this before I continue. Can I change this default to make it always start online?

Cheers.

---

### Post by kalesh7 on 2008-06-18
> **sajackson said:**
> Thanks, kalesh7, that worked fine - it is 32bit as I suspected.

Another couple of things I am a bit confused about:-

1. My network icon at the top of the screen has an exclamation mark on it (!) and says "No network connection". The thing is I am using it now and connected to the internet fine (DHCP via router and cable modem). Also I can connect to the shared folders on my Windows machines and download files, etc. :confused:

2. Each time I start Firefox it starts in "Work Offline" mode and I have to untick this before I continue. Can I change this default to make it always start online?

Cheers.
your problem 2 is connected to problem 1. something is telling the network icon(and firefox and whatever) that there is no connection, and that is why firefox starts in offline, unfortunately I have no idea what that may be,(I guess you should start new thread for this). also post output of iwconfig and ifconfig

---

### Post by sajackson on 2008-06-18
Thanks again kalesh7. I will do that..... wait for it..... how do I get the output of iwconfig and ifconfig ?

---

### Post by kalesh7 on 2008-06-18
> **sajackson said:**
> Thanks again kalesh7. I will do that..... wait for it..... how do I get the output of iwconfig and ifconfig ?
open a terminal Application->Accesories->terminal
type iwconfig (followed by enter)
select what you get using mouse and right click-> copy
paste here
repeat for ifconfig

---

### Post by Dino05 on 2008-06-18
I was also having problems installing jave jre untill I saw this post and was able to 've jre running using the method posted by stchman
 **" sudo apt-get -y install sun-java6... ... ." **
Then I saw the next post by pjotr123 that will enable full multimedia support. Since I already installed java,  would it hurt if I run pjotr123's method? I go to lots of sites with streaming video and most of the time totem or vlc wont work without lots configuration headaches.

---

### Post by sajackson on 2008-06-20
Hi again Kalesh7, "iwconfig" returns no wireless connections for both "lo" & "eth0". "ifconfig" returns the following:-

eth0      Link encap:Ethernet  HWaddr 00:e0:20:7e:18:69  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:20ff:fe7e:1869/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:881 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1682127 (1.6 MB)  TX bytes:95405 (93.1 KB)
          Interrupt:10 Memory:e3000000-e30000ff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:850 errors:0 dropped:0 overruns:0 frame:0
          TX packets:850 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:42500 (41.5 KB)  TX bytes:42500 (41.5 KB)

The IP address of my router is set to 192.168.0.1

---

### Post by Abu_Dayya on 2008-06-20
> **sajackson said:**
> Hi again Kalesh7, "iwconfig" returns no wireless connections for both "lo" & "eth0". "ifconfig" returns the following:-

eth0      Link encap:Ethernet  HWaddr 00:e0:20:7e:18:69  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:20ff:fe7e:1869/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:881 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1682127 (1.6 MB)  TX bytes:95405 (93.1 KB)
          Interrupt:10 Memory:e3000000-e30000ff 

The IP address of my router is set to 192.168.0.1

Well, it looks that you're connected, as 'eth0' has an IP assigned to it. Its weird how your network icon says no connection.

Try this: go to system -> administration -> network (it will ask for your password). then click on wireless connection to highlight it. them click properties. untick where it says 'enable roaming mode'. click ok. then go back again and tick ' enable roaming mode'. I don't know if that will help, I just figured maybe you should refresh your network settings.

---

### Post by sajackson on 2008-06-21
Hi Abu_Dayya, thanks for the help. I did what you said but there is no wireless connection, only the wired connection which is ticked and point to point connection which is not.

I tried what you said to the wired connection but no difference, I'm afraid.

---

### Post by sajackson on 2008-06-21
I did a "lspci" and got the following message about the ethernet card:-

00:0c.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. Unknown device 2031 (rev 01)

Maybe this explains why Ubuntu thinks there is no network connection even though there is.

Any ideas how to fix this?

---

### Post by Abu_Dayya on 2008-06-24
Try installing the driver with NDISWrapper

---

### Post by Methuselah on 2008-06-24
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

