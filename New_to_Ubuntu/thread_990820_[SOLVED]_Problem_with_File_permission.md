---
title: "[SOLVED] Problem with File permission"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by TheDarkMaster on 2008-11-23
Hi all,
I'm trying to install a rather big game in Wine so it says I don't have enough space on my virtual C-Drive. Well I already tried to re-size it but that didn't work out so now I'm trying to install into another place on my HDD. I've got 500GB external HDD with Ubuntu installed on it. Now in my /-folder there is an host-folder which contains the files that where on my HDD before I installed Ubuntu(dual-booted). Now if I try to install the game there it won't let me because I have no permission not even if I execute it as root(sudo). It's a vfat file system. Also I tried to change the file permission with Nautilus(no success), chmod(no success) and chown(also no success). I'm getting rather desperate so if anyone please has an idea, I would really appreciate that.

---

### Post by chuckyp on 2008-11-23
What do you mean by your "virtual c drive" ? Wine applications get installed in your /home/<username>/.wine/c_drive/  directory.

---

### Post by TheDarkMaster on 2008-11-23
That's what I mean, wine treats it as separate HDD so I called it virtual c-drive.

---

### Post by Michael.Godawski on 2008-11-23
Can you please post the result of this command so we get a picture of the permissions on your machine
```

ls -la
```

---

### Post by TheDarkMaster on 2008-11-23
Here's the output of "ls -la"

```

totaal 680
drwxr-xr-x 82 thijs thijs   4096 2008-11-23 10:15 .
drwxr-xr-x  7 root  root    4096 2008-11-21 15:56 ..
drwx------  2 thijs thijs   4096 2008-11-09 22:12 .abuse
drwx------  3 thijs thijs   4096 2008-11-12 21:53 .adanaxis
drwx------  3 thijs thijs   4096 2008-11-09 12:04 .adobe
drwxr-xr-x  4 thijs thijs   4096 2008-11-20 21:44 Afbeeldingen
drwxr-xr-x  4 thijs thijs   4096 2008-11-09 13:29 .alien-arena
drwx------  3 thijs thijs   4096 2008-11-10 20:56 .armyops250
drwxr-xr-x  3 thijs thijs   4096 2008-11-14 21:58 .avogadro
-rw-------  1 thijs thijs  12124 2008-11-23 11:45 .bash_history
-rw-r--r--  1 thijs thijs    220 2008-11-09 10:58 .bash_logout
-rw-r--r--  1 thijs thijs   3115 2008-11-09 10:58 .bashrc
drwxr-xr-x  2 thijs thijs   4096 2008-11-14 22:02 .bkchem
drwxr-xr-x  5 thijs thijs   4096 2008-11-14 19:14 .blender
drwx------  2 thijs thijs   4096 2008-11-09 21:57 .bogofilter
drwx------  2 thijs thijs   4096 2008-11-09 15:29 .btanks
drwxr-xr-x  2 thijs thijs   4096 2008-11-23 10:07 Bureaublad
drwxr-xr-x  6 thijs thijs   4096 2008-11-19 22:41 .cache
drwx------  3 thijs thijs   4096 2008-11-09 11:20 .compiz
drwxr-xr-x 18 thijs thijs   4096 2008-11-23 09:54 .config
drwx------  3 thijs thijs   4096 2008-11-09 11:09 .dbus
drwxr-xr-x  5 thijs thijs   4096 2008-11-14 22:05 .dia
-rw-------  1 thijs thijs     86 2008-11-21 15:00 .directory
-rw-------  1 thijs thijs     28 2008-11-23 09:54 .dmrc
drwxr-xr-x  9 thijs thijs   4096 2008-11-20 22:07 Documenten
drwxr-xr-x  2 thijs thijs   4096 2008-11-20 16:13 dwhelper
drwxr-xr-x  3 thijs thijs   4096 2008-11-13 21:45 .earth3d
-rw-------  1 thijs thijs     16 2008-11-09 11:09 .esd_auth
drwxr-xr-x  8 thijs thijs   4096 2008-11-20 22:11 .evolution
lrwxrwxrwx  1 thijs thijs     26 2008-11-09 10:58 Examples -> /usr/share/example-content
-rw-r--r--  1 thijs thijs  31294 2008-11-18 22:56 .face
-rw-r--r--  1 thijs thijs    292 2008-11-13 16:51 .fbhighlevelshistory
-rw-r--r--  1 thijs thijs    197 2008-11-13 16:51 .fbhighscores
-rw-r--r--  1 thijs thijs   1196 2008-11-13 16:24 .fbrc
drwx------  2 thijs thijs   4096 2008-11-22 10:09 .filezilla
drwxr-xr-x  2 thijs thijs   4096 2008-11-19 22:45 .fontconfig
drwx------  3 thijs thijs   4096 2008-11-14 22:05 .FontForge
drwx------  5 thijs thijs   4096 2008-11-23 09:55 .gconf
drwx------  2 thijs thijs   4096 2008-11-23 11:45 .gconfd
drwx------  7 thijs thijs   4096 2008-11-19 17:30 .gdesklets
drwx------  4 thijs thijs   4096 2008-11-19 22:45 .gegl-0.0
drwx------  3 thijs thijs   4096 2008-11-11 17:29 .gftp
drwxr-xr-x 22 thijs thijs   4096 2008-11-19 22:46 .gimp-2.6
-rw-r-----  1 thijs thijs      0 2008-11-23 11:00 .gksu.lock
drwxr-xr-x  3 thijs thijs   4096 2008-11-09 18:29 .gnome
drwx------ 16 thijs thijs   4096 2008-11-22 18:51 .gnome2
drwx------  2 thijs thijs   4096 2008-11-09 11:09 .gnome2_private
drwx------  2 thijs thijs   4096 2008-11-20 19:56 .gnupg
drwx------  3 thijs thijs   4096 2008-11-18 18:16 .googleearth
drwxr-xr-x  2 thijs thijs   4096 2008-11-20 20:51 .gpilotd
-rw-r--r--  1 thijs thijs      5 2008-11-20 20:51 .gpilotd.pid
-rw-r--r--  1 thijs thijs     10 2008-11-09 22:07 .gshutdown
drwxr-xr-x  2 thijs thijs   4096 2008-11-18 17:04 .gstreamer-0.10
-rw-r--r--  1 thijs thijs    115 2008-11-23 10:01 .gtk-bookmarks
dr-x------  2 thijs thijs      0 2008-11-23 09:54 .gvfs
-rw-------  1 thijs thijs  12528 2008-11-23 09:54 .ICEauthority
drwxr-xr-x  4 thijs thijs   4096 2008-11-15 13:48 .icons
drwx------  3 thijs thijs   4096 2008-11-09 12:00 .kde
drwx------  2 thijs thijs   4096 2008-11-13 21:40 .kino-history
-rw-r--r--  1 thijs thijs   2970 2008-11-13 21:40 .kinorc
drwx------  3 thijs thijs   4096 2008-11-09 11:10 .local
drwx------  3 thijs thijs   4096 2008-11-09 12:04 .macromedia
drwxr-xr-x  3 thijs thijs   4096 2008-11-09 13:52 .mcop
-rw-------  1 thijs thijs     31 2008-11-19 20:40 .mcoprc
drwx------  5 thijs thijs   4096 2008-11-20 21:53 .mozilla
-rw-r--r--  1 thijs thijs    269 2008-11-21 15:10 Mozilla Firefox.desktop
drwx------  3 thijs thijs   4096 2008-11-16 09:04 .mozilla-thunderbird
drwxr-xr-x  2 thijs thijs   4096 2008-11-19 22:30 .mplayer
drwxr-xr-x  3 thijs thijs   4096 2008-11-20 16:59 Muziek
drwxr-xr-x  3 thijs thijs   4096 2008-11-22 18:51 .nautilus
drwx------  3 thijs thijs   4096 2008-11-13 17:40 .netpanzer
drwxr-xr-x  2 thijs thijs   4096 2008-11-10 19:18 .neverball
drwxr-xr-x  3 thijs thijs   4096 2008-11-12 16:32 .nexuiz
-rw-------  1 thijs thijs      0 2008-11-11 18:08 nl_NL.UTF-8
drwxr-xr-x  3 thijs thijs   4096 2008-11-11 19:38 .openarena
drwxr-xr-x  2 thijs thijs   4096 2008-11-09 11:09 Openbaar
drwx------  3 thijs thijs   4096 2008-11-22 18:30 .openoffice.org2
drwxr-xr-x  2 thijs thijs   4096 2008-11-15 21:47 Photos
drwxr-xr-x  2 thijs thijs   4096 2008-11-14 21:58 .praat-dir
-rw-r--r--  1 thijs thijs    675 2008-11-09 10:58 .profile
drwxr-xr-x  3 thijs thijs   4096 2008-11-21 15:28 Programmes
drwxr-xr-x  2 thijs thijs   4096 2008-11-09 11:10 .pulse
-rw-------  1 thijs thijs    256 2008-11-09 11:09 .pulse-cookie
drwx------  6 thijs thijs   4096 2008-11-23 11:43 .purple
drwxr-xr-x  2 thijs thijs   4096 2008-11-09 13:52 .qt
-rw-r--r--  1 thijs thijs    198 2008-11-18 16:40 QuickTime Player.desktop
-rw-------  1 thijs thijs   2142 2008-11-22 18:30 .recently-used
-rw-------  1 thijs thijs   3854 2008-11-23 10:15 .recently-used.xbel
drwxr-xr-x  4 thijs thijs   4096 2008-11-21 15:31 .runrev
-rw-r--r--  1 thijs thijs    244 2008-11-18 16:41 Safari.desktop
drwx------  2 thijs thijs   4096 2008-11-20 19:50 .scim
drwx------  4 thijs thijs   4096 2008-11-11 18:09 .screem
drwxr-xr-x  3 thijs thijs   4096 2008-11-19 17:40 .screenlets
drwx------  7 thijs thijs   4096 2008-11-13 20:19 .secondlife
-rw-r--r--  1 thijs thijs   1398 2008-11-14 22:03 .simrc
drwxr-xr-x  2 thijs thijs   4096 2008-11-09 11:09 Sjablonen
drwx------  2 thijs thijs   4096 2008-11-20 19:56 .ssh
-rw-r--r--  1 thijs thijs      0 2008-11-09 11:29 .sudo_as_admin_successful
drwxr-xr-x  4 thijs thijs   4096 2008-11-09 16:55 .sudoku
drwx------  3 thijs thijs   4096 2008-11-09 19:40 .supertux2
drwxr-xr-x  2 thijs thijs   4096 2008-11-09 19:10 .supertuxkart
drwxr-xr-x  5 thijs thijs   4096 2008-11-20 21:23 .themes
drwx------  5 thijs thijs   4096 2008-11-09 19:35 .thumbnails
drwxr-xr-x  2 thijs thijs   4096 2008-11-09 11:19 .update-manager-core
drwx------  2 thijs thijs   4096 2008-11-09 11:10 .update-notifier
drwxr-xr-x  2 thijs thijs   4096 2008-11-20 16:14 Video's
drwxr-xr-x  2 thijs thijs   4096 2008-11-18 16:51 .wapi
-rw-r--r--  1 thijs thijs      4 2008-11-23 10:14 .windows-label
drwxr-xr-x  4 thijs thijs   4096 2008-11-23 11:32 .wine
-rw-------  1 thijs thijs    117 2008-11-23 09:54 .Xauthority
drwxr-xr-x  2 thijs thijs   4096 2008-11-12 09:16 .xine
drwx------  5 thijs thijs   4096 2008-11-21 17:01 .xmoto
-rw-r--r--  1 thijs thijs    129 2008-11-09 19:34 .xscreensaver-getimage.cache
-rw-r--r--  1 thijs thijs 200135 2008-11-23 10:16 .xsession-errors

```

thijs is the admin account
the file permission of the folder I need is set to: "drwxr-xr-x"

---

### Post by Michael.Godawski on 2008-11-23
Off topic: I realize I had a long break from the Ubuntuforums...I think slower...
Back to topic: 
and what are the current  permissions from the 
*.wine* directory and from the
*drive_c* directory?

---

### Post by Paqman on 2008-11-23
> **TheDarkMaster said:**
> Now in my /-folder there is an host-folder which contains the files that where on my HDD before I installed Ubuntu(dual-booted).

You installed with Wubi, right?

To get more room in your /home folder (which is where Wine's C: drive is located) you can use [LVPM]("http://lubi.sourceforge.net/lvpm.html").

---

### Post by Zorgoth on 2008-11-23
You can't change the permissions a vfat drive except at mounting.  See my thread here:

[http://pennsylvania.ubuntuforums.com/showthread.php?p=6002763](http://pennsylvania.ubuntuforums.com/showthread.php?p=6002763)

bodhi.zazen's response

Unmount it and remount it the way he says.

---

### Post by Zorgoth on 2008-11-23
> **Zorgoth said:**
> You can't change the permissions a vfat drive except at mounting.  See my thread here:

[http://pennsylvania.ubuntuforums.com/showthread.php?p=6002763](http://pennsylvania.ubuntuforums.com/showthread.php?p=6002763)

bodhi.zazen's response

Unmount it and remount it the way he says.

I believe that only one of them worked for me, so try both sets of numbers if one doesn't work.

---

### Post by TheDarkMaster on 2008-11-23
Thx zorgoth but it's on the boot drive so I can't unmount it through nautilus(doesn't work through umount and pumount too) and so I can't change the dmask and fmask, also I don't really get them:O.

---

### Post by Zorgoth on 2008-11-23
Hmm...  If your Ubuntu is actually installed on a vfat drive, your permissions will always be annoying.  Vfat doesn't get the concept of multiple users.  If you *really* need the permissions to work, you could re-install your system by putting Ubuntu on an ext3 partition and your vfat files on a vfat partition, but you probably don't want to do that.  I've never had Ubuntu on a vfat partition (only used one to share files with Windows), so I don't have too much experience with this.

By the way, were you using sudo with the setup file?  I'm pretty sure that should be gksudo (it's got a GUI, no?), not that it will change the result.

Just a thought; I don't know what I'm talking about really because I don't use wine:

Is it possible to mount an ext3 partition (if you can make one big enough) into your virtual C drive?  Then permissions could be changed with chmod and chown (or should be able to be; I don't know what effect having a vfat installation has on this).

For future reference, dmask and fmask aren't hard; you do them with the mount command used with -o.  For more information, try:

man mount

Hopefully I'm not *completely* useless.

---

### Post by TheDarkMaster on 2008-11-24
Thx again Zorgoth that with gksudo could be the problem as it is indeed a GUI, I reinstalled Ubuntu now so I'll try again when I got my settings back(I really messed the system up:() Could you give some more details on the ext3 partition, please because I like the idea(exept the fact that windows could not use it anymore but I wasn't going to boot into Windows again exept when it's really necessary, like now:P). So if I(before I install Ubuntu again) make 2 partition on my HDD, first I keep 200GB for the vfat(windows) partition an then make a 300GB ext3 partition, was that what you ment(and the install Ubuntu into the ext3)? And would that work with the permissions do you think?

---

### Post by CatKiller on 2008-11-24
> **TheDarkMaster said:**
> (exept the fact that windows could not use it anymore but I wasn't going to boot into Windows again exept when it's really necessary, like now:P).

There is a Windows driver that will let you read an ext partition from Windows. I don't use Windows any more, so I can't remember what it's called.

>  So if I(before I install Ubuntu again) make 2 partition on my HDD, first I keep 200GB for the vfat(windows) partition an then make a 300GB ext3 partition, was that what you ment(and the install Ubuntu into the ext3)? And would that work with the permissions do you think?

That will certainly help. You might find it useful, if you are transferring files between your Ubuntu and Windows installs, to have another partition. So you could have a 200 GB FAT/NTFS Windows partition, a 200 GB ext3 Ubuntu partition, a swap partition, and the rest as a FAT/NTFS partition for random data that you want to access from both. Ubuntu is able to read and write to your Windows partition, if you want it to, so that's an option, but I understand that you might not want to risk messing things up on the Windows side - which is why I suggested a neutral data partition.

One thing to bear in mind is that FAT, as well as not understanding user permissions, can't understand links either, so you can't have your ~/.wine folder on your neutral data partition, since it includes links to other files. I learned this the hard way, and at the time the error messages were erroneously about permissions.

---

### Post by TheDarkMaster on 2008-11-24
Thanks a lot that helped a great way, I will set it solved as fast as I know for sure that it worked out fine.

---

### Post by TheDarkMaster on 2008-11-24
Okay, I wanted to try the last post's idea but I can't find a right partitioner::mad::mad::mad:. Anyone please tell me if you know a free, trustworthy partitioner which I can run from within windows.

---

### Post by Jammy4041 on 2008-11-24
You could use EXT2 IFS which is a windows driver extension tat allows you to read your ext3 partition. (It will say it is mounted as an ext2 though) 

[http://www.fs-driver.org/](http://www.fs-driver.org/)

I hope this helps, it just may not make you reinstall ubuntu.

As for your partitioner, most partioners have to run from a cd, so it has unmounted file systems so you could use your ubuntu cd (System>>Administration>>Partiton Editor)
because gParted does everything.

---

### Post by TheDarkMaster on 2008-11-24
Thanks for the idea about how to not reinstall Ubuntu but I'm afraid that's already necessary. I messed up the Virtual /dev/loop0 & /dev/loop1 partition and can't get them right:(

---

### Post by CatKiller on 2008-11-24
> **TheDarkMaster said:**
> Okay, I wanted to try the last post's idea but I can't find a right partitioner::mad::mad::mad:. Anyone please tell me if you know a free, trustworthy partitioner which I can run from within windows.

See, I'd view the last two requirements as being mutually exclusive :)

I'd recommend either the GParted that comes on the Ubuntu cd, or the [Gparted live cd]("http://gparted.sourceforge.net/").

I don't think you'll be able to change the Ubuntu / partition from FAT to ext3 without a format, which means a re-install. So you can set up your new partitions at the same time as you re-install Ubuntu.

---

### Post by TheDarkMaster on 2008-11-24
All thanks great work, especially CatKiller who brought the final idea. I worked it out and everything works fine now.
Here's what I did for people who don't want to read the whole thread again:
1) I uninstalled wubi
2) I used Gparted live CD to create a new ext3 partition
3) I burned inside windows a Ubuntu 8.10 Live CD
4) I rebooted from the live CD and installed Ubuntu into my 270GB ext3 partition

Result: 
*I have a 200Gb big home partition and lots of space left. Even on the windows partition.*

Again really thanks everybody!:guitar:

I'll mark this thread as SOLVED now

---

