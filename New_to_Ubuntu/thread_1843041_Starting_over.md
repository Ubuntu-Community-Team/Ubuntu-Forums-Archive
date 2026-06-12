---
title: "Starting over"
date: 2011-09-12
forum: New to Ubuntu
---

### Post by AWCJR on 2011-09-12
Well after a complete system failure , it took me 6 days to reload windows , now that it's stable I want to put Xubuntu in my lap top.I have a Dell 1737 studio with Vista Home Premium 64 bit.I am not very good with partitions and don't want to screw it up, I had trouble the last time trying to change the size while installing. If someone would give me step by step on what to do from start to finish . I do know that I'll need a driver for my wireless,it's built into the mother board,if I remember right it is a BCM43 driver. Also any other help would be very welcome, Thanks Art.

---

### Post by Rex Bouwense on 2011-09-12
Here are a few sites that will help you.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
There are others but these should answer any questions that are in the back of your mind.

---

### Post by haqking on 2011-09-12
> **AWCJR said:**
> Well after a complete system failure , it took me 6 days to reload windows , now that it's stable I want to put Xubuntu in my lap top.I have a Dell 1737 studio with Vista Home Premium 64 bit.I am not very good with partitions and don't want to screw it up, I had trouble the last time trying to change the size while installing. If someone would give me step by step on what to do from start to finish . I do know that I'll need a driver for my wireless,it's built into the mother board,if I remember right it is a BCM43 driver. Also any other help would be very welcome, Thanks Art.


First thing i suggest is to download the live CD/DVD version and trying it out for a while to make sure you like it and runs comfortably on your hardware, using the Live option will not harm you current system, you can do this from a USB stick also

[http://www.xubuntu.org/get](http://www.xubuntu.org/get)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

you also have the option of WUBI
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

You could also consider a dual boot:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

all of these help you keep your windows system aswell as be able to use Xubuntu until you are experienced or sure you want to leave windows completely.

When you are ready you make sure you have all your personal data backed up to a external HDD etc for porting into your new Linux install and also incase of error.

Also you can back-up windows drivers and the like or do a complete system clone incase you wish to revert later. [www.clonezilla.org]("http://www.clonezilla.org")

good luck

regards 

haqking

---

### Post by Paddy Landau on 2011-09-12
WUBI is OK for experimenting, but not for long-term use as it is unstable.

Dual-boot is the best long-term solution.

---

### Post by audiomick on 2011-09-12
Here is some info on Partitioning as such.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by AWCJR on 2011-09-12
Thank you all for the help so far.I did forget to say that I am going to make it a Dual Boot at least for a while anyway. Again thanks,this is a start and I'll try these thing out and see where it goes.

---

### Post by Mark Phelps on 2011-09-12
Just make sure that regardless of HOW you ultimately decide to do the dual boot you do NOT allow the installer to shrink your Vista OS partition to make room.  If you're going to avoid Wubi and use separate partitions, be sure to FIRST, use the Vista Disk Management utility to shrink the OS partition to leave some unallocated space.

Also, while in Disk Management, take a look at your partitions.  If you already have the maximum of four, do NOT force the creation of any more. Doing so will automatically convert your existing partitions into Dynamic Disks -- something you do not want to do.

---

### Post by haqking on 2011-09-12
> **Mark Phelps said:**
> Just make sure that regardless of HOW you ultimately decide to do the dual boot you do NOT allow the installer to shrink your Vista OS partition to make room.  If you're going to avoid Wubi and use separate partitions, be sure to FIRST, use the Vista Disk Management utility to shrink the OS partition to leave some unallocated space.

Also, while in Disk Management, take a look at your partitions.  If you already have the maximum of four, do NOT force the creation of any more. Doing so will automatically convert your existing partitions into Dynamic Disks -- something you do not want to do.

+1

If i was you make a clone first using clonezilla or similar. if you trash things you can just image it back to how it was before.  [www.clonezilla.org]("http://www.clonezilla.org")

---

### Post by walt.smith1960 on 2011-09-12
> **haqking said:**
> +1

If i was you make a clone first using clonezilla or similar. if you trash things you can just image it back to how it was before.  [www.clonezilla.org]("http://www.clonezilla.org")

Oohhhhh yeah.  I just did a full Win7 install.  It took the better part of a day by the time I got O.S., updates, drivers, applications, anti-virus etc. all installed.  Restoring an image may take a half hour on a slow machine and you can be doing something else most of that time.

---

### Post by haqking on 2011-09-12
> **walt.smith1960 said:**
> Oohhhhh yeah.  I just did a full Win7 install.  It took the better part of a day by the time I got O.S., updates, drivers, applications, anti-virus etc. all installed.  Restoring an image may take a half hour on a slow machine and you can be doing something else most of that time.


indeed.

Make sure you cleanly dismount any partitions though, espceially NTFS ones, and make sure you choose to check if restoreable also

If there is a problem then run clonezilla in expert mode and choose the option of:

fsck-src-part option

cant remember off top of head what the complete option is but you will see it

---

### Post by AWCJR on 2011-09-12
Thank you all for the help so far and it looks like a very long night ahead of me again. And also a bunch of homework for me to do.I'm sure that I'm far from being done with this and may need more help ,when I get to that point I will sure ask again. Again thanks to you all , stay out of the sun and have fun gotta run get this done. Thank's Art.

---

### Post by haqking on 2011-09-12
> **AWCJR said:**
> Thank you all for the help so far and it looks like a very long night ahead of me again. And also a bunch of homework for me to do.I'm sure that I'm far from being done with this and may need more help ,when I get to that point I will sure ask again. Again thanks to you all , stay out of the sun and have fun gotta run get this done. Thank's Art.


no problem you are very welcome.

post back with any issues and we will try to help where we can.

oh and welcome to the forums.

peace

---

### Post by AWCJR on 2011-09-17
After having to leave to go bury a friend I'm back. While gone I had one of my better half's family do the install only because he was MS Cert and he still screwed it up. I got it this evening and it had no bcmwl kernel , I downloaded it from Broadcom and left it zipped in downloads, then rebooted into Xubuntu and brought it up and sent it to the desk top for installation . Can someone please tell me how to finish this I'm not to sure so I don't want to mess with it just yet.I would like to find out about putting Windows in a VM ,would like to keep Windows don't know why but I do.From all the playing around with Xubuntu I like it a lot much more easy to use and find things.All help is always welcome,thank's Art.

---

### Post by wildmanne39 on 2011-09-17
Hi, if wireless is all you still need post the results of these commands here so we can see exactly what is going on, you will need to run these commands in a terminal you can open it by hitting ctrl+alt+t then just copy and paste the command into the terminal then paste the output of the commands here please.
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Paddy Landau on 2011-09-17
> **AWCJR said:**
> I would like to find out about putting Windows in a VM...
First: Your computer needs to be powerful enough to run Windows and Xubuntu at the same time. Otherwise stick to dual-boot.

Second: Go to [Virtual Box Linux downloads]("http://www.virtualbox.org/wiki/Linux_Downloads"). Scroll down to "Debian-based Linux distributions." Follow the instructions for your particular Xubuntu installation. You will probably want to install the Oracle VM VirtualBox Extension Pack (from the [downloads page]("http://www.virtualbox.org/wiki/Downloads")). There's a bit of a learning curve, but once you have it running, it's easy to use.

Another alternative, which I have never used, is to use a [hypervisor]("http://en.wikipedia.org/wiki/Hypervisor") (virtual machine manager). It allows you to swap between the two systems without rebooting. The officially supported [hypervisor in Ubuntu is Xen]("https://help.ubuntu.com/community/Xen") (also [see instructions]("http://aethylred.blogspot.com/2011/05/xen-41-and-ubuntu-1104.html")), and on Ubuntu Server it is [KVM]("https://help.ubuntu.com/community/KVM"). (Well, it was the last time I looked.)

However, to use a hypervisor, your hardware must have [64-bit virtualisation]("http://en.wikipedia.org/wiki/X86_virtualization"). Enter the following command in a terminal:```
grep -qF lm /proc/cpuinfo && grep -cE 'svm|vmx' /proc/cpuinfo
```If the result is 0 or nothing, you cannot use a hypervisor; if it is 1 or more, you have 64-bit virtualisation and can use hypervisor.

---

### Post by haqking on 2011-09-17
> **AWCJR said:**
> After having to leave to go bury a friend I'm back. While gone I had one of my better half's family do the install only because he was MS Cert and he still screwed it up. I got it this evening and it had no bcmwl kernel , I downloaded it from Broadcom and left it zipped in downloads, then rebooted into Xubuntu and brought it up and sent it to the desk top for installation . Can someone please tell me how to finish this I'm not to sure so I don't want to mess with it just yet.**I would like to find out about putting Windows in a VM ,would like to keep Windows don't know why but I do**.From all the playing around with Xubuntu I like it a lot much more easy to use and find things.All help is always welcome,thank's Art.


We are still awaiting your reply with the details from the commands suggested above so as for VM then .

Visit [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

and download latest version for your system (it is in the software centre but a bit out of date)

Also download the extension pack on the same download page

To make USB work (common question here) you need to add yourself to the Vboxusers group by doing the following:

sudo usermod -a -G vboxusers username 

Then  you are set to go.

After installing your chosen OS in a VM you will need to install the VboxAdditions (not the extension pack, you should of installed this already as they are different)

The additions install inside the VM to add graphics functions and the like.

see here [http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html) for installing additions

Youg might also consider [www.clonezilla.org](www.clonezilla.org) to take an Image of your current Windows Install then image that into a VM, whch can often be very useful.


Have fun

Regards

haqking

---

### Post by AWCJR on 2011-09-27
I have to say to all that gave me help in this thread that I'm sorry for not getting back to anyone. I had another complete system failure,this time it was the HD. It smoked,bit the dust,**** the bed. I now have a new HD this time it's a 750GB 7200RPM 16MB cache.I'm going to load Ubuntu 11.04 later this evening,before I do the install should I shrink the drive in Windows Vista first?I need to say this,the system is on a Dell Lap top Studio 1737 w/4GB of memory with Widows Vista Home Premium 64 bit,it uses Broadcom drivers for my wifi.I'm also useing a Verizon Wireless MIFI 2200 for internet connection. After I install will Ubuntu detect my drivers for  this,it is a BCM43 and if so what will I need to do to make it connect. I will have more questions later after I get this part done,so please feel free to help me again as I've had enough stress this past month because of this computer.

---

### Post by wildmanne39 on 2011-09-27
Hi, as far as connecting with your wireless card we can not tell you until you have ubuntu working and post the results of this command.
```
lspci -nn | grep -e 0280 -e 0200
```
Thank you

---

### Post by Paddy Landau on 2011-09-27
Yes, shrink the Vista partition from within Vista itself using Vista's disk management utility (I forget its name). That tends to be the most reliable method.

When you install Ubuntu, ensure your computer is connected to the Internet -- if possible using an Ethernet connection. The installation will look on-line for drivers. This gives you the best chance of success.

---

### Post by AWCJR on 2011-09-27
> **Paddy Landau said:**
> Yes, shrink the Vista partition from within Vista itself using Vista's disk management utility (I forget its name). That tends to be the most reliable method.

When you install Ubuntu, ensure your computer is connected to the Internet -- if possible using an Ethernet connection. The installation will look on-line for drivers. This gives you the best chance of success.

The shrinking part I can do but I only have one way of connecting to the internet and that's wireless.I should still be able to install the driver shouldn't I? Thanks Art.

---

### Post by wildmanne39 on 2011-09-27
Hi, yes it maybe a little more work, depending on the card you have.

You can run that command from the livecd then post the results here.

Also what version of ubuntu are you installing? 
Thank you

---

### Post by kurt18947 on 2011-09-27
> **AWCJR said:**
> After having to leave to go bury a friend I'm back. While gone I had one of my better half's family do the install only because he was MS Cert and he still screwed it up. I got it this evening and it had no bcmwl kernel , I downloaded it from Broadcom and left it zipped in downloads, then rebooted into Xubuntu and brought it up and sent it to the desk top for installation . Can someone please tell me how to finish this I'm not to sure so I don't want to mess with it just yet.I would like to find out about putting Windows in a VM ,would like to keep Windows don't know why but I do.From all the playing around with Xubuntu I like it a lot much more easy to use and find things.All help is always welcome,thank's Art.

I always recommend keeping a minimal Windows install.  Sure as the sun rises in the east at some point you'll have a need for which there is no Linux app.  Mine is my GPS data card & a specialist chart display & printing application. I also found that I had to format a USB key in Windows in order for a Linux Live USB key to boot on one machine.  The key formatted to FAT32 with Gparted would boot on 2 machines, it would not boot on a third.

---

### Post by haqking on 2011-09-27
Go for a VM IMHO, unless you play windows games then a VM will pretty much do all you need to retain your windows funcitonality.

---

### Post by cmcanulty on 2011-09-27
Even if you hate partitioning make a separate home partition for your files and settings and a 10-20GB /partition for programs.My / is 18GB but I am a program junkie, can't resist experimenting. That way if your system has a disaster you keep all your files and settings intact. Feel free to PM me if you need a walk through. You could even casll me if you pm me I will give my phone to you.

---

### Post by AWCJR on 2011-09-28
Well it look's like windows won't let me shrink it,it says windows is 715405MB and shrink space is 0.My HD is 750GB and I'm using only 7% of it,about 46.1GB.Should I do this install with out shrinking the drive.I'm already stressed enough and don't want another failure.Any input that I can understand is welcome,but right now my brain is freezing up and I've had to much coffee today.Thanks Art.

---

### Post by Paddy Landau on 2011-09-29
Windows uses some of the disk as swap space, and some more for its System Restore. To shrink the partition successfully in your case, you'll need to disable both of them (temporarily; re-enable them after shrinking your partition).

Unfortunately, I no longer have my notes on how to do this (I stopped using Windows three years ago). Try Google, or pop over to [Windows Answers]("http://answers.microsoft.com/") or one of the other support forums and ask there how to shrink your disk.

After you shrink your disk, you will need to reboot into Windows at least twice (I don't remember why), re-enable your swap and System Restore, and reboot again.

Ubuntu can shrink your disk for you, but unfortunately it carries a risk of causing your Windows to fail.

Before shrinking your disk, **make a full backup of your data** first! Also make a full backup before installing Ubuntu. Although both processes are tried-and-tested, there is always a small risk of data failure.

**EDIT:** Do you have a C: and D: drive? It may be that Windows is stored on a small partition, while you have another partition for your data.

---

### Post by rjbl on 2011-09-29
> **Paddy Landau said:**
> WUBI is OK for experimenting, but not for long-term use as it is unstable.

Dual-boot is the best long-term solution.

WUBIed 11.04 onto an XPsp3 box a month ago. Solid as a rock; please account for your assertion that WUBI is unstable.

rjbl

---

### Post by wildmanne39 on 2011-09-29
Hi, it is recommended to run defrag on your window partition at least twice before shrinking it.
Thank you

---

### Post by Paddy Landau on 2011-09-29
> **rjbl said:**
> ... please account for your assertion that WUBI is unstable.
Many threads showing WUBI giving unexpected sudden failures, particularly after upgrades.

Unfortunately, recovering WUBI is often impossible, whereas recovering Ubuntu is usually quite quick.

If you use WUBI, ensure you keep frequent backups. Do a fresh install rather than an upgrade (mind you, that often holds for Ubuntu, too).

---

### Post by rjbl on 2011-09-29
> **Paddy Landau said:**
> Many threads showing WUBI giving unexpected sudden failures, particularly after upgrades.

Unfortunately, recovering WUBI is often impossible, whereas recovering Ubuntu is usually quite quick.

If you use WUBI, ensure you keep frequent backups. Do a fresh install rather than an upgrade (mind you, that often holds for Ubuntu, too).

Thanks for the tips. I can't say that I'd ever bother directly upgrading any WUBI, or Ubuntu box; I'd always do a fresh install - lifetime of working on Windows systems has made me very, very skeptical of in-situ OS upgrades. Can't see from, from first principles, why any WUBIed box should give unexpected sudden failures - but this is an area of Ubuntuworld where FUD seems fairly thick on the ground, so I'll keep my eyes well open - its not a critical deployment anyway - just seeing what all the fuss about Unity was about. S'pose 'tis ok if you are really into fondle-slabs, innit?

Cheers
rjbl

---

### Post by Paddy Landau on 2011-09-29
LOL

Ubuntu seems to be fine with upgrades when on the "right" hardware and if not much modified. Otherwise, go for fresh installations when upgrading.

I stay with LTS versions where possible as stability and reliability are more important for me than cutting-edge.

---

### Post by AWCJR on 2011-10-09
Sorry it took so long to get back to you guy's but I had more windows problems.I had to do another install of windows this time I just loaded Vista to the point that SP2 would go in and stopped their.Then I installed Ubuntu 11.04 and in went in like a charm,took ten min to get my wifi drivers to work,and rebooted. It worked right out of the box the first time,I'm a very happy camper now all I need is to get my scanner and printer to work.Any help is more then welcome. This is the scanner I have it's a Visioneer,9520 photo scanner and they don't support linux with any drivers,my printer is a Lexmark,Z2320 and again no drivers.Are their any that will  work for these,I need them bad.Also thank you all for the help,I needed it,just couldn't figure it out,again thank's Art.

---

### Post by Paddy Landau on 2011-10-10
You may need to start two new separate threads, one for your printer and one for your scanner. Search these forums and Google for your models first -- you may find an answer.

In my experience, only HP has great drivers for their products for Linux, so I always use HP.

---

### Post by haqking on 2011-10-10
> **AWCJR said:**
> Sorry it took so long to get back to you guy's but I had more windows problems.I had to do another install of windows this time I just loaded Vista to the point that SP2 would go in and stopped their.Then I installed Ubuntu 11.04 and in went in like a charm,took ten min to get my wifi drivers to work,and rebooted. It worked right out of the box the first time,I'm a very happy camper now all I need is to get my scanner and printer to work.Any help is more then welcome. This is the scanner I have it's a Visioneer,9520 photo scanner and they don't support linux with any drivers,my printer is a Lexmark,Z2320 and again no drivers.Are their any that will  work for these,I need them bad.Also thank you all for the help,I needed it,just couldn't figure it out,again thank's Art.

there is a thread here for your printer [http://ubuntuforums.org/showthread.php?t=855415](http://ubuntuforums.org/showthread.php?t=855415)

starts in 8.04 a few years back but ends up in 11.04 in 2011 see if any of it helps

---

