---
title: "Problem Installing Ubuntu with windows 8 via USB"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by nishant91 on 2013-03-17
hi everyone i need a bit of advice

i have installed windows 8 on my device today now i am trying to install ubuntu along with it with bootable USB i created it from instruction given on ubuntu support and its booting perfectly.

[B]The Problem is :
when i install ubuntu with USB everything is fine till the step where i select it to be installed along with windows 8 after that the computer restarts to do installation but then it boots from USB again and the whole process starts once again i am not able to go past that i know it can work properly if i use a DVD but my dvd drive is not working and i need to know if its possible to do with USB ?

Thanks
Nishant[/B]

---

### Post by oldfred on 2013-03-17
If there is some issue with partitioning on drive, the installer may fail.

Can you boot USB installer in live mode? If so from terminal post this.

sudo fdisk -lu

---

### Post by nishant91 on 2013-03-21
it worked with windows 7 perfectly ... i read somewhere that there are some problems with windows 8 & both OS can't be installed on same partition .... is that true ? if so then i may have to make separate partition for ubuntu

---

### Post by oldfred on 2013-03-21
You cannot install Ubuntu on a Windows partition except with wubi. And now with wubi you have to install it from inside Windows just like any other Windows program.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by nishant91 on 2013-03-23
ok so i will have to make a different partition for ubuntu .... it worked fine with windows 7 so i thought might as well work with windows 8. 
Thanks for the help just one more thing even though i don't have ubuntu installed right now but when i boot up i still get the option to choose between ubuntu & windows 8 i think the previous installation with windows 7 isn't removed properly is there a way to get rid of it ?

---

### Post by squakie on 2013-03-23
Carefully read all of oldfred's links regarding efi/uefi, windows 8 and ubuntu before trying this.

---

### Post by oldfred on 2013-03-23
If you have UEFI, it remembers previous entries and you have to go into the UEFI menu and delete boot entries from there.
Also if you have an ubuntu folder in the efi partition it will probably add entries. So you may have to delete that folder also.

---

### Post by nishant91 on 2013-03-28
Thanks for the links i'll read them all carefully just one little question 
As i found out through some reading that ubuntu can't be installed on same partition as windows 8 so will it be wise to create 2 partitions and install them seperately ? what do you say ? i really liked ubuntu and i wanna use it but can't leave windows because of few programmes that don't work on ubuntu :( And like you said i have that UEFI option in my BIOS settings

---

### Post by oldfred on 2013-03-28
You mentioned Windows 7, so is system originally Windows 7? It is the new Windows 8 pre-installed systems that use UEFI with secure boot.
Many Windows 7 systems have UEFI but it is in CSM or BIOS legacy mode, so not really different than all the old systems with BIOS. 
Windows only boots from gpt partitioned drives with UEFI and UEFI requries gpt partitioning. 

So if drive is MBR(msdos), you are not really using UEFI even if you have it. But either way both Windows and UBuntu have to be installed in the same UEFI or BIOS mode to dual boot.

Lets see what partitions you have. If it says msdos, you will be BIOS. If gpt with an efi boot partition then you are using UEFI. How you best install depends on which you have.

       sudo parted /dev/sda unit s print

---

### Post by nishant91 on 2013-03-29
the system didn't come with any OS installed i bought the parts & assembled it myself but i was using windows 7 64bit on it and i never noticed UEFI boot at that time but now i have it but it is disabled by default and the description says i need to enable it if i want to boot drive larger than 2TB & this command isn't working "sudo parted /dev/sda unit s print" as i am using windows 8 and looks like it workd on ubuntu.
So now the question is can i install both OS in my C drive or should i create seprate drive like shown in a few videos on youtube ? like this one "http://www.youtube.com/watch?v=wNCSbTyUzoM"

Thanks

---

### Post by squakie on 2013-03-29
I was going to put more info here, but I think it's important to go a step at a time and oldfred is the leader here.  Indeed the command is a Linux command, not a Windows command.  What I would recommend is booting the LiveDVD and select "Try Ubuntu" to be sure that boots and you get to the desktop.  If so, then from there you can open a terminal window (ctrl/alt/F1) and put in the command oldfred gave you.  If you have internet access while on the LiveDVD, then copy and paste the output back here.  If you don't have internet access then I would just copy the output to a removable media (like a USB flash drive) then reboot Windows and copy the output back here.  Oldfredd can use that information to help you further.

---

### Post by oldfred on 2013-03-29
+1 on squakie's suggestions.

If drive is over 2TB it needs to use gpt partitioning and Windows only boots from gpt partitioning with UEFI. Ubuntu can boot from MBR(msdos) or gpt(GUID) partitioning with either BIOS mode or UEFI mode.
       MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
Windows does not follow UEFI spec on size of protective MBR
[http://thestarman.pcministry.com/asm/mbr/GPT.htm](http://thestarman.pcministry.com/asm/mbr/GPT.htm)

---

### Post by nishant91 on 2013-03-29
Thanks guys i made different partitions and installed them both and they both work fine now . :)

so i guess the solution is to create 2 different partition when using windows 8 for both OS

---

