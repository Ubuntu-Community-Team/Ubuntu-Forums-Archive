---
title: "Is there a 32 bit version of Ubuntu 16.04 or 16.10 available"
date: 2016-12-11
forum: New to Ubuntu
---

### Post by westone2 on 2016-12-11
Completely new to this.
Before replacing my Desktop system mainly used for Image processing I wanted to try out Linux on an old Laptop. Intel T5500 1.66Ghz processor, 1.0Gb RAM, 32bit. Hopefully this is powerful enough to use the basics, email, web, word processing and spreadsheet etc to give me a feel for Linux.. When downloading from the Ubuntu website it just seems to offer 64 bit versions. I've looked at the alternative downloads on this site but can only find  Bittorrent (What is this please?)  for 32 bit versions. One of the links took me to Kent University but this only seemed to list server versions. I wanted to try installing from a bootable USB (ie start my learning curve at the very beginning) and have the instructions for this. If I get on OK with Linux I will need to investigate Darktable and Gimp photo processing software etc in order to establish if  this is suitable for my Image processing needs. 
 Can any help me to get a 32 bit version if they exist.
Thanks

---

### Post by howefield on 2016-12-11
Try this page.. : [http://releases.ubuntu.com/xenial/](http://releases.ubuntu.com/xenial/)

ubuntu-16.04.1-desktop-i386.iso  appears to be the file that you want.

Bittorrent is an alternative to downloading direct from the website whereby you gets "pieces" of the download from many sources (seeders) but you would need a Bittorent client to take advantage of it. It is often faster and has built in error correction so the integity of your download is pretty much guaranteed to be robust.

---

### Post by westone2 on 2016-12-11
OK howefield thanks. I'll search again for this file.

---

### Post by oldos2er on 2016-12-11
With only 1GB of RAM I would try Lubuntu instead of regular Ubuntu, it has lighter system requirements.

lubuntu.net

---

### Post by mörgæs on 2016-12-11
A T5500 processor is 64 bit. 
Still, if you have only 1 GB of memory in the computer a 32 bit Lubuntu is a good option.

---

### Post by poorguy on 2016-12-11
@ mörgæs or oldos2er,

What amount of ram would be considered enough to run 64bit Lubuntu 16.04.

---

### Post by RobGoss on 2016-12-11
I don't think even the lighter distributions of Ubuntu shouldn't have anything less then **2-GB of Ram** if you want a system to run correctly. With each new distribution of Ubuntu it is using more Ram then it did way back when.

---

### Post by oldos2er on 2016-12-11
> **poorguy said:**
> @ mörgæs or oldos2er,

What amount of ram would be considered enough to run 64bit Lubuntu 16.04.

I don't really know. Offhand I'd say 2GB, 1GB for 32-bit. If you read the system requirements given on lubuntu.net, they discuss amounts of RAM less than 1GB. I've personally run Lubuntu on an older Dell P4 system that had 1GB RAM which I later updated to 4GB. Although it ran with 1GB it tried my patience!

---

### Post by poorguy on 2016-12-11
Hey oldos2er,

I'm running Lubuntu 16.04 64bit on a Dell Optiplex 320 Pentium d 950 and 2.0gb DDR2 ram and  [AMD/ATI] RC410 [Radeon Xpress 200/1100] and I can relate about the trying of the patience when opening certain web pages.
I'm sure my integrated graphics adaptor doesn't help but I only paid $1.00 for this computer so ain't really complaining.

---

### Post by poorguy on 2016-12-11
> **RobGoss said:**
> I don't think even the lighter distributions of Ubuntu shouldn't have anything less then **2-GB of Ram** if you want a system to run correctly. With each new distribution of Ubuntu it is using more Ram then it did way back when.
Yes it does appear that the Ubuntu 16.04 distros do use more memory the the Ubuntu 14.04 distros.

---

### Post by Yellow Pasque on 2016-12-11
If you seriously want to use this system for GIMP, put "more RAM" on your shopping list..

---

### Post by mörgæs on 2016-12-12
Here is a comparison of memory requirements:

[https://bryanquigley.com/memory-usage/ubuntu-16-04-livecd-memory-usage-compared](https://bryanquigley.com/memory-usage/ubuntu-16-04-livecd-memory-usage-compared)

The 32-64-bit question is not that important. 
The choice of distro makes a big difference. 
The choice of applications is the most important, especially heavy- versus lightweight browsers.

---

### Post by westone2 on 2016-12-12
Thanks everyone. The Laptop describes itself as 32 bit but it really was hopeless with the Windows Vista it originally came with. It is well past its sell by date so I might just bite the bullet and get a better spec renovated Thinkpad. By the way I tried to download the Rufus USB installer from The Rufus USB Secursoft site (as recommended on the Ubuntu website) but it contained a Trojan Horse virus. Someone might want to check this is the case. If so can a warning be placed on the Forum for beginners like me.

---

### Post by mörgæs on 2016-12-12
> **westone2 said:**
> The Laptop describes itself as 32 bit 

My guess is that you are running 32 bit Vista on a 64 bit capable processor.


You shouldn't buy new stuff before you have personal, hands-on experience with your present hardware. Vista is a slug but give Lubuntu 16.04.1 a thorough test before making up your mind. 

I run several computers older than this one with good results.

---

### Post by howefield on 2016-12-12
> **westone2 said:**
> .... but it contained a Trojan Horse virus..

The actual download link used and the way you ascertained the file had a virus would be helpful ?

---

### Post by RobGoss on 2016-12-12
> **poorguy said:**
> Yes it does appear that the Ubuntu 16.04 distros do use more memory the the Ubuntu 14.04 distros.

Yes this is correct, even the 32 bit version should have at least 1-GB to 2-GB, of Ram. I know some require 512 MB but on a older machine depending on the hardware you may have to bump it up to at least 1-GB in order to have Decent Performance.

I have a old Toshiba laptop with Linux lite and I believe it has 768 MB and I tried installing lighter distributions of Ubuntu and it has been unsuccessful the hardware just can't Handel the OS

---

### Post by poorguy on 2016-12-12
> **westone2 said:**
>  By the way I tried to download the Rufus USB installer from The Rufus USB Secursoft site (as recommended on the Ubuntu website) but it contained a Trojan Horse virus. Someone might want to check this is the case. If so can a warning be placed on the Forum for beginners like me.
Here is a link to Lubuntu 16.04. 
I would choose 32bit.

[http://cdimage.ubuntu.com/lubuntu/releases/16.04.1/release/](http://cdimage.ubuntu.com/lubuntu/releases/16.04.1/release/)


Try this link I have just downloaded from here and I received nothing bad.

[https://rufus.akeo.ie/](https://rufus.akeo.ie/)

Also you may want to try to install Lunubtu 16.04 32bit by creating a bootable DVD. 
Just make sure to WRITE IMAGE TO DISK and not copy iso.

[http://infrarecorder.org/?page_id=5](http://infrarecorder.org/?page_id=5)

[http://www.softpedia.com/get/CD-DVD-Tools/Data-CD-DVD-Burning/Infra-Recorder.shtml#download](http://www.softpedia.com/get/CD-DVD-Tools/Data-CD-DVD-Burning/Infra-Recorder.shtml#download)

---

### Post by westone2 on 2016-12-12
Re your Question howefield. The actual download link was [*"snipped"*]("*snipped*") then their download button for the USB installer. Just as the download started my virus checker reported a "Malsign.Generic.095 Trojan Horse which allows remote access to the Laptop. This happened on the two occasions I tried. It seems best I should try Lubuntu (at least for email, web, office stuff before worrying about my image processing at this stage)) before spending money on new machines and thanks to those who have provided alternative down load links and suggested using DVD installers. Iam rather busy over the next few days so will give it a go at the end of the week.

---

### Post by howefield on 2016-12-12
> **westone2 said:**
> Re your Question howefield. The actual download link was ["*snipped*"]("*snipped*") then their download button for the USB installer.

OK, so not as you claimed.. 

> By the way I tried to download the Rufus USB installer from The Rufus USB Secursoft site (as recommended on the Ubuntu website) but it contained a Trojan Horse virus. Someone might want to check this is the case. If so can a warning be placed on the Forum for beginners like me.

Links are provided (as posted above by another poster) for beginners like you in order that they do not foolishly download the wrong file.

---

### Post by westone2 on 2016-12-13
OK Howefield I apologise.  That's why I asked if someone could check me out in case I was wrong. The Ubuntu website suggested you needed to download the Rufus USB installer without providing a link. I guess I picked 
an unofficial site  for this.

---

### Post by howefield on 2016-12-13
> **westone2 said:**
> ...The Ubuntu website suggested you needed to download the Rufus USB installer without providing a link.

That's ok, the correct and proper link is there, I guess that you made an honest mistake in missing the large font, prominent clickable link with the download icon.

---

