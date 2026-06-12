---
title: "dual boot starting with vista"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by HelterSkelter1989 on 2008-10-13
i have read a how to guide on setting up dual boot when u start wih vista. i have on problems except that i can't get my laptop to boot from the cd as it says. as far as i know i made the cd right, i burned the iso to the disc with power iso and everything went fine. my laptop is a toshiba satellite a215, with a turion 64 x2 tl-60, so i'm guessing i was supposed to use the second download for 64 bit processors (correct me if i'm wrong). however i tried both downloads and neither of them would boot. as i started up my comp i went to the boot menu and selected boot from cd/dvd and when i hit enter all it did was start up windows. please let me know what i've done wrong,if anything, or if my computer is some special case.

---

### Post by handydan918 on 2008-10-13
> **HelterSkelter1989 said:**
> i have read a how to guide on setting up dual boot when u start wih vista. i have on problems except that i can't get my laptop to boot from the cd as it says. as far as i know i made the cd right, i burned the iso to the disc with power iso and everything went fine. my laptop is a toshiba satellite a215, with a turion 64 x2 tl-60, so i'm guessing i was supposed to use the second download for 64 bit processors (correct me if i'm wrong). however i tried both downloads and neither of them would boot. as i started up my comp i went to the boot menu and selected boot from cd/dvd and when i hit enter all it did was start up windows. please let me know what i've done wrong,if anything, or if my computer is some special case.

Try the cd on another computer. If it boots on another box, then the cd is OK. If not, good chance it's borked....

---

### Post by HelterSkelter1989 on 2008-10-13
i don't have another computer i can use :{

---

### Post by Keen101 on 2008-10-13
most likely your settings are not set to boot from CD in your BIOS.

Check your BIOS settings.




as for the part about 64bit vs 32bit ... it doesn't really matter.  It's all up to your preference. In the future 64bit programs should work better than 32bit, but at this point in time they are about the same. 

(in fact you might still need to run 32bit programs like flash on a 64bit system until the programmers make a 64bit version)

---

### Post by Amstell on 2008-10-13
> **Keen101 said:**
> most likely your settings are not set to boot from CD in your BIOS.

Check your BIOS settings.

Load up your bios at boot and look for a section called boot.  You'll need to make sure that cdrom is loaded before your hard drive.  This will allow you to boot from your cd.

Save changes and restart.  Your cd should boot right into ubuntu

Cheers

Amstell

---

### Post by HelterSkelter1989 on 2008-10-13
i had tried that, it still refuses to boot from disk. could someone tell me step by step what u are supposed to do to burn the iso to a cd, maybe i am just an idiot and did that wrong. also one thing i though was funny was it said there wasn't enough room on a cd to burn the 64 bit iso, but i manged for the other. what am i doing wrong?

---

### Post by Keen101 on 2008-10-13
are you sure you did not just burn the file onto the CD. IE when you browse the CD in windows what is displayed. does it display a cd with the .iso file on the disk, or does the CD have a name, and several folders and files on the disk?

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by HelterSkelter1989 on 2008-10-13
okay that worked :} . i dunno why my program wouldn't burn it correctly. anyways im about to try to set up the dual boot thing, so wish me luck!

---

### Post by HelterSkelter1989 on 2008-10-13
one last thing. in the guide it says to shrink the volume so that ubuntu will install on the largest continuous partition (may have said that wrong). my problem with that is it leaves only 14 gb left on my hard drive as free space. once i install ubuntu, can i then boot up in vista then extend the volume to take up the space unused by the installation or will it be tied up forever? also how could i uninstall ubuntu if i ever need to?

here is the link to the guide: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2)

---

### Post by bodhi.zazen on 2008-10-13
> **HelterSkelter1989 said:**
> my problem with that is it leaves only 14 gb left on my hard drive as free space. once i install ubuntu, can i then boot up in vista then extend the volume to take up the space unused by the installation or will it be tied up forever?

Well in theory you could do that, but it would be difficult.

I think you are tight on hard drive space and I suggest you get a second hard drive (OS hate it when you run out of space).

I also think you could (should) install Ubuntu into 10 Gb of total space.

---

### Post by HelterSkelter1989 on 2008-10-13
if i freed up only 10 gb of space, then selected install into largest continuous space would it install into the 10 gb or somewhere else that was maybe larger?

---

### Post by HelterSkelter1989 on 2008-10-13
like say if i made a 10 gb space by shrinking the volume, that would leave about 60 gb on my hard drive. would it then install on my hard drive or the 10 gb space.

---

### Post by bodhi.zazen on 2008-10-13
You need to point the installer at the 10 Gb free space (or make your partitions before hand).

I suggest you read and understand exactly what you are doing before you proceed as making a mistake may be costly.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

    [uhelp]community/Installation[/uhelp]

[Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by HelterSkelter1989 on 2008-10-13
i've made a 10gb partition, i can tell ubuntu to install there instead of somewhere else? like instead of it just installing to the largest available space i can tell it to install to the 10 gb partition i made?

---

### Post by bodhi.zazen on 2008-10-13
> **HelterSkelter1989 said:**
> i've made a 10gb partition, i can tell ubuntu to install there instead of somewhere else? like instead of it just installing to the largest available space i can tell it to install to the 10 gb partition i made?

Yes you can. You may also wish to make a swap partition as well.

---

