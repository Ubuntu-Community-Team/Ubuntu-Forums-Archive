---
title: "Cannot Show folder Contents"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by Damiox on 2008-05-30
i was moving vids and mp3s from another hard drive...then whent back to check them and it gave me that error....im using nautilus in root to access them but i cant regular......this is not good,im a musician and i do not need to lose those files.....i tried adjusting the permisions on my home dir but that hasnt changed anything....nothing will open from the menu.....the hard drive i was pulling from was a win xp ridden with virus's and spyware...the original user was using Kazza..i wonder if any win virus could even effect a linux box...maybe this is the effect...???

its all on the same partion....a 40 gb...with 1 gb ram, 1 gb swap ,2gb 32 bit processor...ubuntu 7 ...Gnome

ok i can open my programs just not locations.....

---

### Post by pytheas22 on 2008-05-30
It's very unlikely that any Windows virus could damage Linux, although it's possible that it damaged the file system of the remote disk while it was still running on Windows, which could be the source of the errors.  Please open a terminal (Applications>Accessories>Terminal) and change to the directory where the files are.  If it's an external hard drive, it's probably under the /media directory, so you want to do something like this:
```

cd /media/disk
```

note that the name may not really be 'disk'; you can just type cd /media and then press tab twice, and the terminal will display the options available; try to choose the one that looks appropriate.

After you've cd'd to the right directory, type the command:
```

ls -al
```

and please copy and paste the output here.

---

### Post by Damiox on 2008-05-30
here u go..... its an internal hard drive that i just put in a min ago too check and wipe..and it is listed as "disk" 

damiox@Home-Ubuntu-Main:~$ ls -al
total 667412
drwxrwx--- 52 damiox damiox      4096 2008-05-30 01:41 .
drwxr-xr-x  4 root   root        4096 2008-05-28 21:42 ..
drwxrwx---  7 damiox damiox      4096 2008-05-22 16:43 1
drwxrwx---  7 damiox damiox      4096 2008-05-24 13:07 2
drwxrwx---  7 damiox damiox      4096 2008-05-24 23:05 3
drwxrwx---  7 damiox damiox      4096 2008-05-25 22:53 4
drwxrwx---  7 damiox damiox      4096 2008-05-25 23:57 4.0
-rw-r-----  1 damiox damiox   3965932 2008-05-22 15:00 49020_yeonil_ziemniaaki.wav
drwxrwx---  3 damiox damiox      4096 2008-05-29 11:24 .adobe
drwxrwx---  4 damiox damiox      4096 2008-05-29 12:42 .armagetronad
-rw-------  1 damiox damiox        14 2008-05-28 23:29 .bash_history
-rw-r-----  1 damiox damiox       220 2008-05-28 21:40 .bash_logout
-rw-r-----  1 damiox damiox      2298 2008-05-28 21:40 .bashrc
drwxrwx---  3 damiox damiox      4096 2008-05-28 22:08 .cache
drwxrwx---  7 damiox damiox      4096 2008-05-30 01:59 .config
drwxrwx---  2 damiox damiox      4096 2008-05-30 00:21 .dbus-keyrings
-rw-r-----  1 damiox damiox        63 2008-05-30 00:24 .DCOPserver_Home-Ubuntu-Main__0
lrwxrwxrwx  1 damiox damiox        44 2008-05-30 00:24 .DCOPserver_Home-Ubuntu-Main_:0 -> /home/damiox/.DCOPserver_Home-Ubuntu-Main__0
drwxrwx---  2 damiox damiox      4096 2008-05-30 01:41 Desktop
-rw-------  1 damiox damiox        28 2008-05-30 00:17 .dmrc
drwxrwx---  2 damiox damiox      4096 2008-05-18 16:38 Documents
-rw-------  1 damiox damiox        16 2008-05-28 22:08 .esd_auth
lrwxrwxrwx  1 root   root          26 2008-05-28 23:18 Examples -> /usr/share/example-content
drwxrwx---  2 damiox damiox      4096 2008-05-28 23:12 .fontconfig
drwxrwx---  4 damiox damiox      4096 2008-05-30 00:17 .gconf
drwxrwx---  2 damiox damiox      4096 2008-05-30 01:58 .gconfd
-rw-r-----  1 damiox damiox         0 2008-05-30 00:18 .gksu.lock
drwxrwx---  2 damiox damiox      4096 2008-05-29 12:50 .gl-117
drwxrwx---  3 damiox damiox      4096 2008-05-28 22:08 .gnome
drwxrwx--- 12 damiox damiox      4096 2008-05-30 01:07 .gnome2
drwx------  2 damiox damiox      4096 2008-05-28 22:07 .gnome2_private
drwxrwx---  2 damiox damiox      4096 2008-05-30 00:32 .gstreamer-0.10
-rw-r-----  1 damiox damiox       112 2008-05-30 00:17 .gtk-bookmarks
-rw-r-----  1 damiox damiox        88 2008-05-28 22:08 .gtkrc-1.2-gnome2
-rw-------  1 damiox damiox       567 2008-05-30 00:24 .ICEauthority
drwxrwx---  2 damiox damiox      4096 2008-05-28 22:21 .icons
drwxrwx---  2 damiox damiox      4096 2008-05-21 04:28 ISO'S
drwxrwx---  3 damiox damiox      4096 2008-05-29 12:46 .kde
drwxrwx---  3 damiox damiox      4096 2008-05-28 22:08 .local
drwxrwx---  3 damiox damiox      4096 2008-05-29 11:24 .macromedia
drwxrwx---  3 damiox damiox      4096 2008-05-30 00:29 .mcop
-rw-------  1 damiox damiox        31 2008-05-30 00:29 .mcoprc
drwxrwx---  3 damiox damiox      4096 2008-05-28 21:42 .mozilla
drwxrwx---  3 damiox damiox      4096 2008-05-30 01:19 Music
drwxrwx---  3 damiox damiox      4096 2008-05-29 22:43 .nautilus
-rw-r-----  1 damiox damiox 393779967 2008-05-20 17:37 nexuiz-242.zip
-rw-r-----  1 damiox damiox 284278194 2008-05-20 23:18 oa076.zip
drwxrwx---  3 damiox damiox      4096 2008-05-28 23:49 .openoffice.org2
drwxrwx---  2 damiox damiox      4096 2008-05-29 23:43 .orbit
drwxrwx---  6 damiox damiox      4096 2008-05-29 23:20 .pcsx
drwxrwx---  2 damiox damiox      4096 2008-05-22 12:30 Pictures
drwxrwx--- 10 damiox damiox      4096 2008-05-29 23:21 .pingus
-rw-r-----  1 damiox damiox       566 2008-05-28 21:40 .profile
drwxrwx---  2 damiox damiox      4096 2008-05-18 16:38 Public
drwxrwx---  5 damiox damiox      4096 2008-05-30 01:58 .purple
drwxrwx---  2 damiox damiox      4096 2008-05-30 00:24 .qt
-rw-r--r--  1 damiox damiox    401324 2008-05-30 01:41 .recently-used.xbel
-rw-r-----  1 damiox damiox         0 2008-05-28 22:11 .sudo_as_admin_successful
drwxrwx---  2 damiox damiox      4096 2008-05-29 23:46 .supertuxkart
drwxrwx---  2 damiox damiox      4096 2008-05-18 16:38 Templates
drwxrwx---  7 damiox damiox      4096 2008-05-22 16:15 test
drwxrwx---  2 damiox damiox      4096 2008-05-28 22:37 .themes
drwxrwx---  4 damiox damiox      4096 2008-05-30 01:01 .thumbnails
drwxrwx---  2 damiox damiox      4096 2008-05-30 01:19 .Trash
-rw-------  1 damiox damiox        44 2008-05-22 15:13 Untitled1.crashed.wav
-rw-------  1 damiox damiox        44 2008-05-22 15:13 Untitled2.crashed.wav
drwxrwx---  2 damiox damiox      4096 2008-05-28 22:11 .update-manager-core
drwxrwx---  2 damiox damiox      4096 2008-05-28 22:08 .update-notifier
drwxrwx--T  8 damiox damiox      4096 2008-05-29 23:47 .vegastrike.4.x
drwxrwx---  2 damiox damiox      4096 2008-05-30 01:18 Videos
drwxrwx---  2 damiox damiox      4096 2008-05-28 22:15 .wapi
drwxrwx---  3 damiox damiox      4096 2008-05-24 03:07 wav
-rw-------  1 damiox damiox       127 2008-05-30 00:17 .Xauthority
drwxrwx---  2 damiox damiox      4096 2008-05-30 00:24 .xine
-rw-r-----  1 damiox damiox     47012 2008-05-30 01:59 .xsession-errors
damiox@Home-Ubuntu-Main:~$

---

### Post by Damiox on 2008-05-30
also the main hard drive was a clean format and install..i didnt do the whole duel boot thing...ive been with linux for a while..just kinda new to ubuntu....this tech support is great....the win hard drive is a completly different hard drive slaved off the main ide cable...everthing was fine till i started cuting and pasting files...

i have to "sudo nautilus" to be able to access any files

---

### Post by Damiox on 2008-05-30
ok..that was the ubuntu harddrive...here is the win "disk" hard drive

damiox@Home-Ubuntu-Main:/media/disk$ ls -al
total 132288
drwx------ 21 damiox root      4096 1969-12-31 19:00 .
drwxr-xr-x  5 root   root      4096 2008-05-30 00:21 ..
drwx------  3 damiox root      4096 2004-01-30 14:13 03dc7f18fac9a79fdb2c1b26
drwx------  5 damiox root      4096 2004-04-13 07:21 51522a811168b09d833b
drwx------  3 damiox root      4096 2004-01-30 14:52 797a9574237dc869d31d
drwx------  3 damiox root      4096 2000-08-05 15:45 Acrobat3
-rwx------  1 damiox root       575 2004-02-19 07:59 autoexec.bat
-rwx------  1 damiox root       194 2004-07-29 12:16 boot.ini
-rwx------  1 damiox root       512 2004-01-26 20:19 BOOTSECT.DOS
-rwx------  1 damiox root       296 2004-01-26 08:45 CONFIG.SYS
-rwx------  1 damiox root     19837 2004-08-30 09:12 counter.cab
-rwx------  1 damiox root      7099 2004-08-12 19:52 CStv.log
drwx------ 23 damiox root      4096 2004-01-26 20:39 Documents and Settings
drwx------  2 damiox root      4096 2000-10-04 06:51 ESM2
drwx------  2 damiox root      4096 2001-06-11 10:39 GENLEDFM
drwx------  2 damiox root      4096 2004-02-11 14:09 GLF7B.tmp
drwx------  2 damiox root      4096 2000-08-05 15:34 GWCI
-r-x------  1 damiox root    222390 1999-04-23 21:22 IO.SYS
-rwx------  1 damiox root      1117 2004-02-11 14:13 IPH.PH
-rwx------  1 damiox root     54904 2001-01-16 02:17 lcd.ttf
-rwx------  1 damiox root      8503 2001-01-16 02:17 license.txt
-rwx------  1 damiox root    129078 1999-04-23 21:22 LOGO.SYS
-r-x------  1 damiox root      1687 2004-01-25 08:16 MSDOS.SYS
drwx------  2 damiox root      4096 2001-02-18 21:15 My Music
drwx------  2 damiox root      4096 2000-10-06 09:01 NCDTREE
-rwx------  1 damiox root       888 2004-08-02 10:17 net_save.dna
drwx------  2 damiox root      4096 2004-01-28 21:14 New Folder
-r-x------  1 damiox root     47580 2002-08-28 20:08 ntdetect.com
-r-x------  1 damiox root    233632 2002-08-29 00:05 ntldr
-rwx------  1 damiox root 134217728 2004-12-15 21:27 pagefile.sys
dr-x------ 82 damiox root      8192 2004-07-29 12:29 Program Files
drwx------ 15 damiox root      8192 2000-12-08 12:43 QUICKENW
drwx------  2 damiox root      8192 2000-08-05 15:45 RECYCLED
-rwx------  1 damiox root       225 2000-08-05 15:54 RESETLOG.TXT
-rwx------  1 damiox root    153184 2004-01-25 07:57 SahAgent.log
-rwx------  1 damiox root     51111 2004-01-26 14:06 SCANDISK.LOG
-rwx------  1 damiox root       857 2004-01-26 08:45 SETUPXLG.TXT
-rwx------  1 damiox root       193 2004-02-09 22:22 Shortcut to CD Drive.lnk
-rwx------  1 damiox root         0 2004-01-26 16:20 SQL.LOG
drwx------  4 damiox root      4096 2004-01-26 21:31 System Volume Information
drwx------  2 damiox root      4096 2004-01-26 20:22 undo
-rwx------  1 damiox root     92632 2003-12-03 12:51 updaterInstall_112.exe
-rwx------  1 damiox root     40960 2000-08-05 15:38 VIDEOROM.BIN
drwx------ 82 damiox root     20480 2000-01-06 13:01 WINDOWS
-rwx------  1 damiox root        63 2000-09-02 18:02 WINDOWSWinHlp32.BMK
drwx------  2 damiox root      4096 2004-01-28 18:31 WUTemp
damiox@Home-Ubuntu-Main:/media/disk$

---

### Post by Damiox on 2008-05-30
the heck with it...ill just do ""another "" clean install on another hard drive ...(ive got like eight of them) mabey ill get the  next one right

---

### Post by pytheas22 on 2008-05-30
Root owned all of the files and no one else had read or write permissions; that's why you had to use sudo to see them.  Sorry I didn't respond sooner, but if you haven't already wiped the disk, this command should solve the access problem:
```

sudo chmod -R 777 /media/disk/*
```

or you could use chown to change ownership of the files to your user account, which is probably a better solution (a lot of Unix people get worked up about 777 permissions).  I'm not sure of the exact syntax but I think that it would look like:
```

sudo chown -R YOUR-NAME /media/disk/*
```

OR you could use the GUI to change permissions by running sudo nautilus and right clicking on the icon for the disk, and selecting properties, then the permissions tab.

---

### Post by Damiox on 2008-05-31
i did the final update and it fixed it....i did try to use the properties in nautilus but it didnt seem to make a difference...oh well....thanks anyway

---

