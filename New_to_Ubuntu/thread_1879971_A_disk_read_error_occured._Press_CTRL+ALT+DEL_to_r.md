---
title: "A disk read error occured. Press CTRL+ALT+DEL to restart"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by nemov on 2011-11-12
HI Folks, 
I would really really appreciate some advice on my first big mess up with Ubuntu...

I just picked up a nice, used HP desktop for my wife, from ebay this morning. It came with Windows 7 installed, but no startup discs. So as soon as I can, I go to install Ubuntu 11.10, but my wife wants Windows 7 to stay on there too. Well, when I downloaded the latest version of Ubuntu, and created a USB start up disc, I was surprised that I had to partition the HD, but attempted to split it 50/50 between Windows and Ubuntu. (I chose the option to install Ubuntu but to keep WIndows too) It Took ages and finally gave an error asking to restart. Now when I start the computer it gives the followoing error message:

A disk read error occured. Press CTRL+ALT+DEL to restart

If I do as it says, it continually loops with the same error. (when i restart i have the USB stick inserted for Ubuntu boot,). Although it gives the same error message if I take the stick out. 

Help!! Have I lost Windows 7? Any advice on what to do next and how to do it~?

Many thanks, 

Nate (Berkshire, England)

---

### Post by LinuxFan999 on 2011-11-12
How old is the computer you picked up?

---

### Post by lolpenguin on 2011-11-12
Enter the boot menu (usually F12, but may be different on other BIOSes), and select the partition for Windows 7. If this does not work, you've probably broken you hard disk.
Boot into the USB from the boot menu, and try mounting the partitions. If they mount successfully fsck them.

---

### Post by Mark Phelps on 2011-11-12
You said you shrunk Win7 by 50%.  You didn't do this using the Ubuntu installer, did you?

If so, in the best of cases, you only corrupted the Win7 OS partition, rendering it unbootable.  This can be repaired by doing the following:
1) Using the link below, download the proper Win7 OS ISO file (you will have to purchase it).  Had you not been in such a RUSH to install Ubuntu, you could have created this same disk inside Win7 for only the price of a blank CD.
2) Burn the ISO file to a CD.  This will create a Win7 Repair CD.
3) Boot from the PC and run Startup Repair three times -- not once, three times.

Then, it should boot into Win7.

If it does not do that, you may have (in your rush) wiped out Win7.  To check on that, since you can't boot into Ubuntu, you will have to boot from the Ubuntu desktop CD, open a terminal, and enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out the partitions on your drive.  We will be able to tell from that if the Wi7 OS partition exists, and if it is now empty.

---

### Post by nemov on 2011-11-12
Thanks for answers so far... much appreciated. The computer is an HP Slimline 3000 (Intel Pentium Dual Core 2140 (2 x 1.8GHz)...

Unfortunately it will not even allow me to enter the boot menu - so I can't see the option list to boot from HDD, CD Drive, USB... it just loops back to that error code :o(

I know I was hasty in getting Ubuntu onto the machine but I just followed the instructions from Ubuntu.com..., and the install software gave no option but to partition the drive (though it was my choice to partition 50/50 rather than the default 60%Windows/40%Linux.  

I have Windows XP on CD so could use that to boot, and I have the Ubuntu OS on USB stick, but wanted to know if there was anything I can do to save / revert to Windows 7 before I install XP. If I can..... perhaps you are right lolpenguin and I have shot my HDD somehow.

---

### Post by Miljet on 2011-11-12
You say you have Ubuntu on a USB stick, but can you boot from it? I don't mean install, just boot without changing your computer. If you can boot it, try Mark Phelps suggestion to open a terminal and type sudo fdisk -l. That will allow us to see how much damage has been done.

---

### Post by Miljet on 2011-11-12
By the way, the error message you are getting seems to indicate that the computer is trying to boot into Windows but is unable to complete the boot sequence. If that is true, there is a good chance that your Win 7 install is still intact except for the boot files.

---

### Post by rng on 2011-11-12
Boot using ubuntu livecd. Then download boot_info_script from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and run it as root (sudo boot_info_script.sh). The output will be stored in RESULTS.txt in that folder which you can post here. It will clarify all the partitions as well as booting info.

---

### Post by nemov on 2011-11-13
Hi Guys, Well I cannot even boot from the USB stick (and I did not make a Boot CD)... is there a difference between booting from USB vs CD? In any case when I turn the computer on, I get the blue HP screen with Esc for Boot menu, F10 for Setup, F11 for System Recovery. But if i select any option, I just get the error message. I do (obviously) have another laptop - but no cd burner apart from the one on the HP. 

Thanks again for all your inputs - if I can just boot up and follow instructions above, I think we'll get somewhere! Cheers, Nate

---

### Post by rng on 2011-11-13
Try and see if windows xp cd boots. Do not install it but if it boots that means a linux livecd will also boot.  In the Windows Recovery Console you can see which hard disk partitions are there. I am not sure if fixing mbr with windows xp cd may help. 

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

[http://techzonez.com/forums/showthread.php?t=3975](http://techzonez.com/forums/showthread.php?t=3975)

[http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/)

---

### Post by nemov on 2011-11-13
Well the computer did give me the option to Boot from CD after inserting the XP Boot CD. I tried to boot from the cd, and Setup then loaded all the files and drivers but then I got a Stop Error on a blue screen. I restarted but got the same stop error message telling me: "A problem has been detected and windows has been shutdown to prevent damage. If you see this screen again, check for viruses, remove any newly installed HDD or HDD controllers and run chkdsk /f to check the status of the drive."
 When it gives me the option to boot from CD, should I simply type "run chkdsk /f"? or something else recommended? I can't beluieve (or don't want to believe!) that I could have damaged the HDD by running the partition... 

All ideas welcome - many thanks, Nate (Berkshire, England)

---

### Post by rng on 2011-11-13
I don't think hard disk is physically damaged. Trying chkdsk is unlikely to cause any further harm and may help.

---

### Post by Mark Phelps on 2011-11-13
F1 not working is NOT good news!  Even if the Win7 boot loader is damaged, F11 should work because that's a recovery option that most probably, boots using WinPE, not Win7.

You can't repair Win7 from an XP disk, so quit trying to do that. 

My post #4 provided instructions you will need to follow if you want to be able to boot into Win7 again.  You need to use another PC to do the download and burn the CD image.

---

### Post by nemov on 2011-11-13
Good news is that I was able to boot using Ubuntu from the USB stick. I am not sure which, but either having the XP CD inserted, or holding down the "R" key whilst restarting the machine helped me get a boot menu. So thanks guys - both suggestions came from you. 

Upon opening Ubuntu - I ran the "sudo fdisk -lu" script in Terminal, but everything is running so slowly I cannot copy & paste the text. At one point the screen froze ... apparently opening terminal and desktop search was overloading the system. Is this a symptom of my problem? Anyway, I have attached a jpeg of the terminal script. Hopefully it will show some clues about my HDD? 

So what next? @Mark Phelps - could you post the url you mention? Also is buying this iso file, the same cost as buying Windows 7? If so I would be happy to use Ubuntu and Xp for the moment to save costs. 

Otherwise - what is the advice now? Should I try again to INSTALL Ubuntu? It sounds like if the boot files in Win7 are lost anyway, then i have nothing more to lose by trying to install Ubuntu again? What do you think?

Cheers, Nate

---

### Post by dFlyer on 2011-11-13
Boot the ubuntu live cd/usb and run disk utility to check the status of your hard drive for bad sectors.

---

### Post by rng on 2011-11-13
Suggestion: Reboot with ubuntu usb attached, at the grub menu press 'c' to go grub command line mode. Enter following commands (pressing ENTER after each command): 

 set root=(hd0,1)
 chainloader +1 
 boot

It may start windows7

---

### Post by Mark Phelps on 2011-11-14
> **nemov said:**
> So what next? @Mark Phelps - could you post the url you mention? 

Link below:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

> Also is buying this iso file, the same cost as buying Windows 7? 

NO -- the cost is $9.75 USD -- a LOT less than Windows costs.

> Should I try again to INSTALL Ubuntu? It sounds like if the boot files in Win7 are lost anyway, then i have nothing more to lose by trying to install Ubuntu again? What do you think?

Cheers, Nate

If you've totally lost Win7, then of course, if you don't want it back, you have nothing to lose by reinstalling Ubuntu in its place.

---

