---
title: "Windows-to-Ubuntu"
date: 2015-12-31
forum: New to Ubuntu
---

### Post by Nuraj on 2015-12-31
I am new to Ubuntu so i'd like to gather much more information about it before using it. I am currently using Windows 8.1 as my operating system. Recently, I am having problems with my OS so i am intending to switch from Windows to Ubuntu. There are two partitions in my Windows OS. For example,if i install Ubuntu in one of the partition called C: then, will i be able to have access to files of other drive D: after installing Ubuntu or is there any other ways for doing that. Similarly,my current Windows OS have some files stored in C: drive which right now,have been compromised and i am unable to create backup of that.So, will i be able to retrieve the files in the process of installing Ubuntu or after Ubuntu being installed.
I hope to get help from you all soon.
Regards,
Nuraj

---

### Post by grahammechanical on 2015-12-31
Which partition is Windows 8.1 installed on? The fact is that if you install Ubuntu onto drive C you will lose everything on drive C. Ubuntu will need at least two partitions - one for Ubuntu and one for swap.

If the motherboard has a UEFI boot system with GPT partitioning for the hard drive then Ubuntu will also need a partition for its efi boot files. So, that will make it 3 partitions.

 If the machine came with Windows 8.1 pre-installed then it is most likely that the motherboard has an UEFI boot system with GPT partitioning and also a efi boot partition which Windows 8.1 is using for its efi boot files. Ubuntu can use that same partition for its efi boot files.

If Windows 8.1 is installed in EFI mode then Ubuntu must also be installed in efi mode as well. If you intend to keep Windows 8.1 and upgrade it to Windows 10, then you will loose the ability to load Ubuntu as the Windows upgrade will over-write the Ubuntu boot loader.

So, my advice is to fix Windows 8.1 and upgrade to Windows 10 before installing Ubuntu if you intend to keep the Windows OS. And download a Ubuntu ISO image and burn it to a DVD or USB memory stick and run a live/try Ubuntu session and see if you can access the files on drive D.

[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Regards.

---

### Post by stalkingwolf on 2016-01-01
you should be able to boot a Live ubuntu either usb or dvd  and access your files.  If by compromised you mean virus and malware damage i would download and run the avira 
rescue disk.  Ive had very good luck running that soft ware.  you can also try downloading the Hirens disk and running the hdd regenerator tool.  again i have had great luck using that tool.

---

### Post by ian-weisser on 2016-01-01
> **Nuraj said:**
> I am having problems with my OS so i am intending to switch from Windows to Ubuntu.

Ubuntu is not a drop-in replacement for Windows.
Ubuntu does not run Windows applications.
Ubuntu does not behave like Windows. You will have much to re-learn.
Consider fixing your current OS before switching.

> **Nuraj said:**
> So, will i be able to retrieve the files in the process of installing Ubuntu or after Ubuntu being installed.

Only if you keep Windows installed alongside Ubuntu - a difficult and risky task for an unskilled user.
A wrong setting will happily overwrite your entire Windows install and delete all your current data.

It is possible, as stalkingwolf described in Post #3, to recover Windows files using Linux-based LiveUSB media...however it is difficult for beginners, and risks data loss to unskilled users who do not understand Linux commands, filesystems, and conventions.

I suggest looking into the many Windows-based solutions for file recovery.

---

### Post by Herdo on 2016-01-01
I honestly think the best solution here is to just buy an SSD and install Ubuntu on that.  It makes things a whole lot easier for new users.

Samsung 850 EVO 250GB for $89 ---> [http://www.newegg.com/Product/Product.aspx?Item=N82E16820147372&cm_re=samsung_850-_-20-147-372-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16820147372&cm_re=samsung_850-_-20-147-372-_-Product)

I'd personally pay the extra $50 for the Pro 256GB, but either would work great --->  [http://www.newegg.com/Product/Product.aspx?Item=9SIA2W01V61639&ignorebbr=1](http://www.newegg.com/Product/Product.aspx?Item=9SIA2W01V61639&ignorebbr=1)

250GB is plenty for an Ubuntu install, and SSDs are so cheap nowadays there is no reason not to.  Worst case scenario, you end up with a 250GB SSD for Windows.

---

