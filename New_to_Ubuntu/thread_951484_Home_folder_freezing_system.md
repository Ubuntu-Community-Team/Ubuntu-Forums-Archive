---
title: "Home folder freezing system"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by rafeg on 2008-10-18
Hi all,
         I'm having a problem with my home folder freezing the system when I open it.
I log in ok and can use the internet, e-mail etc., but when I open my home folder the whole system freezes!  Even "force quit" only goes round in a loop and I just have to re-boot.  Have tried using Linux Mint on another hard drive with the same results!
        Have used Ubuntu Hardy since its release with no problems until now.
If anyone can help it would be much appreciated.

---

### Post by t0p on 2008-10-18
Can you please clarify: Does this happen *only* when you try to open your home directory specifically?  Or when you use nautilus (the file manager) generally? ie, does this happen when you try to open /?

---

### Post by rafeg on 2008-10-18
It seems to be only when I click on the home folder icon.  If I go to "places" and click documents or pictures it opens and performs ok.  If I try "home" it opens but immediately
freezes.  After a few seconds the screen starts to grey out and nothing but a re-boot does any good.  I hope this makes things clearer and thanks for taking the time to help.

---

### Post by Xiong Chiamiov on 2008-10-18
Could you please [open a terminal]("http://www.psychocats.net/ubuntu/terminal") and enter this, and paste the results?
```

cd ~
ls -Al

```

---

### Post by rafeg on 2008-10-18
Here is the result.

robert@home:~$ cd ~
robert@home:~$ ls -Al
total 3852
drwxr-x---  2 root   admin    4096 2008-06-30 12:45 2008-06-30_12.41.04.818418.home.ful
drwx------  2 robert robert   4096 2008-10-12 13:20 .AbiSuite
-rw-r--r--  1 robert robert    284 2008-06-21 18:02 Acrobat Reader 5.0.desktop
-rw-r--r--  1 robert robert    861 2008-06-21 18:02 Acrobat Reader 5.0.lnk
drwx------  5 robert robert   4096 2008-10-15 19:24 .adobe
drwxr-xr-x  2 robert robert   4096 2008-06-23 19:37 .assistant
drwxr-xr-x  2 robert robert   4096 2008-10-15 20:16 .audacity1.3-robert
drwxr-xr-x  4 robert robert   4096 2008-10-15 20:16 .audacity-data
-rw-r--r--  1 robert robert 389471 2008-10-16 12:32 Bandboy.pdf
-rw-------  1 robert robert   6161 2008-10-18 19:57 .bash_history
-rw-r--r--  1 robert robert    220 2008-05-16 20:43 .bash_logout
-rw-r--r--  1 robert robert   2928 2008-05-16 20:43 .bashrc
drwx------  2 robert robert   4096 2008-05-21 07:34 .bogofilter
drwxr-xr-x  3 robert robert   4096 2008-05-16 20:44 .cache
-rwx------  1 robert robert  17725 2008-08-24 15:17 Calendar.ods
-rw-r--r--  1 robert robert 654802 2008-10-16 12:40 chilton.pdf
drwx------  3 robert robert   4096 2008-05-16 20:54 .compiz
drwxr-xr-x 10 robert robert   4096 2008-10-16 09:36 .config
drwxr-xr-x  2 robert robert   4096 2008-10-18 19:43 Desktop
-rw-------  1 robert robert     28 2008-10-18 19:08 .dmrc
drwxr-xr-x  2 robert robert   4096 2008-10-13 17:05 Documents
-rw-------  1 robert robert     16 2008-05-16 20:44 .esd_auth
-rw-r--r--  1 robert robert 378351 2008-10-16 12:32 etherial lady Vic Smeed ff power.pdf
drwx------  3 robert robert   4096 2008-10-13 16:16 evo_backup
drwxr-xr-x  8 robert robert   4096 2008-10-18 18:58 .evolution
lrwxrwxrwx  1 robert robert     26 2008-05-16 20:43 Examples -> /usr/share/example-content
drwxr-xr-x  4 robert robert   4096 2008-10-15 20:35 FF model downloads
drwxr-xr-x  2 robert robert   4096 2008-07-03 13:52 .fontconfig
drwx------  2 robert robert   4096 2008-10-13 19:55 .gcjwebplugin
drwx------  6 robert robert   4096 2008-10-18 19:08 .gconf
drwx------  2 robert robert   4096 2008-10-18 19:57 .gconfd
drwxr-xr-x 22 robert robert   4096 2008-10-16 12:45 .gimp-2.4
-rw-r-----  1 robert robert      0 2008-10-17 15:49 .gksu.lock
drwx------ 13 robert robert   4096 2008-10-18 19:01 .gnome2
drwx------  2 robert robert   4096 2008-09-17 06:34 .gnome2_private
drwx------  2 robert robert   4096 2008-10-18 19:08 .gnupg
drwxr-xr-x  2 robert robert   4096 2008-08-24 13:57 .gstreamer-0.10
-rw-r--r--  1 robert robert    112 2008-10-18 19:10 .gtk-bookmarks
dr-x------  2 robert robert      0 2008-10-18 19:08 .gvfs
drwxr-xr-x  2 robert robert   4096 2008-05-25 17:25 .helix
-rw-r--r--  1 robert robert  10120 2008-06-29 15:25 highflight.html
-rw-r--r--  1 root   root        0 2008-05-16 20:43 .hwdb
-rw-------  1 robert robert   1395 2008-10-18 19:08 .ICEauthority
drwxr-xr-x  2 robert robert   4096 2008-05-16 21:01 .icons
drwxr-x---  7 robert robert   4096 2008-06-16 18:01 .inkscape
drwxr-xr-x  3 robert robert   4096 2008-05-16 20:44 .local
drwx------  3 robert robert   4096 2008-05-18 20:49 .macromedia
-rw-r--r--  1 robert robert   3146 2008-05-25 17:26 .mailcap
-rw-r--r--  1 robert robert 231874 2008-10-16 12:32 Mamselle vic smeed.pdf
drwxr-xr-x  2 robert robert   4096 2008-08-24 14:21 Manchester Assembly 08
-rw-r--r--  1 robert robert 103012 2008-10-16 12:32 mini madcap.pdf
drwx------  5 robert robert   4096 2008-10-12 14:28 .mozilla
drwxrwxrwx  8 robert robert   4096 2008-10-12 14:14 mpark_14_10_08
drwxr-xr-x  2 robert robert   4096 2008-10-12 18:51 .mplayer
drwxr-xr-x  3 robert robert  12288 2008-10-18 12:58 .nautilus
drwx------  3 robert robert   4096 2008-10-18 19:10 .openoffice.org2
-rw-r--r--  1 robert robert 113321 2008-10-16 12:21 output.pdf
drwx------  2 robert robert   4096 2008-05-30 20:22 PDF
drwxr-xr-x  4 robert robert   4096 2008-10-15 16:43 Photos
drwxr-xr-x  4 robert robert   4096 2008-10-15 20:54 Pictures
-rw-r--r--  1 robert robert    586 2008-05-16 20:43 .profile
drwxr-xr-x  2 robert robert   4096 2008-05-18 20:50 .pulse
-rw-------  1 robert robert    256 2008-05-16 20:44 .pulse-cookie
drwx------  4 robert robert   4096 2008-07-17 14:16 .purple
drwxr-xr-x  2 robert robert   4096 2008-05-23 17:04 PWP-manual
drwxr-xr-x  2 robert robert   4096 2008-08-08 18:55 .qt
-rw-------  1 robert robert  13140 2008-10-18 19:10 .recently-used
-rw-r--r--  1 robert robert 272210 2008-10-18 19:10 .recently-used.xbel
-rw-r--r--  1 robert robert 577656 2008-06-29 15:57 Screenshot-1.jpg
-rw-r--r--  1 robert robert 156582 2008-06-30 18:59 Screenshot-2.png
-rw-r--r--  1 robert robert 165194 2008-06-30 19:00 Screenshot-3.png
-rw-r--r--  1 robert robert 180842 2008-06-30 18:59 Screenshot.png
drwxr-xr-x  2 robert robert   4096 2008-10-14 15:45 sharptools_files
-rw-r--r--  1 robert robert  27726 2008-10-14 15:45 sharptools.html
drwx------  2 robert robert   4096 2008-05-16 20:44 .ssh
drwxr-xr-x  2 robert robert   4096 2008-10-15 19:43 .stellarium
-rw-r--r--  1 robert robert      0 2008-05-16 20:47 .sudo_as_admin_successful
drwxr-xr-x  2 robert robert   4096 2008-05-16 21:01 .themes
drwx------  5 robert robert   4096 2008-06-09 07:46 .thumbnails
drwxr-xr-x  5 robert robert   4096 2008-10-12 19:38 .tomboy
-rw-r--r--  1 robert robert   5121 2008-10-12 20:54 .tomboy.log
drwxr-xr-x  2 robert robert   4096 2008-10-12 20:51 .update-manager-core
drwx------  2 robert robert   4096 2008-10-13 06:26 .update-notifier
-rw-r--r--  1 robert robert 250152 2008-10-16 21:47 vic smeed courtesan.pdf
drwxr-xr-x  3 robert robert   4096 2008-05-28 21:37 .vlc
drwxr-xr-x  2 robert robert   4096 2008-10-12 14:17 .vuescan
drwxr-xr-x  3 robert robert   4096 2008-10-12 14:16 VUESCAN
-rw-r--r--  1 robert robert     97 2008-05-25 13:48 .vuescanrc
drwxr-xr-x  2 robert robert   4096 2008-10-15 16:37 .wapi
drwxr-xr-x  4 robert robert   4096 2008-10-17 11:28 .wine
-rw-------  1 robert robert    115 2008-10-18 19:08 .Xauthority
-rw-r--r--  1 robert robert    146 2008-05-17 19:49 .xscreensaver-getimage.cache
-rw-r--r--  1 robert robert   3538 2008-10-18 19:20 .xsession-errors
robert@home:~$

---

