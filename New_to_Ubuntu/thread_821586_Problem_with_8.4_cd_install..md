---
title: "Problem with 8.4 cd install."
date: 2008-06-07
forum: New to Ubuntu
---

### Post by hman1945 on 2008-06-07
I am using a disk I ordered from Ubuntu and when I insert the cd and select "install inside Windows" the program runs for a while and appears to have loaded correctly. I get a error message saying there is no disk in the drive.
When I reboot and select Ubuntu I am taken to a prompt "BusyBox V1.1.3) initramfs".
I follow the direction in the WubiGuide Ubuntu installer page 19-20 but I'm still getting the BusyBox initramfs prompt.
What am I doing wrong??????????????
Thanks in advance

---

### Post by fedex1993 on 2008-06-07
I woundlt do wubi its sort of bad. [https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

---

### Post by avtolle on 2008-06-07
Are you on Vista? If so, take a look at this: [http://ubuntuforums.org/showthread.php?t=764686](http://ubuntuforums.org/showthread.php?t=764686)

---

### Post by hman1945 on 2008-06-07
I'm using Windowsxp sp2 on an emachine. I know the cd is ok because I can load it at work on a Windowsxp pro computer?

---

### Post by lisati on 2008-06-07
These might be obvious but here goes:

[LIST]
[*]If you are able to boot from the disk, are you able to use the "Check disk for errors" option?
[*]It should be burnt as "disk image", **not** as a file
[/LIST]

---

### Post by hman1945 on 2008-06-07
That is WindowsXP Home SP2.

---

### Post by avtolle on 2008-06-07
I must say this; just because the CD worked on one or more other computers does not mean it is "OK" for the computer on which you are trying to install. For example, I've two desktops (admittedly older) and a laptop. For the laptop, an iso burnt to a CD-RW works just fine; yet, neither desktop will boot from a CD-RW; CD-R must be used for these (which works very well for the laptop, BTW). Now, with that out of the way:

Since you ordered it from Shipit, I'm presuming there is no media problem. Next analytical note: neither the older desktops will boot from a "Live" (or Desktop) CD; the laptop will. I've seen posts from other users whose machines won't boot from a Live CD, but the alternate installer (text based) works well for them, which is another illustration of why "it works on another computer" is  fool's gold when it comes to a CD not working on the computer upon which installation is being tried. Since you installed via Wubi, I'm aware it is a Live (Desktop) CD. Let me get to the Wubi Forum here and see if I can find something that may be helpful, and I'll report back. :-)

---

### Post by avtolle on 2008-06-07
[http://ubuntuforums.org/showthread.php?t=816415](http://ubuntuforums.org/showthread.php?t=816415) Have you tried the suggested solution found at post #2 on this thread?

---

### Post by hman1945 on 2008-06-07
Yes . I've tried that and I can boot from that drive.

---

### Post by avtolle on 2008-06-07
> **hman1945 said:**
> Yes . I've tried that and I can boot from that drive.
To clarify, you have multiple drives, and Ubuntu (through Wubi) is installed on one of them? Be back in a while.

EDIT: While you aren't getting Error 15, as I understand your post, perhaps [https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230](https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230) and the discussion of multiple drives might help you.

---

### Post by hman1945 on 2008-06-07
I selected " run inside windows ..." and the program runs and a screen appears that says the install was OK. But my disk will unload and I get the error screen that says the disk needs to loaded.
This is the same drive I use for system restores ect .....

---

### Post by avtolle on 2008-06-07
I'm not really clear on just what you are saying there, but if you can get a drive to boot (I presume this means without the Busy Box window showing), have you updated your Ubuntu install, such as updating the kernel? The reason for the question is that (while this makes little sense to me in light of what I understand you to say) there is a bug under Wubi where the kernel is updated from .16 where the file system under Windows is FAT32, or FAT32 converted to NFTS, and only "pure" NFTS will work. So, on the drive that boots, as I understand it, is the file system "pure" NFTS; and the file system on the drive that dumps you into Busy Box, FAT32? There is a thread going on the Wubi Forum about this at the moment, sorry, didn't grab the link, but is this helpful in any way?

Dropping back a moment, I've read that "hard shutdowns" (pressing the power button) can also cause problems; one recommended fix is to run checkdsk -r under Windows. Have you given that a run?

---

### Post by hman1945 on 2008-06-07
I'll give checkdsk -r a try ......

---

### Post by hman1945 on 2008-06-08
I uninstalled Ubuntu and reinstalled it again. I loaded the disk, selected " install inside Windows ". The program runs and I get two windows. One window says " Completing the Ubuntu setup Wizard " click finish to reboot now, the other window says " there is no disk in the drive. Please insert a disk into drive D: and select cancel, try again, and continue. The Ubuntu disk also unloads. 
If I load the disk and select " try again " or " continue " nothing happens. If I load the disk and select " try again " the whole process starts up again and the program will run in " live CD " mode.
I've done the checkdisk procedure and also I've done the edit at boot time and entered " irqpoll ", like in the WubiGuide instructions and I still get the " BusyBox/(initramfs) prompt.

---

