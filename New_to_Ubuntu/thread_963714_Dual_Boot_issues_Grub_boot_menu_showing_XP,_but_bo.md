---
title: "Dual Boot issues: Grub boot menu showing XP, but booting Ubuntu- Newbie!!"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by Conja100 on 2008-10-30
I recently installed windows XP on a laptop that has Ubuntu Hardy Heron on it already. I went through the steps of recovering grub from the Ubuntu cd. So, at this point, Ubuntu was all I could boot from the grub boot menu.

I then went into my /boot/grub/menu.lst and did what was required for the Windows XP option to show in the Grub boot menu.

However, the problem is that when I click on Windows XP, it boots Ubuntu. The menu looks like this: 

title       Windows XP
root        (hd0,1)
makeactive
chainloader +1

This has been placed after the line: 

### END DEBIAN AUTOMAGIC KERNELS LIST


I have one hard drive, on which I have 4 partitions (ubuntu partition, windows fat32 partition, swap partition and shared fat32 partition)

I am very new to all of this and I am slow on the uptake (!!), so if I could please get some clear help? Would be hugely appreciative!

---

### Post by Het Irv on 2008-10-30
Open up the terminal and type [CODE]sudo fdisk -l[CODE] and paste the output here.
Note: It will ask for your password and just type in your login password.  Nothing will show, but thats normal.

---

### Post by phidia on 2008-10-30
From a terminal what is the output of "sudo fdisk -l"?

I don't know what partition xp is on but the partition you are trying to boot with the menu.lst you provided is the second partition on the first drive. sd or hda2.

Note grub counts starting with 0. So if xp is on the first partition you need to edit that menu.lst entry to show (hd0,0).

---

### Post by rolnics on 2008-10-30
opps!

---

### Post by logos34 on 2008-10-30
nm

---

### Post by Conja100 on 2008-10-31
Okay, the output of "sudo fdisk -l" is as follows:

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xceffceff

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1245    10000431   83  Linux
/dev/hda2            1246        2490    10000462+   b  W95 FAT32
/dev/hda3   *        2491        2614      996030   82  Linux swap/solaris
/dev/hda4            2615        4864    18073125    b  W95 FAT32


XP is installed on hda2, the smaller of the 2 FAT32 partitions.

Apologies for the cramped view, had to retype it, home internet down right now!

---

### Post by caljohnsmith on 2008-10-31
Something doesn't seem quite right, because if you are using the following entry to boot Windows:
```
title Windows XP
root (hd0,1)
[COLOR="Blue"]makeactive[/COLOR]
chainloader +1
```
Then the "makeactive" line should set the boot flag on the hda2 Windows partition when you boot it, yet your fdisk output shows the Linux swap hda3 partition is marked active. How about rebooting, select the Windows entry in the Grub menu, press "e" to edit it, and see if it shows the exact Windows entry above with the makeactive line. Let me know what it says. 

In the meantime, if you have your Windows Install CD, I would boot that up, go to the "recovery console", and run:
```
fixboot
```
That will reinstall the Windows boot sector to the Windows partition, which sounds like it could be your issue if you are booting Ubuntu when you select Windows. Also, while you are in the recovery console, it would be good to run:
```
chkdsk /r
```
And run that as many times as it takes until it returns no errors. Let me know how it goes.

---

### Post by Conja100 on 2008-10-31
> **caljohnsmith said:**
> Something doesn't seem quite right, because if you are using the following entry to boot Windows:
```
title Windows XP
root (hd0,1)
[COLOR="Blue"]makeactive[/COLOR]
chainloader +1
```
Then the "makeactive" line should set the boot flag on the hda2 Windows partition when you boot it, yet your fdisk output shows the Linux swap hda3 partition is marked active. How about rebooting, select the Windows entry in the Grub menu, press "e" to edit it, and see if it shows the exact Windows entry above with the makeactive line. Let me know what it says. 

In the meantime, if you have your Windows Install CD, I would boot that up, go to the "recovery console", and run:
```
fixboot
```
That will reinstall the Windows boot sector to the Windows partition, which sounds like it could be your issue if you are booting Ubuntu when you select Windows. Also, while you are in the recovery console, it would be good to run:
```
chkdsk /r
```
And run that as many times as it takes until it returns no errors. Let me know how it goes.


When I reboot and press 'e' while the windows XP option is highlighted in the grub boot menu, it says:

root (hd0,1)
makeactive
chainloader +1

I then used my windows cd and using the recovery console, ran 'fixboot' as well as 'chkdsk /r'.

I was a bit confused here. If there had been an error, would it have displayed this fact while in recovery console?

This did not happen, and I rebooted, but now when I select the windows xp option in the grub boot menu, it says:

starting up ...

Disk error
Press any key to restart

---

### Post by caljohnsmith on 2008-10-31
How about again posting the output of (and make sure you post the full output):
```
sudo fdisk -l
```
And next post the output of:
```
sudo mkdir /mnt/hda2 /mnt/hda4
sudo mount /dev/hda2 /mnt/hda2
sudo mount /dev/hda4 /mnt/hda4
ls -l /mnt/hda2 /mnt/hda4
```
Where "-l" is a lowercase L. 

When you ran the chkdsk, it should have reported something about its status as it was checking and also when it finished. Did it say anything at all?

---

### Post by Conja100 on 2008-10-31
From “sudo fdisk -l” I get:

Disk /dev/hda: 40.0 GB, 40007761920 bytes 
255 heads, 63 sectors/track, 4864 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xceffceff 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/hda1               1        1245    10000431   83  Linux 
/dev/hda2   *        1246        2490    10000462+   b  W95 FAT32 
/dev/hda3            2491        2614      996030   82  Linux swap / Solaris 
/dev/hda4            2615        4864    18073125    b  W95 FAT32 


From "sudo mkdir /mnt/hda2 /mnt/hda4
      sudo mount /dev/hda2 /mnt/hda2
      sudo mount /dev/hda4 /mnt/hda4
      ls -l /mnt/hda2 /mnt/hda4"

I get:

/mnt/hda2: 
total 328 
-rwxr-xr-x  1 root root      0 2008-10-29 10:14 autoexec.bat 
-rwxr-xr-x  1 root root    245 2008-10-29 10:01 boot.ini 
-rwxr-xr-x  1 root root    512 2008-10-29 07:40 bootsect.dos 
-rwxr-xr-x  1 root root      0 2008-10-29 10:14 config.sys 
drwxr-xr-x  7 root root   8192 2008-10-29 07:41 Documents and Settings 
-r-xr-xr-x  1 root root      0 2008-10-29 10:14 io.sys 
-r-xr-xr-x  1 root root      0 2008-10-29 10:14 msdos.sys 
-r-xr-xr-x  1 root root  47580 2003-03-31 12:00 ntdetect.com 
-r-xr-xr-x  1 root root 233632 2003-03-31 12:00 ntldr 
dr-xr-xr-x 18 root root   8192 2008-10-29 10:13 Program Files 
drwxr-xr-x  3 root root   8192 2008-10-29 10:23 System Volume Information 
drwxr-xr-x 35 root root   8192 2008-10-29 07:36 windows 
 
/mnt/hda4: 
total 64 
drwxrwx--- 2 root plugdev 16384 2008-10-02 10:32 Microsoft.Office.2007.Enterprise-WiNK - hardhell4me 
drwxrwx--- 2 root plugdev 16384 2008-10-02 10:59 Movies 
drwxrwx--- 8 root plugdev 16384 2008-10-02 10:45 Music 
drwxrwx--- 3 root plugdev 16384 2008-10-29 10:25 System Volume Information


When I ran the chkdsk /r, it reported that it was "first checking or recovering", then it went through a series of additional "checking or recovering" sequences. No error was reported, but then nothing else was reported either.

---

### Post by caljohnsmith on 2008-10-31
OK, it looks pretty clear that you have a Windows problem and not a Grub problem at this point. One more thing you can do that might work is to use "testdisk" to help repair the Windows boot sector; first enable all your repositories in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD (hda) and "proceed", choose "intel", choose "advanced", select the Windows XP partition (hda2), choose "boot", then choose "Rebuild BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know what happens. :)

---

### Post by Conja100 on 2008-10-31
Ok, this is another problem. I have tried to set the net etc up on my laptop, but it doesn't work. When i plug the dsl modem cable in, it registers the network connection, but it doesn't work.

At this point, I am using the net from my home pc, and working on my laptop separately. So, downloading and running testdisk will be a problem. Thanks so much for the effort so far, I appreciate it, just keen to get everything working!

---

### Post by caljohnsmith on 2008-10-31
Since you don't have internet access from the laptop, you could instead download the "[SystemRescueCD]("http://www.sysresccd.org/")" and use that, since it has testdisk included.

---

### Post by Conja100 on 2008-10-31
Testdisk did the trick, both operating systems are booting perfectly now! Thanks so much for all the help, its really appreciated!

---

### Post by caljohnsmith on 2008-10-31
That's great news, glad it's all working now. Cheers and have fun. :)

---

