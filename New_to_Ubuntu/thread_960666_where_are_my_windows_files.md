---
title: "where are my windows files?????"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by pilarchen on 2008-10-27
Hi everybody,
I'm looking for help. My harddisk is divided (windows/xubuntu) and the windows part is under media listed but I can't find my old files..... I don't know were they are now
A Friend of mine instaled Xubuntu yesterday and i was working perfect, but today I lost the both Panels (top und button), and now, when I got back them, I'm missing all my old files
what should i do??????

---

### Post by Keen101 on 2008-10-27
you could double check that the windows partitions are intact.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

or you could try

> sudo fdisk -l

and post back the contents here

---

### Post by pilarchen on 2008-10-27
staschy@staschy-desktop:~$ sudo fdisk -
[sudo] password for staschy: 
Konnte - nicht öffnen
bash: pilar: command not found
Konnte - nicht öffnen


and now?

---

### Post by nhasian on 2008-10-27
If you can mount and access your windows partition, the default locations for userfiles in Windows XP is Documents and Settings or My Documents, but in Vista its in Users/*yourusername*

---

### Post by Keen101 on 2008-10-27
> sudo fdisk -

did you add the letter l ?

**dash lowercase letter L**

```
sudo fdisk -l
```

---

### Post by Crafty Kisses on 2008-10-27
Paste this command into the terminal:
```
sudo fdisk -l
```
Look for the drive in question. Let's just say, for the sake of this example, that it's /dev/hda1 and NTFS (if it's something else, post it back here, and I or someone else will help you modify the appropriate command). Then paste these commands into the terminal:
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
```
Launch up the file browser and browse the /media/windows directory, and you should see all your files. There is probably a GUI way to do this, too, but it depends greatly on what version of Ubuntu you're using... or if you're using Kubuntu or Xubuntu.

---

### Post by pilarchen on 2008-10-27
staschy@staschy-desktop:~$ sudo mkdir /media/windows
mkdir: kann Verzeichnis &#8222;/media/windows&#8220; nicht anlegen: File exists

I was working... but now the "/media/windows" is empty!!!


should I use the second code????

I really don't want to lose my files!!!!!

---

### Post by pilarchen on 2008-10-27
i thank you all guys!!! and please don't let me down.... I'm really hopeless!

---

### Post by Crafty Kisses on 2008-10-27
In order for us to help you, we really need to see this command:
```
sudo fdisk -l
```
Something similar to this should appear after you have ran that command:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         832     6289888+   c  W95 FAT32 (LBA)
/dev/sda2   *         833        5585    35932680    7  HPFS/NTFS
/dev/sda3            5586       10251    35274960   83  Linux / Solaris


```
What that command has just shown is what file systems are available on the computer, and what their device file names are. So for example in the table above, the NTFS partition would be /dev/sda2. So we need to see that command, now run another command in the terminal:
```
gksudo gedit /etc/fstab
```
Type in your password, nothing will show up that is normal, so what you want to do is add a line something similar to this, it needs to match your partition table:
```
/dev/sda2	/media/Windows     ntfs    defaults,nls=utf8,umask=007,gid=46       0       1
```
The above would be correct for the table given, but for yours it would obviously be different. Once you have done that, save your changes and run this command:
```
sudo mkdir /media/Windows
```
Once you've done that you can now mount the drive by doing the following:
```
sudo mount -a
```
Once that is done your NTFS drive should be mounted and your Windows files should be accessible to you.

---

### Post by scorchgeek on 2008-10-27
Don't worry...nothing is going to happen to your files even if this takes a long time to solve.

---

### Post by mbstrlbstr on 2008-10-28
Heh, I was wondering how to do the same thing, here are my fstab results

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9        1314    10485760    7  HPFS/NTFS
/dev/sda3   *        1314       14267   104047612    7  HPFS/NTFS
/dev/sda4           14267       14594     2621440    f  W95 Ext'd (LBA)
/dev/sda5           14267       14594     2620416   dd  Unknown

```

---

