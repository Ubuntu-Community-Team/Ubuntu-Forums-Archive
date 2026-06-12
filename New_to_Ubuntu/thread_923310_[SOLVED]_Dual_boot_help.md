---
title: "[SOLVED] Dual boot help"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by SKDgarbage on 2008-09-18
I need a little help setting up GRUB. I've gone through 2 or 3 installs of Ubuntu and XP at this point. (it's quite a headache just for Warhammer online -_-)

I'm using two SATA hard drives both 75 GB. I installed XP first on the primary drive and Ubuntu 8.04 on the second. After the updates for Ubuntu I restarted and loaded GRUB when given the option and XP didn't show up. After some trolling and a little work I got XP to show up but when I go to load it says NTLDR is missing. 

Do I just need to edit /boot/grub/menu.lst? or is it more likely something a little more complicated? 

I know there's more than a few post on the issue but they're not specific to my setup and I'm too tired at this point to make much use of the info there. So ny help would be greatly appreciated :P

---

### Post by hellion0 on 2008-09-18
It looks like when you're trying to boot over to Windows, it's expecting the NT Loader. Sounds like something happened to it.

[This article may give you some ideas on what to do.](http://www.quickonlinetips.com/archives/2005/12/ntldr-is-missing-press-any-key-to-restart/)

---

### Post by caljohnsmith on 2008-09-18
Yes, probably all you need to do is modify your menu.lst. Please post the following:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
Or, if you're feeling lucky :), add both of the following entries to your menu.lst, and most likely one of them will boot Windows:
```
title	   Windows on (hd1)
rootnoverify (hd1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows on (hd0)
root       (hd0,0)
makeactive
chainloader +1
```

---

### Post by SKDgarbage on 2008-09-18
```
  
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9038    72597703+   7  HPFS/NTFS

 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         165     1325331   82  Linux swap / Solaris
/dev/sdb2             166        9039    71280405   83  Linux


```

annnd

```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a4c9f8cd-0575-4818-8ec4-cfead106bf44 ro quiet splash vga=788
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a4c9f8cd-0575-4818-8ec4-cfead106bf44 ro quiet splash vga=788
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

```

I think that's all you need from them right? If not let me know :P

---

### Post by bumanie on 2008-09-18
NTLDR has nothing to do with grub or /boot/grub/menu.lst The NT bootloader is missing and I don't think it can be repaired via console mode in xp. As far as I know there is no way to fix it other than following the above posters suggestion, however, if you are lucky, it could be that windows is searching for a the boot sector on the wrong disc ie order of HDD's have changed in bios somehow. That can cause this error message - check your bios out first. I have read that one can copy the NTLDR and boot.ini and ntdetect from an xp cd and place them where they are required. Attached is a screen shot of my xp HDD taken from within ubuntu. If you have the means to get the three files and you have ubuntu working with ntfs-3g installed, you should be able to copy the files to  the same place from within ubuntu. Can't guarantee this will work, but it should if the files are OK and copied to the correct place in windows. Hope this helps.

---

### Post by caljohnsmith on 2008-09-18
You weren't feeling lucky? :) I think you would have got it with the second entry:
```
title	   Windows on (hd0)
root       (hd0,0)
makeactive
chainloader +1
```
Just replace your existing Windows entry with the one above in your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
Give that a shot and let me know how it goes.

---

### Post by SKDgarbage on 2008-09-18
After all this you think I'd be feeling lucky? haha. Well I tried it and it was a no go.

---

### Post by caljohnsmith on 2008-09-18
> **SKDgarbage said:**
> After all this you think I'd be feeling lucky? haha. Well I tried it and it was a no go.
So did you get the same NTLDR error? Because if you did, then Bumanie is right, your Windows partition is probably missing ntldr and maybe its other boot files too. First do:
```
sudo umount /dev/sda1
```
That just to make sure it isn't mounted elsewhere, then do:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Then we can see which boot files you are missing.

---

### Post by SKDgarbage on 2008-09-18
:-/ 
```

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /mnt -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /mnt ntfs-3g force 0 0

```

---

### Post by caljohnsmith on 2008-09-18
OK, try:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
```
Post any errors or the output.

---

### Post by SKDgarbage on 2008-09-18
That fixed her 
```

total 2095160
-rwxrwxrwx 1 root root          0 2008-09-18 00:31 AUTOEXEC.BAT
-rwxrwxrwx 1 root root          0 2008-09-18 00:31 CONFIG.SYS
drwxrwxrwx 1 root root       4096 2008-09-18 00:35 Documents and Settings
-rwxrwxrwx 1 root root          0 2008-09-18 00:31 IO.SYS
-rwxrwxrwx 1 root root          0 2008-09-18 00:31 MSDOS.SYS
drwxrwxrwx 1 root root          0 2008-09-18 00:39 NVIDIA
-rwxrwxrwx 1 root root 2145386496 2008-09-18 00:49 pagefile.sys
drwxrwxrwx 1 root root          0 2008-09-18 01:22 ProgramData
drwxrwxrwx 1 root root       8192 2008-09-18 01:50 Program Files
drwxrwxrwx 1 root root          0 2008-09-18 00:47 RECYCLER
drwxrwxrwx 1 root root       4096 2008-09-18 00:34 System Volume Information
drwxrwxrwx 1 root root      40960 2008-09-18 01:50 WINDOWS

```

---

### Post by caljohnsmith on 2008-09-18
OK, so you are missing all your Windows boot files for some reason. Download the attached file to this message, save it to your desktop, and do the following (this assumes you still have Windows sda1 mounted on /mnt):
```
cd ~/Desktop
tar xvf "Windows boot files.tar.gz"
sudo mv boot.ini /mnt
sudo mv NTDETECT.COM /mnt
sudo mv ntldr /mnt
```
Reboot, and let me know what happens.

---

### Post by myidbe on 2008-09-18
Additional reference:
This tutorial from IBM is a good introduction to boot loaders and how to make them relatively quickly do what you what them to do.
(To access it, however, you need to sign up for a free IBM account/username).
([http://www.ibm.com/developerworks/edu/l-dw-linux-lpic1102-i.html?S_TACT=105AGX03&S_CMP=EDU](http://www.ibm.com/developerworks/edu/l-dw-linux-lpic1102-i.html?S_TACT=105AGX03&S_CMP=EDU))

---

### Post by SKDgarbage on 2008-09-18
Posting from XP (after a quick scan of the hard drive):P thanks for all the help cal, and I promise I'll only use it for a few games ;]

---

### Post by caljohnsmith on 2008-09-18
> **SKDgarbage said:**
> Posting from XP (after a quick scan of the hard drive):P thanks for all the help cal, and I promise I'll only use it for a few games ;]
Great, glad it's working now. :)

---

