---
title: "New to linux! (haven't installed it yet)"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by soona86 on 2008-10-02
hi,
i downloaded the cd from the site..
and after that i burnt it on a CD using the windows wizard..
and i read in the help section (after reading two pages) that i should have burnt it using a certain burning program!!!
so,
why didn't u just write all that from the beginning!
do i have to read a whole page that says (burn it onto a CD)
then i read another page about (if u find problems burning a CD)
that's a second page and THEN i find out that i should burn it with another program!
why didn't u say that from the beginning!!!!

all i wanna say is that i'm a very new user (actually i haven't used linux yet!) and u have to make it easier that this..

sorry if i sound a bit annoyed but actually i'm not...i'm just sooo confused with the issue..
i've tried a distro called (pendrivelinux) or something like that..a friend told me to download..
i opened it from windows and i can't do anything with it..

i hope someone helps me with all that..i'm so excited about using a new OS and that Open Source idea..
and i also know it's not easy for me..it needs someone who knows about errrr...codes...or something like that...
it sounds like programming codes or commands..i'm an old user of MS-DOS and i know a bit about typing such lines like CD (x) to open folders etc...
and i wish someone just tells me the whole story without reading so many pages!

so BRIEFLY (if u don't like to read much like me) my problem is i don't know how to USE that (pendrivelinux) and don't know how to install (ubuntu)

do u know of any vids on the net that explain how to use linux?
like (very) simple use...
how to open programs or how to install them or how to EXPLORE MY OWN PC! or things like that..

i really felt so dumb when i couldn't open a single drive in the (computer) icon or whatever it is... 

i hope u understand what i mean..

this forum is to help new users...right?

---

### Post by oldos2er on 2008-10-02
You have to boot from the pendrive to run Linux from it.

 Here's a very nice web page geared toward beginners: [http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

---

### Post by Flynn555 on 2008-10-02
hmmm pen drive linux is supposed to be ran from a usb stick. not installed on your hard drive;

if you're a beginner i would recommend just installing ubuntu

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by LowSky on 2008-10-02
OK first things first.

1. the downloaded file need to be to a CD as an ISO. Programs like Nero and a few free one can handle this.

2. Pendrive linux has to put on to a Flash drive(aka Pen drive)

3. Both the Ubuntu LiveCD and Pendrive aren't normal run from inside Windows, unless using Wubi or VMware.

4. To install ubuntu put disc in computer at startup, make sure computer can boot from DVD drive (might need to set BIOS)

5. I wouldn't suggest installing Ubuntu on a machine you really care about until you know that you will like it.

---

### Post by soona86 on 2008-10-02
> **Flynn555 said:**
> hmmm pen drive linux is supposed to be ran from a usb stick. not installed on your hard drive;

if you're a beginner i would recommend just installing ubuntu

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

thanks flynn555,
i read that page..

and about that distro (pendrivelinux) i already ran it from windows..i just downloaded a file called (QemuPDL1.1.0.exe) and ran it(it was like a setup)..i don't know much about these maybe i'm wrong..
but after the setup i opened a window that has a (desktop) with a mouse and icons u know..i think that's a Linux OS, right?

---

### Post by soona86 on 2008-10-02
> **oldos2er said:**
> You have to boot from the pendrive to run Linux from it.

 Here's a very nice web page geared toward beginners: [http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)


thnx for the page..

---

### Post by soona86 on 2008-10-02
thanks guys for ur help :)
but a new question just popped-up in my mind....

do i have to partition my hard disk to install it?! :o

i mean..(LowSky)'s reply made me wonder if it will be partitioned or not..

and for this part of his reply :
> 3. Both the Ubuntu LiveCD and Pendrive aren't normal run from inside Windows, unless using Wubi or VMware.

4. To install ubuntu put disc in computer at startup, make sure computer can boot from DVD drive (might need to set BIOS)

5. I wouldn't suggest installing Ubuntu on a machine you really care about until you know that you will like it.

3-thanks for that notice..and yeah, i think i don't have wubi or VMware..i just double-clicked the thing u know! :D

4-i understand about that booting issue..i mean when my windows crash..i put the windows CD and it boots...because i made the PC boot from the cd u know..
isn't setting the BIOS is that pressing on (DEL) button when the PC starts..if it is that then i know it yeah..i already made it set to read the floppy (i still have a floppy disk driver!) then the CD then the hard disk..
if this isn't (setting) the BIOS then plz tell me what's that..

5- this point makes me wonder? why? will it wipe everything out!? or what? i mean like formatting the hard drive and re-partitioning it?!

and this part too :
> 1. the downloaded file need to be to a CD as an ISO. Programs like Nero and a few free one can handle this.

1- isn't burning it using the regular windows burning wizard enough? i mean i never needed other software since windows has it's own burning software, u know..

do u think booting didn't work because i used the regular burning windows wizard???

and finally, thanks man for taking me step by step! :)
i hope u answer me soon... :)

---

### Post by H.Callahan on 2008-10-02
The Ubuntu Live CD is kind of a combination disk.  When it first boots up, it gives you the option to run Ubuntu totally off the the CD.  No changes are made to your hard drive or setup on the machine.  The purpose of this is to allow you try out Ubuntu and many Linux applications without any risk to your current setup.  It also allows you to check out to see if all your hardware works properly with Ubuntu.  When you are done playing, you can reboot your computer (after removing the CD) and everything will be the same as it was before you ran the CD.  No changes you made will be saved.

After you have played with it a while, there is a desktop icon on the Ubuntu Live desktop that, when clicked, will install an Ubuntu system on your hard disk.  This WILL make changes to your system and you will need a little (not too much) understanding of how you want to set your system up before you do the install.  Ask question in this forum if you need help at this point.  Note that if you sufficient drive space that it is possible to dual boot with another operating system (ie. Windows) so that you can choose whether you want to use Ubuntu or the other OS when you boot your computer.

The BIOS options are, indeed, those options that you get when you hit 'Del' when the PC starts.  It sounds like you already have that set up correctly for the Live CD to boot.

LowSky's point 5 is just recommending that you do not use the installer to actually install the system to your hard drive until you have played with the Live CD Ubuntu enough to know that you like it sufficiently that you actually want to make changes to your computer.

Files that end in .ISO are an image of a CD.  This is kind of like an archive file (.zip or .rar, for example) in that the files that are to end up on the CD are enclosed within the .ISO file.  Burning a CD with the Windows burning wizard will only burn the archive (.ISO) file to the CD.  This is similar to copying a .zip file from one subdirectory to another.  The archive moves, but the files are not extracted.  You need a CD burning program that understands what an .ISO file is and is capable of extracting the embedded files out of the .ISO and burning them on the CD.  This is similar to using a program like WinZip to extract the files to a new subdirectory.

Since the .ISO file also contains other, not usually user accesable, information needed to create a totally bootable CD, it is not usually possible just to extract the files to your computer and then use the Windows cd wizard to burn the disk.  If you have Nero or a similar commercial CD burning program, it probably (Nero definitely does) can handle an .ISO file.  Otherwise, there are several free CD burning applications that will correctly handle .ISO files.  You need to find one and use that to burn your CD from the .ISO file.

---

### Post by Paqman on 2008-10-02
If you're finding the CD install method a bit confusing, you should try [Wubi](http://wubi-installer.org/). 

Just boot up into Windows, download and run the wubi.exe. It'll grab the correct Ubuntu disk image and automatically install it into a special virtual hard drive on your Windows partition (give it 10-20GB). No need to mess about burning CDs or creating partitions.

To uninstall, just boot back into Windows and go to Add/Remove Applications.

The main advantage of creating a LiveCD is that you get to test out your hardware to make sure it's compatible before installing. So it might be worth doing that before installing through Wubi, but it's up to you.

---

### Post by LowSky on 2008-10-02
> **H.Callahan said:**
> 
LowSky's point 5 is just recommending that you do not use the installer to actually install the system to your hard drive until you have played with the Live CD Ubuntu enough to know that you like it sufficiently that you actually want to make changes to your computer.


Exactly what I meant. Many people install Ubuntu thinking it will be sunshine and rainbows, but thats isn't always the case. The issue I want to bring up that many people erase their Windows install because they think they will never use 
Windows again, for a few of us that is possible but for people who don't have a printer or wifi support or can't play games under ubuntu, having Windows as a back-up is the best option.
I say play with the LiveCD until yuo are positive on the choice you want to make. At the same time try other versions of Linux like Kubuntu, or PCLOS,, or Fedora, or OpenSuse. Maybe you'll like one better. All are availible for download for free. give them a try.

---

### Post by soona86 on 2008-10-02
> **H.Callahan said:**
> The Ubuntu Live CD is kind of a combination disk.  When it first boots up, it gives you the option to run Ubuntu totally off the the CD.  No changes are made to your hard drive or setup on the machine.  The purpose of this is to allow you try out Ubuntu and many Linux applications without any risk to your current setup.  It also allows you to check out to see if all your hardware works properly with Ubuntu.  When you are done playing, you can reboot your computer (after removing the CD) and everything will be the same as it was before you ran the CD.  No changes you made will be saved.

After you have played with it a while, there is a desktop icon on the Ubuntu Live desktop that, when clicked, will install an Ubuntu system on your hard disk.  This WILL make changes to your system and you will need a little (not too much) understanding of how you want to set your system up before you do the install.  Ask question in this forum if you need help at this point.  Note that if you sufficient drive space that it is possible to dual boot with another operating system (ie. Windows) so that you can choose whether you want to use Ubuntu or the other OS when you boot your computer.

The BIOS options are, indeed, those options that you get when you hit 'Del' when the PC starts.  It sounds like you already have that set up correctly for the Live CD to boot.

LowSky's point 5 is just recommending that you do not use the installer to actually install the system to your hard drive until you have played with the Live CD Ubuntu enough to know that you like it sufficiently that you actually want to make changes to your computer.

Files that end in .ISO are an image of a CD.  This is kind of like an archive file (.zip or .rar, for example) in that the files that are to end up on the CD are enclosed within the .ISO file.  Burning a CD with the Windows burning wizard will only burn the archive (.ISO) file to the CD.  This is similar to copying a .zip file from one subdirectory to another.  The archive moves, but the files are not extracted.  You need a CD burning program that understands what an .ISO file is and is capable of extracting the embedded files out of the .ISO and burning them on the CD.  This is similar to using a program like WinZip to extract the files to a new subdirectory.

Since the .ISO file also contains other, not usually user accesable, information needed to create a totally bootable CD, it is not usually possible just to extract the files to your computer and then use the Windows cd wizard to burn the disk.  If you have Nero or a similar commercial CD burning program, it probably (Nero definitely does) can handle an .ISO file.  Otherwise, there are several free CD burning applications that will correctly handle .ISO files.  You need to find one and use that to burn your CD from the .ISO file.

thanks man, i'm really very grateful for ur explanation :)

---

### Post by soona86 on 2008-10-02
> **Paqman said:**
> If you're finding the CD install method a bit confusing, you should try [Wubi](http://wubi-installer.org/). 

Just boot up into Windows, download and run the wubi.exe. It'll grab the correct Ubuntu disk image and automatically install it into a special virtual hard drive on your Windows partition (give it 10-20GB). No need to mess about burning CDs or creating partitions.

To uninstall, just boot back into Windows and go to Add/Remove Applications.

The main advantage of creating a LiveCD is that you get to test out your hardware to make sure it's compatible before installing. So it might be worth doing that before installing through Wubi, but it's up to you.

thanks for the Wubi :) i downloaded it :)

---

### Post by H.Callahan on 2008-10-02
> **soona86 said:**
> thanks man, i'm really very grateful for ur explanation :)

No problem.  I hope it helped clear a couple of things up.

---

### Post by Paqman on 2008-10-02
> **soona86 said:**
> thanks for the Wubi :) i downloaded it :)

No problem. It does have a couple of limitations that the traditional way of installing doesn't: it won't hibernate, and it really doesn't like interruptions to the power supply. Otherwise it's pretty awesome.

---

