---
title: "Using Ubutnu on an External HD"
date: 2013-07-07
forum: New to Ubuntu
---

### Post by jtoem on 2013-07-07
Hello everyone!

I am an absolute beginner, but I think my question is about installation, so move it if you see fit.

I recently broke my Nexus 7 and I like to write, email, and surf. I am using a friend's computer. It runs Windows XP Professional from 2002 with Service Pack 3. The processor is an Intel Celeron at 1.8GHz and the computer has 1GB of RAM. I want to start using Ubuntu because it seems user friendly. I want to start using Linux because I want to learn more about computers. 

I have a 1TB Seagate External HD USB 2.0/3.0 that has a SATA port. I got these external drive to backup my MacBook, which I don't have with me. The drive is therefore formatted with NTFS. But most computers here in Madagascar run Windows. Can I change the format? Should I partition? I plan to build a computer within the next few months. I will use an Ivy Bridge i5 3570K. 

From Ubuntu.com, it seems like I can download, for example, Ubuntu 12.04.2 Desktop i386, put it on a flash drive, and install it to the computer. But I want to install it on the external HD. Is that possible? Will I need to connect the HD via SATA or can I just connect it via USB to the back of the tower? I don't want to lose any of my friend's files. Is that version of Ubuntu OK? I don't really fancy needing a new one when I have my own computer, so I want to get a version compatible with both.

What I hope to do is walk around with my external HD and boot computers in cyber cafes with the Seagate so that I can continue writing without worrying about saving and updating and deleting different versions of the documents. Is that crazy? 

Thanks in advance.

PS - I cracked the screen on my Nexus 7. The screen is fused to the digitzer so the replacement was expensive: 130usd. I have the 300 usd 32GB/Data version, so I ordered a replacement. I installed it and it doesn't illluminate. Aftraid I did something wrong, I had a technician take a look; he said the screen is defective. The crack happened late May, so I have been using other peoples devices for a long while.

---

### Post by Impavidus on 2013-07-07
With 1GB or RAM you'll be better of using Xubuntu, which is somewhat lighter on resources, but has less eye-candy. You said that you don't need that. It also runs on the latest computers, however, most new computers are better of using 64 bit systems, but the old one with only 1GB RAM is better of using 32 bit.

You can install Ubuntu on an external drive. Connect it to the computer using the fastest connection available, or it will be a lot slower than running from an internal drive. Ubuntu must be installed on an ext4 partition (or something related), which is not supported by windows, so if you want to share files with windows machines you'll have to make a separate ntfs partition on it.

There is one problem with walking around with your external hard drive, plugging it into random computers at cyber cafés and booting them from it (assuming you already checked you can boot those computers from an external drive). The hardware has to be compatible with the drivers installed on your external drive. This may be a problem when you use proprietary drivers for for example the video card or a wireless network card.

---

### Post by jtoem on 2013-07-08
I need to use something lighter, like Xubuntu, on this computer but a newer computer should run a 64 bit system. That means I will need to get a new OS for whatever hd I use in a new computer. Is it possible to run Xubuntu on a flash drive?  I have a 32GB FAT32 flash drive and a 128GB NTFS flash drive. 

Also, I sea that I was in error about the file system of my mac; it is windows that uses ntfs. mac uses hfs. this PC reads and writes on both those flash drives, but it wont reconize the hd. that must be hfs? I definitely put files from the macbook onto the 32GB and the Seagate external HD. So I am a bit confused...

---

### Post by Impavidus on 2013-07-09
It's all about RAM. With less than 2GB it's better to use a light flavour, like Xubuntu. With more RAM it doesn't matter and comes down to what you like most. With less than 2GB I also recommend to use a 32 bit system, with more than 3GB 64 bit is better. 32 bit still works, but won't be able to use your computer's full potential. 64 bit has to be supported by the CPU, but all moderns CPUs support it.

Just like Ubuntu, Xubuntu and most (all?) other Linux variants can be installed on a removable flash drive.It has to be formatted ext4 (or ext3). Without additional software, Windows only works with ntfs and fat32 and has to be installed on ntfs, Linux can work with ext3/4, fat32 and ntfs and has to be installed on ext3/4, Mac handles hfs and fat32 and has to be installed on hfs (I think, I'm not a specialist in this). With additional software some other systems may be supported, but for installation of the OSes themselves only the native file system is supported.

Your 1TB external drive is probably formatted hfs, which is only supported by Mac. The 32 GB flash drive is supported by all systems, the 128GB flash drive may be unsupported by Mac. You can install Ubuntu or Xubuntu on  any of your external drives/flash drives, but when you do so they have to be fomatted (destroying all files on them) ext4, so that they can no longer be used by Windows or Mac.

---

### Post by newb85 on 2013-07-09
You could install Ubuntu and add the Xubuntu desktop environment.   Them you could choose which DE to use when you log in, depending on the resources of the machine you're using at the time. If you can stick with the open source drivers, that would be best for what you're trying to do.

---

### Post by dannyboy79 on 2013-07-09
> **Impavidus said:**
> Your 1TB external drive is probably formatted hfs, which is only supported by Mac. The 32 GB flash drive is supported by all systems, the 128GB flash drive may be unsupported by Mac. You can install Ubuntu or Xubuntu on  any of your external drives/flash drives, but when you do so they have to be fomatted (destroying all files on them) ext4, so that they can no longer be used by Windows or Mac.
this is not true, IF you want to run Ubuntu from a USB drive it doesn't have to formatted as ext(X). I used multisystem ( [http://liveusb.info/dotclear/](http://liveusb.info/dotclear/) ) to create a usb stick which can boot multiple Linux ISO's all from a FAT32 usb stick and still even store stuff on it which I can access from within windows. I have portableapps installed on it so I can run a ton of windows apps from the flash drive and never have to install the apps on the computer I am using the usb stick in. I call it my magic stick. ;)  Only certain ISO's work with it but the ones I have on mine are Ubuntu 12.04, Parted Magic, and System Rescue.

Here's a little guide showing you how to create the multisystem stick but you do need a linux box to create the stick, not sure if there's a multisystem application (the application which creates the bootable usb stick with multiply iso's on it) for windows or mac. [http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

---

### Post by oldfred on 2013-07-09
If you want to save Windows data the NTFS (or FAT32) partition must be first on a flash drive. Windows only "sees" the first partition with flash drives. USB Hard drives for some reason can be read from but you cannot boot Windows from them.

 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

      
 With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2128205](http://ubuntuforums.org/showthread.php?t=2128205)
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)


 Full install - C.S.Cameron post #2
[http://ubuntuforums.org/showthread.php?t=2116798](http://ubuntuforums.org/showthread.php?t=2116798)
Full install of 12.04 to 64GB USB device C.S.Cameron post #3
[http://ubuntuforums.org/showthread.php?t=2092077](http://ubuntuforums.org/showthread.php?t=2092077)


 HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

---

