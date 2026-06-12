---
title: "New here, best way to install linux"
date: 2015-06-17
forum: New to Ubuntu
---

### Post by gary62 on 2015-06-17
Hello, for uni next year we will be using linux in our computing labs and I figured I would try to get a head start and teach myself how to use it over summer. So my laptop is running windows 7. I have never used linux before so I apoligise for asking amateur questions that have no doubt been asked several times before. I am thinking about having it dual boot between windows 7 and ubuntu but have no idea how I would go about doing this and was wondering what the best way to go about doing this would be. Also, out of interest, if I don't like ubuntu or if I want to switch to a different version of linux or something how easy is it to uninstall? I would be really grateful if someone could explain the best way to install it and is it possible to keep all my files or will I have to wipe the machine?

---

### Post by slickymaster on 2015-06-17
Hi gary62, welcome to the forums.

Start here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by LastDino on 2015-06-17
I started from Dual boot method but if your PC has good enough hardware, using VM to get used to is rather safer and more interactive option than Live booting. You can also try installing on spare HD/SSD/USB, that is as long as they are big enough.

Dual booting is not a bad option either, it just requires you to read more, be careful and take full backup before you do something which you shouldn't have, and you'll see lot of threads here which will give you an idea about that.

Again, take full backup first before going for dual boot. I can't stress enough on this.

---

### Post by grahammechanical on 2015-06-17
The Ubuntu Live session/Install session will give us these options.

1) Install Ubuntu alongside them [that is other operating systems detected]
2) Erase disk and install Ubuntu
3) Encrypt the new Ubuntu installation for security
4) Use LVM with the new Ubuntu installation
5) Something Else

The simplest method apart from #2 is #1 - Install alongside. But that will give us a partition for Ubuntu and a partition for swap and all our data will be on the Ubuntu partition. We need to have our data on a partition just for data. Then we can re-install or install over Ubuntu without loosing our data. This is more complicated and to do that we choose the Something Else option where we create our own partitions and instruct the installer how to use them. So, you need to study how to partition in Linux.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Some advice 

a) Use Windows utilities to defrag Windows more than once, testing that Windows loads each time.
b) Use Windows utilities to resize and move Windows partitions to create unallocated space that Linux can use as Linux partitions.
c) The Windows boot loader does not recognise Linux operating systems so every Linux distribution installs its own boot loader which will let us load Linux or Windows. 
d) The last Linux distribution to be installed will control the boot menu.
c) If we remove a Linux distribution that controls the boot menu we will not be able to load the still existing operating systems until we have installed another boot loader.
d) If we only have Windows and Linux re-install the Windows boot loader before removing the Linux OS.
e) Have a Windows repair disk or whatever is used in Windows to re-store it.
f) Know the difference between a BIOS boot system with a 4 Primary partition limit and the need to create Extended and Logical partitions, and a UEFI boot system with GPT (GUID Partition Table) which does not have the same limitations as the BIOS boot system.

By the way, which does your machine have? BIOS or UEFI? Well, you did want to start school early. :)

Regards.

---

### Post by gary62 on 2015-06-17
> **LastDino said:**
> I started from Dual boot method but if your PC has good enough hardware, using VM to get used to is rather safer and more interactive option than Live booting. You can also try installing on spare HD/SSD/USB, that is as long as they are big enough.

Dual booting is not a bad option either, it just requires you to read more, be careful and take full backup before you do something which you shouldn't have, and you'll see lot of threads here which will give you an idea about that.

Again, take full backup first before going for dual boot. I can't stress enough on this.

Out of curiosity what are the pros and cons of a VM and dual booting? I'd imagine dual booting would be faster? I have 2 laptops, one being a surface pro so I was thinking of maybe using a VM on that for linux mint. 

Perhaps this sounds stupid but I feel I will force myself to use ubuntu more if it is dual boot. Just a little worried about installing it since I've never really done something like this before. Out of interest, since windows 10 is coming out soon, if I wanted to update my laptop running windows 7 to windows 10 and it has ubuntu installed do I have to go about updating it in a different way?

Again I apologise for any stupid questions

---

### Post by oldfred on 2015-06-17
Best to back up Windows, which you really should be doing anyway.

Also use Windows own partitioning tools to shrink its own partition and reboot immediately so it can run chkdsk and repair itself to its new size.

Many systems with Windows 7 used all 4 primary partitions that is allowed with BIOS/MBR. A few new Windows 7 systems may be UEFI which is a lot different. 

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
Do not create new partitions with Windows, use gparted for Linux.

The default install is /(root) and swap, but often better to have /home and/or a data partition. If dual booting with Windows a NTFS data partition is usually the best choice. You cannot create the NTFS partition during install, but can partition in advance with gparted or leave space for it and add it later.
      
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by grahammechanical on 2015-06-17
You said that you are going to learn Linux. You will not learn much by just installing one Linux distribution. You need also to learn about dual booting and VM installs and multiply boots.

---

### Post by LastDino on 2015-06-17
> **gary62 said:**
> Out of curiosity what are the pros and cons of a VM and dual booting? I'd imagine dual booting would be faster? I have 2 laptops, one being a surface pro so I was thinking of maybe using a VM on that for linux mint. 

Perhaps this sounds stupid but I feel I will force myself to use ubuntu more if it is dual boot. Just a little worried about installing it since I've never really done something like this before. Out of interest, since windows 10 is coming out soon, if I wanted to update my laptop running windows 7 to windows 10 and it has ubuntu installed do I have to go about updating it in a different way?

Again I apologise for any stupid questions


Booting directly will most likely provide better performance but VM provides you certain safety net which you wont have if you're dual booting. Links provided so far in this thread are absolutely must for you to read carefully and follow if you want to do it correctly. Again, both have pros and cons, VM wont utilize your hardware at max like what direct booting will do (Like graphic card), but direct dual booting has chance of screwing up with your existing system and by some slim chance you encounter something like incompatible hardware problem, you'll end up blaming Linux. So, it's better to have training wheels, VM also helps to reduces need of direct installation of range of Linux distros you'll be exposed to soon enough.;)

You should really start with posting your hardware config, and whether you have UEFI or not, that detail is going to decide course of this thread.

---

### Post by LastDino on 2015-06-17
And sorry, I forgot to answer upgrading W8 to W10 issue. If you want to dual boot Windows and Linux you will need Linux native boot-loader. i.e: Grub2 etc. Which is installed by Ubuntu by default.

Which I'm fairly certain will be removed by big update like version update of windows as it will try to install its own windows native boot-loader again. 

Can't answer that in detail as I'm yet to try that update myself and there is no way to really tell how much effect it will have till someone who has tried it can tell you.

---

### Post by kurt18947 on 2015-06-17
I've been 'playing' with Virtualbox. It's an interesting and useful tool. One thing stands out though - I wouldn't use it on a machine with less than 4 GB. RAM and the more the merrier. Ubuntu-Gnome & Win 10 preview take around 2900 MB. and that's just with perhaps Firefox running on one machine.  I seem to be having better luck downloading the Virtualbox .deb files from Virtualbox.org than using the version in the 14.04 repositories, the version in the repositories is somewhat dated. The ability to export an 'appliance' to portable storage and import the 'appliance' to another Virtualbox install on another machine is handy, far quicker than doing a bare metal reinstall then all the settings and add-on apps.

---

### Post by Bucky Ball on 2015-06-17
You could download the .iso and use Unetbootin or Universal Disk Installer to burn it or install to a USB stick and run Ubuntu off the stick. If you just want to try it out, you can burn install media, boot from it and 'Try Ubuntu'. That will give you a look around but not as fast as hard drive install and you may have issues with graphics and wireless that could be fixed in a HDD install. Welcome to the forums and good luck. :)

---

### Post by cooleryawner on 2015-06-17
Best and safest way to install: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

