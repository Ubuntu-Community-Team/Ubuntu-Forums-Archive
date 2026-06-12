---
title: "[SOLVED] bios"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by gettinoriginal on 2008-07-07
I am dual booting with WinXP, but since installing hardy, I have totally lost the ability to numlock on the windows partition.  I have tried f1, f8, etc, to find the bios to see what happened.  Is there another way to get to the bios on startup ??  These are my specs if they tell you anything.  It is a used homemade computer, so I have no idea how to find the bios.

Computer
Processor	AMD Athlon(tm)
Memory	1035MB (301MB used)
Operating System	Ubuntu 8.04.1
User Name	gettin (gettin)
Date/Time	Sat 05 Jul 2008 07:12:54 AM EDT
Display
Resolution	1280x1024 pixels
OpenGL Renderer	GeForce FX 5200/AGP/SSE/3DNOW!
X11 Vendor	The X.Org Foundation
Multimedia
Audio Adapter	NFORCE - NVidia nForce2
Audio Adapter	MPU-401 UART - MPU-401 UART
Input Devices
Macintosh mouse button emulation	
AT Translated Set 2 keyboard	
Power Button (FF)	
Power Button (CM)	
Sleep Button (CM)	
PC Speaker	
Printers (CUPS)
DESKJET_950C	(Default)
PDF	
IDE Disks
SCSI Disks
ATA Maxtor 6Y080L0	
SAMSUNG CD-R/RW SW-252F

---

### Post by sydbat on 2008-07-07
Try 'Delete'. Not sure if it is a BIOS issue though.

---

### Post by petdog on 2008-07-07
Give us ur Mobo name and spec! :D We can search for tech!

---

### Post by Prefader on 2008-07-07
Do try "Delete", but also try another keyboard.  Are you absolutely positive that the numlock key is working at all?

---

### Post by jamesrfla on 2008-07-07
Try pressing Esc when the system boots to get into the BOIS. Also try another keyboard.

---

### Post by gettinoriginal on 2008-07-07
numlock works in ubuntu with this keboard, even though I have to manually turn it on each time.  I have tried another keyboard, no luck.  I will try the esc and delete.  My mobo is a Biostar m7ncg ver 1.4 if that tells you anything.

---

### Post by gettinoriginal on 2008-07-07
Ok, I'm totally freaked, delete did let me into bios, and numlock was off, now on.  When booting numlock comes on but still cannot type anything into windows password space despite trying 3 keyboards.  Soooooooo, can someone tell me how to format the entire C: drive so I can just give it all to Ubuntu ??  Or am I just better off leaving things alone.

---

### Post by jamesrfla on 2008-07-07
Did you try Esc?

---

### Post by gettinoriginal on 2008-07-07
yes, esc did not let me in, but delete did.  But as I stated above, I have lost all ability to type in the password on windows, so I guess I am totally Ubuntu now  LOL

---

### Post by jamesrfla on 2008-07-07
Did you try the numbers above the alphabet letters?

---

### Post by bigken on 2008-07-07
> **gettinoriginal said:**
> yes, esc did not let me in, but delete did.  But as I stated above, I have lost all ability to type in the password on windows, so I guess I am totally Ubuntu now  LOL


log into windows in safe mode use the administrator account go to control panel user accounts and remove your password

---

### Post by jamesrfla on 2008-07-07
> **bigken said:**
> log into windows in safe mode use the administrator account go to control panel user accounts and remove your password

Yeah you can try that too. I do that when I lose my passwords in windows.

---

### Post by gettinoriginal on 2008-07-07
ok, let me simplify this.  I did get into bios.  Numlock is now on by default in the bios.  Grub will let me boot windows.  At the log in page, I cannot type anything into the password space, numbers, letters, or otherwise despite changing keyboards 3 times.  Everything works here in Ubuntu with all 3 keyboards.  So, my ability to enter the bios is solved.  But now I am stuck with a dual boot that I cannot use.  I think I will just leave it alone, as my windows partition only has 30G anyway, ubuntu has 46, so no problem.

---

### Post by gettinoriginal on 2008-07-07
But the password is not the problem, I cannot type anything while in windows, so cannot log into anything.  The cursor just sits there, no recognition of keystrokes.

---

### Post by bigken on 2008-07-07
F8 (strait after the bios screen)


or shut the pc down while its booting windows the it automatically give you the options to boot from

---

### Post by gettinoriginal on 2008-07-07
Did the safe mode thing, let me remove the password, but still will not let me type anything.  I have tried different keyboards, uninstalled the keboards in hardware, and rebooted, all to no avail.  Just cannot type in windows, so I give up.  Would rather just format C: and install ubuntu on the whole drive.  Does anyone know how to format a hard drive ??

---

### Post by jamesrfla on 2008-07-07
Can you afford to lose all your files from XP and Ubuntu? Also are you using a PS2 keyboard or a USB keyboard. Try a different port.

---

### Post by bigken on 2008-07-07
just use the gparted or run the live cd to delete c:\ and create a new linux partition

---

### Post by gettinoriginal on 2008-07-07
It is a PS2 keyboard, but it works here and now, so I will just kiss windows goodbye, actually no reason to keep it anyway.

---

### Post by kansasnoob on 2008-07-07
Whoa, slow down! Try something as simple as Windows System Restore! Honestly!

Think about it. If it were BIOS related both Windows and Ubuntu would be hosed. It's likely you have a Windows glitch ............. none of us have had them before, eh?

Just pick a Win Sys restore date before the problem started. It will not (or should not) hose GRUB, it's easy, and you can calm down!

---

### Post by bigken on 2008-07-07
> **kansasnoob said:**
> Whoa, slow down! Try something as simple as Windows System Restore! Honestly!

Think about it. If it were BIOS related both Windows and Ubuntu would be hosed. It's likely you have a Windows glitch ............. none of us have had them before, eh?

Just pick a Win Sys restore date before the problem started. It will not (or should not) hose GRUB, it's easy, and you can calm down!


sounds like he wants to ditch windows so let him

---

### Post by gettinoriginal on 2008-07-07
Yup, ditched windows, no looking back now  :)  Plus, with all of you at my back, how can I lose ??  ):P  Sorry it took so long, but I had company, the whole process without the interruption probably took 20 minutes, and I even have all my files back. :popcorn:

---

### Post by bigken on 2008-07-07
well done :)

---

### Post by kansasnoob on 2008-07-07
> **bigken said:**
> sounds like he wants to ditch windows so let him

My philosophy on that is different. I love Ubuntu, but until everyone catches up let's keep the old technology close to hand ........ like in a dual boot.

I'm not too fond of virtual machines either. But it's all a matter of choice.

---

### Post by bigken on 2008-07-07
> **kansasnoob said:**
> My philosophy on that is different. I love Ubuntu, but until everyone catches up let's keep the old technology close to hand ........ like in a dual boot.

I'm not too fond of virtual machines either. But it's all a matter of choice.

if he is happy with ubuntu and thinks he can do without windows let him crack on I have a duel boot machine and cant remember the last time I booted into windows

---

### Post by gettinoriginal on 2008-07-07
Well, if all else fails, I have the disk, and can spend a dreadful afternoon reinstalling XP.  But I really don't think I will miss it.  Thanks to all of you for your help, after all, even if I failed, I learned, so in the end I won.:KS

---

