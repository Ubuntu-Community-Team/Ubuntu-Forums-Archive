---
title: "HOWTO dual boot using NTLDR"
date: 2008-04-15
forum: Outdated Tutorials &amp; Tips
---

### Post by hums07 on 2008-04-15
**_Background_**
Search on the topic lead me to old threads, some of which are obsolete or a bit complicated (e.g. needs proprietary software: [http://ubuntuforums.org/showthread.php?t=208951](http://ubuntuforums.org/showthread.php?t=208951)).

**_Why_**
NTLDR is the bootloader for Windows NT based OS which includes Windows 2000/NT/XP. Using GRUB is safe and should be encouraged, but if you want a booting process within Windows environment, then this howto is for you.

This howto works for Windows 2000/NT/XP, and [COLOR="Red"]does not work with Vista[/COLOR]. Vista has its own bootloader.

**_During Ubuntu installation_**
Install GRUB on the partition where you install Ubuntu. Do not let GRUB written to MBR. If you use liveCD, at the last step (i.e. Ready to Install), click Advance button and fill in (hd0,X) where X is your Ubuntu partition.

**_Option 1. Using grldr_**
grldr can be found in [COLOR="Blue"][grub4dos]("http://sarovar.org/projects/grub4dos/")[/COLOR].
[COLOR="Blue"]In these codes, you may need to change /hda to /sda[/COLOR]
1. While you are running Ubuntu (e.g. from liveCD):
Copy **menu.lst** found in /boot/grub/ of your Ubuntu partition to C:\ (Windows root folder).
```
sudo cp /boot/grub/menu.lst /media/hda1
```
IF the above instruction is not successful because Windows partition is not yet mounted, run these codes:```
sudo mkdir /media/hda1
sudo mount /dev/hda1 /media/hda1
sudo cp ubuntu.mbr /media/hda1
```
2. Next steps can be done in Ubuntu or Windows: Extract grldr file from [[COLOR="Blue"]grub4dos[/COLOR]]("https://gna.org/projects/grub4dos/") to C:\.
3. Edit **C:\boot.ini** and add this line:
```
C:\grldr="Ubuntu Loader (grub4dos)"
```
4. Next time you restart, NTLDR gives you a choice to start Windows or Ubuntu Loader. If you choose Ubuntu loader, Grub4Dos will display grub menu as usual.

**_Option 2. Using copy of Ubuntu boot sector_**
[COLOR="Blue"]In these codes, you may need to change /hda to /sda[/COLOR]
1. While running Ubuntu (e.g. from liveCD), make a copy of Ubuntu boot sector (modify /dev/hda2 to correct position of your Ubuntu partition):```
sudo dd if=/dev/hda2 of=ubuntu.mbr bs=512 count=1
```
2. Copy **ubuntu.mbr** to C:\```
sudo cp ubuntu.mbr /media/hda1
```
IF the above instruction is not successful because Windows partition is not yet mounted, run these codes:```
sudo mkdir /media/hda1
sudo mount /dev/hda1 /media/hda1
sudo cp ubuntu.mbr /media/hda1
```
3. This step can be done in Ubuntu or Windows: Edit **C:\boot.ini** and add this line:
```
C:\ubuntu.mbr="Start Ubuntu Grub"
```
4. Next time you restart, NTLDR gives you a choice to start Windows or Ubuntu Grub. If you choose Ubuntu Grub, Grub will display menu as usual.

**_IF Grub is already on MBR_**
If Grub has been written to MBR, and you want to use NTLDR instead.
**A.If you wish to use grldr,**  you need to:
1. Reinstall Grub to Ubuntu partition
2. Reinstall MBR: [http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)
3. Go to Option 1 above and follow the steps.
To reinstall Grub to Ubuntu partition, while running Ubuntu run these codes:
```
sudo grub
find /boot/grub/stage1
root (hd?,?)  #replace ?,? with the output of the above "find" instruction
setup (hd?,?)
quit
```

**B. If you wish to use Ubuntu partition sector,**  you need to
1. Reinstall Grub to Ubuntu partition
2. Do the above Option 2 step 1.
3. Do the above Option 2 step 2.
4. Reinstall MBR:  [http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)
5. Do the above Option 2 step 3 in Windows.

**_NOTE 1._**
To edit boot.ini in Windows:
1. Open Notepad
2. Goto File - Open (or press Ctrl - O), write in the Filename box: **C:\boot.ini**.

**_NOTE 2._**
I use grub4dos version 0.4.1pre22 and it works for me. In this case, menu.lst has to be put on folder C:\boot\grub (not on C:\).
EDIT: I attach grldr from grub4dos-0.4.1pre22 which I always use. In Windows you can extract it using [7-zip]("http://www.7-zip.org/").

---

