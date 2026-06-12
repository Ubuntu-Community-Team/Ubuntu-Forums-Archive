---
title: "File System Seems Messed Up"
date: 2012-05-20
forum: New to Ubuntu
---

### Post by DGINSD on 2012-05-20
I was just trying to work through why I couldn't seem to write to a SDcard in the built in slot and I noticed some odd things. For example if I copy a file from my documents directory and try to paste the copied file in my home directory "paste" in the context menu is grayed out and not allowed.

Ok now I'm really confused, I just tried to duplicate the issue the same as before, and this time no problems. 

I fixed my SDcard issue by adding this line to my fstab file.

```
# built in SD card port
/dev/sdb1       /media/SDcard   auto    noauto,user,exec     0 0 
```

A few things relevant to my system: 

The I have a separate home partition, 12.04 was freshly installed over 11.10 and the home partition was left unformated to maintain my old data and settings.

I converted my file systems from ext3 to ext4 using the instructions found here [https://help.ubuntu.com/community/ConvertFilesystemToExt4]("https://help.ubuntu.com/community/ConvertFilesystemToExt4")

To be honest I really don't even know what I'm asking, now that it's seemingly working as designed. I guess is there a way to fix file system permissions? or even deturmine if they are actually broken? Or if someone has any idea as to what could cause something seemingly random like this?

Side note, issuing the command ```
gksudo nautilus
``` seems to do what its supposed to do, but printed in the terminal where the command is issued is this.

```
david@david-HP-Pavilion-g6-Notebook-PC:~$ gksudo nautilus
Initializing nautilus-gdu extension
Shutting down nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


```

Normal? Something needs changing? Related?

---

### Post by Lisiano on 2012-05-20
[LIST]
[*]Post the output of ```
df
``` and ```
mount
```
[*]Keeping old files from 11.10 shouldn't cause problems. At least not enough to block writing to a disk.
[*]It is possible your home is owned by root, to check that, issue ```
ls -la
```This will show what is owned by who. If . is owned by root or anyone else or even a UID, that is probably why. Run this to make every file in your home yours. ```
sudo chown -R $USER:$USER /home/$USER
```
[*]That error refers to that you don't have Samba installed. Unless you wish to use it, you can disregard the error. Or it might be a false error from running nautilus under root. If that error doesn't appear when you run without root, then it's a false error ([lpbug]499288[/lpbug])
[/LIST]

---

### Post by DGINSD on 2012-05-20
```
david@david-HP-Pavilion-g6-Notebook-PC:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda5       50906044  7256080  41061704  16% /
udev             1747420        4   1747416   1% /dev
tmpfs             702484      904    701580   1% /run
none                5120        0      5120   0% /run/lock
none             1756200      696   1755504   1% /run/shm
/dev/sda6      291100100 65969808 210341792  24% /home
/dev/sdb1        1954368       32   1954336   1% /media/SDcard

```

```
david@david-HP-Pavilion-g6-Notebook-PC:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda6 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)
/dev/sdb1 on /media/SDcard type vfat (rw,nosuid,nodev,user=david)

```

Check this out; weird???

```
david@david-HP-Pavilion-g6-Notebook-PC:~$ sudo chown -R $USER:$USER /home/$USER
[sudo] password for david: 
chown: cannot access `/home/david/.gvfs': Permission denied

```

---

### Post by idoitprone on 2012-05-20
> **DGINSD said:**
> ```
david@david-HP-Pavilion-g6-Notebook-PC:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda5       50906044  7256080  41061704  16% /
udev             1747420        4   1747416   1% /dev
tmpfs             702484      904    701580   1% /run
none                5120        0      5120   0% /run/lock
none             1756200      696   1755504   1% /run/shm
/dev/sda6      291100100 65969808 210341792  24% /home
/dev/sdb1        1954368       32   1954336   1% /media/SDcard

``````
david@david-HP-Pavilion-g6-Notebook-PC:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda6 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)
/dev/sdb1 on /media/SDcard type vfat (rw,nosuid,nodev,user=david)

```Check this out; weird???

```
david@david-HP-Pavilion-g6-Notebook-PC:~$ sudo chown -R $USER:$USER /home/$USER
[sudo] password for david: 
chown: cannot access `/home/david/.gvfs': Permission denied

```

```
sudo fusermount -u /home/david/.gvfs 
```

now try those commands that lisiano said to do

---

### Post by DGINSD on 2012-05-20
Something else odd which is likely my not understanding than any thing else...

```
david@david-HP-Pavilion-g6-Notebook-PC:~$ ls -la
total 59636
drwxr-xr-x 66 david david     4096 May 20 14:57 .
drwxr-xr-x  7 root  root      4096 May  2 17:25 ..
drwx------  4 david david     4096 Feb 14 06:34 .adobe
drwxrwxr-x  3 david david     4096 Apr  8 14:14 .arista
drwxrwxr-x  4 david david     4096 Apr  5 20:16 .audacity-data
drwxrwxr-x  2 david david     4096 Apr  5 19:41 Audiobooks
-rw-------  1 david david    12130 May 20 14:56 .bash_history
-rw-r--r--  1 david david      220 Feb 12 21:09 .bash_logout
-rw-r--r--  1 david david     3353 Feb 12 21:09 .bashrc
drwx------  2 david david     4096 Mar 27 07:16 .bogofilter
drwx------ 37 david david     4096 May 19 20:17 .cache
drwxrwxr-x  2 david david     4096 Apr 29 15:00 catalyst12.4
drwxrwxr-x  3 david david     4096 Feb 12 22:43 .compiz-1
drwx------ 40 david david     4096 May 17 00:37 .config
drwx------  3 david david     4096 Feb 12 21:19 .dbus
drwxr-xr-x  2 david david     4096 May 12 23:47 Desktop
-rw-rw-r--  1 david david      162 Apr 25 19:45 .devede
-rw-r--r--  1 david david       26 May 20 14:57 .dmrc
drwxr-xr-x  6 david david     4096 May 19 19:04 Documents
drwxr-xr-x  8 david david     4096 May 18 21:04 Downloads
-rw-------  1 david david      206 Mar 28 18:46 duplicity-full.20120329T014602Z.manifest.gpg
-rw-------  1 david david      202 Mar 28 18:46 duplicity-full.20120329T014602Z.vol1.difftar.gpg
-rw-------  1 david david      199 Mar 28 18:46 duplicity-full-signatures.20120329T014602Z.sigtar.gpg
drwxr-xr-x 14 david david     4096 May 19 14:44 .dvdcss
drwxrwxr-x  4 david david     4096 Mar 25 15:13 DVDFab
drwxr-xr-x  2 david david     4096 Apr  3 20:34 .dvdrip
drwxrwxr-x  3 david david     4096 Apr  6 18:43 dvdrip-data
-rw-rw-r--  1 david david    29127 Apr  3 19:38 .dvdriprc
-rw-rw-r--  1 david david        6 May 15 05:35 .dvdshrink.pid
-rw-rw-r--  1 david david      129 May 14 06:07 .dvdshrinkrc
-rw-------  1 david david       16 Feb 12 21:19 .esd_auth
-rw-r--r--  1 david david      179 Feb 12 21:09 examples.desktop
-rw-r--r--  1 david david    17474 Apr 29 13:23 .face
drwxr-xr-x  2 david david     4096 May 15 06:08 .fontconfig
drwx------  5 david david     4096 May 20 14:57 .gconf
drwx------  4 david david     4096 Feb 15 05:48 .gegl-0.0
drwxr-xr-x 22 david david     4096 May  4 06:38 .gimp-2.6
drwxr-xr-x 24 david david     4096 May  6 22:12 .gimp-2.8
drwxr-xr-x  5 david david     4096 May 20 11:00 .gkrellm2
-rw-r-----  1 david david        0 May 20 13:02 .gksu.lock
drwx------  6 david david     4096 May  9 06:23 .gnome2
drwx------  2 david david     4096 Feb 13 05:42 .gnome2_private
drwx------  3 david david     4096 Feb 28 06:22 .gnome-commander
drwx------  2 david david     4096 Mar 28 18:46 .gnupg
-rw-------  1 david david       77 May  9 06:23 .goutputstream-01CODW
-rw-------  1 david david        0 Apr 15 12:59 .goutputstream-5DXICW
-rw-------  1 david david       77 May 16 23:12 .goutputstream-6L1LEW
-rw-------  1 david david       77 May 19 19:09 .goutputstream-6RBFEW
-rw-------  1 david david       77 Apr 29 15:22 .goutputstream-I3UKDW
-rw-------  1 david david       77 Apr 29 14:08 .goutputstream-IJS5CW
-rw-------  1 david david        0 Mar  3 08:35 .goutputstream-NBGKAW
-rw-------  1 david david       77 May 11 21:05 .goutputstream-PPY2DW
-rw-r--r--  1 david david     1437 May 19 21:54 grub.bck
drwxrwxr-x  2 david david     4096 May 19 14:44 .gstreamer-0.10
-rw-rw-r--  1 david david      275 May 20 14:57 .gtk-bookmarks
dr-x------  2 david david        0 May 20 14:57 .gvfs
-rw-------  1 david david    51540 May 20 14:57 .ICEauthority
drwxrwxr-x  4 david david     4096 Apr 12 19:49 .icedtea
drwxr-xr-x  3 david david     4096 Mar  6 06:12 .icons
-rw-r--r--  1 david david 60181836 Feb 12 22:33 icon-theme.cache
drwxrwxrwx 11 david david     4096 Apr  2 17:38 Icon Work
drwx------  3 david david     4096 Feb 16 21:26 .kde
drwx------  3 david david     4096 May 15 20:54 .launchpadlib
-rw-rw-r--  1 david david     9636 Apr 30 19:23 libnautilus-gksu.so
drwxrwxr-x  3 david david     4096 Feb 14 00:49 .libreoffice
drwxrwxr-x  3 david david     4096 Feb 12 21:19 .local
drwx------  3 david david     4096 Feb 14 06:34 .macromedia
drwx------  3 david david     4096 Feb 12 21:20 .mission-control
-rw-r--r--  1 david david        6 May  6 12:04 .mousetweaks.pid
drwx------  4 david david     4096 Feb 13 06:20 .mozilla
drwxrwxr-x  2 david david     4096 Mar 18 09:40 .mplayer
drwxrwxr-x 20 david david     4096 Apr 17 22:50 Music
drwxr-x---  6 david david     4096 May 15 05:12 .openshot
drwxrwxr-x  2 david david     4096 Mar 23 05:34 PcSetup
drwxrwxr-x  5 david david     4096 Apr 14 23:40 Phone Stuff
drwxr-xr-x  4 david david     4096 May 20 12:15 Pictures
drwx------  3 david david     4096 Feb 12 22:05 .pki
drwxrwxr-x  2 david david     4096 Apr  5 19:41 Podcasts
-rw-r--r--  1 david david      675 Feb 12 21:09 .profile
drwxr-xr-x  2 david david     4096 Feb 12 21:19 Public
drwx------  2 david david     4096 May 20 14:57 .pulse
-rw-------  1 david david      256 Feb 12 21:19 .pulse-cookie
drwxrwxr-x  4 david david     4096 Apr 10 05:26 .quodlibet
drwx------  2 david david     4096 May  4 23:04 .remmina
drwxr-xr-x  2 david david     4096 Feb 25 15:20 .rpmdb
drwxrwxr-x  5 david david     4096 May  2 19:38 .shotwell
-rw-rw-r--  1 david david    58157 Apr 27 05:58 software-list
drwxrwxr-x  2 david david     4096 Feb 14 19:19 .spumux
-rw-r--r--  1 david david        0 Feb 12 22:09 .sudo_as_admin_successful
drwxrwxr-x  3 david david     4096 Apr 11 20:04 .teamviewer
drwxr-xr-x  2 david david     4096 Feb 12 21:19 Templates
drwxr-xr-x  3 david david     4096 Mar 10 22:01 .themes
drwx------  5 david david     4096 Feb 13 22:21 .thumbnails
drwx------  4 david david     4096 Feb 13 05:42 .thunderbird
drwxrwxr-x  5 david david     4096 Apr  9 06:26 Ubuntu One
drwxr-xr-x  7 david david     4096 May 20 12:59 Videos
drwxrwxr-x  2 david david     4096 Feb 22 06:09 .wicd
-rw-rw-r--  1 david david        2 Mar 24 13:00 .windows-serial
drwxrwxr-x  4 david david     4096 May 16 18:54 .wine
drwxrwxr-x  2 david david     4096 Feb 12 22:41 .winff
-rw-------  1 david david      154 May 20 14:57 .Xauthority
-rw-rw-r--  1 david david       37 May  2 21:14 .Xmodmap
-rw-------  1 david david   117930 May 20 15:15 .xsession-errors
-rw-------  1 david david   118959 May 20 14:56 .xsession-errors.old

```

The 4th line down ".." owned by root? like I said likely my lack of understanding more than anything else. ".." is one level back which would be /home which I shouldn't own?

---

### Post by idoitprone on 2012-05-20
> **DGINSD said:**
> Something else odd which is likely my not understanding than any thing else...

```
david@david-HP-Pavilion-g6-Notebook-PC:~$ ls -la
total 59636
drwxr-xr-x 66 david david     4096 May 20 14:57 .
drwxr-xr-x  7 root  root      4096 May  2 17:25 ..
drwx------  4 david david     4096 Feb 14 06:34 .adobe
drwxrwxr-x  3 david david     4096 Apr  8 14:14 .arista
drwxrwxr-x  4 david david     4096 Apr  5 20:16 .audacity-data
drwxrwxr-x  2 david david     4096 Apr  5 19:41 Audiobooks
-rw-------  1 david david    12130 May 20 14:56 .bash_history
-rw-r--r--  1 david david      220 Feb 12 21:09 .bash_logout
-rw-r--r--  1 david david     3353 Feb 12 21:09 .bashrc
drwx------  2 david david     4096 Mar 27 07:16 .bogofilter
drwx------ 37 david david     4096 May 19 20:17 .cache
drwxrwxr-x  2 david david     4096 Apr 29 15:00 catalyst12.4
drwxrwxr-x  3 david david     4096 Feb 12 22:43 .compiz-1
drwx------ 40 david david     4096 May 17 00:37 .config
drwx------  3 david david     4096 Feb 12 21:19 .dbus
drwxr-xr-x  2 david david     4096 May 12 23:47 Desktop
-rw-rw-r--  1 david david      162 Apr 25 19:45 .devede
-rw-r--r--  1 david david       26 May 20 14:57 .dmrc
drwxr-xr-x  6 david david     4096 May 19 19:04 Documents
drwxr-xr-x  8 david david     4096 May 18 21:04 Downloads
-rw-------  1 david david      206 Mar 28 18:46 duplicity-full.20120329T014602Z.manifest.gpg
-rw-------  1 david david      202 Mar 28 18:46 duplicity-full.20120329T014602Z.vol1.difftar.gpg
-rw-------  1 david david      199 Mar 28 18:46 duplicity-full-signatures.20120329T014602Z.sigtar.gpg
drwxr-xr-x 14 david david     4096 May 19 14:44 .dvdcss
drwxrwxr-x  4 david david     4096 Mar 25 15:13 DVDFab
drwxr-xr-x  2 david david     4096 Apr  3 20:34 .dvdrip
drwxrwxr-x  3 david david     4096 Apr  6 18:43 dvdrip-data
-rw-rw-r--  1 david david    29127 Apr  3 19:38 .dvdriprc
-rw-rw-r--  1 david david        6 May 15 05:35 .dvdshrink.pid
-rw-rw-r--  1 david david      129 May 14 06:07 .dvdshrinkrc
-rw-------  1 david david       16 Feb 12 21:19 .esd_auth
-rw-r--r--  1 david david      179 Feb 12 21:09 examples.desktop
-rw-r--r--  1 david david    17474 Apr 29 13:23 .face
drwxr-xr-x  2 david david     4096 May 15 06:08 .fontconfig
drwx------  5 david david     4096 May 20 14:57 .gconf
drwx------  4 david david     4096 Feb 15 05:48 .gegl-0.0
drwxr-xr-x 22 david david     4096 May  4 06:38 .gimp-2.6
drwxr-xr-x 24 david david     4096 May  6 22:12 .gimp-2.8
drwxr-xr-x  5 david david     4096 May 20 11:00 .gkrellm2
-rw-r-----  1 david david        0 May 20 13:02 .gksu.lock
drwx------  6 david david     4096 May  9 06:23 .gnome2
drwx------  2 david david     4096 Feb 13 05:42 .gnome2_private
drwx------  3 david david     4096 Feb 28 06:22 .gnome-commander
drwx------  2 david david     4096 Mar 28 18:46 .gnupg
-rw-------  1 david david       77 May  9 06:23 .goutputstream-01CODW
-rw-------  1 david david        0 Apr 15 12:59 .goutputstream-5DXICW
-rw-------  1 david david       77 May 16 23:12 .goutputstream-6L1LEW
-rw-------  1 david david       77 May 19 19:09 .goutputstream-6RBFEW
-rw-------  1 david david       77 Apr 29 15:22 .goutputstream-I3UKDW
-rw-------  1 david david       77 Apr 29 14:08 .goutputstream-IJS5CW
-rw-------  1 david david        0 Mar  3 08:35 .goutputstream-NBGKAW
-rw-------  1 david david       77 May 11 21:05 .goutputstream-PPY2DW
-rw-r--r--  1 david david     1437 May 19 21:54 grub.bck
drwxrwxr-x  2 david david     4096 May 19 14:44 .gstreamer-0.10
-rw-rw-r--  1 david david      275 May 20 14:57 .gtk-bookmarks
dr-x------  2 david david        0 May 20 14:57 .gvfs
-rw-------  1 david david    51540 May 20 14:57 .ICEauthority
drwxrwxr-x  4 david david     4096 Apr 12 19:49 .icedtea
drwxr-xr-x  3 david david     4096 Mar  6 06:12 .icons
-rw-r--r--  1 david david 60181836 Feb 12 22:33 icon-theme.cache
drwxrwxrwx 11 david david     4096 Apr  2 17:38 Icon Work
drwx------  3 david david     4096 Feb 16 21:26 .kde
drwx------  3 david david     4096 May 15 20:54 .launchpadlib
-rw-rw-r--  1 david david     9636 Apr 30 19:23 libnautilus-gksu.so
drwxrwxr-x  3 david david     4096 Feb 14 00:49 .libreoffice
drwxrwxr-x  3 david david     4096 Feb 12 21:19 .local
drwx------  3 david david     4096 Feb 14 06:34 .macromedia
drwx------  3 david david     4096 Feb 12 21:20 .mission-control
-rw-r--r--  1 david david        6 May  6 12:04 .mousetweaks.pid
drwx------  4 david david     4096 Feb 13 06:20 .mozilla
drwxrwxr-x  2 david david     4096 Mar 18 09:40 .mplayer
drwxrwxr-x 20 david david     4096 Apr 17 22:50 Music
drwxr-x---  6 david david     4096 May 15 05:12 .openshot
drwxrwxr-x  2 david david     4096 Mar 23 05:34 PcSetup
drwxrwxr-x  5 david david     4096 Apr 14 23:40 Phone Stuff
drwxr-xr-x  4 david david     4096 May 20 12:15 Pictures
drwx------  3 david david     4096 Feb 12 22:05 .pki
drwxrwxr-x  2 david david     4096 Apr  5 19:41 Podcasts
-rw-r--r--  1 david david      675 Feb 12 21:09 .profile
drwxr-xr-x  2 david david     4096 Feb 12 21:19 Public
drwx------  2 david david     4096 May 20 14:57 .pulse
-rw-------  1 david david      256 Feb 12 21:19 .pulse-cookie
drwxrwxr-x  4 david david     4096 Apr 10 05:26 .quodlibet
drwx------  2 david david     4096 May  4 23:04 .remmina
drwxr-xr-x  2 david david     4096 Feb 25 15:20 .rpmdb
drwxrwxr-x  5 david david     4096 May  2 19:38 .shotwell
-rw-rw-r--  1 david david    58157 Apr 27 05:58 software-list
drwxrwxr-x  2 david david     4096 Feb 14 19:19 .spumux
-rw-r--r--  1 david david        0 Feb 12 22:09 .sudo_as_admin_successful
drwxrwxr-x  3 david david     4096 Apr 11 20:04 .teamviewer
drwxr-xr-x  2 david david     4096 Feb 12 21:19 Templates
drwxr-xr-x  3 david david     4096 Mar 10 22:01 .themes
drwx------  5 david david     4096 Feb 13 22:21 .thumbnails
drwx------  4 david david     4096 Feb 13 05:42 .thunderbird
drwxrwxr-x  5 david david     4096 Apr  9 06:26 Ubuntu One
drwxr-xr-x  7 david david     4096 May 20 12:59 Videos
drwxrwxr-x  2 david david     4096 Feb 22 06:09 .wicd
-rw-rw-r--  1 david david        2 Mar 24 13:00 .windows-serial
drwxrwxr-x  4 david david     4096 May 16 18:54 .wine
drwxrwxr-x  2 david david     4096 Feb 12 22:41 .winff
-rw-------  1 david david      154 May 20 14:57 .Xauthority
-rw-rw-r--  1 david david       37 May  2 21:14 .Xmodmap
-rw-------  1 david david   117930 May 20 15:15 .xsession-errors
-rw-------  1 david david   118959 May 20 14:56 .xsession-errors.old

```The 4th line down ".." owned by root? like I said likely my lack of understanding more than anything else. ".." is one level back which would be /home which I shouldn't own?

/home is owned by root dont worry

---

### Post by Lisiano on 2012-05-20
> **DGINSD said:**
> ```
david@david-HP-Pavilion-g6-Notebook-PC:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda5       50906044  7256080  41061704  16% /
udev             1747420        4   1747416   1% /dev
tmpfs             702484      904    701580   1% /run
none                5120        0      5120   0% /run/lock
none             1756200      696   1755504   1% /run/shm
/dev/sda6      291100100 65969808 210341792  24% /home
/dev/sdb1        1954368       32   1954336   1% /media/SDcard

```Good, your disks aren't full so it's not the Root reserved space letting root write.
> **DGINSD said:**
> ```
david@david-HP-Pavilion-g6-Notebook-PC:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda6 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)
/dev/sdb1 on /media/SDcard type vfat (rw,nosuid,nodev,user=david)

```
Everything is mounted as read-write which is good.
> **DGINSD said:**
> 
Check this out; weird???

```
david@david-HP-Pavilion-g6-Notebook-PC:~$ sudo chown -R $USER:$USER /home/$USER
[sudo] password for david: 
chown: cannot access `/home/david/.gvfs': Permission denied

```
That's normal. .gvfs is a folder that contains all your GVFS mounts, for example mounted ISOs, mounted archives, mounted Audio disks, basically everything which is not a real device. This folder is created automatically and if you look at mount, it's impossible to reassign who sees it's contents, which is why chown fails to change it, even thought it's already owned by david.

> **DGINSD said:**
> Something else odd which is likely my not understanding than any thing else...

```
david@david-HP-Pavilion-g6-Notebook-PC:~$ ls -la
total 59636
drwxr-xr-x  7 root  root      4096 May  2 17:25 ..

```

The 4th line down ".." owned by root? like I said likely my lack of understanding more than anything else. ".." is one level back which would be /home which I shouldn't own?
It's okay that /home is owned by root, in fact it's correct that it's owned by root.


Can you write to your home folder normally now?

---

### Post by DGINSD on 2012-05-20
Yes I can, it was rather odd, I couldn't copy and paste files moving them from directory to directory. Then as I was writing my OP, I tested it again to make sure I was wording it correctly, and the problem was gone. Hasn't shown up again since. Go figure?

Thanks for your help.

---

