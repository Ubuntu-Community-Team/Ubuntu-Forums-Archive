---
title: "Total newbie help with iPhone tethering"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by leighanne on 2012-08-11
Hi all please bear with me I have practically no idea and am a little intimidated by all this tbh!
Ok, so a family friend got Ubuntu 12.04 up and running on a really old pc we got donated but now it's home I'm panicking. I tried following these instructions

"To get iPhone USB tethering working again on Ubuntu 12.04, we need following packages installed:
ipheth-utils
libimobiledevice-dev
libimobiledevice-utils

Installation of Utils, open Terminal and enter following command:
sudo apt-get install ipheth-utils libimobiledevice-dev libimobiledevice-utils"

After apt-get update like it suggested ive got
W: some index files failed to download. They have been ignored or old ones used instead.

So am I close to running mobile Internet from this iPhone or am I never going to get there?
All help is very much appreciated if you have the time for me! :-s

---

### Post by methuseal on 2012-11-02
I'm having problem with tethering my iPhone5's internet connection to my ubuntu 12.04 by wireless. When I turned on wireless tethering on iPhone5, it appeared in the Wireless Network list on my ubuntu. But when I tried to connect to it, the password dialog kept popping up. Eventually I can't connect to my iPhone5. 
I searched the forum but didn't find a thread discussing it so I put it under this USB tethering thread. Hope someone will help the two of us. Thanks.

---

### Post by techvish81 on 2012-11-03
> **methuseal said:**
> I'm having problem with tethering my iPhone5's internet connection to my ubuntu 12.04 by wireless. When I turned on wireless tethering on iPhone5, it appeared in the Wireless Network list on my ubuntu. But when I tried to connect to it, the password dialog kept popping up. Eventually I can't connect to my iPhone5. 
I searched the forum but didn't find a thread discussing it so I put it under this USB tethering thread. Hope someone will help the two of us. Thanks.


both of these problems are basically different.  connecting through wireless, you require proprietary drivers (if there is any required) installed. 

 for the first question regarding usb tethering,      
you need to give more details , what package failed to download ? all of them or only some?  it happens sometimes , when a server is busy, you have to try again after sometime.

---

### Post by methuseal on 2012-11-17
> **techvish81 said:**
> both of these problems are basically different.  connecting through wireless, you require proprietary drivers (if there is any required) installed. 

 for the first question regarding usb tethering,      
you need to give more details , what package failed to download ? all of them or only some?  it happens sometimes , when a server is busy, you have to try again after sometime.

To techvish81:

Sorry to reply so late. Thanks for the answer.

But what do you mean by *proprietary drivers*? If you suggest that there's some hardware driver problem with my wireless adapter then can you tell me how to get those drivers?
I've checked out the network status using *nm-tool* command and there seemed no problems with my wifi connections. What confuses me is that there's no problem to connect to my router using wifi meanwhile unable to connect to my iPhone5.

---

### Post by methuseal on 2012-11-24
After a re-installation of Ubuntu 12.10 yesterday, the problem seemed non-existed any more. Now I can connect to the wifi access point of my iPhone5 with no trouble. I'm guessing that maybe some recent updates fixed this problem but I don't know which. Thanks anyway for replying, [techvish81]("http://ubuntuforums.org/member.php?u=1435576").

---

### Post by Eugene King on 2012-12-16
I am also the owner of a new iPhone 5 and am beating my brains out trying to get it to tether via USB cable. I am currently doing it using wifi but my netgear usb wifi adapter is not happy with ubuntu 12.10 so I went back to 11.10.

I've found patch for the linux kernel that modifys ipheth.c .........but I can't for the life of me fine it. Also its been posted that the next version of Linux will include this patch
"FS#32245 - [linux-3.7.x] Add support for Iphone 5 in tethering"

Is their going to be a kernal update? I don't mind tethering with WiFi but since you can't turn off the brodcast it be nice to just use the USB cable...........

This bit of news was posted around a month ago for Linux at [http://www.h-online.com/open/features/Kernel-Log-Coming-in-3-7-Part-2-Networking-1752099.html](http://www.h-online.com/open/features/Kernel-Log-Coming-in-3-7-Part-2-Networking-1752099.html)
**Drivers**

 	 	 		[IMG]http://www.h-online.com/open/imgs/45/9/4/8/6/7/2/Kernel_Log_Penguin.jpg-2772ff8328727478.jpeg[/IMG] 	 	 	 	 As in almost every kernel version, some drivers have been extended to  support additional hardware: iPhone tethering driver ipheth [now supports]("http://git.kernel.org/linus/af1b85e49089f945deb46258b0fc4bc9910afb22") the iPhone 5 and Atheros' ath9k wireless driver now supports the AR9565 Wi-Fi chip ([1]("http://git.kernel.org/linus/0c8070f92f483b764623f6d3960a4d69f8911351"), [2]("http://git.kernel.org/linus/a4a2954ff49e72ce3fa1f78a156b2492a023c89d"), [3]("http://git.kernel.org/linus/aaa53ee97dab2b4c98ea2765e4f16af62d8694bb"), [4]("http://git.kernel.org/linus/77fac465b4b65056a2cec62c1acdc754b7ae86ed") and others). 



Will this very same thing be happening with Ubuntu? I can't USB tether in 12.10.......and since I happened to buy the netgear wifi adapter that isn't happy with Lubuntu and Ubuntu I went back to 11.10 which I will say I am perfectly happy with.

---

### Post by Eugene King on 2012-12-16
I will also add that I had installed the packages necessary to tether with my 3GS iPhone a few years ago but those Libimobiledevice packages along with ipheth-utils will not respond to my new "5" phone. It mounts the phone and I can see pictures, documents and what not...........just doesn't tether when only trying via the USB cable.

---

### Post by Eugene King on 2012-12-16
Update........I just installed Linux Kernel 3.7 in my Ubuntu 11.10 and now I can tether using my usb cable and knowlonger need my WiFi adapter.............

this link is how I did it:

[http://www.upubuntu.com/2012/12/installupgrade-to-linux-kernel-37-under.html](http://www.upubuntu.com/2012/12/installupgrade-to-linux-kernel-37-under.html)

---

