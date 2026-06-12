---
title: "Windows 7 Installation"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by Mikesla on 2011-11-09
Hello.

 I have decided to take a look at Ubuntu, actually it's my very first time ever wanting to look at a linux OS (I am a MS-DOS, and Windows user).

 I am looking to install Ubuntu under Windows 7, and I am wondering once I do install Unbuntu will I still have read access for files on the installed drive, or will Ubuntu simply reformat the HD, and keep it for it's own use?

 I have two HD's, one Drive C, and the Other drive D. Windows 7 of course is installed on drive C (as normal), and I have other software saved/in storage on drive D, so if I decide to install under Windows the Ubuntu software on drive D will it wipe out all of my files on drive D?...

 I know odd question, but I have to make a decision on how I am going to proceed.

Thank You.

---

### Post by Toafan on 2011-11-09
There's an installer (Wubi) to run within Windows to install Ubuntu alongside Windows.  I've never used it myself, so I can't recommend it (I hear there are weird, unique problems to it), but it's intended for the kind of thing you're talking about.  

I've installed my Ubuntu an another drive (basically, your drive D idea, although drives are identified differently under linux) and it works fine.  But yeah, if you install Ubuntu on this other drive you'll have to format it, and will lose everything currently on the drive.  

One caveat, I read somewhere else that the "install Ubuntu alongside Windows" option on the installer will install using Wubi, and that if you want to install on a separate drive you need to select the "something else" option.  This was for Ubuntu 11.04, so I don't know if it still applies to 11.10.  But something to keep in mind.  

If/When you got to install that way, you'll need to figure out which one is Windows.  Come on back, we'll help out.

---

### Post by Mikesla on 2011-11-09
> **Toafan said:**
> There's an installer (Wubi) to run within Windows to install Ubuntu alongside Windows.  I've never used it myself, so I can't recommend it (I hear there are weird, unique problems to it), but it's intended for the kind of thing you're talking about.  

I've installed my Ubuntu an another drive (basically, your drive D idea, although drives are identified differently under linux) and it works fine.  But yeah, if you install Ubuntu on this other drive you'll have to format it, and will lose everything currently on the drive.  

One caveat, I read somewhere else that the "install Ubuntu alongside Windows" option on the installer will install using Wubi, and that if you want to install on a separate drive you need to select the "something else" option.  This was for Ubuntu 11.04, so I don't know if it still applies to 11.10.  But something to keep in mind.  

If/When you got to install that way, you'll need to figure out which one is Windows.  Come on back, we'll help out.


 Thank you very much for responding. I'll definitely keep these things in mind for sure.

Which now brings me to one more question which has totally slipped my mind. I forgot to mention I also have an external (usb) backup drive (120 gig) which I am not using at the moment, is it possible for me to make or turn this external drive into a full Ubuntu installation without the need for messing around with my two other drives, or dual-booting?

 I know that there is a "show me how" on the Ubuntu website, but that is for usb sticks. I suspect that there would be differences between usb sticks, and usb HD's (I could be wrong though).

Like I said I just moved into the Linux neighborhood, so everything will be new to me. :)

---

### Post by OrangeCrate on 2011-11-09
Guidance on dual booting is available here:

[http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Dual-Booting_Windows_and_Ubuntu)

---

### Post by waynefoutz on 2011-11-10
Wubi isn't a bad way to get your feet wet at all. If you are unsure, and don't want to partition your drive, this is the way to go. What Wubi does is essentially creates a big file on your Windows drive, and fools Ubuntu into thinking that file is a physical drive. The down side to this is if that file gets corrupted, no more Ubuntu, so it's not meant to be permanent. The upside is if you don't like Ubuntu, you can boot into Windows and uninstall Ubuntu with the windows, Add/remove programs in the control panel.

---

### Post by Toafan on 2011-11-10
> **Mikesla said:**
> ... I also have an external (usb) backup drive (120 gig) which I am not using at the moment, is it possible for me to make or turn this external drive into a full Ubuntu installation without the need for messing around with my two other drives, or dual-booting?
Well, I know there are ways to install Ubuntu / Linux on USB drives (flash drives, usb hard disks, whatevs).  It can definitely be done.  How to do it, I haven't a clue - you'd have to do some googleing, there are definitely tutorials/walkthroughs out there somewhere.  

If you can pull that off, though, you're in geek heaven - you can boot it on just about any computer with boot-from-USB and have a full Ubuntu install right there.  'Course, portable usb installs are more finicky than non-portable traditional installs, since hardware-unique drivers and bits require hardware-unique configurations.  Ubuntu will take care of those configs for you normally, but they still need the hardware (nvida card for nvidia graphics drivers, for example)

---

### Post by ixtok on 2011-11-10
> **Mikesla said:**
> Thank you very much for responding. I'll definitely keep these things in mind for sure.

Which now brings me to one more question which has totally slipped my mind. I forgot to mention I also have an external (usb) backup drive (120 gig) which I am not using at the moment, is it possible for me to make or turn this external drive into a full Ubuntu installation without the need for messing around with my two other drives, or dual-booting
 

I think that installing to your usb external is a great way to try ubuntu out. I have done just that. You must get a live cd or use a usb stick which the live cd was installed to. Boot the computer with either the live cd or the live cd usb stick. Choose to install and when the installer gives you options about where to install, Choose the one that matches your 120 gb external drive. The easiest way is to use the whole drive. Make sure that you have the boot loader grub also installed in the 120 gb external. If you don't install grub there and it gets onto your main drive, you will have trouble booting winddows if the external drive is not connected. To boot ubuntu you must change your boot options and choose to boot from the external and everything should be fine.

---

### Post by waynefoutz on 2011-11-10
> **Toafan said:**
> Well, I know there are ways to install Ubuntu / Linux on USB drives (flash drives, usb hard disks, whatevs).  It can definitely be done.  How to do it, I haven't a clue - you'd have to do some googleing, there are definitely tutorials/walkthroughs out there somewhere.  

If you can pull that off, though, you're in geek heaven - you can boot it on just about any computer with boot-from-USB and have a full Ubuntu install right there.  'Course, portable usb installs are more finicky than non-portable traditional installs, since hardware-unique drivers and bits require hardware-unique configurations.  Ubuntu will take care of those configs for you normally, but they still need the hardware (nvida card for nvidia graphics drivers, for example)

The easiest way for a Windows user to create a USB stick is with unetbootin. It will even download the .iso of your choice for you.

---

### Post by mastablasta on 2011-11-10
either unebootin: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
or an even nicer Linux Live USB Creator: [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

---

### Post by rng on 2011-11-10
I realized that in longer run it is best to understand about partitions and their management. So why not create a separate partition on one of the existing hard disks on system and install ubuntu there. It will be done almost automatically by installing from livecd. The partitioning step will also be done during installation procedure. Just remember to defragment the disk first from windows. Ability to dual boot and better linux performance will be added advantages.

---

### Post by Mikesla on 2011-11-10
Thanks guys, allot of info but I finally decided for now is to install it via Windows until I get comfortable with it, hopefully maybe I will eventually dedicate my 160 gig drive to the os. I'm very much interested in getting to know Linux which brings me to my first small problems I have so far encountered...

 Well for starters thank god I grew up using dos or I would be totally lost.

My 1st problem is very simple, and that is Root access, and trying to setup my modem, and getting netzero to work. Once I can figure those things out I should be well on my way.

 Well I'm off to hunt down how to get my internal modem working, and get root access.

 Again thanks guys for helping me make a solid deciding on what type of install to first work with.

Cheers...

---

### Post by Mark Phelps on 2011-11-11
> **Mikesla said:**
> ... and trying to setup my modem, and getting netzero to work. Once I can figure those things out I should be well on my way.

If it's one of the infamous "WinModems", you're not going to be able to get it to work because it relies on internal MS Windows system calls to function.

---

### Post by Mikesla on 2011-11-14
> **Mark Phelps said:**
> If it's one of the infamous "WinModems", you're not going to be able to get it to work because it relies on internal MS Windows system calls to function.


Aaahh, okay. Finally now I can put it to rest then. :(

Thanks guys for all of your help, I really appreciate allot.

Cheers.

---

### Post by I2k4 on 2011-11-15
That "Show Me How" on the Ubuntu site is very good for trial running various alternatives with "Live USB" without mucking up your hard drive - the one thing it omits is at Step 2 where you can configure the Pendrive installer for Persistence (I'd set everything on the USB drive above 2GB as Persistence) which allows you to save settings and delete/install software.  It's worth testing several versions because they not only run differently on different machines with different specifications, but have different operating system interfaces and come with different sets of preinstalled software.  Live USB gives a good feel for what your choices are and how it runs on your box. 

Do some research into dual booting, if that's what you decide.  A surprising (to me) consequence was that Ubuntu replaces the Windows boot up interface with GRUB, and once GRUB is installed it's not obvious how to get rid of it if you change your mind.  I'm happy with dual boot W7/Lubuntu on my little netbook, but not at all wild about the GRUB thing.  Study up.

---

### Post by Mark Phelps on 2011-11-16
> **I2k4 said:**
> A surprising (to me) consequence was that Ubuntu replaces the Windows boot up interface with GRUB, and once GRUB is installed it's not obvious how to get rid of it if you change your mind.


Then, you should check into Boot-Repair ... see below.  That can be used to rewrite the disk MBR back to a Windows MBR: 

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

