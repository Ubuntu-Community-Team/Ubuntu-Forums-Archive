---
title: "Installed 8.10 on xp, Now xp won't start."
date: 2008-07-12
forum: New to Ubuntu
---

### Post by rosemaryr on 2008-07-12
Hi all!

I installed Ubuntu 8.10 on my XP machine last night. Ubuntu works great, but unfortunately, it doesn't recognize my monitor or usb wireless adapter. 

So, I rebooted, and when I saw the menu asking me if I'd like to boot into Ubuntu or XP, I chose XP, and NOTHING happened! I had to manually turn off the machine and try again. Still nothing.

I checked out the forums and decided it would probably be too difficult to remedy these problems (I have no idea what an MSR or a GRUB is!), so I decided I wanted to uninstall Ubuntu. Unfortunately, I couldn't figure out how to do that either.

So, finally, I decided to simply use my Gateway XP recovery disk and do a Full System restore (including "reformatting the hard drive"), but guess what? Even after the restore is "complete", I still get that same menu asking me what operating system I'd like to boot into, and XP still doesn't work.

I'm totally new to Linux, but tired of Bill's tyranny, so I HAD to have a look! Unfortunately I don't have a lot of time for this. 

I'm not afraid of a command prompt because I grew up on DOS and VMS...but I need to know where to find it!

Can anybody help with a minimum of jargon??? Thanks.

Rosemary

---

### Post by scragar on 2008-07-12
put in the XP install disk if you have it, and you should have the option to enter recovery mode, choose that, then run the command:```
fixmbr
```which should restore the windows boot loader letting you get into windows, no idea why you would encounter a problem with grub though, it should have been automaticaly replaced by the master boot record(**mbr**) when you did the system repair.

---

### Post by rosemaryr on 2008-07-12
Thanks for the swift response, scragar...<br><ol style="list-style-type: decimal;"><li>I'm having trouble with GRUB because I don't know what it is! <img src="http://ubuntuforums.org/images/smilies/icon_smile.gif" alt="" title="Smile" smilieid="1" class="inlineimg" border="0"></li><li>I don't think that my Gateway restore disk gives me an option to enter a command...</li></ol><br>
Rosemary

---

### Post by kk0sse54 on 2008-07-12
Make sure your grub is configured right for windows xp. Go into Ubuntu or if Ubuntu doesn't work for your monitor stick in the liveCD then go into the terminal and type ```
sudo gedit /boot/grub/menu.lst
``` enter your password and you will open up the text for grub. Scroll down to Windows XP and make sure it's pointing to the right place. If that doesn't work try the recovery way but also make sure you didn't delete your windows files by accident by deleting your window partition or some other small mistake

---

### Post by rosemaryr on 2008-07-12
My monitor works, but the resolution isn't correct.

I can get to the desktop.

where is grub?

Thanks.

R

---

### Post by kk0sse54 on 2008-07-12
Grub is the bootloader that lets you choose what os to boot when you start your computer. Sometimes after an install it won't be configured correctly causing the OS you are trying to boot to not start. Type in the command and just make sure that it's looking for Windows on the right partition. Quick question can you mount your windows filesystem in Ubuntu and see all your files?

---

### Post by rosemaryr on 2008-07-12
I don't know how to determine whether I deleted my windows files.

Why do I need them on the disk if I want to do a full system restore from the factory disk? Aren't all the xp files on my restore disk? I did a full system restore a few days ago (pre-Ubuntu!) and I had no problems.

I just looked grub up on wiki: 
[I]Grub is a boot loader package from the GNU Project.
[/I]
But I don't know how to access it.
Thanks.

---

### Post by rolnics on 2008-07-12
you don't access it yourself, it's part of the boot up process. Grub is a menu that allows you to choose what operating system you want to load. It then tells your system where to go to load the give os.

---

### Post by kk0sse54 on 2008-07-12
GRUB starts up everyday you turn on your computer, you can try the factory recovery as long as it doesn't mess up your MBR which happens sometimes with a full re installation of windows along side linux in which case you would have to re-install GRUB

---

### Post by rosemaryr on 2008-07-12
Yes, I can see the dirs in the windows partition.

On the Ubuntu side, I see a grub folder under the "boot" folder with 12 files, including one called "default". I double-clicked on that file and it wouldn't open.

Is the file I want in this folder? 

When I find the correct file, what exactly should I look for?

Thanks!

---

### Post by rosemaryr on 2008-07-12
OK, that OS menu is the GRUB! So where(?) do I enter what(?) text to make the Grub find my XP OS?

Thanks ~ R

---

### Post by rosemaryr on 2008-07-12
I'm very confused about the forum...

I thought I'd posted 5 or 6 "replies" but now I can't find them! 

I know what the GRUB is now: its the menu of OS.

I can get to the desktop, and I can find the grub folder in the boot folder. 

What should I edit? where do I enter text? 

Thanks, 
R

---

### Post by kk0sse54 on 2008-07-12
okay I'll explain again sometimes after an installation grub doesn't get properly configured although usually resulting in some kind of error when you try to boot from one of the OS's. In order to check that it was properly configured for windows go into the terminal and type ```
sudo gedit /boot/grub/menu.lst
``` which opens up the text file which displays the grub menu when you start up your computer. Scroll down until you find windows xp and then make sure that it's pointing to the right place which for me is (hd0,1). If this doesn't work then it's not grub that isn't working instead you will have to do a recovery probably because some of your xp system files were deleted during the partitioning process. Just be aware that you might have to re install grub from a liveCD after the recovery process.

---

### Post by rosemaryr on 2008-07-12
> **C!oud said:**
> Make sure your grub is configured right for windows xp. Go into Ubuntu or if Ubuntu doesn't work for your monitor stick in the liveCD then go into the terminal and type ```
sudo gedit /boot/grub/menu.lst
``` enter your password and you will open up the text for grub. Scroll down to Windows XP and make sure it's pointing to the right place. If that doesn't work try the recovery way but also make sure you didn't delete your windows files by accident by deleting your window partition or some other small mistake

OK, I found the menu.1st file in the grub folder. Double clicked to view, and I see that the root for XP Home edition is pointing to hdo,o
Where should it be pointing?

Thanks,

Rosemary

---

### Post by kk0sse54 on 2008-07-12
I can't tell you that because I don't know what partition you installed Windows on but if it's the first on then that's right, sounds like then you are going to have to try the recovery way just make sure you don't wipe your Ubuntu partition and have the liveCD handy in case you have to re install GRUB. Goodluck :)

---

### Post by rosemaryr on 2008-07-12
I've edited the file in gedit, but unfortunately, when I try to save it, it tells me I don't have permission!?

I don't know where to enter my password for this... I just don't see a command line anywhere, so I browsed to the file. I'm logged on with my name and password, so I don't understand why I don't have permissions...

Thanks.

R

byw, what is the diff between respond and and quick response on the forum?

---

### Post by Samhain13 on 2008-07-12
Go to Applications > Accessories > Terminal or Hit Alt + F2, then type-in "gnome-terminal" to get a terminal.

In the terminal, type "gksu gedit /boot/grub/menu.lst"... but it woud be a good idea to first do "sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup" to make a backup file of the Grub Menu before tinkering with it.

:)

---

### Post by AnLGP on 2008-07-12
you have to sudo (super user do) the grub file.  Basically sudo allows you permission to modify important system information.  When you ran this

sudo gedit /boot/grub/menu.lst

it should have asked you for your password.  The command line is under applications - accessories - terminal.

The quick reply just doesn't have as many functions as the normal reply.  It's just stuff like smilies and text formatting and things of that nature, I believe.

I agree with the above poster, please back up that file using the command he used.

---

### Post by kk0sse54 on 2008-07-12
Go to Accessories > terminal and then type ```
sudo gedit /boot/grub/menu.lst
``` this will give you root access while editing the file. The reason you don't have permission is because menu.lst is a system file which can only be accessed by root which for security reasons your regular account is not which is why we use sudo to grant us temporary root access. As for quick reply that just let's you use the reply box on the bottom of the page.

---

### Post by avtolle on 2008-07-12
I'm not too clear on what you have done, but to get to the CLI do (if you are in Ubuntu) Applications>>Accessories>>Terminal. At the CLI, to open a file for editing in gedit, do```
gksudo gedit NAMEOF FILE
```where NAMEOFFILE is the file name. When prompted for your password, type it in, you will receive no visual feedback; then press Enter. The file should then come up, and you may then edit it. Then save the file after editing (I don't use gedit, but since it is a GUI editor, I presume that this is a selection under File), and then proceed.

---

### Post by rosemaryr on 2008-07-12
Thank you AnLGP and Samhain13!

I was finally able to find the terminal and edit the file. I found the setting for XP way down at the bottom of the file.

I changed XP pointer to hdo, 1
and the other Win pointer to hdo, 0 

( I reversed them ) and saved. Restarted. 

Tried to boot into XP and NOTHING.

Unfortunately, my system restore disk is not helping me because it does not reformat the drive as advertised.

Can you think of any other settings I might try in the menu.lst file?

I'll be back in a few hours, anxious to try again.

Thanks for all your help!

Rosemary

---

### Post by rosemaryr on 2008-07-12
The recovery way. 

???

Gateway's system recovery disk has not worked. Is there something I'm missing (last time I was missing the terminal because I didn't know where to find it, stupid me, I was looking in the system area.) Now I'm thinking maybe I'm using the wrong recovery disk? Am I supposed to recover windows with my Ubuntu disk?
My Gateway disk offers me only 2 options and NO TERMINAL that I am aware of. Partial and Full recovery. Full didn't do it. In the old days format would have wiped the disk clean for a new install, but I guess format is something entirely different these days?
OH well, I'll get my computer back one of these days. (sigh)

Rosemary

---

### Post by louieb on 2008-07-12
Don't get the letter o and a zero mixed up. as in  root (hd0,1)   you want zero.  
It can be fixed. 
Post 2 things 1st post file /boot/grub/menu.list.
And post your partition table. 
open Applications>Accessories>terminal  and run
```
**sudo fdisk  -l** 
``` (lowercase L at the end)

Kind of odd the Grub installer did not get it right. I guess you have a single hard drive in the PC.
I've seen the grub installer get confused when a PC has a mix of ide and sata drives. But thats neither here not there.

---

