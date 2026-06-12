---
title: "Dual Boot - Booting Ubuntu brings me to Grub Command Line - New User"
date: 2016-10-24
forum: New to Ubuntu
---

### Post by mrsrobot on 2016-10-24
Greetings Ubuntu community !
I have a ASUS X55 (Intel(R) Core i5-5200 CPU @ 2.20GHz with 8GB RAM) I currently have Windows 10 , Version 1607.
Last week I had Ubuntu running on my computer however it was slightly buggy so I decided to remove it and try to re install it. I removed it, however I am having extreme difficulty trying to put it back on. I've watched countless YouTube installation videos , tried RUFUS , UUI and I still cant get it to work. I've spent 2-3 hours trying to solve this. I am new to Ubuntu so im hoping the community can help me with this one so I can pay it forward further down the line.
I also checked the hashes for my Ubuntu 16.04.1 iso and those are fine
When I write the iso to a USB and then attempt to boot from USB using (settings >Update and security > recovery > advanced startup) I am brought to a grub prompt grub>.
What the heck can I do to fix this ? 
I have also tried booting into BIOS and changing the boot order so ubuntu is #1 but this brings the same problem I outlined above.
Thanks - KG

---

### Post by oldfred on 2016-10-24
Is grub prompt from flash drive or from internal drive which would give errors as no install anymore?

You should be directly booting in UEFI mode from UEFI, not from Windows.
But in Windows make sure fast start up is off.

       Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[http://ubuntuforums.org/showthread.php?t=2327103&page=3](http://ubuntuforums.org/showthread.php?t=2327103&page=3)
[http://ubuntuforums.org/showthread.php?t=2327570](http://ubuntuforums.org/showthread.php?t=2327570)

---

### Post by mrsrobot on 2016-10-24
This is only happening when I boot from a USB drive.

I have attempted to disable fast boot however it still brings me to the

[http://imgur.com/a/IXyVR](http://imgur.com/a/IXyVR)

---

### Post by oldfred on 2016-10-25
If that is really from live installer, then live installer is not correctly configured.

Are you booting from UEFI boot menu? Often f10 or f12, but varies by brand.

Live installer uses grub for UEFI boot & syslinux for BIOS boot.
But installer will have a correctly grub install inside it and should not give an error unless flash drive is not correct or is corrupted.

Do you have secure boot on or off in UEFI? Try with Secure Boot off. May say "Windows" or "Other".

       Ubuntu UEFI install ISO
Also links on how to create a bootable DVD or USB flash drive, from Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Easy way to create UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by mrsrobot on 2016-10-25
so I have tried booting this usb with fast bootup turned off and secure boot off. I booted from the bios menu ( i hold f2 and restart ) . I am still getting the grub> 
These damn grubs

---

### Post by Geoffrey_Arndt on 2016-10-25
Might try "Etcher" to create the Live USB Flash-Stick.    Is a better tool than several other apps I've tried.   

Also, have you verified via your owner manual (pdf) what the one-time boot menu key is.  It can vary wildly by brand.   On my System76 Galago (with Ubuntu pre-installed), the "F7" key is pressed **_during the restar_**t (so, not a Function Key, and "then a restart"??? . . . that just ain't right at all).   The PC should not restart after pressing the one-time boot key - - that negates (erases) anything prior.

ps:  instead of F2, did you try the "Del" key?   Or the "Esc" key?   On many Asus notebooks, those are the one-time boot triggers whereas the F2 key is just used to change the BIOS . . . . 

Further, Pls see:

[URL="http://supportforasus.iyogi.com/boot-menu.html"]http://www.asus.com/us/support/FAQ/1008277

[/URL][http://supportforasus.iyogi.com/boot-menu.html](http://supportforasus.iyogi.com/boot-menu.html)

---

### Post by mrsrobot on 2016-10-26
I just tried to press the esc key and restart and that brings me to the one time boot. Inside the one time boot I choose to boot from ubuntu and it still brings me to the grub>

What else can I try ? I also tried to reset windows , save my files and put a new copy of windows however this did not help the problem.

---

### Post by oldfred on 2016-10-26
The escape key is used by UEFI boot in Linux to get to grub menu when not normally shown.
So I assume the escape key is not normally used by most or any brands of systems.

Or check your manual on correct key for UEFI one time boot, not grub menu.

---

### Post by Geoffrey_Arndt on 2016-10-26
If you can boot into Ubuntu via the Live media (meaning either DVD disk or USB_Flash-stick) . . . . then you can run the program on the live media called "gparted".   That in turn allows you to scan your internal & external drives simultaneously to display what partitions, OS's are actually on your system.   That info would clarify some currently "muddy" issues.    In addition, there is a "Boot_Repair" diagnostic CD that allows you to get a full boot report, which often provides more info on if your basic install was correct (or not).   Running that program provides a URL with a link to the report that can be posted back to this thread.

One other question . . . in your first post, you wrote you removed Ubuntu . . . how exactly did you do that?   

Here is the url for that disk . . need to burn that iso to disk (or usb-stick) and try to boot from that:   [https://sourceforge.net/p/boot-repair-cd](https://sourceforge.net/p/boot-repair-cd)

---

### Post by mrsrobot on 2016-10-26
@[[COLOR=#000000]Geoffrey_Arndt[/COLOR]]("https://ubuntuforums.org/member.php?u=1973436")[COLOR=#000000]  [/COLOR]I am not able to boot into Ubuntu from the live media... that is the problem. When I boot from the live media it brings me directly to the grub command line screen.Can you explain in more depth how you want me to run the program called g parted ? 

I will try the Boot_Repair and get back to you with the report. 

I cant remember what I did exactly but it involved deleting the partion inside disk managament and then expanding the partion back into my c: drive 

Thanks so much...........If i could afford another laptop I would buy the pre insatlled ubuntu one.....
Windows has been giving me a ton of pain recently. Slowly pushing me towards using Ubuntu as a main OS.

---

### Post by mrsrobot on 2016-10-26
Hi Geoffrey, 

I just downloaded rufus and boot-repair iso and burnt the iso to the ubs-stick. 
I then booted into BIOS using f2
I then changed the boot priority so the first priority is the usb - stick
Then I saved and exit
I then entered a GNU Grub screen with the option to boot from the usb 
I Pushed enter 
Boot repair loading screen comes up 
waited 10 min and it just stayed in the loading screen

I then held the power button down and went back into BIOS
changed priorities back to normal 
now Im here 

*This is off topic but I have a question*

Under Boot Option Priorities there are three options
Boot Option #1 Windows Boot Manager
Boot Option #2 Ubuntu PO: ST100
Boot Option #3 UEFI JetFlash Trans ( this is the usb - stick ) 

Why is ubuntu an option ? I havent installed it yet

---

### Post by mrsrobot on 2016-10-26
I just tried boot-repair and it gets stuck on the loading screen !!!!! What can I try next ?

---

### Post by oldfred on 2016-10-26
Often better to boot Ubuntu and add Boot-Repair to it.

But if issues it may be you have to have a boot parameter.

UEFI does not forget entries, unless you unplug drive then it forgets everything.
You can manually delete old UEFI entries with efibootmgr in Ubuntu when you get it working.

---

### Post by mrsrobot on 2016-10-26
I CANNOT boot into ubuntu , before I get to Ubuntu I get a grub command line. It will not let me boot into Ubuntu.

---

### Post by mrsrobot on 2016-10-26
I have unplugged the usb-stick with Ubuntu on it and Ubuntu is still a option in the boot priorities

---

### Post by Geoffrey_Arndt on 2016-10-26
Can you still boot into Windows?

---

### Post by Geoffrey_Arndt on 2016-10-26
Here is another thread from AskUbuntu about booting the Asus x55.    Read it carefully.

[http://superuser.com/questions/747760/how-to-boot-from-cd-rom-on-asus-x551m](http://superuser.com/questions/747760/how-to-boot-from-cd-rom-on-asus-x551m)

I think there are two likely issues:   You still have a remnant of the old Ubuntu install files on you hdd including the grub bootloader.    (when you highlight the Ubuntu option (choice#2) and enter, what happens?).   The other problem area is you still don't seem to be pulling up a valid "one time boot menu"  (it normally appears as a popup - versus displaying a full screen) . . . . AND/OR you don't have a valid burn to a bootable image of the ISO.   When you boot from an external live media source, whether it is a bootable DVD or USB-Stick, then, that is the controlling device (in other words, you should not see the grub menu you list in post #11.   When you see that boot menu, it's not coming from the Live media, it's coming from the HDD.  (hope you understand what I'm writing here).

If you can still boot to Windows OS - - then, try recreating the Live media using another tool (program) such as "Etcher" . . . google it, and download it.   Etcher runs on Windows, Mac and Linux   Create a new Live Media and try that out.   Note, if the Asus was my laptop, I would literally try every F key during a restart (especially the F9 and F8 keys).  You have to be able to boot from the Live media (or your only choice is to take the PC to a PC repair shop).

---

### Post by mrsrobot on 2016-10-27
Hurrah Hooray Ubuntu is running. I used etcher to burn the ubuntu iso and then changed my boot order so UEFI : Jetflash trans was first priority . I can now successfully boot into Ubuntu.

My first concerns are:
How do I install it to a partition now ? What is the recommenced size for the partition ? Should I just keep it on the USB stick and run it off of there ?  


secondly my concerns are:

When I bring my BIOS and then boot option ( priorities ) there are four options now:


Boot Option # 1 windows boot manager 
Boot Option # 2 Ubuntu 
Boot Option # 3 UEFI : JetFlash Trans
Boot Option # 4 PO: ST1000LM024

How do I properly delete the unwanted boot options ? I wish to rid of Ubuntu and PO:ST10000LM024

Thanks

FYI when that Ubuntu loading screen popped up I was more than excited !!!!!!!!!!!!

Happy  HALLOWEEN

---

### Post by oldfred on 2016-10-27
I think the PO:ST1000.. is a default hard drive boot entry, probably BIOS created by UEFI. Best to leave it.

       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). With Ubuntu you need sudo, others must be at root.
efibootmgr -b XXXX -B 
# for more details on efibootmgr (not sure if in live installer or only after you have installed?)
man efibootmgr

Be sure to install Ubuntu in same boot mode as Windows, probably UEFI.
      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Only use Windows to shrink NTFS partitions and reboot immediately so it can run chkdsk.
Make sure fast start up in Windows is off.
Best to have fast boot in UEFI off and some work better with UEFI Secure Boot off, but still be sure to boot in UEFI mode.

I use 25G for / (root), but have a large data partition. Newer users often find it easier just to have the separate /home as that can be configured during install and auto sets mount, ownership & permissions. And those using Windows often find a separate shared NTFS data partition useful, but fast start up must be off as Windows also keeps all NTFS partitions mounted/hibernated with its fast start up setting.

More details in link below in my signature.

---

### Post by Geoffrey_Arndt on 2016-10-27
Good news . . . now you have some options.   Let me "splain" a bit:

>   Running off the Live media is useful as a learning tool, and, as a rescue/info tool.   Would not recommend running off Live media as your standard method.   You can't update the system or make other necessary changes.

>   DO NOT delete, or worry about deleting anything on your Grub menu.   That is the least of your concerns.   Unless you have OCD personality type, leave it be.

>   Now, you want to see the "Forest versus only the Trees" . . . . in other words, how exactly is your hard drive set up now?   Exactly what is on it and where?

>   So, to do the above, you can now run the "gparted" program from the Live usb media.   BUT - - be careful.    Do not update or change anything!   Gparted will show you the disk layout, partitions, etc.   A really good thing for you to do is to head over to good ol Youtube and do a search on "gparted" . . . suggest you watch at least one-half dozen (that be 6) videos of how it looks and works.   If you're the type that also learns from reading - - go to the gparted website and read about it, including FAQ etc.    This may take you a week or even two.   Meanwhile, you can run the Live media.

>   The key will be to "over-write" the existing Ubuntu install (you never did explain how you uninstalled Ubuntu - - which is a misnomer as Ubuntu can't really be un-installed in the traditional sense like a program).   That's why remnants of it are still on the PC (e.g., the Grub bootloader).    But it can be "over-written" by a new install (including re-install of Grub) - - provided you have enough room on the hdd.    One thing to remember, you should use Linux programs to manipulate Linux partitions, and conversely, you should use Windows programs to manipulate (expand, shrink, etc.) Windows partitions.

Anyway, take a look at gparted - - it would be very helpful to get a screen shot of your disk layout.

---

