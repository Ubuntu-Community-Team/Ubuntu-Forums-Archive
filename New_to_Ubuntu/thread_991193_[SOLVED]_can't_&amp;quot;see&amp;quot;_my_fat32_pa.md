---
title: "[SOLVED] can't &amp;quot;see&amp;quot; my fat32 partition"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by socngill on 2008-11-23
I have just done a clean install of Kubuntu 8.10 and my fat32 partition is not viewable.  When I go into root-media it isn't there.  It does list my NTFS XP partition, but not the fat32 one which holds all my music, pictures, documents etc.

Any idea how I can get Linux to recognise it, and also how to auto mount it on start up?

Thanks.

Oh, I have checked GParted and it is there, but it appears to be on the same partition as the SWAP file.  Could this be causing the problem?

---

### Post by Michael.Godawski on 2008-11-23
Can you please post the result of:
```
df -h
```

and 
```

gksudo gedit /etc/fstab
```

---

### Post by socngill on 2008-11-23
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              25G  2.1G   22G   9% /
tmpfs                 632M     0  632M   0% /lib/init/rw
varrun                632M  100K  632M   1% /var/run
varlock               632M     0  632M   0% /var/lock
udev                  632M  2.8M  629M   1% /dev
tmpfs                 632M     0  632M   0% /dev/shm
lrm                   632M  2.0M  630M   1% /lib/modules/2.6.27-7-generic/volatile
**/dev/sda5              60G   10G   50G  17% /dos**
/dev/sda1              30G   26G  3.5G  89% /media/disk


I have highlighted the drive in question.

and:

> neil@Kubuntu:~$ gksudo gedit /etc/fstab

(gksudo:5528): Gtk-WARNING **: libbonoboui-2.so.0: cannot open shared object file: No such file or directory

(gksudo:5528): Gtk-WARNING **: libbonoboui-2.so.0: cannot open shared object file: No such file or directory

Which ven to me doesn't look good!!

---

### Post by marshall.robert on 2008-11-23
> **Michael.Godawski said:**
> Can you please post the result of:
```
df -h
```

and 
```

gksudo gedit /etc/fstab
```

on a kde system you use kate instead of gedit i think

---

### Post by drs305 on 2008-11-23
For kubuntu:
```
kdesudo kate /etc/fstab
```

---

### Post by Michael.Godawski on 2008-11-23
Can you navigate in Nautilus, I mean just look for the fstab file manually if it is there at all?
Perhaps the application gedit caused the problem.

edit:
thx .[drs305]("http://ubuntuforums.org/member.php?u=223945")

---

### Post by socngill on 2008-11-23
> neil@Kubuntu:~$ kdesu kate /etc/fstab
bash: kdesu: command not found


Something would appear to be not quite right....?  I did "sudo" in front as well with the same result.

---

### Post by diablo75 on 2008-11-23
That command looks right.  Try it again in a fresh terminal window...

---

### Post by socngill on 2008-11-23
> **diablo75 said:**
> That command looks right.  Try it again in a fresh terminal window...

Went one better and restarted, but still has the same problem.  Found out that Kwrite was not installed (I thought it would be automatically installed?).  So have installed it and still get the same error message:

> kdesu kate /etc/fstab

---

### Post by diablo75 on 2008-11-23
What happens if you just type "kate" and nothing else?

---

### Post by socngill on 2008-11-23
> **diablo75 said:**
> What happens if you just type "kate" and nothing else?

> neil@Kubuntu:~$ kate
kate(5837): createDoc
kate(5837) KateSessionManager::KateSessionManager: LOCAL SESSION DIR:  "/home/neil/.kde/share/apps/kate/sessions"
kate(5837) KateApp::initKate: Setting KATE_PID: ' 5837 '
kate(5837) KateViewDocumentProxyModel::updateBackgrounds: false
kate(5837) KateMainWindow::KateMainWindow: **************************************************************************** 0x8d6f0c0
kate(5837) KateViewDocumentProxyModel::updateBackgrounds: false
kate(5837) KateViewDocumentProxyModel::updateBackgrounds: false
kate(5837) KateApp::startupKate: KateApplication::init finished successful
kate(5837) KateViewDocumentProxyModel::updateBackgrounds: true

and then kate opens.

Its the kdesu bit which seems ot be causing the problem.

---

### Post by drs305 on 2008-11-23
Can you open any other graphical apps as root? If so, open your file browser as root, then navigate to /etc and open fstab from your file browser's options menu.

---

### Post by socngill on 2008-11-23
I have opened the file in Kate, and this is what it says:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=72cacf54-f076-4524-b642-572a95f54527 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=48FA-4F85  /dos            vfat    utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=79507a37-3a12-4d4f-a20f-c2a9981bb369 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by socngill on 2008-11-23
> **drs305 said:**
> Can you open any other graphical apps as root? If so, open your file browser as root, then navigate to /etc and open fstab from your file browser's options menu.

In 8.10 I seem to be unable to open anything as root.  All the options (right clicking etc) no longer give the option to "open as root".  Which is very annoying, but for another thread :)

---

### Post by drs305 on 2008-11-23
Here is the line you want to add to fstab, but read all before doing it:
```

/media/**dos** vfat auto,users,uid=1000,umask=027,utf8 0 0

```

First, you are going to have to be able to access fstab as root. You said you got Kate to open, but was it as root? If not, you will be able to make the changes but not save them.

Second, you said it was the **dos** folder in post #3. If it was really supposed to be another device (**dos** just doesn't sound right), change the mountpoint accordingly. Also make sure the mountpoint exists.

Added: (This post was being written as you made you last post).
To regain root privileges, you will probably have to boot to the recovery mode, get to the root prompt, and run the following to give yourself admin powers:
```

adduser *yourusername* admin

```

---

### Post by socngill on 2008-11-23
It would appear that it has been readable all along.  Opened up Partition Manager to check the details of the drive and noticed that mount point said Dos - so i went to root folder and found "dos" folder, clicked on it and there it was!

It was not showing as a a drive/folder in "media" and that was what was causing me to think it wasn't working.  Now, I used sudo nano and added the line as specified above, so it may well have been that which sorted the problem.  I also ran the usser admin command from recovery but it said I was already admin.  Had to turn the mahcine off (as I don't now how to get back to the recovery menu once i have dropped to root) and on restart it did find some errors which it fixed.

So, it could be either of the those two things which helped, or it could have been there all along - either way a big thank you to all who made such quick and helpful responses.

---

