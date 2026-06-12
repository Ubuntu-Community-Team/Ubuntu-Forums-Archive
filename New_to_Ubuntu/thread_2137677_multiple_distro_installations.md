---
title: "multiple distro installations"
date: 2013-04-21
forum: New to Ubuntu
---

### Post by Saberwing91 on 2013-04-21
Hey guys, I've been curious about Linux for a while and I've finally decided I want to try it out.
What I'm trying to do is a tad complex and I've researched all over the web with limited success,
I have an Acer laptop with Win7 installed and a 1TB EHDs and (depending on what you guys think)
I either want to install all the distros to my EHD so I have a portable way of showing it to people
who are looking for something different than Windows, or free up enough space on my laptop to have
one main distro (most likely Ubuntu) and use the EHD to install the rest. I apologize in advance if
I missed any key points you guys need to know in order to help me. I'll gladly answer any questions.

Thanks

---

### Post by ibjsb4 on 2013-04-21
You could install ubuntu and then install the different desktops inside ubuntu and choose which one you want to use at login.  That way you would have:

Unity
Lubuntu
Xubuntu
Gnome Shell
Gnome Classic

That should be enough to keep you busy for a while.

---

### Post by Saberwing91 on 2013-04-22
Well I wanted to have a bit more variety in the distros. I definitely want Ubuntu and Mint and I was thinking about Fedora and maybe some other popular ones.

I just need help on the technical side of how I would install all (or most) of them on my EHD.

---

### Post by HermanAB on 2013-04-22
Howdy,

The way to do this, is to install Virtualbox and then make as many virtual machines as you want.

There is a forum topic for virtualization.

---

### Post by BlinkinCat on 2013-04-22
> **HermanAB said:**
> Howdy,

The way to do this, is to install Virtualbox and then make as many virtual machines as you want.

There is a forum topic for virtualization.

Hi,

For general guides on virtualization, pages may be found in NewDocs - See link in my signature.

Cheers - :)

---

### Post by Saberwing91 on 2013-04-23
Thanks for the replies guys, but virtual machines just aren't what I'm looking for.
I don't have enough disk space on my laptop for more than one distro, and I would be
 splitting up RAM between windows and the distros. Plus it wouldn't be portable enough
for me to show my friends.

---

### Post by fantab on 2013-04-23
Create partitions of about 15-20GB and keep installing the distros you want. About 4 or 5 partitions should suffice, I guess. Assuming that you already have Ubuntu, you will also have GRUB from Ubuntu install. 

Now, when you install a new Distro Ubuntu-Grub will be replaced by the Distro's. If you don't want to replace Ubuntu-Grub then DON'T install GRUB from any other distro. After installing the Distro log back into Ubuntu and run: 

sudo update-grub

 Some Distros may not give you an option to not install Grub, in that case install the Grub on the distros '/' partition, log back into Ubuntu and update Grub. 

If you install Grub from another Distro and later decide to remove that Distro then you will have to Fix the Grub, using either Ubuntu Live CD/USB or "Boot Repair".

---

### Post by Saberwing91 on 2013-04-24
Yes! Precisely the information I'm after, thank you so much fantab.
If you don't mind, I have some other questions about the installation process.

As I mentioned earlier I'm going to be installing the various distros on my external hard drive. Would it be more or less the same process of installing a distro on my laptop?

Also, if I did want Ubuntu on my laptop, would Ubuntu-GRUB still be able to interface with the distros on my EHD?

---

### Post by fantab on 2013-04-24
Ok. I missed that you want to install on ExHDD.
Yes it will be same as installing a Distro on HDD. Except you cannot use 'auto-install' methods and opt for Manual install. 
Yes, Ubuntu-Grub can handle distros from ExHDD, but I won't recommend that. Lets just have a Boot-Loader on each HDD or ExHDD. It keeps things simple and more efficient.

Suggestion: Leave your Laptop HDD Untouched. Let it have Ubuntu and its Grub.

If you want to install on ExHDD, then:
** Does your Laptop has UEFI boot? If yes, then you have to create a partition to accomodate that. 
*Make 15-20 GB partitions on your ExHDD.
* Install distros (follow the Grub install procedure I suggested in my earlier post). 
* You will still need only one Grub on your ExHDD, so pick a distro from which you want to use the Grub. I suggest you use one that uses apt-get, ie Debian or Ubuntu-based distro, because they will more or less have same CLI commands to deal with Grub. Other distros use different commands. If you want to learn different CLI then ignore my suggestion.

** Check your BIOS/UEFI settings and enable 'to boot USB devices first'. This way when USB ExHDD is plugged in the Mobo will boot that first. If its not plugged in it will boot your regular HDD. If your Mobo does not have this feature to boot usb devices first then you have to manually select the ExHDD from Bios.

EDIT: Create SWAP on EXHDD too.

Good Luck...

You might find [**THIS**]("http://www.howtogeek.com/howto/39747/how-to-boot-10-different-live-cds-from-1-usb-flash-drive/") Useful too.

---

### Post by Saberwing91 on 2013-04-25
Ok, I think I've got a good idea of what I want to do, thanks to all the awesome help you've provided :)
Should have done more research before I started question spamming, sorry.

---

### Post by fantab on 2013-04-25
A default Ubuntu install takes place on three partitions (if you don't interfere manually with 'Something Else Option"), which are "/' root, "/home" and "SWAP". 15-20GB for "/" partitions, usually is more than enough. After installing everything I need from Software Center I have 10GB Free space in my 20GB "/" partition. If you feel that you will need more then go for 25-30GB more than that will be waste of HDD real estate. 

If you don't create a separate /home partition (which will house your personal DATA plus your settings and preferences for software applications) then "Home" will be created in the "/" partition. If you opt for this kind of set up then you will have to create a separate partition for your DATA. To do this just create an ext4 formatted partition and do NOTHING during install. Later you use this partition to store your DATA which will be OS independent. /home will not be OS independent. Since you are planning to go for multiple Distros, I suggest you consider NOT having a separate /home.  Ideally it would serve you better if you have this separate DATA partition on Laptop HDD. Because if you create this on EXHDD then when it is not plugged in then you can't access your DATA, can you?
If you want you can use additional DATA partition on ExHDD, or you can use it as a back up for your main DATA partition. 

Separate DATA compared to separate /home is preferable when multi-booting. In this set up each distro's '/' partition will have its own 'Home' and there will be no conflicts, as there would be if you share a /home between different distros. An alternative will be to have as many separate /home as many distros you install.
[URL="http://ubuntuforums.org/showthread.php?t=1748541&p=10765330#post10765330"][B]
This POST[/B][/URL] has some excellent advice on how to go about backing up, if you are interested to learn. 

Yes, create a SWAP on both partitions, preferably. In case you want to save space and want only one SWAP then that must be on Laptop HDD. But if you plan to plug or use your other ExHDD on other computers as well then you must put a SWAP there as well. 2-4GB of SWAP should be more than enough, I have 4GB. However, if you plan or use 'Hibernate" function then SWAP must be equal to or more than your RAM in GiB not GB. 1GiB=1024MiB while 1GB=1000MB.

---

