---
title: "Impossible install"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by maxrubino on 2012-12-30
Good afternoon,
I am trying to install Ubuntu (and other Linux issues like Zorin, Bodhi etc) but I just encounter several problems.
But then I finally did install it, Ubuntu, once but then again there was an unexpected problem and it did not work anymore, it just ask me user and password and nothing else so I uninstall it.
Now I am trying to re install it and I just get this (see attachment). I try many times already, with and without internet connection. Note: I already get this message on my first attempt, then I remove the internet connection (cable) and it works fine. But then, as I said, I uninstall it and now no way to re install.
Is there a real way to give up with Windows? I really trying my best but I end up in nothing and burning hours and hours.
Can somebody help me step by step with clear instruction?
Thank you all and happy new year. See the attachment.

---

### Post by Cheesemill on 2012-12-30
First of all, don't try and install 11.04 as it is no longer supported. This is why the installer can't download the iso file.

Try installing 12.04 instead, instuctions are on the web site.
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)

---

### Post by rrich1974 on 2012-12-30
you are using a bad way to install, you better install it as dual boot. 
go for ubuntu 12.04.

---

### Post by maxrubino on 2012-12-30
Hi, thanks for fast replay.
I did install 12.04 already (I don't remember the screen resolution) but it was too slow. Really impossible to use as slow. So I install 11 and it was fast, just insufficient resolution. But now that I remove it due to a mysterious accident and now I cannot reinstall it as you can see from the screen shot.

"First of all, don't try and install 11.04 as it is no longer supported. This is why the installer can't download the iso file."
On my first attempt i did install it removing the cable from internet but now not anymore. my first attempt was 2 days ago.

"you are using a bad way to install, you better install it as dual boot"
What is dual boot?
I have no dvd as it is a joybook.


Any suggestion to reinstall it (not 12.04)? Thanks to all

---

### Post by Cheesemill on 2012-12-30
Don't use 11.04 as it has reached end-of-life.
This means that it doesn't receive bug fixes or security updates any more and you won't get support for using it.

Instead you should install 12.04 and fix your issue with it being slow rather than using an outdated OS.

---

### Post by audiomick on 2012-12-30
> **maxrubino said:**
> 
What is dual boot?

What you appear to be doing is a WUBI install
[http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29]("http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29")

a proper dual boot installs Ubuntu (or whichever system is being used) on it's own partition(s). Ubuntu installs the GRUB boot loader to take care of choosing which OS to boot to.

Here
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")


You might like to look at Xubuntu or Lubuntu if you find 12.04 too slow on your system.
[http://xubuntu.org/]("http://xubuntu.org/")
[http://lubuntu.net/]("http://lubuntu.net/")

---

### Post by maxrubino on 2012-12-30
Hi, thanks.
I think I can install 12 as I did it already. then how to fix these issues?
It was ssslllooowww, anytime i have to click something I have to wait minutes for reaction. So even install a program from the software center was impossible.
Or better to try Lubuntu?
I cannot use DVD as it is a Joybook.
Bye

---

### Post by grahammechanical on 2012-12-30
Have you read through this?

[http://www.ubuntu.com/download/help/install-desktop-long-term-support]("http://www.ubuntu.com/download/help/install-desktop-long-term-support")

Note section 4 - Allocate drive space.

Option 1: Install Ubuntu alongside Windows 7. That will give you a dual boot system where you will get a menu and you can choose to boot/load either Ubuntu or Windows.

This is the better way to install Ubuntu as it is an independent operating system. The method that you are trying is called , by us, a Wubi install. It installs Ubuntu inside Windows and Ubuntu runs as if it is a Windows application.

This method is useful if you want to examine Ubuntu without altering your hard disk. Ubuntu can be uninstalled as easily as uninstalling a Windows application. But a Wubi install is not designed as a long term method of using Ubuntu. This is why we are recommending the dual boot method.

Ubuntu 12.04 may not give a good user experience when it is run on a low specification machine and inside Windows because it does not have direct access to the hardware.

You might have a different experience if Ubuntu is directly installed onto the machine's hardware as a dual boot system.

Looking here I see that

[http://www.laptopmag.com/review/laptops/benq-joybook-lite-u101.aspx]("http://www.laptopmag.com/review/laptops/benq-joybook-lite-u101.aspx")

the Joybook has a 1.6-GHz Intel Atom processor with 1.5GB of RAM. That should be sufficient to run Ubuntu 12.04.

Regards.

---

### Post by maxrubino on 2012-12-30
Mmh,
i did not know this delicate technical difference. 
I use to avoid a "real installation" as I did it with Zorin and Bodhi and then I could not anymore uninstall it and I had to reset completely the computer as, after a problem, I receive on start up only "no partition bootable...."
and I would like not to reset again the whole computer also because i have no Windows disk and I have to go to the shop and pay.
So, if I will try a real installation, do you suggest me Lubuntu or Ubuntu?
And if then too slow, how can I remove it? In an easy way for a non programmer like me.
Thanks

---

### Post by audiomick on 2012-12-30
You have several options. One of them is to simply install a standard Ubuntu as a dual boot and see how it goes. If it is too slow for you, you can easily install the desktop package for both Xubuntu and Lubuntu  and see which one you like best. You can choose which one to start when you log in. They can happily co-exist on a system because only one is every running at the one time.

If you decide to get rid of Ubuntu, it is also not difficult. You remove the partitions that the Ubuntu is on and expand the windows partition back into the space, and then you have to restore the MBR so that windows will boot. There are a couple of ways to do that, For instance, I believe this tool will do it.

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by maxrubino on 2012-12-31
Good morning Micheal and all,
I check the link [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
It is not so clear as I understand 50% of what they wrote but I understand the meaning.
Anyway with the help of you guys I think i will manage.
Go step by step:
1) I will install Ubuntu dual boot without wubi.
So: it is correct to use Unetbootin or I have to use the create USB...?
So when I will know from you if OK Unetbootin or USB I will proceed further and I will update to you.
Any answeryou will give to me please try to details as much as possible so I will not do mistake while using Unetbootin or USB. I don't have DVD.
Thanks and happy new year.
Massimo

---

### Post by audiomick on 2012-12-31
You only have a Windows install working at the moment, right?

I haven't used unetbooting (I don't think so, anyway..) but I did use the windows tool mentioned here once or twice.

[https://help.ubuntu.com/community/Installation/FromUSBStick#From_Windows]("https://help.ubuntu.com/community/Installation/FromUSBStick#From_Windows")

Go thruugh the whole page there. I think there is pretty much all you need to know about getting a USB installer happening on there.

---

### Post by maxrubino on 2013-01-02
Hi everybody, I hope you had a nice start with 2013.
So, I try Lubuntu with the USB (Try Lubuntu without install) and it was fine. I start the installation procedure (no wubi) and then it crashed. After that I cannot use anymore neither the "Try Lubuntu without install".
I just get a text console "Panic occurred".
What to do next? :(

Update:
After 2 attempt I had 4 partition on hard disk: C, D (from windows) and 2 more hidden. I manage to transform them in logical drive in Windows (X and Y). So now I have many small partition but this issue is not a problem.
After this i could manage again to use "Lubuntu without install". Now I am ready to install it but I am scared that something will crash again. It crashed 2 times after choosing the location in the installation process.
Any suggestion before my next attempt? 
Note: Lubuntu 12.10
Thanks

---

### Post by mastablasta on 2013-01-02
1. after downloading the image you need to make sure the image is exactly the same as the one on server. you do this by checking the md5sum ([https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM))
2. you need to make sure that you do not have too many primary partitions on the hard disk. 4 is maximum so windows can have only 3, as you will need one free for linux. you can have plenty secondary partitions.
3. you never posted any system specs. lubuntu had some bugs in installer when it crashed if it didn't have enough ram. not sure if this is the case here. as it was mentioned different desktops can be installed later on. for example you want lubuntu you just install lubuntu desktop from software center.
4. to cretae USB unebooting and lili (linux live usb) seems to work well in windows.
5. in linux drivers are often part of kernel so newer kernel means newer/imporved drivers and (usually) alos less issues for older hardware.
 
good luck with your install. as long as you have a free primary partition, good downloaded OS image. things should go smooth.

---

### Post by maxrubino on 2013-01-02
> **mastablasta said:**
> 1. after downloading the image you need to make sure the image is exactly the same as the one on server. you do this by checking the md5sum ([https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM))

[COLOR=Magenta]**OK, got it**[/COLOR]

2. you need to make sure that you do not have too many primary partitions on the hard disk. 4 is maximum so windows can have only 3, as you will need one free for linux. you can have plenty secondary partitions.

[COLOR=Magenta][B]So now I have 4, how to transform in 3?
What the different between primary and secondary?[/B][/COLOR]

3. you never posted any system specs. lubuntu had some bugs in installer when it crashed if it didn't have enough ram. not sure if this is the case here. as it was mentioned different desktops can be installed later on. for example you want lubuntu you just install lubuntu desktop from software center.

[COLOR=Magenta][B]Benq Joybook 1.6processor, 1 GB ram, no DVD
If I install Ubuntu I cannot use neither from "try it without install" so I turn in Lubuntu, or should I try Kubuntu?[/B][/COLOR]

4. to cretae USB unebooting and lili (linux live usb) seems to work well in windows.

[COLOR=Magenta]**OK**[/COLOR]

5. in linux drivers are often part of kernel so newer kernel means newer/imporved drivers and (usually) alos less issues for older hardware.
 
good luck with your install. as long as you have a free primary partition, good downloaded OS image. things should go smooth.

[COLOR=Magenta][B]So I will wait you suggestion about partition, Kubuntu/Lubuntu and I will try again.
Do you think one day I will also be able to give suggestion to others people?
Thanks[/B][/COLOR]

---

### Post by maxrubino on 2013-01-02
Hi everybody.
I did try all but I cannot do anything, I just get "panic occurred, switch to text console..."
I don't know why as yesterday I could use it without install it (with USB) but now not anymore. So something happen and I don't know how to fix it.:confused:
Any help?
I really don't want to give up as yesterday I could use it but I am in a dead end way at this point.
Thanks

---

### Post by maxrubino on 2013-01-03
Hi again,
is there anybody around here that can visit me to install it?
Or suggest me how to do it as I don't know what to do next.:cry:

---

### Post by tlhIngan on 2013-01-03
I believe the "Panic occurred" screen you are refering to is the startup screen after a crash. Just select one of the options and it should be fine.

If the installer is still crashing, you should probably try the [alternate installer]("http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/"). It worked for me.
You should also stick to 12.04 as it has long-term support, not 12.10.

Cheers!

---

### Post by mastablasta on 2013-01-03
> **maxrubino said:**
> 
[COLOR=magenta]**So now I have 4, how to transform in 3?**[/COLOR]
**[COLOR=magenta]What the different between primary and secondary?[/COLOR]**

 
primary partitions is needed for windows and other OS to boot from. the disk can have max 4 primary partitions. you have to transform one of the parittion into secondary or remove one partition.
[http://en.wikipedia.org/wiki/Disk_partitioning#Primary_partition](http://en.wikipedia.org/wiki/Disk_partitioning#Primary_partition)
 
>  
A primary partition contains one file system. In [DOS]("http://en.wikipedia.org/wiki/DOS") and earlier versions of [Microsoft Windows]("http://en.wikipedia.org/wiki/Microsoft_Windows") systems, the [system partition]("http://en.wikipedia.org/wiki/System_partition") was required to be the first partition. More recent Windows operating systems (Windows 7, XP, etc.) can be located on any partition, but the boot files (bootmgr, ntldr, etc.) must be on a primary partition. However, other factors, such as a PC's [BIOS]("http://en.wikipedia.org/wiki/BIOS") (see [Boot sequence on standard PC]("http://en.wikipedia.org/wiki/Booting#Boot_sequence_on_standard_PC_.28IBM-PC_compatible.29")) may also impart specific requirements as to which partition must contain the primary OS.
The partition type code for a primary partition can either correspond to a file system contained within (e.g. [0x07]("http://en.wikipedia.org/wiki/Partition_type#PID_07h") means either an [NTFS]("http://en.wikipedia.org/wiki/NTFS") or an OS/2 [HPFS]("http://en.wikipedia.org/wiki/HPFS") file system) or indicate that the partition has a special use (e.g. code [0x82]("http://en.wikipedia.org/wiki/Partition_type#PID_82h") usually indicates a Linux swap partition). The [FAT16]("http://en.wikipedia.org/wiki/FAT16") and [FAT32]("http://en.wikipedia.org/wiki/FAT32") file systems have made use of a number of partition type codes due to the limits of various DOS and Windows OS versions. Though a Linux operating system may recognize a number of different file systems ([ext4]("http://en.wikipedia.org/wiki/Ext4"), [ext3]("http://en.wikipedia.org/wiki/Ext3"), [ext2]("http://en.wikipedia.org/wiki/Ext2"), [ReiserFS]("http://en.wikipedia.org/wiki/ReiserFS"), etc.), they have all consistently used the same partition type code: [0x83]("http://en.wikipedia.org/wiki/Partition_type#PID_83h") ([Linux native file system]("http://en.wikipedia.org/wiki/File_system#Linux")).

 
 
[COLOR=magenta]**> [COLOR=magenta][B]Benq Joybook 1.6processor, 1 GB ram, no DVD**[/COLOR][/B]> 
**[B][COLOR=magenta]If I install Ubuntu I cannot use neither from "try it without install" so I turn in Lubuntu, or should I try Kubuntu?[/COLOR]**[/B]> 
[/COLOR]
 
Lubuntu should run a lot better on your setup. you can always move to Kubuntu later on.
 
 
it could be that you are experiencing hardware issue.
but it's hard to say without knowing more or getting more error messages. if you say it boot from USB once but not the second time this definatelly smells like hardware related issue. you could try one of the boot options: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
maybe nomodeset.
 
you can as mentioned try alternate installer. it's a text based installer. doesn't look as good but does the job anyway. i think 12.04 still had it. i would suggets you stick with 12.04. alternate install disk can be foudn here: [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

---

### Post by NikTh on 2013-01-03
> **tlhIngan said:**
> 
If the installer is still crashing, you should probably try the [alternate installer]("http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/").
Alternate iso is always an option .. well , until 12.10 .. because dropped now. 
So I agree with alternate install if desktop .iso crashes.

> **tlhIngan said:**
> You should also stick to 12.04 as it has long-term support, not 12.10.

For clarification. 
Lubuntu 12.04 is not an LTS version. Supported only for 18 months 
Xubuntu 12.04 is an LTS version supported for 3 years 
Ubuntu 12.04 is an LTS version supported for 5 years. 

@maxrubino you can give us more info about your machine so we can suggest a version of Ubuntu that fits without problems. 

From the live session (Try Ubuntu without install) open a terminal or lxterminal and copy-paste from here the commands below. 

```
lscpu
lspci -nnk | grep -iA2 vga
free -m
sudo fdisk -l
```Post back here the results. 

_Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read._ [See here how]("http://i.stack.imgur.com/zADbK.png")

---

### Post by maxrubino on 2013-01-04
Hi everybody, thanks for help.
I did not understand what you suggest me as maybe you think I am skilled in programming but I cannot understand 80% of your suggestion.
Anyway I try Ubuntu 12.04 (live) and I got a strange flickering useless half screen but it did not panic occurred.
Then I try Lubuntu with Wubi and it works fine. I already try it and did not work so I was surprise that this time I could install it! Then I try to surf the web and I did discover that the internet cable (LAN) was disconnected! So maybe the connection was the clue that did not allowed me to install it. I am quite sure now about it as I did not change anything else.
Now I wait before uninstall and reinstall with USB as now I can use it. Can I keep it like this, I mean, Lubuntu born from a Wubi installer?
I have a strange red icon on the lower right panel (see attachment).
Then I download some programs (Open office for Linux and more). I got a compressed folder. I know how to decompress it. And then? How to install it (see attachment)?
I really appreciate your help and I would like to ask more: try to explain it (how to install) step by step, maybe with screen shot as I google around how to install and I try many ways but still no success. I think I am missing something basic.
After I will be able to install programs from the compressed folder I think this time I will also be able to walk alone.  
Ops, still another things. Play around with installation system I think I did something wrong about Libre office (see attachment). When I click it nothing happen.
How to eventually uninstall completely (Open Office I prefer).
Bye the way, when I digit this in terminal:
lscpu lspci -nnk | grep -iA2 vga free -m sudo fdisk -l
I got this:
degkorat@ubuntu:~$ lscpu  Floating point exception (core dumped)  degkorat@ubuntu:~$ lspci -nnk | grep -iA2 vga  00:02.0 VGA compatible controller [0300]: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller [8086:8108] (rev 07)  Subsystem: Benq Corporation Device [17ff:500f]  Kernel driver in use: gma500  degkorat@ubuntu:~$ free -m  total used free shared buffers cached  Mem: 2007 1454 552 0 530 638  -/+ buffers/cache: 285 1721  Swap: 255 0 255  degkorat@ubuntu:~$ sudo fdisk -l

Note VGA in red

Thanks again to all for help.

---

### Post by NikTh on 2013-01-04
> **maxrubino said:**
> ```

degkorat@ubuntu:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller [8086:8108] (rev 07)  
Subsystem: Benq Corporation Device [17ff:500f]  
Kernel driver in use: gma500  
```

Well , here is the problem (at my opinion). The poulsbo Intel driver is not fully supported yet , by Linux.

Read here: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)
and here: [http://www.phoronix.com/scan.php?page=news_item&px=MTAzNTE](http://www.phoronix.com/scan.php?page=news_item&px=MTAzNTE)

Thanks.

---

### Post by tlhIngan on 2013-01-04
> **maxrubino said:**
> Hi everybody, thanks for help.
Then I download some programs (Open office for Linux and more). I got a compressed folder. I know how to decompress it. And then? How to install it (see attachment)?

You should not download programs manually. The best way to install programs is to find them in your package manager (System Tools > Synaptic package Manager). This will ensure you have all the libraries and modules that program needs, and it installs all of it for you.
:)

---

### Post by Cheesemill on 2013-01-04
You shouldn't go around downloading files from websites if you want to install a program, instead just use the Software Centre...

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by maxrubino on 2013-01-05
Hi,
I understand.
But there is no open office in Software centre. Neither Google Earth, how to install these 2 programs?
And about Synaptic package manager, I looked at it, how to use it? If I write open office in the search box then I get a long list of I don't know what.
Thanks.

---

### Post by NikTh on 2013-01-06
> **maxrubino said:**
> 
But there is no open office in Software centre. Neither Google Earth, how to install these 2 programs? 
Search in Software Center for libreoffice and googleearth packages. See the attachments. Read the descriptions before install , contains useful info.

> **maxrubino said:**
> And about Synaptic package manager, I looked at it, how to use it? If I write open office in the search box then I get a long list of I don't know what.


OpenOffice is deprecated and not supported anymore search for libreoffice instead.
Synaptic package manager is a lightweight alternate for software center (most people - me included - consider synaptic better than software center, but is not so fancy)

Thanks

---

### Post by maxrubino on 2013-01-06
[FONT=Arial][SIZE=3]Hi guy, I am happy that there is always somebody ready to answer me.
But this often don't solve the problems.
Today I manage to install Google Sketchup with wine. This was painful as I use the whole day. And still some function does not work.
I also manage to install Google Earth with terminal 
[/SIZE][/FONT][FONT=Arial][SIZE=3]sudo dpkg -i google-earth-stable_current_i386.deb
I will try Libre office tomorrow[/SIZE][/FONT][FONT=Arial][SIZE=3].
I am wondering, before I let the notebook fell from my office balcony on the people that is passing by,
is there somebody with some time willing to help me by chat (MSN or Skype or other) so that I can have an usable computer in few days?
I can be thankful, maybe a little far to meet you (Thailand) but I will really appreciate.
Thanks again for reading my desperate appeal.
Bye.[/SIZE][/FONT]

---

### Post by maxrubino on 2013-01-10
I try to install Libre office.
Via synaptic no way. The system crash.
Via Ubuntu software center it says that is in conflict with another writer then I unistall the writer then it says the source is not authenticate.
Is there a way to really use Lubuntu or it is just a time consuming hobby?
This is my last post, if no answer I will remove Lubuntu from my PC and I will never ever heard that word again as I spend time in many forum and everybody just let me down with link and not understandable comment :sad::sad: as a royal elite of programmer that don't want normal people to use it

---

### Post by maxrubino on 2013-01-11
Today I gave you last chance. I try to install a messenger.
No way. Just a window that say impossible to install.
Good bye Ubuntu, go back to Mister Windows (That I did not like) but at least works!!!
To who will I charge all my useless days spent on Ubuntu?
And where is your help?

---

### Post by oldos2er on 2013-01-11
Everyone here is a volunteer; demanding help will not get you far. If you want professional support please see [http://www.ubuntu.com/business/services](http://www.ubuntu.com/business/services)

Thread closed.

---

