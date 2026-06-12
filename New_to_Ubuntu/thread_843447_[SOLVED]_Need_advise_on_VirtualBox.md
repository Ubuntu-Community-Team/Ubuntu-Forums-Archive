---
title: "[SOLVED] Need advise on VirtualBox"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by wariskampar on 2008-06-28
My system is Pentium M 1.83Ghz, 1GB RAM,HP Pavilion dv4000. Is it ok if I run XP along my current Hardy Heron using VirtualBox? I will anticipate slight performance decrease but it is just want to confirm that it will only happen whenever I turn on XP, right? I intend to install XP as contingency plan only so most of the time it will just linger in my system. Please give some advise

---

### Post by Canis familiaris on 2008-06-28
Go ahead and install XP in Virtualbox, it wont slow down Ubuntu at all. 
XP will run well too since you have a gigabyte of RAM.
If you want [this]("http://amitech.50webs.com/ultimate.html"), then post in affirmative now.

---

### Post by wariskampar on 2008-06-28
yes! that's what i'm intending to do. now! need to learn the installation process. Any advise?

---

### Post by Canis familiaris on 2008-06-28
First you need to install Virtual box of course.
Go to Applications->Add/Remove, search for Virtualbox and install it.
Then Run Virtualbox and create a Virtual Machine, pretty straightforward, no need to explain. Then run the Virtual Machine. It will give am error message. Please post that error msg so that I could direct you how to move further.

BTW Do you have Compiz running?

---

### Post by kestrel1 on 2008-06-28
XP runs fine on Ubuntu.
My current spec is 1.8ghz Athlon & recently upgraded to 1.5gb Ram.
I was using 1GB & it still ran fine. Only thing you may have a problem with is using you normal XP key. I used mine & found that when I went to activate it wouldn't, saying that the key was invalid. I got around this by using another genuine key that I had. You may be lucky though.
If you try to run a webcam, you will notice a big reduction in performance.
I also have an older machine that only has 512MB ram & 1ghz processor. This machine runs virtualbox with Windows 2000 SP4 no problems.

---

### Post by vishzilla on 2008-06-28
This guide should be good [[link]("http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html")]

---

### Post by kestrel1 on 2008-06-28
My advice would be not to use the OSE version of Virtual box.
Download the full version here: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by Canis familiaris on 2008-06-28
> **kestrel1 said:**
> My advice would be not to use the OSE version of Virtual box.
Download the full version here: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Why not? The OSE works very well and is maintained in the repos.

---

### Post by philinux on 2008-06-28
It does not support USB. :(

---

### Post by Canis familiaris on 2008-06-28
> **philinux said:**
> It does not support USB. :(

Oh! I suppose the OP would make the choice whether he wants USB support in the Virtual Machine. Personally I prefer that way, because virtual Windows does not recognise pen drives and thus is more safe for infection.

BTW The link vishzilla directed appeared to solve this problem.

---

### Post by Elfy on 2008-06-28
> BTW The link vishzilla directed appeared to solve this problem.The link, when new, pointed at the vbox repositories which used the non ose version.

The version from sun also doesn't suffer when the kernel is updated and the virtual box parts are left behind.

---

### Post by Canis familiaris on 2008-06-28
Sorry! Wrong Post!

---

### Post by Canis familiaris on 2008-06-28
> **forestpixie said:**
> The link, when new, pointed at the vbox repositories which used the non ose version.

The version from sun also doesn't suffer when the kernel is updated and the virtual box parts are left behind.

Oh! I understand!
I use Virtualbox OSE. Will it stop working on a kernel update? What'll I do then?
Also is it possible to remove OSE and install the version from Sun. without losing the existing Virtual Machines.

---

### Post by Oldsoldier2003 on 2008-06-28
> **kestrel1 said:**
> My advice would be not to use the OSE version of Virtual box.
Download the full version here: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

+1 the ose version lacks some features and updating. also you can update the kernel module easily when you use the puel version.

---

### Post by Oldsoldier2003 on 2008-06-28
> **Anurag_panda said:**
> Oh! I understand!
I use Virtualbox OSE. Will it stop working on a kernel update? What'll I do then?
[COLOR="Red"]Also is it possible to remove OSE and install the version from Sun. without losing the existing Virtual Machines.[/COLOR]

yes. there is no problem with doing this.

---

### Post by kestrel1 on 2008-06-28
If you have USB enabled virtual Windows will recognise pen drives & external USB HDD's, you just have to choose them before you enter the virtual machine.

---

### Post by Canis familiaris on 2008-06-28
Is this the right link for the closed source version of VirtualBox? Or am I downloading the copen source version again.

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

Is there any repository for the latest closed source version of VirtualBox.

---

### Post by Canis familiaris on 2008-06-28
> **kestrel1 said:**
> If you have USB enabled virtual Windows will recognise pen drives & external USB HDD's, you just have to choose them before you enter the virtual machine.

Am I right in assuming that the closed source version will have option to disable USB if needed.

---

### Post by wariskampar on 2008-06-28
In Synaptic, the latest version is 1.5.6 but according to link given by philinux it should be 1.6. which one i should install.

---

### Post by Elfy on 2008-06-28
Yes that is the right place to get it and yes you don't have to have the usb enabled.

Current version is 1.6.2
and the deb is virtualbox_1.6.2-31466_Ubuntu_hardy_i386

AS oldsoldier says it's an easy enough changeover.

I will add that when you are using the puel version and ther is a kernel change which affects it - you get an error message which is good enough to tell you exactly what command to run to restart the vbox driver.

---

### Post by Canis familiaris on 2008-06-28
> **forestpixie said:**
> Yes that is the right place to get it and yes you don't have to have the usb enabled.

Current version is 1.6.2
and the deb is virtualbox_1.6.2-31466_Ubuntu_hardy_i386

So basically there is no way to install VirtualBox closed source through the repos. I prefer the repos, because they update automatically.

---

### Post by Elfy on 2008-06-28
There might be, but tbh I have never bothered too much with looking for one. Maybe a quick google or a search on the sun site might unearth one - if you do find one, post it here for the next to come looking.

I don't think it actually changes much - I tend to leave it as it is until I change buntu versions.

---

### Post by Canis familiaris on 2008-06-28
> **forestpixie said:**
> There might be, but tbh I have never bothered too much with looking for one. Maybe a quick google or a search on the sun site might unearth one - if you do find one, post it here for the next to come looking.

I don't think it actually changes much - I tend to leave it as it is until I change buntu versions.

I searched but did not find one. I guess I have to downloaded and install it from a site. 
Luckily it is .deb. Long live APT. :)

---

### Post by Canis familiaris on 2008-06-28
I downloaded and installed the closed source version. Working Well.
However there was one change I noticed:
The command line version is VBoxManage instead of vboxmanage. Dunno why this change though.

---

### Post by wariskampar on 2008-06-28
Already install VB 1.6. Now what? I got one empty partition of 18GB. I plan to install XP on this partition but I dont know whether it's possible or not. Btw, /home and filesystem are on their dedicated partition respectively. Any suggestion guy?

---

### Post by Elfy on 2008-06-28
Install xp really or as a virtual machine - either is possible you can point the virtual box hdd at that partition.

When you make the virtual hard drive be careful with it's size as I don't think you can resize it, but I could be wrong there.

---

### Post by WRDN on 2008-06-28
> **forestpixie said:**
> Install xp really or as a virtual machine - either is possible you can point the virtual box hdd at that partition.

When you make the virtual hard drive be careful with it's size as I don't think you can resize it, but I could be wrong there.

I installed XP in VirtualBox today. Im dual booting, but often need Windows apps that cant be run in WINE, so its more conveniant to run a Virtual Machine.
With regards to the hard drive size, if you create a fixed size image, the size cannot be changed. I would not recommend doing this however. Rather, it is a better idea to create a disk that will become larger dynamically. When you use this option, HDD space is not used until files are written to the disk by the OS, unlike the fixed size image. This means, you can create a very large dynamic image that will never be fully used. However, because it doesnt use HDD space, it gives the OS Space, while removing any space issues.

---

### Post by Elfy on 2008-06-28
Sorry - that is as I meant - I use a dynamic disc size myself, what I meant was to do as WRDN says - use the dynamic sized hdd but to use the size of the partition.

If as you have a 18Gb partition to use - if you made the vbox a hardrive of 7Gb then that is as big as it can be - a fixed vbox hdd would immediately have the 7Gb, dynamic vbox hdd would use what it needed.

So if you did want to use the whole of the partition -  make the hdd that size.

---

### Post by wariskampar on 2008-06-28
I really dont understand about the dynamic hdd sort of thing. How do we set it? As I mentioned in my 1st post, I do not intend to XP but just install in case of unforeseen matter later on. So I want to install strip down version of XP (discard Outlook, Games etc). I really need recommendation on optimum size (sufficient but not too many!) for my XP. Btw, here is my fsdisk:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1946    15631213+  83  Linux
/dev/sda2            9536        9729     1558305    5  Extended
/dev/sda3            1947        7137    41696707+  83  Linux
/dev/sda4            7138        9535    19261935   83  Linux
/dev/sda5            9536        9729     1558273+  82  Linux swap / Solaris

Partition table entries are not in disk order

Hope somebody can show me the right way

---

### Post by jbrown96 on 2008-06-28
Sorry, I'm no pro on reading the fdisk output. You have several Linux partitions listed. Could you explain how they are mounted and such. 
My partitions are:
11.5GB ubuntu  reiserfs
11.5GGB OpenSUSE reiserfs
~120GB music/movies xfs

I have VirtualBox setup in Ubuntu with a 5GB dynamically expanding partition, and it barely uses anything. Granted I only use XP for itunes giftcards (grumbles at family). 

You made it sound like you're not using it for much, so I would assume that this setup would work for you as well. I'm not sure about the version in the repos, but the version from the website is awesome. It's got some really great features now. I really like the seamless windows.

---

### Post by wariskampar on 2008-06-28
Thanks guys!(what is the proper way?) I had installed XP in VirtualBox. Take me a very long time to update to SP3 (it is 4 am now!). Just to share with everybody here is my setting:
RAM 512Mb
Partition Size 7GB
Format FAT
For now, i installed XP on my /home and will learn some more to transfer this to dedicated partition. Thanks again

---

