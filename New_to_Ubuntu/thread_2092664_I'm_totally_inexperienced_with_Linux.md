---
title: "I'm totally inexperienced with Linux"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by MAFinOKC on 2012-12-08
I use a Toshiba Satellite L305 laptop that is several years old. It still has the original Windows Vista OS that came loaded on it. I disliked Vista intensely from the start. I intended to upgrade the OS to Windows 7, but my opinion of Windows 7 is only *slightly *higher than of Vista. Now comes Windows 8, and even if this laptop were compatible with Windows 8, I don't even want to *think* about messing with it on this laptop. So I started thinking about Linux. I did a web search for Linux on Toshiba laptops, and I found a page with a long list of Toshiba laptop models including mine, and notes from 2009 from a user about his installation of Ubuntu 8.10, which seemed to go well. Considering that that version of Ubuntu has long since been superseded, and that I have otherwise no experience with any version of Linux, I am asking the community in general for advice about what to do at this point. The question of setting up a dual-boot also arises, but my question regarding that is how much more disk space does that require? As this unit has only a 250-Gb hard disk and I don't know if buying a larger disk is worth it at this point.

---

### Post by camelface on 2012-12-08
I just installed 12.04 and it required about 4gigs. You should be fine with 250gb. I wonder if you could get the Ubuntu installation to take out your Vista. 

Anyway, I don't know too well how it works on laptops, but I would suggest you get 10.04 which I think is the second last LTS (would be good if one was provided with updates to firefox, openoffice/libreoffice, etc). If you don't like Windows 8 I fail to see how you will like the new Ubuntus (the ones with Unity, 11.10 and after).

---

### Post by pkadeel on 2012-12-08
The best thing I like about major linux distros in general is that you can test it before actually installing it on your computer. Just go a head and download an iso of any major distro. Burn that iso to a DVD or a USB and boot from it. When asked, select the Try option and it will start the whole OS from that disk. Check the working of all devices on you computer and if satisfied then install it actually.

Due to the running of OS from a DVD or USB, you might feel a slowness but that is ok. A computer which can run vista can very easily handle ubuntu.

---

### Post by germanix on 2012-12-08
Hi, and welcome to the forums. I found myself in a similar situation in 2008. I badly wanted to get away from Windows and had no knowledge of linux at that time. My then 4 years old Sony Viao was running XP and I installed Ubuntu 8.04. My laptop is now 8 years old and I upgraded to all f the Ubuntu versions as they came out right up to 12.04 with Unity. All version ran out of the box. My Sony has a 1,6 Ghz. single core chip and 2 GB of Ram. I am now running Xubuntu because I am not a big fan of the Unity Desktop in the latest Ubuntu versions. I find Xubuntu faster and the desktop more to my liking. 
Linux is great. There is a slight learning curve but their are many people on the forum ready to help should problems occur.
Never liked dual booting myself but it depends if you need windows as well. I cannot imagine why (unless you are a gamer and some games are not available under Linux?)
I do everything that I need with Linux and have never looked back.
Do not know about your machine but Linux runs practically on anything.

---

### Post by oldfred on 2012-12-08
Welcome to the forums.

I have an older Toshiba laptop Satellite A105 with a 160GB and XP. I purposely bought it the week before Vista came out as the previews were not good & I knew XP.
We only really used Laptop when travelling but I would copy my Firefox & Thunderbird profiles from my Desktop to the laptop & using Samba and that became frustrating as the Ubuntu updates & every Windows update to virus, firewall or Windows itself seemed to cause Samba to reset. 
So I then just installed Ubuntu in dual boot and use NFS to copy data without much issue.

I have XP in 50GB, 20GB of shared NTFS for the FF & TB profiles and some other data & my Ubuntu install is the rest. 

An install can be as small as 10GB (even less as it really only uses about 4.5GB) but you need room for updates and if writing a DVD you may need another 4GB in tmp just while writing. I usually suggest 25GB, but then it depends on whether you have a separate /home or not. I usually suggest a separate /home but do not use one as all my data is in shared NTFS or Linux formatted partitions.

I use my laptop more as desktop when travelling so I do not use all the features, but for what I do it works well. Some Toshiba have different configurations and may work better or worse depending on just how it is configured.

Not sure if close to your model or not.
[http://www.linlap.com/toshiba_satellite_l300d-l305d](http://www.linlap.com/toshiba_satellite_l300d-l305d)
All laptops seem to run warm even in Windows. 

Be sure to back up all your data and may be best to do a full backup of Vista. Some overwrite Windows but find one application that does not have a good equivalent in LInux to Windows and then want Windows back. 

How many primary partitions are used? Windows 7 systems almost always use all 4 and make it difficult to install but Vista often did not.
Post this from Ubuntu liveUSB terminal. I suggest USB for testing & installing as it is a bit faster than CD/DVD.
sudo fdisk -lu

       [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
    
Use Vista's tools to shrink Vista but not to create any new partitions. Use gparted to create new partitions.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

    
       Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

    
       Install options, Do not use erase entire drive unless that is really what you want.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by grahammechanical on 2012-12-08
Here is the installation guide which will show you images of the screens you will see during installation. Ubuntu will install in less than 5GB but 10 - 15 GB is more useful.

[http://www.ubuntu.com/download/help/install-desktop-long-term-support]("http://www.ubuntu.com/download/help/install-desktop-long-term-support")

Regards.

---

### Post by Swagman on 2012-12-08
Some important things you ***need*** to know right from first base.

1: iTunes is **incompatible**. If you *have* to have it then either duel boot or setup a vm.

2: Any document created or edited using Libre Office/Open Office will cause you formatting grief within Ms Office. <-- Many people will disagree with this but just as many will agree !!

3: I'm sure others will add to this list.

I've laid these out for you right here so you are not disappointed later.

Also remember..As a N00b you are likely to accidently wipe your windows install when first time attempting a duel boot installation.

Also.. Here's an old but very apt read, still relevent today.

[** Linux is NOT Windows**](http://linux.oneandoneis2.org/LNW.htm)


If you decide to go ahead with the install you now have your eyes wide open. We're all here to help you with any problems/glitches you may run into.

Good luck ... & Welcome to the world of Gnu Linux

---

### Post by snowpine on 2012-12-08
Welcome to the forums!

Here is an easy & fun way to experiment with Ubuntu, *without* any permanent changes/risks to your existing system: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

I recommend that all new users test-drive Ubuntu for a couple of weeks before they commit to a full, permanent install.

---

### Post by Bashing-om on 2012-12-08
MAFinOKC; Hi Welcome to the forum.

My input, Your laptop has a celeron processor and I doubt "pae" enabled, thus ubuntu will not run. However lubuntu will scream on your lappie. As others advise boot up the install disk -> "try" mode ( be advised may have to edit the kernel boot line with acpi_osi="linux parameter) and play with lubuntu, see if you like it and all devices  work.

I left windows behind a long time ago and have never looked back. The only advantage to keeping windows that I am aware of is:
a. games you are fond of;
b. Any proprietary applications that you can not leave behind, -- I am unaware of any windows aps that an alternative is not available in 'buntu.

What else can I say, but welcome to our world, may be a steep learning curve departing from windows and learning a different operating system; but, believe me the effort is well worth it !
[INDENT]my 2 pounds worth ==> BDQ

[/INDENT]

---

### Post by mungatsuma on 2012-12-08
> **Swagman said:**
> Some important things you ***need*** to know right from first base.

1: iTunes is **incompatible**. If you *have* to have it then either duel boot or setup a vm.

2: Any document created or edited using Libre Office/Open Office will cause you formatting grief within Ms Office. <-- Many people will disagree with this but just as many will agree !!

3: I'm sure others will add to this list.

I've laid these out for you right here so you are not disappointed later.

Also remember..As a N00b you are likely to accidently wipe your windows install when first time attempting a duel boot installation.

Also.. Here's an old but very apt read, still relevent today.

[** Linux is NOT Windows**]("http://linux.oneandoneis2.org/LNW.htm")


If you decide to go ahead with the install you now have your eyes wide open. We're all here to help you with any problems/glitches you may run into.

Good luck ... & Welcome to the world of Gnu Linux

To add on to the list

4. Power point presentations saved in post Office 2007( read Vista and Windows 7) .pptx format will be a pain to edit and view in Libreoffice/ openOffice Impress. The workaround i have found is fire Windows, and save in XP/2003 office .ppt format, then you can view and edit in LO/OO with ease.

5. Getting Ms Office 2010 to work in Linux is difficult and will not be perfect, but LO is better anyway.

6. If you do not like the way the desktop looks like, you can change to another, more to your liking. Not just the wallpaper, but a whole lot more. it feels like a totally new system. In Ubuntu there is Kubuntu, Lubuntu, Xubuntu ( KDE, LXDE and XFCE respectively) and a host of many others. Just try one after the other. I left Ubuntu out since its the default (Unity)

Welcome to Linux for Humans.

---

### Post by DuckHook on 2012-12-08
Hello MAFinOKC. Another welcome from the community! Firstly, 'bravo' to your foresight in coming here and poking around before charging ahead with an install. If more people approached their installs with your methodical caution, there would be a lot less desperation and fewer cries for help on these forums.

> **pkadeel said:**
> The best thing I like about major linux distros in general is that you can test it before actually installing it on your computer. Just go a head and download an iso of any major distro. Burn that iso to a DVD or a USB and boot from it. When asked, select the Try option and it will start the whole OS from that disk. Check the working of all devices on you computer and if satisfied then install it actually.

Due to the running of OS from a DVD or USB, you might feel a slowness but that is ok. A computer which can run vista can very easily handle ubuntu.

+1 to pkadeel. This is by far the best way to start. Most of all, make sure that you can surf and ping a site like google.com, esp wirelessly. This will mean that your wireless card is supported. Actually, the biggest general issue with Linux installs is the graphics card, but an incompatibility there would be self-evident: the desktop won't start up.

Once you feel that you are ready to install, make sure you read this link first:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

It's really quite easy. I feel that it's easier than a Windows install, but opinions differ.

Here's the important stuff, though:

1. Before doing anything *BACK UP* all of your data to an outside drive/DVD/USB stick. Then check the data to make sure it is good. This is far and away the most important step. If this is done, disaster is averted and any misstep is limited to being an inconvenience at most.
2. If you want to dual boot, then it is best to create/modify your partitions properly beforehand. This way, at the point where the installation asks you how you want to install, you can select "something else" and customize your installation in a more controlled fashion (see point 3 below). Alternatively, you can simply choose the "install Ubuntu alongside" option and the installer will use a default partitioning scheme that is perfectly serviceable.
3. This step is optional. It is more complicated and you may wish to forego it at this point until you are more familiar with partitioning, Linux file structures, etc: I used to recommend a separate /home partition, but have since modified my recommendation based on advice from @oldfred. If you want to preserve your data so that future installs do not wipe it out, then it is advisable to create a separate partition for data. Provided that you select "something else" during the install process, you will be given a chance to tell the operating system where to mount this partition. I would mount it at /home/data but others are happy with /mnt/data or /media/data.
4. What follows is just general advice and preferences. The above measures assume that you want to set Ubuntu up as an independent operating system that runs outside of Windows--a true dual boot. There is also an alternate way to install Ubuntu, called WUBI, that runs it from *within* Windows. I strongly discourage this method, but that is just my opinion. Others are better placed to advise you on the WUBI method, as I have never used it.

Happy install! Hope you enjoy Linuxing.

*Edit: Wow. In the time it took me to write my post, you received tons of good advice from others. All good stuff. Esp listen to @oldfred*

---

### Post by DuckHook on 2012-12-08
> **Bashing-om said:**
> Your laptop has a celeron processor and I doubt "pae" enabled, thus ubuntu will not run. However lubuntu will scream on your lappie. As others advise boot up the install disk -> "try" mode ( be advised may have to edit the kernel boot line with acpi_osi="linux parameter) and play with lubuntu, see if you like it and all devices  work.

'buntu (all flavours) 12.10 will not run, but 12.04 is still on the 3.2.x kernel and will run. I would advise beginners to use 12.04 in any case due to the long term support. Good call on Lubuntu. IMO the better choice for people coming from Windows because the environment is very similar.

---

### Post by DuckHook on 2012-12-08
> **Bashing-om said:**
> I am unaware of any windows aps that an alternative is not available in 'buntu

Not to contradict, but unfortunately, there are many Windows apps that have no (or insufficient) alternative in the Linux world. In the business world that I came from, there are no real alternatives to:

1. AutoCAD
2. MS Project
3. Industry-specific accounting suitable for dozens of concurrent users
4. High-level industry-specific CRM

I don't know about other industries, but the same can probably be said elsewhere. Now, I agree that these are not typical casual desktop-user apps, but the problem is that if even one of these are critical to the user, then Windows is still indispensable and must somehow be accommodated. Personally, I do so using a virtual machine. Others dual boot.

Therefore, I rarely recommend that a new user simply dump Windows entirely. Problem is that, like it or not, Windows is the predominant desktop OS in the world and there are applications that are written only for it. It needs to be kept around--like the crazy uncle in the attic maybe--but for most people, we don't know what we might need it for.

---

### Post by Manodedios on 2012-12-08
Just thought i'd comment - i registered just to make this post.  I was a M$ zombie for many many...many years until I started getting into Android (Via my smart phone). I have a  desk top Running  Win 7 64 - ultimate and I have a Toshiba L355D-S7901 - Dual core AMD on Win Vista 32. so since my wife mainly uses the desktop the lappie was left to me and my evil machinations.

needless to say with minimal research I dual booted Ubuntu 12  - love it! I have no clue how to do stuff but worked out of the box . I've have to Dl a wireless card driver, Video card driver and flash and learned to install. I  will say its a steeeeep learning curve but you wont learn if you dont try. I will say, had i researched a little more i might have chosen Mint instead. but im an all in type of guy so here i am. :P

---

### Post by MAFinOKC on 2012-12-15
According to Monsieur Belarc (une blague, une blague), this laptop has an Intel Pentium processor and according to what I read, PAE *is *enabled on the 32-bit versions of Vista.

---

### Post by MAFinOKC on 2012-12-16
Thanks to everyone for their helpful suggestions! So far I have looked at Ubuntu 12.10, Xubuntu 12.10, and the latest version(s) of Mint and have downloaded their ISO files for burning to disc. I see also that Ubuntu provides a Windows installer (wubi.exe) that if I am not mistaken sets up a dual-boot option at start-up. There are numerous posts on how to manage dual-booting of Windows Vista or 7 and Ubuntu. I have two reasons for being reluctant to go that way: 1) The computer in question is a Toshiba laptop with a 250-Gb hard drive and I'm already closely monitoring disk usage so as to keep the disk at about its current state of being 60-70% full. Partitioning the disk for two OS's and the ramifications thereof are something I'd like to avoid. 2) I am gravitating toward Linux because I want to *get away *from Vista, which I've disliked intensely since the beginning. Wouldn't running a Windows virtual machine or emulator under Ubuntu be a better way to go? Apparently the program Wine does that. I've appreciated all the good advice so far and am hoping for some guidance in this.

---

### Post by Ozymandias_117 on 2012-12-17
Wubi doesn't actually create a real dual boot, it simply installs Ubuntu as a program inside of Windows, so it is actually still on the same partition as Windows, as a file.  The main problem with trying to use VBox is you won't have very good 3d acceleration. If you're only using basic programs and not any games or other 3d intensive applications you should be fine.  The only problem with Wine is that there is overhead in converting the Windows system commands to Linux system commands, which means programs will run somewhat slower (Although usually not noticably) also, only some programs work with it.  Check [http://appdb.winehq.org/]("http://http://appdb.winehq.org/") to see if the programs you can't live without and can't find a suitable replacement for work in Wine.

---

### Post by JKyleOKC on 2012-12-17
If I'm interpreting your user name correctly, we're both in zip area 731xx. Not too many of us using Linux here in Thunder country, but I believe there's a user group...

Welcome to the fun! I recommend Xubuntu; I've used it for five years now and it's done all that I could want. I'm not a gamer so I can't say much about game performance, though. I do run virtual machines loaded with WinXP to support my Windows-using customers, and ran "wubi" for a while on a laptop that didn't want to accept a native install. Never tried WINE.

You'll find these forums quite helpful!

---

