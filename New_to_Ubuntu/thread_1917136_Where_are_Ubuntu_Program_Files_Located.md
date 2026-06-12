---
title: "Where are Ubuntu Program Files Located?"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by chughes27 on 2012-01-29
Just something I was wondering about, where are the program files for Ubuntu software located in the file system?

Thanks!

---

### Post by doublewitt on 2012-01-29
Under FILE SYSTEM: /usr/share/applications

---

### Post by Cheesemill on 2012-01-29
Mostly in /bin or /usr/bin.
To find out where a particular application is installed you can use the which command, for example:
```
$ which firefox
/usr/bin/firefox
```Program settings are usually in a hidden folder in your home folder.

Applications are **NOT** in /usr/share/applications. Those are just the .desktop files which contain information about the applications (sort of like shortcuts in the Windows start menu).

---

### Post by chughes27 on 2012-01-29
Thanks Cheesemill, I found what I was looking for but it wasn't exactly what I expected. I thought it would be more like the Windows program files set up with organized folders and stuff. In the Ubuntu program files its just a mess.

---

### Post by Cheesemill on 2012-01-29
For more info:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

I think that when you get your head round it it actually makes more sense :)

---

### Post by mcduck on 2012-01-29
...actually the programs on Linux are not located on any single place, instead the program's files are distributed around the filesystem, each file going to different place based on that particular file's purpose.

So you'll find the main executable files in /usr/bin, icons in /usr/share/icons, libraries in /usr/share/lib, images in /usr/share/pixmpas, doucumentation in /usr/share/doc, launcher in /usr/share/applications and so on.

The rest of the files with no specific place in the filesystem go to /usr/share/*nameoftheapplication*.

This might seem strange if you are used to the Windows way of dumping all the program's files in one directory, but it's actually very convenient once you learn the few most important locations.

For example regardless of what the program is, I'll always know I can find it's executable in /usr/bin, and documentation in /usr/share/doc. I never need to browse around Program Files-folder trying to remember if that particular applications folder was named after the app, the company that developed it, or something else, and then browse around the apps folders looking for how it's developers decided to arrange the files.


Like Cheesemill said, you can use the "which" command to find a program's executable file (although yu can be pretty sure it's going to be in /usr/bin anyway), and  also you can use the "whereis" command to list all the locations where a program has files.

---

### Post by zzllxxllzz on 2013-03-11
Hello,

I saw this thread and it's very informative, but* how exactly* do you go about viewing these files? Specifically user/bin?

I am an absolute beginner and my understanding of the command prompt is limited. 

At best I know how to cut and paste codes.

---

### Post by Cheesemill on 2013-03-11
If you open nautilus (the file manager) and click on 'Computer' in the pane on the left it will take you to / (the root of the filesystem). From there you can navigate to wherever you want.

Also you mean /usr/bin, there is no such folder as /user (usr stands for Unix System Resources).

If you are using the terminal then just use the cd (change directory) command and the ls (list) command...
```
rob@raring:~$ cd /usr/bin
rob@raring:/usr/bin$ ls
total 224M
-rwxr-xr-x 1 root   root     39K Jan 17 07:03 [
lrwxrwxrwx 1 root   root       8 Jan 27 19:18 2to3 -> 2to3-2.7
-rwxr-xr-x 1 root   root      96 Mar  8 08:10 2to3-2.7
-rwxr-xr-x 1 root   root      96 Mar  8 07:08 2to3-3.3
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 411toppm
-rwxr-xr-x 1 root   root    104K Feb 10 17:43 a2p
-rwxr-xr-x 1 root   root     19K Feb 28 02:54 aconnect
-rwxr-xr-x 1 root   root    6.3K Oct  9 14:48 acpi_fakekey
-rwxr-xr-x 1 root   root     15K Feb 26 08:19 acpi_listen
-rwxr-xr-x 1 root   root    8.2K Feb 15 19:14 add-apt-repository
-rwxr-xr-x 1 root   root    6.2K Feb  4 20:49 addpart
-rwxr-xr-x 1 root   root     28K Feb 22 15:24 addr2line
-rwxr-xr-x 1 root   root     72K Feb 28 02:54 alsaloop
-rwxr-xr-x 1 root   root     64K Feb 28 02:54 alsamixer
-rwxr-xr-x 1 root   root     15K Feb 28 02:54 alsaucm
-rwxr-xr-x 1 root   root     19K Feb 28 02:54 amidi
-rwxr-xr-x 1 root   root     52K Feb 28 02:54 amixer
-rwxr-xr-x 1 root   root    2.7K Jun 18  2012 amuFormat.sh
lrwxrwxrwx 1 root   root      25 Feb 26 19:41 animate -> /etc/alternatives/animate
-rwxr-xr-x 1 root   root    6.2K Feb 25 19:54 animate.im6
-rwxr-xr-x 1 root   root    5.6K Feb  7 10:43 anytopnm
-rwxr-xr-x 1 root   root     276 Oct  1 17:12 apg
-rwxr-xr-x 1 root   root     31K Oct  1 17:12 apgbfm
-rwxr-xr-x 1 root   root     60K Feb 28 02:54 aplay
-rwxr-xr-x 1 root   root     19K Feb 28 02:54 aplaymidi
lrwxrwxrwx 1 root   root      30 Feb 26 19:53 appletviewer -> /etc/alternatives/appletviewer
-rwxr-xr-x 1 root   root    2.5K Mar  7 15:11 apport-bug
-rwxr-xr-x 1 root   root     13K Mar  7 15:15 apport-cli
lrwxrwxrwx 1 root   root      10 Mar  7 15:15 apport-collect -> apport-bug
-rwxr-xr-x 1 root   root    1.6K Mar  7 15:15 apport-unpack
-rwxr-xr-x 1 root   root     11K Aug  7  2012 appres
lrwxrwxrwx 1 root   root       6 Dec 16 17:10 apropos -> whatis
lrwxrwxrwx 1 root   root      21 Feb 26 19:53 apt -> /etc/alternatives/apt
lrwxrwxrwx 1 root   root      18 Feb 15 19:14 apt-add-repository -> add-apt-repository
-rwxr-xr-x 1 root   root    116K Mar  2 08:05 apt-cache
-rwxr-xr-x 1 root   root     23K Mar  2 08:05 apt-cdrom
-rwxr-xr-x 1 root   root     19K Mar  2 08:05 apt-config
-rwxr-xr-x 1 root   root    1.1K Dec 17 11:07 aptdcon
-rwxr-xr-x 1 root   root     23K Mar  2 08:05 apt-extracttemplates
-rwxr-xr-x 1 root   root    188K Mar  2 08:05 apt-ftparchive
-rwxr-xr-x 1 root   root    197K Mar  2 08:05 apt-get
lrwxrwxrwx 1 root   root      26 Feb 26 18:13 aptitude -> /etc/alternatives/aptitude
-rwxr-xr-x 1 root   root    1.9K Feb 26 08:43 aptitude-create-state-bundle
-rwxr-xr-x 1 root   root    4.4M Feb 26 08:44 aptitude-curses
-rwxr-xr-x 1 root   root    2.8K Feb 26 08:43 aptitude-run-state-bundle
-rwxr-xr-x 1 root   root    8.0K Mar  2 08:03 apt-key
-rwxr-xr-x 1 root   root     51K Mar  2 08:05 apt-mark
-rwxr-xr-x 1 root   root     31K Mar  2 08:05 apt-sortpkgs
-rwxr-xr-x 1 root   root     273 Jun 12  2012 apturl
-rwxr-xr-x 1 root   root    1.6K Jul 18  2012 apturl-gtk
-rwxr-xr-x 1 root   root     60K Feb 22 15:24 ar
-rwxr-xr-x 1 root   root     31K Jan 17 07:03 arch
lrwxrwxrwx 1 root   root       5 Feb 28 02:54 arecord -> aplay
-rwxr-xr-x 1 root   root     23K Feb 28 02:54 arecordmidi
-rwxr-xr-x 1 root   root    2.3M Dec 28 17:14 aria2c
-rwxr-xr-x 1 root   root     11K Mar  9 08:07 arm2hpdl
-rwsr-xr-x 1 root   root     19K Oct  3 00:36 arping
-rwxr-xr-x 1 root   root    337K Feb 22 15:24 as
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 asciitopgm
-rwxr-xr-x 1 root   root     15K Feb 28 02:54 aseqdump
-rwxr-xr-x 1 root   root     19K Feb 28 02:54 aseqnet
-rwxr-xr-x 1 root   root    160K Oct  1 17:13 aspell
-rwxr-xr-x 1 root   root    2.0K Oct  1 17:13 aspell-import
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 assistant -> qtchooser
-rwsr-sr-x 1 daemon daemon   55K Jun 11  2012 at
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 atktopbm
-rwxr-xr-x 1 root   root     11K Jan 10 10:10 atobm
-rwxr-xr-x 1 root   root    258K Oct 29  2010 AtomicParsley
lrwxrwxrwx 1 root   root       2 Jun 11  2012 atq -> at
lrwxrwxrwx 1 root   root       2 Jun 11  2012 atrm -> at
-rwxr-xr-x 1 root   root    6.4M Feb  7 12:31 audacity
-rwxr-xr-x 1 root   root     27K Oct  8 22:53 avahi-browse
lrwxrwxrwx 1 root   root      12 Oct  8 22:53 avahi-browse-domains -> avahi-browse
-rwxr-xr-x 1 root   root     19K Oct  8 22:53 avahi-publish
lrwxrwxrwx 1 root   root      13 Oct  8 22:53 avahi-publish-address -> avahi-publish
lrwxrwxrwx 1 root   root      13 Oct  8 22:53 avahi-publish-service -> avahi-publish
-rwxr-xr-x 1 root   root     15K Oct  8 22:53 avahi-resolve
lrwxrwxrwx 1 root   root      13 Oct  8 22:53 avahi-resolve-address -> avahi-resolve
lrwxrwxrwx 1 root   root      13 Oct  8 22:53 avahi-resolve-host-name -> avahi-resolve
-rwxr-xr-x 1 root   root     15K Oct  8 22:53 avahi-set-host-name
-rwxr-xr-x 1 root   root    109K Jan 24 14:22 avconv
-rwxr-xr-x 1 root   root     77K Jan 24 14:22 avplay
-rwxr-xr-x 1 root   root     44K Jan 24 14:22 avprobe
-rwxr-xr-x 1 root   root    100K Jan 24 14:22 avserver
lrwxrwxrwx 1 root   root      21 Feb 26 18:12 awk -> /etc/alternatives/awk
-rwxr-xr-x 1 root   root     33K Nov 27 19:08 axi-cache
-rwxr-xr-x 1 root   root    207K Jan 16 18:15 baobab
-rwxr-xr-x 1 root   root     35K Jan 17 07:03 base64
-rwxr-xr-x 1 root   root     27K Jan 17 07:03 basename
-rwxr-xr-x 1 root   root    6.9K Nov 29 15:05 bashbug
-rwxr-xr-x 1 root   root     152 Jun 11  2012 batch
-rwxr-xr-x 1 root   root     84K Feb  7 12:42 bc
-rwxr-xr-x 1 root   root     11K May 16  2012 bdftopcf
-rwxr-xr-x 1 root   root     11K May 16  2012 bdftruncate
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 bioradtopgm
-rwxr-xr-x 1 root   root     95K Jan 10 10:10 bitmap
-rwxr-xr-x 1 root   root     19K Dec  6 16:53 bluetooth-agent
-rwxr-xr-x 1 root   root     40K Mar  8 06:38 bluetooth-applet
-rwxr-xr-x 1 root   root     32K Mar  8 06:38 bluetooth-sendto
-rwxr-xr-x 1 root   root     32K Mar  8 06:38 bluetooth-wizard
-rwxr-xr-x 1 root   root    3.9K Dec  6 16:52 bluez-simple-agent
-rwxr-xr-x 1 root   root    2.9K Dec  6 16:52 bluez-simple-service
-rwxr-xr-x 1 root   root    3.4K Dec  6 16:52 bluez-test-adapter
-rwxr-xr-x 1 root   root    1.1K Dec  6 16:52 bluez-test-audio
-rwxr-xr-x 1 root   root    5.2K Dec  6 16:52 bluez-test-device
-rwxr-xr-x 1 root   root    1.6K Dec  6 16:52 bluez-test-discovery
-rwxr-xr-x 1 root   root    1.1K Dec  6 16:52 bluez-test-input
-rwxr-xr-x 1 root   root     913 Dec  6 16:52 bluez-test-manager
-rwxr-xr-x 1 root   root    1.2K Dec  6 16:52 bluez-test-network
-rwxr-xr-x 1 root   root    1.2K Dec  6 16:52 bluez-test-serial
-rwxr-xr-x 1 root   root    1.1K Dec  6 16:52 bluez-test-service
-rwxr-xr-x 1 root   root    4.0K Dec  6 16:52 bluez-test-telephony
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 bmptopnm
lrwxrwxrwx 1 root   root       8 Feb  7 10:43 bmptoppm -> bmptopnm
-rwxr-xr-x 1 root   root     11K Jan 10 10:10 bmtoa
-rwxr-xr-x 1 root   root    434K Jan 25 04:23 brasero
-rwxr-xr-x 1 root   root    167K Feb 22 23:48 brltty-ctb
-rwxr-xr-x 1 root   root    119K Feb 22 23:48 brltty-trtxt
-rwxr-xr-x 1 root   root    136K Feb 22 23:48 brltty-ttb
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 brushtopbm
-rwxr-xr-x 1 root   root     11K Jan  8 09:54 bsd-from
-rwxr-sr-x 1 root   tty      15K Jan  8 09:54 bsd-write
-rwxr-xr-x 1 root   root     27K Oct  1 21:29 btcflash
-rwxr-xr-x 2 root   root     36K Feb 10 17:42 c2ph
lrwxrwxrwx 1 root   root      21 Feb 26 19:30 c89 -> /etc/alternatives/c89
-rwxr-xr-x 1 root   root     428 May  7  2006 c89-gcc
lrwxrwxrwx 1 root   root      21 Feb 26 19:30 c99 -> /etc/alternatives/c99
-rwxr-xr-x 1 root   root     454 Apr 11  2011 c99-gcc
-rwxr-xr-x 1 root   root     59K Feb 18 03:25 cabextract
lrwxrwxrwx 1 root   root       4 Jan  8 09:54 cal -> ncal
-rwxr-xr-x 1 root   root     28K Jan  8 09:54 calendar
-rwxr-xr-x 1 root   root     24K Oct  8 17:36 calibrate_ppa
-rwxr-xr-x 1 root   root     11K Nov 29 18:55 canberra-gtk-play
-rwxr-xr-x 1 root   root     14K Feb 15 11:08 cancel
lrwxrwxrwx 1 root   root       3 Feb  8 15:34 captoinfo -> tic
-rwxr-xr-x 1 root   root    3.4K Feb  9 07:22 catchsegv
-rwxr-xr-x 1 root   root     31K Dec 16 17:10 catman
-rwxr-xr-x 1 root   root     853 Jan  8 10:38 cautious-launcher
lrwxrwxrwx 1 root   root      20 Feb 26 19:30 cc -> /etc/alternatives/cc
-rwxr-xr-x 1 root   root     27K Mar  4 09:15 cd-create-profile
-rwxr-xr-x 1 root   root     26K Mar  4 09:15 cd-fix-profile
lrwxrwxrwx 1 root   root       5 Oct  1 17:25 cdrecord -> wodim
-rwxr-xr-x 1 root   root     27K Feb 22 15:24 c++filt
lrwxrwxrwx 1 root   root      10 Nov 29 14:51 chacl -> /bin/chacl
-rwxr-sr-x 1 root   shadow   54K Jan  2 17:33 chage
-rwxr-xr-x 1 root   root    4.4K Jul 20  2011 chardet
lrwxrwxrwx 1 root   root       9 Nov 13 01:02 charmap -> gucharmap
-rwxr-xr-x 1 root   root     11K Jan  2 11:26 chattr
-rwxr-xr-x 1 root   root     59K Jan 17 07:03 chcon
-rwxr-xr-x 1 root   root     787 Mar  7 20:39 checkbox-qt
-rwxr-xr-x 1 root   root    2.8K Mar  1 10:34 check-language-support
-rwsr-xr-x 1 root   root     46K Jan  2 17:33 chfn
-rwxr-xr-x 1 root   root    3.6K Feb  4 20:49 chkdupexe
-rwxr-xr-x 1 root   root     19K Feb  4 20:49 chrt
-rwsr-xr-x 1 root   root     41K Jan  2 17:33 chsh
-rwxr-xr-x 1 root   root    106K Dec  6 16:53 ciptool
-rwxr-xr-x 1 root   root    116K Oct  9 05:25 ckbcomp
-rwxr-xr-x 1 root   root     24K Mar  4 19:32 ck-history
-rwxr-xr-x 1 root   root     11K Mar  4 19:32 ck-launch-session
-rwxr-xr-x 1 root   root     11K Mar  4 19:32 ck-list-sessions
-rwxr-xr-x 1 root   root     31K Jan 17 07:03 cksum
-rwxr-xr-x 1 root   root    6.2K Feb  8 15:34 clear
-rwxr-xr-x 1 root   root     11K Nov 29 15:05 clear_console
-rwxr-xr-x 1 root   root     43K Feb 25 10:36 cmp
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 cmuwmtopbm
-rwxr-xr-x 1 root   root     11K Feb 18 13:55 codepage
-rwxr-xr-x 1 root   root     11K Jan  8 09:54 col
-rwxr-xr-x 1 root   root     11K Jan  8 09:54 colcrt
-rwxr-xr-x 1 root   root     42K Mar  4 09:15 colormgr
-rwxr-xr-x 1 root   root     11K Jan  8 09:54 colrm
-rwxr-xr-x 1 root   root     15K Jan  8 09:54 column
lrwxrwxrwx 1 root   root       9 Oct  8 13:49 combinediff -> interdiff
-rwxr-xr-x 1 root   root     35K Jan 17 07:03 comm
-rwxr-xr-x 1 root   root     15K Mar  9 08:07 command2foo2lava-pjl
lrwxrwxrwx 1 root   root      25 Feb 26 19:41 compare -> /etc/alternatives/compare
-rwxr-xr-x 1 root   root    6.2K Feb 25 19:54 compare.im6
-rwxr-xr-x 1 root   root     15K Mar  8 10:50 compiz
-rwxr-xr-x 1 root   root    3.0K Mar  8 10:34 compiz-decorator
lrwxrwxrwx 1 root   root      11 Jan  8 10:38 compose -> run-mailcap
lrwxrwxrwx 1 root   root      27 Feb 26 19:41 composite -> /etc/alternatives/composite
-rwxr-xr-x 1 root   root    6.2K Feb 25 19:54 composite.im6
-rwxr-xr-x 1 root   root    7.1K Feb 10 17:42 config_data
lrwxrwxrwx 1 root   root      25 Feb 26 19:41 conjure -> /etc/alternatives/conjure
-rwxr-xr-x 1 root   root    6.2K Feb 25 19:54 conjure.im6
-rwxr-xr-x 1 root   root    395K May 21  2012 conky
lrwxrwxrwx 1 root   root      30 Feb 26 19:53 ControlPanel -> /etc/alternatives/ControlPanel
lrwxrwxrwx 1 root   root      25 Feb 26 19:41 convert -> /etc/alternatives/convert
-rwxr-xr-x 1 root   root    6.2K Feb 25 19:54 convert.im6
-rwxr-xr-x 1 root   root    7.4K Feb 10 17:42 corelist
-rwxr-xr-x 1 root   root    5.0K Feb 10 17:42 cpan
-rwxr-xr-x 1 root   root     22K Feb 10 17:42 cpan2dist
-rwxr-xr-x 1 root   root    3.4K Feb 10 17:42 cpanp
-rwxr-xr-x 1 root   root     545 Feb 10 17:42 cpanp-run-perl
lrwxrwxrwx 1 root   root       7 Dec 19 10:06 cpp -> cpp-4.7
-rwxr-xr-x 1 root   root    566K Mar  7 22:48 cpp-4.7
-rwxr-xr-x 1 root   root     794 Mar  1  2012 crc32
-rwxr-xr-x 1 root   root    4.6K Mar  7 20:30 c_rehash
-rwxr-sr-x 1 root   crontab  36K Feb  9 07:02 crontab
-rwxr-xr-x 1 root   root     47K Jan 17 07:03 csplit
lrwxrwxrwx 1 root   root       6 Dec 13 11:25 ctstat -> lnstat
-rwxr-xr-x 1 root   root     31K Jul 11  2012 cups-calibrate
-rwxr-xr-x 1 root   root     14K Feb 15 11:08 cupstestdsc
-rwxr-xr-x 1 root   root     55K Feb 15 11:08 cupstestppd
-rwxr-xr-x 1 root   root    147K Feb 12 17:15 curl
-rwxr-xr-x 1 root   root     43K Jan 17 07:03 cut
-rwxr-xr-x 1 root   root      45 Dec 13 16:34 cvlc
-rwxr-xr-x 1 root   root     15K Mar  7 02:47 cvt
-rwxr-xr-x 1 root   root     27K Jan  7 18:09 dbus-launch
-rwxr-xr-x 1 root   root     15K Jan  7 18:09 dbus-monitor
-rwxr-xr-x 1 root   root     19K Jan  7 18:09 dbus-send
-rwxr-xr-x 1 root   root     43K Feb  7 12:42 dc
-rwxr-xr-x 1 root   root     44K Feb 13 19:24 dconf
-rwxr-xr-x 1 root   root    124K Feb 13 19:24 dconf-editor
-rwxr-xr-x 1 root   root     11K Feb  4 20:49 ddate
-rwxr-xr-x 1 root   root     11K Feb 18 13:55 deallocvt
-rwxr-xr-x 1 root   root    2.8K Jan  8 10:11 debconf
-rwxr-xr-x 1 root   root     12K Jan  8 10:11 debconf-apt-progress
-rwxr-xr-x 1 root   root     608 Jan  8 10:11 debconf-communicate
-rwxr-xr-x 1 root   root    1.7K Jan  8 10:11 debconf-copydb
-rwxr-xr-x 1 root   root     647 Jan  8 10:11 debconf-escape
-rwxr-xr-x 1 root   root    3.0K Jan  8 10:11 debconf-set-selections
-rwxr-xr-x 1 root   root    1.8K Jan  8 10:11 debconf-show
-rwxr-xr-x 1 root   root    1.4K Oct  8 13:49 dehtmldiff
-rwxr-xr-x 1 root   root    166K Feb  4 21:13 deja-dup
-rwxr-xr-x 1 root   root     31K Feb  4 21:13 deja-dup-preferences
-rwxr-xr-x 1 root   root    6.2K Feb  4 20:49 delpart
-rwxr-xr-x 1 root   root     289 Mar  1 02:47 deluge
-rwxr-xr-x 1 root   root     297 Mar  1 02:47 deluge-gtk
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 designer -> qtchooser
lrwxrwxrwx 1 root   root      20 Dec  1 03:01 desktop-file-edit -> desktop-file-install
-rwxr-xr-x 1 root   root     73K Dec  1 03:01 desktop-file-install
-rwxr-xr-x 1 root   root     65K Dec  1 03:01 desktop-file-validate
-rwxr-xr-x 1 root   root    152K Oct  1 17:25 devdump
-rwxr-xr-x 1 root   root     23K Dec  6 16:53 dfutool
-rwxr-xr-x 1 root   root    526K Dec  4 19:47 dgawk
-rwxr-xr-x 1 root   root    2.5K Jun 17  2012 dh_bash-completion
-rwxr-xr-x 1 root   root    4.1K Dec  7  2011 dh_dkms
-rwxr-xr-x 1 root   root    9.5K Nov  7 21:44 dh_installxmlcatalogs
-rwxr-xr-x 1 root   root    2.0K Feb  1  2012 dh_numpy
-rwxr-xr-x 1 root   root     26K May  2  2012 dh_pycentral
-rwxr-xr-x 1 root   root     12K Jun 30  2012 dh_pysupport
-rwxr-xr-x 1 root   root     31K Jan 27 19:18 dh_python2
-rwxr-xr-x 1 root   root     23K Mar  6 10:36 dh_python3
-rwxr-xr-x 1 root   root    175K Oct 29 16:16 dialog
-rwxr-xr-x 1 root   root    115K Feb 25 10:36 diff
-rwxr-xr-x 1 root   root     55K Feb 25 10:36 diff3
-rwxr-xr-x 1 root   root     35K Feb 23 11:40 diffstat
-rwxr-xr-x 1 root   root    123K Jan 11 14:15 dig
-rwxr-xr-x 1 root   root     39K Jan 17 07:03 dircolors
lrwxrwxrwx 1 root   root      12 Mar  8 18:56 directomatic -> foomatic-rip
-rwxr-xr-x 1 root   root     27K Jan 17 07:03 dirname
-rwxr-xr-x 1 root   root     17K Nov 25  2006 dirsplit
lrwxrwxrwx 1 root   root      25 Feb 26 19:41 display -> /etc/alternatives/display
-rwxr-xr-x 1 root   root    6.2K Feb 25 19:54 display.im6
-rwxr-xr-x 1 root   root     15K Mar  7 23:17 dm-tool
-rwxr-xr-x 1 root   root    5.7K Jan 22 15:01 do-release-upgrade
-rwxr-sr-x 1 root   mail     15K Jan 24 20:51 dotlockfile
-rwxr-xr-x 1 root   root    252K Nov 29 15:13 dpkg
-rwxr-xr-x 1 root   root    120K Nov 29 15:13 dpkg-deb
-rwxr-xr-x 1 root   root    128K Nov 29 15:13 dpkg-divert
-rwxr-xr-x 1 root   root    6.6K Feb 14 03:11 dpkg-log-summary
-rwxr-xr-x 1 root   root    7.9K Nov 29 15:13 dpkg-maintscript-helper
-rwxr-xr-x 1 root   root    128K Nov 29 15:13 dpkg-query
-rwxr-xr-x 1 root   root     59K Nov 29 15:13 dpkg-split
-rwxr-xr-x 1 root   root     51K Nov 29 15:13 dpkg-statoverride
-rwxr-xr-x 1 root   root     67K Nov 29 15:13 dpkg-trigger
-rwxr-xr-x 1 root   root     24K Feb 10 17:42 dprofpp
-rwxr-xr-x 1 root   root     99K Jan 17 07:03 du
lrwxrwxrwx 1 root   root      13 Feb 18 13:55 dumpkeys -> /bin/dumpkeys
-rwxr-xr-x 1 root   root     56K Jan 23 21:06 duplicity
-rwxr-xr-x 1 root   root     23K Oct  1 21:29 dvd-ram-control
-rwxr-xr-x 1 root   root     63K Oct  1 21:29 dvd+rw-booktype
-rwxr-xr-x 1 root   root     39K Oct  1 21:29 dvd+rw-format
-rwxr-xr-x 1 root   root     47K Oct  1 21:29 dvd+rw-mediainfo
-rwxr-xr-x 1 root   root    253K Jan 16  2012 dvgrab
-rwxr-xr-x 1 root   root    1023 Jan 22 22:13 dvipdf
lrwxrwxrwx 1 root   root      11 Jan  8 10:38 edit -> run-mailcap
-rwxr-xr-x 1 root   root    2.1K Oct  8 13:49 editdiff
lrwxrwxrwx 1 root   root      24 Feb 26 18:12 editor -> /etc/alternatives/editor
-rwxr-xr-x 1 root   root     58K Aug  7  2012 editres
-rwxr-xr-x 1 root   root     31K Dec 24 09:49 eject
-rwxr-xr-x 1 root   root     31K Feb 22 15:24 elfedit
-rwxr-xr-x 1 root   root    267K Feb 27 22:42 empathy
-rwxr-xr-x 1 root   root     82K Feb 27 22:42 empathy-accounts
-rwxr-xr-x 1 root   root     52K Feb 27 22:42 empathy-debugger
-rwxr-xr-x 1 root   root     39K Feb 10 17:42 enc2xs
-rwxr-xr-x 1 root   root     15K Oct  1 23:20 enchant
-rwxr-xr-x 1 root   root     11K Oct  1 23:20 enchant-lsmod
-rwxr-xr-x 1 root   root     27K Jan 17 07:03 env
-rwxr-xr-x 1 root   root     35K Mar  7 16:02 envsubst
-rwxr-xr-x 1 root   root    500K Nov 12 21:38 eog
-rwxr-xr-x 1 root   root     638 Jan 22 22:13 eps2eps
-rwxr-xr-x 1 root   root    138K Feb  9 17:11 eqn
-rwxr-xr-x 1 root   root     11K Oct  5 17:43 esc-m
-rwxr-xr-x 1 root   root    467K Feb 22 14:03 evince
-rwxr-xr-x 1 root   root     47K Feb 22 14:03 evince-previewer
-rwxr-xr-x 1 root   root     15K Feb 22 14:03 evince-thumbnailer
lrwxrwxrwx 1 root   root      20 Feb 26 18:12 ex -> /etc/alternatives/ex
-rwxr-xr-x 1 root   root     31K Jan 17 07:03 expand
-rwxr-sr-x 1 root   shadow   23K Jan  2 17:33 expiry
-rwxr-xr-x 1 root   root     39K Jan 17 07:03 expr
lrwxrwxrwx 1 root   root      26 Feb 26 19:53 extcheck -> /etc/alternatives/extcheck
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 eyuvtoppm
-rwxr-xr-x 1 root   root     679 Feb 14 23:52 f2py
-rwxr-xr-x 1 root   root     682 Feb 14 23:52 f2py2.7
-rwxr-xr-x 1 root   root     87K Jan 17 07:03 factor
-rwxr-xr-x 1 root   root    8.2M Feb 18 15:24 FAHClient
-rwxr-xr-x 1 root   root    2.6K Feb 18 14:35 FAHControl
-rwxr-xr-x 1 root   root    1.2M Feb 18 15:24 FAHCoreWrapper
-rwxr-xr-x 1 root   root     19K Jan  2 17:33 faillog
-rwxr-xr-x 1 root   root     19K Nov 22 13:59 faked-sysv
-rwxr-xr-x 1 root   root     23K Nov 22 13:59 faked-tcp
lrwxrwxrwx 1 root   root      26 Feb 26 19:54 fakeroot -> /etc/alternatives/fakeroot
-rwxr-xr-x 1 root   root    3.9K Nov 22 13:59 fakeroot-sysv
-rwxr-xr-x 1 root   root    3.8K Nov 22 13:59 fakeroot-tcp
-rwxr-xr-x 1 root   root     15K Feb  4 20:49 fallocate
-rwxr-xr-x 1 root   root     15K Mar  6 07:19 fc-cache
-rwxr-xr-x 1 root   root     15K Mar  6 07:19 fc-cat
-rwxr-xr-x 1 root   root     11K Mar  6 07:19 fc-list
-rwxr-xr-x 1 root   root     11K Mar  6 07:19 fc-match
-rwxr-xr-x 1 root   root     11K Mar  6 07:19 fc-pattern
-rwxr-xr-x 1 root   root     11K Mar  6 07:19 fc-query
-rwxr-xr-x 1 root   root     11K Mar  6 07:19 fc-scan
-rwxr-xr-x 1 root   root    105K Jan 24 14:22 ffmpeg
lrwxrwxrwx 1 root   root       6 Jan 24 14:22 ffplay -> avplay
lrwxrwxrwx 1 root   root       7 Jan 24 14:22 ffprobe -> avprobe
lrwxrwxrwx 1 root   root       8 Jan 24 14:22 ffserver -> avserver
-rwxr-xr-x 1 root   root    103K Feb  7 10:43 fiascotopnm
-rwxr-xr-x 1 root   root     19K Mar  6 13:34 file
-rwxr-xr-x 1 root   root    492K Feb 22 13:52 file-roller
-rwxr-xr-x 1 root   root     40K Oct  8 13:49 filterdiff
-rwxr-xr-x 1 root   root    225K Oct 29 10:49 find
-rwxr-xr-x 1 root   root     24K Feb 10 17:42 find2perl
-rwxr-xr-x 1 root   root    4.5K Nov 26 09:07 findsmb
lrwxrwxrwx 1 root   root      25 Mar  8 15:48 firefox -> ../lib/firefox/firefox.sh
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 fitstopnm
-rwxr-xr-x 1 root   root    1.9K Oct  8 13:49 fixcvsdiff
-rwxr-xr-x 1 root   root    7.3K Mar  8 16:21 fix-qdf
lrwxrwxrwx 1 root   root       9 Oct  8 13:49 flipdiff -> interdiff
-rwxr-xr-x 1 root   root     15K Feb  4 20:49 flock
-rwxr-xr-x 1 root   root     71K May 11  2010 flvstreamer
-rwxr-xr-x 1 root   root     35K Jan 17 07:03 fmt
-rwxr-xr-x 1 root   root     31K Jan 17 07:03 fold
-rwxr-xr-x 1 root   root     311 Jan 22 22:13 font2c
-rwxr-xr-x 1 root   root     35K May 16  2012 fonttosfnt
-rwxr-xr-x 1 root   root     33K Mar  9 08:07 foo2hbpl2
-rwxr-xr-x 1 root   root     18K Mar  9 08:07 foo2hbpl2-wrapper
-rwxr-xr-x 1 root   root     36K Mar  9 08:07 foo2hiperc
-rwxr-xr-x 1 root   root     17K Mar  9 08:07 foo2hiperc-wrapper
-rwxr-xr-x 1 root   root     36K Mar  9 08:07 foo2hp
-rwxr-xr-x 1 root   root     19K Mar  9 08:07 foo2hp2600-wrapper
-rwxr-xr-x 1 root   root     33K Mar  9 08:07 foo2lava
-rwxr-xr-x 1 root   root     20K Mar  9 08:07 foo2lava-wrapper
-rwxr-xr-x 1 root   root     36K Mar  9 08:07 foo2oak
-rwxr-xr-x 1 root   root     18K Mar  9 08:07 foo2oak-wrapper
-rwxr-xr-x 1 root   root     36K Mar  9 08:07 foo2qpdl
-rwxr-xr-x 1 root   root     19K Mar  9 08:07 foo2qpdl-wrapper
-rwxr-xr-x 1 root   root     32K Mar  9 08:07 foo2slx
-rwxr-xr-x 1 root   root     18K Mar  9 08:07 foo2slx-wrapper
-rwxr-xr-x 1 root   root     32K Mar  9 08:07 foo2xqx
-rwxr-xr-x 1 root   root     18K Mar  9 08:07 foo2xqx-wrapper
-rwxr-xr-x 1 root   root     37K Mar  9 08:07 foo2zjs
-rwxr-xr-x 1 root   root    203K Mar  9 08:07 foo2zjs-icc2ps
-rwxr-xr-x 1 root   root    3.0K Mar  9 08:07 foo2zjs-pstops
-rwxr-xr-x 1 root   root     26K Mar  9 08:07 foo2zjs-wrapper
-rwxr-xr-x 1 root   root    301K Mar  8 18:56 foomatic-rip
-rwxr-xr-x 1 root   root     15K Jan  4 16:31 free
lrwxrwxrwx 1 root   root      22 Feb 26 18:15 from -> /etc/alternatives/from
-rwxr-xr-x 1 root   root     15K May 11  2012 fslsfonts
-rwxr-xr-x 1 root   root     15K May 11  2012 fstobdf
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 fstopgm
lrwxrwxrwx 1 root   root      21 Feb 26 18:15 ftp -> /etc/alternatives/ftp
-rwxr-xr-x 1 root   root     23K Dec 13 16:17 funzip
-rwxr-xr-x 1 root   root     14K Feb  7 10:43 g3topbm
-rwxr-xr-x 1 root   root    6.2K Sep 20 01:19 gamma4scanimage
-rwxr-xr-x 1 root   root    164K Dec  6 16:53 gatttool
-rwxr-xr-x 1 root   root    432K Dec  4 19:47 gawk
-rwxr-xr-x 1 root   root    204K Feb 28 06:49 gcalccmd
lrwxrwxrwx 1 root   root       7 Dec 19 10:06 gcc -> gcc-4.7
-rwxr-xr-x 1 root   root    566K Mar  7 22:54 gcc-4.7
-rwxr-xr-x 1 root   root     23K Mar  7 22:54 gcc-ar-4.7
-rwxr-xr-x 1 root   root     23K Mar  7 22:54 gcc-nm-4.7
-rwxr-xr-x 1 root   root     23K Mar  7 22:54 gcc-ranlib-4.7
-rwxr-xr-x 1 root   root     52K Jan 23 10:36 gconf-merge-tree
lrwxrwxrwx 1 root   root      27 Feb 26 19:31 gconftool -> /etc/alternatives/gconftool
-rwxr-xr-x 1 root   root     60K Jan 23 10:36 gconftool-2
-rwxr-xr-x 1 root   root    1.7K Jan  4  2012 gcore
lrwxrwxrwx 1 root   root       8 Dec 19 10:06 gcov -> gcov-4.7
-rwxr-xr-x 1 root   root    211K Mar  7 22:54 gcov-4.7
-rwxr-xr-x 1 root   root     11K Nov 12 10:53 gcr-viewer
-rwxr-xr-x 1 root   root    6.0M Dec 20 15:57 gdb
-rwxr-xr-x 1 root   root     35K Feb 20 18:47 gdbus
-rwxr-xr-x 1 root   root    9.1K Nov  6 18:12 gdialog
-rwxr-xr-x 1 root   root     15K Feb 12 23:29 gdmflexiserver
-rwxr-xr-x 1 root   root     15K Feb 12 23:29 gdm-screenshot
-rwxr-xr-x 1 root   root    661K Nov 13 00:37 gedit
lrwxrwxrwx 1 root   root       8 Feb  7 10:43 gemtopbm -> gemtopnm
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 gemtopnm
-rwxr-xr-x 1 root   root     23K Feb  9 07:26 gencat
-rwxr-xr-x 1 root   root    587K Oct  1 17:25 genisoimage
-rwxr-xr-x 1 root   root    2.6K Dec 11 17:34 gen-preseed
lrwxrwxrwx 1 root   root       3 Feb  9 17:11 geqn -> eqn
lrwxrwxrwx 1 root   root      11 Apr 30  2012 GET -> lwp-request
-rwxr-xr-x 1 root   root     23K Feb  9 07:26 getconf
-rwxr-xr-x 1 root   root    6.1K Oct  1 17:25 geteltorito
-rwxr-xr-x 1 root   root     28K Feb  9 07:26 getent
lrwxrwxrwx 1 root   root      12 Nov 29 14:51 getfacl -> /bin/getfacl
-rwxr-xr-x 1 root   root    6.1K Feb 18 13:46 gethostip
-rwxr-xr-x 1 root   root    341K Jun 29  2012 get_iplayer
lrwxrwxrwx 1 root   root      11 Jun 29  2012 get-iplayer -> get_iplayer
-rwxr-xr-x 1 root   root     143 Jun 27  2012 get_iplayer_web_pvr
lrwxrwxrwx 1 root   root      19 Jun 29  2012 get-iplayer-web-pvr -> get_iplayer_web_pvr
-rwxr-xr-x 1 root   root     11K Feb 18 13:55 getkeycodes
-rwxr-xr-x 1 root   root     15K Feb  4 20:49 getopt
-rwxr-xr-x 1 root   root     35K Mar  7 16:02 gettext
-rwxr-xr-x 1 root   root     42K Mar  7 16:02 gettextize
-rwxr-xr-x 1 root   root    4.6K Mar  7 16:02 gettext.sh
-rwxr-xr-x 1 root   root     14K Mar  9 08:07 getweb
-rwxr-xr-x 1 root   root     333 Jun 14  2012 gftp
-rwxr-xr-x 1 root   root    315K Jun 14  2012 gftp-gtk
-rwxr-xr-x 1 root   root    198K Jun 14  2012 gftp-text
lrwxrwxrwx 1 root   root       2 Jan 22 22:13 ghostscript -> gs
-rwxr-xr-x 1 root   root     19K Feb  7 10:43 giftopnm
-rwxr-xr-x 1 root   root    151K Oct 29 03:08 gigolo
lrwxrwxrwx 1 root   root       8 Jan 15 15:31 gimp -> gimp-2.8
-rwxr-xr-x 1 root   root    5.5M Jan 15 15:32 gimp-2.8
lrwxrwxrwx 1 root   root      16 Jan 15 15:31 gimp-console -> gimp-console-2.8
-rwxr-xr-x 1 root   root    2.5M Jan 15 15:32 gimp-console-2.8
-rwxr-xr-x 1 root   root     40K Dec  8 10:26 ginstall-info
lrwxrwxrwx 1 root   root      49 Feb 20 18:46 gio-querymodules -> ../lib/x86_64-linux-gnu/glib-2.0/gio-querymodules
-rwxr-xr-x 1 root   root     15K Mar  9 08:07 gipddecode
lrwxrwxrwx 1 root   root      11 Oct  3 01:21 gjs -> gjs-console
-rwxr-xr-x 1 root   root     11K Oct  3 01:21 gjs-console
-rwxr-xr-x 1 root   root     11K Sep 28 02:17 gkbd-keyboard-display
-rwxr-xr-x 1 root   root     28K Oct  2 10:47 gksu
lrwxrwxrwx 1 root   root       4 Oct  2 10:47 gksudo -> gksu
-rwxr-xr-x 1 root   root     15K Nov 29 14:11 gksu-properties
lrwxrwxrwx 1 root   root      55 Feb 20 18:46 glib-compile-resources -> ../lib/x86_64-linux-gnu/glib-2.0/glib-compile-resources
lrwxrwxrwx 1 root   root      53 Feb 20 18:46 glib-compile-schemas -> ../lib/x86_64-linux-gnu/glib-2.0/glib-compile-schemas
-rwxr-xr-x 1 root   root     11K Feb  4  2011 glxdemo
-rwxr-xr-x 1 root   root     23K Feb  4  2011 glxgears
-rwxr-xr-x 1 root   root     15K Feb  4  2011 glxheads
-rwxr-xr-x 1 root   root     27K Feb  4  2011 glxinfo
-rwxr-xr-x 1 root   root    390K Feb 28 06:49 gnome-calculator
lrwxrwxrwx 1 root   root       9 Nov 13 01:02 gnome-character-map -> gucharmap
-rwxr-xr-x 1 root   root    489K Nov 12 20:57 gnome-contacts
-rwxr-xr-x 1 root   root     63K Feb 13 11:11 gnome-control-center
-rwxr-xr-x 1 root   root     28K Nov 15 02:44 gnome-disk-image-mounter
-rwxr-xr-x 1 root   root    244K Nov 15 02:44 gnome-disks
-rwxr-xr-x 1 root   root     23K Sep 28 02:21 gnome-file-share-properties
-rwxr-xr-x 1 root   root     65K Feb 24 16:32 gnome-font-viewer
lrwxrwxrwx 1 root   root       4 Nov 12 21:50 gnome-help -> yelp
lrwxrwxrwx 1 root   root      15 Mar  7 11:53 gnome-keyring -> gnome-keyring-3
-rwxr-xr-x 1 root   root     15K Mar  7 11:53 gnome-keyring-3
-rwxr-xr-x 1 root   root    944K Mar  7 11:53 gnome-keyring-daemon
-rwxr-xr-x 1 root   root    1.5K Mar  1 10:34 gnome-language-selector
-rwxr-xr-x 1 root   root     11K Sep  7  2012 gnome-open
-rwxr-xr-x 1 root   root     64K Mar  8 06:27 gnome-power-statistics
-rwxr-xr-x 1 root   root    130K Feb  9 14:53 gnome-screensaver
-rwxr-xr-x 1 root   root     15K Feb  9 14:53 gnome-screensaver-command
-rwxr-xr-x 1 root   root     82K Nov 13 01:13 gnome-screenshot
-rwxr-xr-x 1 root   root    243K Dec 27 23:52 gnome-session
-rwxr-xr-x 1 root   root     65K Dec 27 23:52 gnome-session-properties
-rwxr-xr-x 1 root   root     11K Dec 27 23:52 gnome-session-quit
lrwxrwxrwx 1 root   root      50 Feb 13 19:18 gnome-settings-daemon -> ../lib/gnome-settings-daemon/gnome-settings-daemon
-rwxr-xr-x 1 root   root     15K Mar  4 00:38 gnome-shell
-rwxr-xr-x 1 root   root     445 Mar  4 00:38 gnome-shell-extension-prefs
-rwxr-xr-x 1 root   root    6.1K Mar  4 00:38 gnome-shell-extension-tool
-rwxr-xr-x 1 root   root    9.8K Mar  4 00:38 gnome-shell-perf-tool
-rwxr-xr-x 1 root   root    143K Feb 13 11:11 gnome-sound-applet
-rwxr-xr-x 1 root   root    119K Nov 13 00:17 gnome-system-log
-rwxr-xr-x 1 root   root    276K Feb 21 11:32 gnome-system-monitor
-rwxr-xr-x 1 root   root    295K Feb 11 20:24 gnome-terminal
-rwxr-xr-x 1 root   root    1.4K Feb 11 17:28 gnome-terminal.wrapper
lrwxrwxrwx 1 root   root      35 Feb 26 19:31 gnome-text-editor -> /etc/alternatives/gnome-text-editor
-rwxr-xr-x 1 root   root     23K Feb 24 16:32 gnome-thumbnail-font
-rwxr-xr-x 1 root   root    2.8K Oct 29 17:06 gnome-tweak-tool
lrwxrwxrwx 1 root   root      35 Feb 26 19:31 gnome-www-browser -> /etc/alternatives/gnome-www-browser
lrwxrwxrwx 1 root   root       7 Feb 22 15:25 gold -> ld.gold
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 gouldtoppm
-rwxr-xr-x 1 root   root      42 Dec  7  2011 gparted-pkexec
-rwsr-xr-x 1 root   root     67K Jan  2 17:33 gpasswd
-rwxr-xr-x 1 root   root    969K Jan  8 10:57 gpg
-rwxr-xr-x 1 root   root     55K Jan  8 10:57 gpgsplit
-rwxr-xr-x 1 root   root    352K Jan  8 10:57 gpgv
-rwxr-xr-x 1 root   root    3.3K Jan  8 10:57 gpg-zip
lrwxrwxrwx 1 root   root       3 Feb  9 17:11 gpic -> pic
-rwxr-xr-x 1 root   root     93K Feb 22 15:24 gprof
lrwxrwxrwx 1 root   root      10 Oct  8 13:49 grepdiff -> filterdiff
-rwxr-xr-x 1 root   root     15K Feb 20 18:47 gresource
-rwxr-xr-x 1 root   root     78K Feb  9 17:11 groff
-rwxr-xr-x 1 root   root    9.6K Feb  9 17:11 grog
-rwxr-xr-x 1 root   root    131K Feb  9 17:11 grops
-rwxr-xr-x 1 root   root     90K Feb  9 17:11 grotty
-rwxr-xr-x 1 root   root     31K Jan 17 07:03 groups
-rwxr-xr-x 1 root   root    119K Oct  1 21:29 growisofs
-rwxr-xr-x 1 root   root     72K Jan 25 00:57 grub-editenv
-rwxr-xr-x 1 root   root    650K Jan 25 00:57 grub-fstest
-rwxr-xr-x 1 root   root    1.7K Jan 25 00:56 grub-kbdcomp
-rwxr-xr-x 1 root   root     48K Jan 25 00:57 grub-menulst2cfg
-rwxr-xr-x 1 root   root     92K Jan 25 00:57 grub-mkfont
-rwxr-xr-x 1 root   root    135K Jan 25 00:57 grub-mkimage
-rwxr-xr-x 1 root   root     72K Jan 25 00:57 grub-mklayout
-rwxr-xr-x 1 root   root     80K Jan 25 00:57 grub-mkpasswd-pbkdf2
-rwxr-xr-x 1 root   root    208K Jan 25 00:57 grub-mkrelpath
-rwxr-xr-x 1 root   root     14K Jan 25 00:56 grub-mkrescue
-rwxr-xr-x 1 root   root    6.3K Jan 25 00:56 grub-mkstandalone
-rwxr-xr-x 1 root   root    477K Jan 25 00:57 grub-mount
lrwxrwxrwx 1 root   root      34 Jan 25 00:57 grub-ntldr-img -> ../lib/grub/i386-pc/grub-ntldr-img
-rwxr-xr-x 1 root   root     95K Jan 25 00:57 grub-script-check
-rwxr-xr-x 1 root   root     11K Jan 22 22:13 gs
-rwxr-xr-x 1 root   root     350 Jan 22 22:13 gsbj
-rwxr-xr-x 1 root   root     352 Jan 22 22:13 gsdj
-rwxr-xr-x 1 root   root     352 Jan 22 22:13 gsdj500
-rwxr-xr-x 1 root   root     19K Feb 20 18:47 gsettings
-rwxr-xr-x 1 root   root     23K Jan 23 10:36 gsettings-data-convert
-rwxr-xr-x 1 root   root     41K Jan 23 10:35 gsettings-schema-convert
-rwxr-xr-x 1 root   root     353 Jan 22 22:13 gslj
-rwxr-xr-x 1 root   root     350 Jan 22 22:13 gslp
-rwxr-xr-x 1 root   root     277 Jan 22 22:13 gsnd
-rwxr-xr-x 1 root   root     23K Dec 11 08:32 gst-discoverer-0.10
-rwxr-xr-x 1 root   root     23K Jan  9 00:50 gst-discoverer-1.0
-rwxr-xr-x 1 root   root    3.1K Jun 26  2012 gst-feedback-0.10
-rwxr-xr-x 1 root   root     40K Jun 26  2012 gst-inspect-0.10
-rwxr-xr-x 1 root   root     40K Jan 29 09:56 gst-inspect-1.0
-rwxr-xr-x 1 root   root    1020 Feb 13 10:38 gst-install
-rwxr-xr-x 1 root   root     32K Jun 26  2012 gst-launch-0.10
-rwxr-xr-x 1 root   root     32K Jan 29 09:56 gst-launch-1.0
lrwxrwxrwx 1 root   root      41 Feb 26 19:31 gstreamer-codec-install -> /etc/alternatives/gstreamer-codec-install
-rwxr-xr-x 1 root   root     11K Jun 26  2012 gst-typefind-0.10
-rwxr-xr-x 1 root   root     11K Jan 29 09:56 gst-typefind-1.0
-rwxr-xr-x 1 root   root    1.7K Dec 11 08:32 gst-visualise-0.10
-rwxr-xr-x 1 root   root     23K Jun 26  2012 gst-xmlinspect-0.10
-rwxr-xr-x 1 root   root     32K Jun 26  2012 gst-xmllaunch-0.10
lrwxrwxrwx 1 root   root       3 Feb  9 17:11 gtbl -> tbl
-rwxr-xr-x 1 root   root     15K Mar  7 02:47 gtf
-rwxr-xr-x 1 root   root     11K Feb  4 14:35 gtk-launch
lrwxrwxrwx 1 root   root      57 Feb 25 18:08 gtk-update-icon-cache -> ../lib/x86_64-linux-gnu/libgtk2.0-0/gtk-update-icon-cache
lrwxrwxrwx 1 root   root      60 Feb  4 14:34 gtk-update-icon-cache-3.0 -> ../lib/x86_64-linux-gnu/libgtk-3-0/gtk-update-icon-cache-3.0
-rwxr-xr-x 1 root   root    163K Mar  8 10:50 gtk-window-decorator
-rwxr-xr-x 1 root   root     73K Nov 13 01:02 gucharmap
-rwxr-xr-x 1 root   root    2.7K Feb 28 07:52 guild
-rwxr-xr-x 1 root   root     11K Mar  6 11:59 gvfs-cat
-rwxr-xr-x 1 root   root     11K Mar  6 11:59 gvfs-copy
-rwxr-xr-x 1 root   root     15K Mar  6 11:59 gvfs-info
-rwxr-xr-x 1 root   root     884 Mar  6 11:58 gvfs-less
-rwxr-xr-x 1 root   root     15K Mar  6 11:59 gvfs-ls
-rwxr-xr-x 1 root   root     11K Mar  6 11:59 gvfs-mime
-rwxr-xr-x 1 root   root     11K Mar  6 11:59 gvfs-mkdir
-rwxr-xr-x 1 root   root     11K Mar  6 11:59 gvfs-monitor-dir
-rwxr-xr-x 1 root   root     11K Mar  6 11:59 gvfs-monitor-file
-rwxr-xr-x 1 root   root     27K Mar  6 11:59 gvfs-mount
-rwxr-xr-x 1 root   root     11K Mar  6 11:59 gvfs-move
-rwxr-xr-x 1 root   root     11K Mar  6 11:59 gvfs-open
-rwxr-xr-x 1 root   root     11K Mar  6 11:59 gvfs-rename
-rwxr-xr-x 1 root   root     11K Mar  6 11:59 gvfs-rm
-rwxr-xr-x 1 root   root     11K Mar  6 11:59 gvfs-save
-rwxr-xr-x 1 root   root     11K Mar  6 11:59 gvfs-set-attribute
-rwxr-xr-x 1 root   root     11K Mar  6 11:59 gvfs-trash
-rwxr-xr-x 1 root   root     11K Mar  6 11:59 gvfs-tree
-rwxr-xr-x 1 root   root    121K Jan 14 16:17 gwibber
-rwxr-xr-x 1 root   root     27K Jan 14 16:17 gwibber-poster
-rwxr-xr-x 1 root   root     15K Jan 14 16:17 gwibber-preferences
-rwxr-xr-x 1 root   root    2.5K Jan 14 16:21 gwibber-service
-rwxr-xr-x 1 root   root     28K Feb 10 17:42 h2ph
-rwxr-xr-x 1 root   root     60K Feb 10 17:42 h2xs
-rwxr-xr-x 1 root   root     15K Dec 17 05:07 hardening-check
-rwxr-xr-x 1 root   root     19K Mar  9 08:07 hbpldecode
-rwxr-xr-x 1 root   root    108K Dec  6 16:53 hcitool
lrwxrwxrwx 1 root   root       7 Jan  8 09:54 hd -> hexdump
-rwxr-xr-x 1 root   root     39K Jan 17 07:03 head
lrwxrwxrwx 1 root   root      11 Apr 30  2012 HEAD -> lwp-request
-rwxr-xr-x 1 root   root    2.5K Nov 22 21:08 helpztags
-rwxr-xr-x 1 root   root     27K Jan  8 09:54 hexdump
-rwxr-xr-x 1 root   root     19K Mar  9 08:07 hipercdecode
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 hipstopgm
-rwxr-xr-x 1 root   root    111K Jan 11 14:15 host
-rwxr-xr-x 1 root   root     27K Jan 17 07:03 hostid
lrwxrwxrwx 1 root   root      23 Mar  9 07:47 hp-align -> ../share/hplip/align.py
lrwxrwxrwx 1 root   root      23 Mar  9 07:47 hp-check -> ../share/hplip/check.py
lrwxrwxrwx 1 root   root      30 Mar  9 07:47 hp-check-plugin -> ../share/hplip/check-plugin.py
lrwxrwxrwx 1 root   root      23 Mar  9 07:47 hp-clean -> ../share/hplip/clean.py
lrwxrwxrwx 1 root   root      26 Mar  9 07:47 hp-colorcal -> ../share/hplip/colorcal.py
lrwxrwxrwx 1 root   root      36 Mar  9 07:47 hp-config_usb_printer -> ../share/hplip/config_usb_printer.py
lrwxrwxrwx 1 root   root      32 Mar  9 07:47 hp-devicesettings -> ../share/hplip/devicesettings.py
lrwxrwxrwx 1 root   root      33 Mar  9 07:47 hp-diagnose_plugin -> ../share/hplip/diagnose_plugin.py
lrwxrwxrwx 1 root   root      33 Mar  9 07:47 hp-diagnose_queues -> ../share/hplip/diagnose_queues.py
lrwxrwxrwx 1 root   root      24 Mar  9 07:47 hp-doctor -> ../share/hplip/doctor.py
lrwxrwxrwx 1 root   root      21 Mar  9 07:47 hp-fab -> ../share/hplip/fab.py
lrwxrwxrwx 1 root   root      26 Mar  9 07:47 hp-faxsetup -> ../share/hplip/faxsetup.py
lrwxrwxrwx 1 root   root      26 Mar  9 07:47 hp-firmware -> ../share/hplip/firmware.py
lrwxrwxrwx 1 root   root      23 Mar  9 07:47 hp-hpdio -> ../share/hplip/hpdio.py
-rwxr-xr-x 1 root   root    558K Mar  9 07:47 hpijs
lrwxrwxrwx 1 root   root      22 Mar  9 07:47 hp-info -> ../share/hplip/info.py
lrwxrwxrwx 1 root   root      24 Mar  9 07:47 hp-levels -> ../share/hplip/levels.py
lrwxrwxrwx 1 root   root      29 Mar  9 07:47 hp-linefeedcal -> ../share/hplip/linefeedcal.py
lrwxrwxrwx 1 root   root      28 Mar  9 07:47 hp-logcapture -> ../share/hplip/logcapture.py
lrwxrwxrwx 1 root   root      28 Mar  9 07:47 hp-makecopies -> ../share/hplip/makecopies.py
lrwxrwxrwx 1 root   root      25 Mar  9 07:47 hp-makeuri -> ../share/hplip/makeuri.py
-rwxr-xr-x 1 root   root     19K Mar  9 07:47 hp-mkuri
lrwxrwxrwx 1 root   root      27 Mar  9 07:47 hp-pkservice -> ../share/hplip/pkservice.py
lrwxrwxrwx 1 root   root      24 Mar  9 07:47 hp-plugin -> ../share/hplip/plugin.py
-rwxr-xr-x 1 root   root     702 Mar  9 07:47 hp-plugin-ubuntu
lrwxrwxrwx 1 root   root      24 Mar  9 07:47 hp-pqdiag -> ../share/hplip/pqdiag.py
lrwxrwxrwx 1 root   root      23 Mar  9 07:47 hp-print -> ../share/hplip/print.py
lrwxrwxrwx 1 root   root      31 Mar  9 07:47 hp-printsettings -> ../share/hplip/printsettings.py
lrwxrwxrwx 1 root   root      23 Mar  9 07:47 hp-probe -> ../share/hplip/probe.py
lrwxrwxrwx 1 root   root      23 Mar  9 07:47 hp-query -> ../share/hplip/query.py
lrwxrwxrwx 1 root   root      22 Mar  9 07:47 hp-scan -> ../share/hplip/scan.py
lrwxrwxrwx 1 root   root      25 Mar  9 07:47 hp-sendfax -> ../share/hplip/sendfax.py
lrwxrwxrwx 1 root   root      23 Mar  9 07:47 hp-setup -> ../share/hplip/setup.py
lrwxrwxrwx 1 root   root      25 Mar  9 07:47 hp-systray -> ../share/hplip/systray.py
lrwxrwxrwx 1 root   root      26 Mar  9 07:47 hp-testpage -> ../share/hplip/testpage.py
lrwxrwxrwx 1 root   root      26 Mar  9 07:47 hp-timedate -> ../share/hplip/timedate.py
lrwxrwxrwx 1 root   root      25 Mar  9 07:47 hp-toolbox -> ../share/hplip/toolbox.py
lrwxrwxrwx 1 root   root      24 Mar  9 07:47 hp-unload -> ../share/hplip/unload.py
lrwxrwxrwx 1 root   root      25 Mar  9 07:47 hp-upgrade -> ../share/hplip/upgrade.py
lrwxrwxrwx 1 root   root      28 Mar  9 07:47 hp-wificonfig -> ../share/hplip/wificonfig.py
-rwxr-xr-x 1 root   root    124K Dec  2 11:35 htop
-rwxr-xr-x 1 root   root     11K Jan 30 11:31 hybrid-detect
lrwxrwxrwx 1 root   root       7 Feb  4 20:49 i386 -> setarch
-rwxr-xr-x 1 root   root    169K Nov 22 20:47 ibus-daemon
-rwxr-xr-x 1 root   root    1.2K Nov 22 20:47 ibus-setup
-rwxr-xr-x 1 root   root    1.2K Mar  2 08:43 ibus-table-createdb
-rwxr-xr-x 1 root   root     27K Dec  4 02:36 iceauth
-rwxr-xr-x 1 root   root     45K Jan 10 10:10 ico
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 icontopbm
-rwxr-xr-x 1 root   root     63K Feb  9 07:26 iconv
-rwxr-xr-x 1 root   root     35K Jan 17 07:03 id
-rwxr-xr-x 1 root   root     52K Oct 16  2010 id3v2
lrwxrwxrwx 1 root   root      26 Feb 26 19:41 identify -> /etc/alternatives/identify
-rwxr-xr-x 1 root   root    6.2K Feb 25 19:54 identify.im6
lrwxrwxrwx 1 root   root      22 Feb 26 19:53 idlj -> /etc/alternatives/idlj
-rwxr-xr-x 1 root   root     19K Feb 28 02:54 iecset
-rwxr-xr-x 1 root   root    3.2K Dec  4 19:47 igawk
-rwxr-xr-x 1 root   root     31K Oct  8 17:43 ijs_pxljr
-rwxr-xr-x 1 root   root     59K Feb  7 10:43 ilbmtoppm
-rwxr-xr-x 1 root   root    9.7K Feb 27 20:51 im-config
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 imgtoppm
-rwxr-xr-x 1 root   root     985 Feb 27 17:34 im-launch
lrwxrwxrwx 1 root   root      24 Feb 26 19:41 import -> /etc/alternatives/import
-rwxr-xr-x 1 root   root    6.2K Feb 25 19:54 import.im6
-rwxr-xr-x 1 root   root    178K Dec  8 10:26 info
lrwxrwxrwx 1 root   root      29 Feb 26 18:15 infobrowser -> /etc/alternatives/infobrowser
-rwxr-xr-x 1 root   root     51K Feb  8 15:34 infocmp
-rwxr-xr-x 1 root   root     21K Dec  8 10:26 infokey
lrwxrwxrwx 1 root   root       3 Feb  8 15:34 infotocap -> tic
-rwxr-xr-x 1 root   root     13M Feb 27 15:01 inkscape
-rwxr-xr-x 1 root   root     11M Feb 27 15:01 inkview
-rwxr-xr-x 1 root   root     22K Jun  9  2012 inputattach
-rwxr-xr-x 1 root   root    116K Jan 17 07:03 install
-rwxr-xr-x 1 root   root    1.2K Dec  8 10:26 install-info
-rwxr-xr-x 1 root   root    264K Dec  3  2011 install-menu
-rwxr-xr-x 1 root   root      95 Mar  8 15:09 install-printerdriver
-rwxr-xr-x 1 root   root    4.3K Feb 10 17:42 instmodsh
-rwxr-xr-x 1 root   root     72K Sep 12 17:04 intel_audio_dump
-rwxr-xr-x 1 root   root     16K Sep 12 17:04 intel_backlight
-rwxr-xr-x 1 root   root     11K Sep 12 17:04 intel_bios_dumper
-rwxr-xr-x 1 root   root     23K Sep 12 17:04 intel_bios_reader
-rwxr-xr-x 1 root   root     16K Sep 12 17:04 intel_disable_clock_gating
-rwxr-xr-x 1 root   root     16K Sep 12 17:04 intel_dpio_read
-rwxr-xr-x 1 root   root     16K Sep 12 17:04 intel_dpio_write
-rwxr-xr-x 1 root   root     31K Sep 12 17:04 intel_error_decode
-rwxr-xr-x 1 root   root     16K Sep 12 17:04 intel_forcewaked
-rwxr-xr-x 1 root   root     793 Sep 12 17:04 intel_gpu_abrt
-rwxr-xr-x 1 root   root     16K Sep 12 17:04 intel_gpu_time
-rwxr-xr-x 1 root   root     40K Sep 12 17:04 intel_gpu_top
-rwxr-xr-x 1 root   root     11K Sep 12 17:04 intel_gtt
-rwxr-xr-x 1 root   root     23K Sep 12 17:04 intel_l3_parity
-rwxr-xr-x 1 root   root     20K Sep 12 17:04 intel_reg_checker
-rwxr-xr-x 1 root   root     64K Sep 12 17:04 intel_reg_dumper
-rwxr-xr-x 1 root   root     16K Sep 12 17:04 intel_reg_read
-rwxr-xr-x 1 root   root     16K Sep 12 17:04 intel_reg_snapshot
-rwxr-xr-x 1 root   root     16K Sep 12 17:04 intel_reg_write
-rwxr-xr-x 1 root   root     36K Sep 12 17:04 intel_sprite_on
-rwxr-xr-x 1 root   root     11K Sep 12 17:04 intel_stepping
-rwxr-xr-x 1 root   root     31K Sep 12 17:04 intel_upload_blit_large
-rwxr-xr-x 1 root   root     31K Sep 12 17:04 intel_upload_blit_large_gtt
-rwxr-xr-x 1 root   root     31K Sep 12 17:04 intel_upload_blit_large_map
-rwxr-xr-x 1 root   root     31K Sep 12 17:04 intel_upload_blit_small
-rwxr-xr-x 1 root   root     48K Oct  8 13:49 interdiff
-rwxr-xr-x 1 root   root     19K Feb  4 20:49 ionice
-rwxr-xr-x 1 root   root     11K Feb  4 20:49 ipcmk
-rwxr-xr-x 1 root   root     11K Feb  4 20:49 ipcrm
-rwxr-xr-x 1 root   root     23K Feb  4 20:49 ipcs
-rwxr-xr-x 1 root   root     15K Nov  6 20:18 ipod-read-sysinfo-extended
-rwxr-xr-x 1 root   root     11K Nov  6 20:18 ipod-time-sync
-rwxr-xr-x 1 root   root     71K Feb 15 11:08 ipptool
-rwxr-xr-x 1 root   root     11K Jan 30 15:11 iproxy
lrwxrwxrwx 1 root   root      19 Feb 20 15:09 iptables-xml -> /sbin/xtables-multi
-rwxr-xr-x 1 root   root     11K Sep 18 23:47 ischroot
-rwxr-xr-x 1 root   root     15K Jan 18 09:18 isdv4-serial-debugger
-rwxr-xr-x 1 root   root    156K Oct  1 17:25 isodump
-rwxr-xr-x 1 root   root     22K Feb 18 13:46 isohybrid
-rwxr-xr-x 1 root   root     14K Feb 18 17:18 isohybrid.pl
-rwxr-xr-x 1 root   root    316K Oct  1 17:25 isoinfo
-rwxr-xr-x 1 root   root    156K Oct  1 17:25 isovfy
-rwxr-xr-x 1 root   root    7.0K Jan 23 17:09 ispell-wrapper
lrwxrwxrwx 1 root   root      21 Feb 26 19:53 jar -> /etc/alternatives/jar
lrwxrwxrwx 1 root   root      27 Feb 26 19:53 jarsigner -> /etc/alternatives/jarsigner
lrwxrwxrwx 1 root   root      22 Feb 26 19:53 java -> /etc/alternatives/java
lrwxrwxrwx 1 root   root      23 Feb 26 19:53 javac -> /etc/alternatives/javac
lrwxrwxrwx 1 root   root      25 Feb 26 19:53 javadoc -> /etc/alternatives/javadoc
lrwxrwxrwx 1 root   root      32 Feb 26 19:53 javafxpackager -> /etc/alternatives/javafxpackager
lrwxrwxrwx 1 root   root      23 Feb 26 19:53 javah -> /etc/alternatives/javah
lrwxrwxrwx 1 root   root      23 Feb 26 19:53 javap -> /etc/alternatives/javap
lrwxrwxrwx 1 root   root      25 Feb 26 19:53 java_vm -> /etc/alternatives/java_vm
lrwxrwxrwx 1 root   root      24 Feb 26 19:53 javaws -> /etc/alternatives/javaws
lrwxrwxrwx 1 root   root      22 Feb 26 19:53 jcmd -> /etc/alternatives/jcmd
lrwxrwxrwx 1 root   root      26 Feb 26 19:53 jconsole -> /etc/alternatives/jconsole
lrwxrwxrwx 1 root   root      21 Feb 26 19:53 jdb -> /etc/alternatives/jdb
lrwxrwxrwx 1 root   root      23 Feb 26 19:53 jexec -> /etc/alternatives/jexec
lrwxrwxrwx 1 root   root      22 Feb 26 19:53 jhat -> /etc/alternatives/jhat
lrwxrwxrwx 1 root   root      23 Feb 26 19:53 jinfo -> /etc/alternatives/jinfo
lrwxrwxrwx 1 root   root      22 Feb 26 19:53 jmap -> /etc/alternatives/jmap
-rwxr-xr-x 1 root   root    3.6K Feb 27 00:07 jockey-text
-rwxr-xr-x 1 root   root     43K Jan 17 07:03 join
-rwxr-xr-x 1 root   root     27K Feb  7 10:43 jpegtopnm
lrwxrwxrwx 1 root   root      21 Feb 26 19:53 jps -> /etc/alternatives/jps
lrwxrwxrwx 1 root   root      28 Feb 26 19:53 jrunscript -> /etc/alternatives/jrunscript
lrwxrwxrwx 1 root   root      27 Feb 26 19:53 jsadebugd -> /etc/alternatives/jsadebugd
-rwxr-xr-x 1 root   root    3.9K Feb 10 17:42 json_pp
lrwxrwxrwx 1 root   root      24 Feb 26 19:53 jstack -> /etc/alternatives/jstack
lrwxrwxrwx 1 root   root      23 Feb 26 19:53 jstat -> /etc/alternatives/jstat
lrwxrwxrwx 1 root   root      24 Feb 26 19:53 jstatd -> /etc/alternatives/jstatd
lrwxrwxrwx 1 root   root      27 Feb 26 19:53 jvisualvm -> /etc/alternatives/jvisualvm
-rwxr-xr-x 1 root   root     11K Feb 18 13:55 kbdinfo
-rwxr-xr-x 1 root   root     11K Jul 20  2012 kerneloops-submit
lrwxrwxrwx 1 root   root      25 Feb 26 19:53 keytool -> /etc/alternatives/keytool
-rwxr-xr-x 1 root   root     24K Nov 29 15:32 killall
-rwxr-xr-x 1 root   root    3.7K Sep 28 12:42 koi8rxterm
-rwxr-xr-x 1 root   root     61K Dec  6 16:53 l2ping
-rwxr-xr-x 1 root   root     77K Dec  6 16:53 l2test
-rwxr-xr-x 1 root   root    2.5K Feb 21 20:02 landscape-client-ui-install
-rwxr-xr-x 1 root   root     19K Jan 30 12:58 last
lrwxrwxrwx 1 root   root       4 Jan 30 12:58 lastb -> last
-rwxr-xr-x 1 root   root     15K Jan  2 17:33 lastlog
-rwxr-xr-x 1 root   root     19K Mar  9 08:07 lavadecode
-rwxr-xr-x 1 root   root    7.7K May 30  2008 lcf
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 lconvert -> qtchooser
lrwxrwxrwx 1 root   root       6 Feb 22 15:25 ld -> ld.bfd
-rwxr-xr-x 1 root   root    828K Feb 22 15:24 ld.bfd
-rwxr-xr-x 1 root   root    5.2K Feb  9 07:22 ldd
-rwxr-xr-x 1 root   root    1.8M Feb 22 15:24 ld.gold
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 leaftoppm
lrwxrwxrwx 1 root   root       9 Nov 22 13:21 less -> /bin/less
lrwxrwxrwx 1 root   root      13 Nov 22 13:21 lessecho -> /bin/lessecho
lrwxrwxrwx 1 root   root      13 Nov 22 13:21 lessfile -> /bin/lesspipe
lrwxrwxrwx 1 root   root      12 Nov 22 13:21 lesskey -> /bin/lesskey
lrwxrwxrwx 1 root   root      13 Nov 22 13:21 lesspipe -> /bin/lesspipe
-rwxr-xr-x 1 root   root     87K Dec 16 17:10 lexgrog
lrwxrwxrwx 1 root   root      21 Feb 27 00:15 lft -> /etc/alternatives/lft
-rwxr-xr-x 1 root   root    2.5K Dec 10 23:27 lft.db
-rwxr-xr-x 1 root   root     11K Jul  2  2012 liblinear-predict
-rwxr-xr-x 1 root   root     15K Jul  2  2012 liblinear-train
-rwxr-xr-x 1 root   root     16K Feb 10 17:42 libnetcfg
lrwxrwxrwx 1 root   root      34 Mar  9 03:02 libreoffice -> ../lib/libreoffice/program/soffice
-rwxr-xr-x 1 root   root    6.1K Feb  4 20:49 line
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 linguist -> qtchooser
-rwxr-xr-x 1 root   root     27K Jan 17 07:03 link
-rwxr-xr-x 1 root   root     55K Mar  2 22:00 lintian
-rwxr-xr-x 1 root   root    4.1K Dec 11 20:09 lintian-info
lrwxrwxrwx 1 root   root       7 Feb  4 20:49 linux32 -> setarch
lrwxrwxrwx 1 root   root       7 Feb  4 20:49 linux64 -> setarch
-rwxr-xr-x 1 root   root    1.6K Feb  5 10:05 linux-boot-prober
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 lispmtopgm
-rwxr-xr-x 1 root   root     11K Aug  7  2012 listres
-rwxr-xr-x 1 root   root     15K Dec 13 11:25 lnstat
lrwxrwxrwx 1 root   root      13 Feb 18 13:55 loadkeys -> /bin/loadkeys
-rwxr-xr-x 1 root   root     23K Feb 18 13:55 loadunimap
-rwxr-xr-x 1 root   root      59 Mar  9 01:00 localc
-rwxr-xr-x 1 root   root     38K Feb  9 07:26 locale
-rwxr-xr-x 1 root   root    324K Feb  9 07:26 localedef
lrwxrwxrwx 1 root   root      24 Feb 26 18:15 locate -> /etc/alternatives/locate
-rwxr-xr-x 4 root   root     15K Dec  3 23:37 lockfile-check
-rwxr-xr-x 4 root   root     15K Dec  3 23:37 lockfile-create
-rwxr-xr-x 4 root   root     15K Dec  3 23:37 lockfile-remove
-rwxr-xr-x 4 root   root     15K Dec  3 23:37 lockfile-touch
-rwxr-xr-x 1 root   root      59 Mar  9 01:00 lodraw
-rwxr-xr-x 1 root   root      53 Mar  9 01:50 loffice
-rwxr-xr-x 1 root   root      64 Mar  9 01:50 lofromtemplate
-rwxr-xr-x 1 root   root     19K Feb  4 20:49 logger
-rwxr-xr-x 1 root   root     27K Jan 17 07:03 logname
-rwxr-xr-x 1 root   root      62 Mar  9 01:00 loimpress
-rwxr-xr-x 1 root   root      59 Mar  9 01:00 lomath
-rwxr-xr-x 1 root   root     11K Jan  8 09:54 look
-rwxr-xr-x 1 root   root    2.7K Jan  8 09:54 lorder
-rwxr-xr-x 1 root   root      58 Mar  9 01:00 loweb
-rwxr-xr-x 1 root   root      61 Mar  9 01:00 lowriter
-rwxr-xr-x 1 root   root     18K Feb 15 11:08 lp
-rwxr-xr-x 1 root   root     15K Feb 15 11:08 lpoptions
-rwsr-xr-x 1 root   lpadmin  14K Feb 15 11:08 lppasswd
-rwxr-xr-x 1 root   root     19K Feb 15 11:08 lpq
-rwxr-xr-x 1 root   root     14K Feb 15 11:08 lpr
-rwxr-xr-x 1 root   root     10K Feb 15 11:08 lprm
-rwxr-xr-x 1 root   root     27K Feb 15 11:08 lpstat
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 lrelease -> qtchooser
-rwxr-xr-x 1 root   root     11K Jan  2 11:26 lsattr
-rwxr-xr-x 1 root   root    3.6K Oct 24 01:32 lsb_release
-rwxr-xr-x 1 root   root     31K Feb  4 20:49 lscpu
lrwxrwxrwx 1 root   root      10 Oct  8 13:49 lsdiff -> filterdiff
-rwxr-xr-x 1 root   root    593K Jul  1  2012 lshw
-rwxr-xr-x 1 root   root     767 Jun  1  2012 lsinitramfs
-rwxr-xr-x 1 root   root    160K Dec  2 02:36 lsof
-rwxr-xr-x 1 root   root     69K Dec  2 00:01 lspci
-rwxr-xr-x 1 root   root    1.1K Dec  2  2011 lspgpot
-rwxr-xr-x 1 root   root    2.5K Feb 18 17:18 lss16toppm
-rwxr-xr-x 1 root   root    133K Jan  9 15:46 lsusb
-rwxr-xr-x 1 root   root    150K Oct  3 00:41 ltrace
-rwxr-xr-x 1 root   root     41K Aug  7  2012 luit
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 lupdate -> qtchooser
-rwxr-xr-x 1 root   root    8.5K Apr 30  2012 lwp-download
-rwxr-xr-x 1 root   root    2.8K Apr 30  2012 lwp-dump
-rwxr-xr-x 1 root   root    2.5K Apr 30  2012 lwp-mirror
-rwxr-xr-x 1 root   root     15K Apr 30  2012 lwp-request
-rwxr-xr-x 1 root   root     419 Sep 28 12:42 lxterm
lrwxrwxrwx 1 root   root       2 Jun 18  2012 lz -> uz
lrwxrwxrwx 1 root   root      23 Feb 26 18:13 lzcat -> /etc/alternatives/lzcat
lrwxrwxrwx 1 root   root      23 Feb 26 18:13 lzcmp -> /etc/alternatives/lzcmp
lrwxrwxrwx 1 root   root      24 Feb 26 18:13 lzdiff -> /etc/alternatives/lzdiff
lrwxrwxrwx 1 root   root      25 Feb 26 18:13 lzegrep -> /etc/alternatives/lzegrep
lrwxrwxrwx 1 root   root      25 Feb 26 18:13 lzfgrep -> /etc/alternatives/lzfgrep
lrwxrwxrwx 1 root   root      24 Feb 26 18:13 lzgrep -> /etc/alternatives/lzgrep
lrwxrwxrwx 1 root   root      24 Feb 26 18:13 lzless -> /etc/alternatives/lzless
lrwxrwxrwx 1 root   root      22 Feb 26 18:13 lzma -> /etc/alternatives/lzma
-rwxr-xr-x 1 root   root     11K Jan  3 17:36 lzmainfo
lrwxrwxrwx 1 root   root      24 Feb 26 18:13 lzmore -> /etc/alternatives/lzmore
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 macptopbm
-rwxr-sr-x 3 root   mail     15K Dec  3 23:37 mail-lock
-rwxr-sr-x 3 root   mail     15K Dec  3 23:37 mail-touchlock
-rwxr-sr-x 3 root   mail     15K Dec  3 23:37 mail-unlock
-rwxr-xr-x 1 root   root    167K Oct  8 17:29 make
-rwxr-xr-x 1 root   root    1.2K Nov 22 14:16 mako-render
-rwxr-xr-x 1 root   root    105K Dec 16 17:10 man
-rwxr-xr-x 1 root   root    127K Dec 16 17:10 mandb
-rwxr-xr-x 1 root   root     287 Jan 25 20:38 manhole
-rwxr-xr-x 1 root   root     27K Dec 16 17:10 manpath
-rwxr-xr-x 1 root   root     19K Feb 18 13:55 mapscrn
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mattrib -> mtools
-rwxr-xr-x 1 root   root    116K Dec 13 15:21 mawk
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mbadblocks -> mtools
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mcat -> mtools
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mcd -> mtools
-rwxr-xr-x 1 root   root    1.7K Jun 18  2012 mcheck
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mclasserase -> mtools
-rwxr-xr-x 1 root   root     847 Jun 18  2012 mcomp
-rwxr-xr-x 1 root   root     15K Feb  4 20:49 mcookie
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mcopy -> mtools
-rwxr-xr-x 1 root   root     36K Jan  9 22:34 mc-tool
-rwxr-xr-x 1 root   root     11K Jan  9 22:34 mc-wait-for-name
-rwxr-xr-x 1 root   root     587 Feb 18 17:18 md5pass
-rwxr-xr-x 1 root   root     39K Jan 17 07:03 md5sum
lrwxrwxrwx 1 root   root       6 Jan 17 07:03 md5sum.textutils -> md5sum
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 mdatopbm
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mdel -> mtools
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mdeltree -> mtools
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mdir -> mtools
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mdu -> mtools
-rwxr-xr-x 1 root   root     30K Jan 29 19:33 melt
-rwxr-xr-x 1 root   root     11K Feb 18 13:46 memdiskfind
-rwxr-xr-x 1 root   root    6.1K Jan 30 12:58 mesg
-rwxr-xr-x 1 root   root    547K Nov 12 21:12 metacity
-rwxr-xr-x 1 root   root     11K Nov 12 21:12 metacity-message
-rwxr-xr-x 1 root   root     24K Nov 12 21:12 metacity-theme-viewer
-rwxr-xr-x 1 root   root     27K Nov 12 21:12 metacity-window-demo
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mformat -> mtools
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 mgrtopbm
-rwxr-xr-x 1 root   root    8.4K Apr 30  2012 mimeopen
-rwxr-xr-x 1 root   root     12K Apr 30  2012 mimetype
-rwxr-xr-x 1 root   root     20K Oct  5 17:43 min12xxw
lrwxrwxrwx 1 root   root       6 Jun 18  2012 minfo -> mtools
-rwxr-xr-x 1 root   root     26K Feb 15 18:28 miniterm.py
-rwxr-xr-x 1 root   root     43K Mar  6 15:52 mir
-rwxr-xr-x 1 root   root     19K Mar  6 15:52 mir_demo_client
-rwxr-xr-x 1 root   root     31K Mar  6 15:52 mir_demo_client_accelerated
-rwxr-xr-x 1 root   root     15K Mar  6 15:52 mir_demo_client_unaccelerated
-rwxr-xr-x 1 root   root    8.6K Feb 18 17:18 mkdiskimage
-rwxr-xr-x 1 root   root     31K Jan 17 07:03 mkfifo
-rwxr-xr-x 1 root   root      65 May 16  2012 mkfontdir
-rwxr-xr-x 1 root   root     31K May 16  2012 mkfontscale
lrwxrwxrwx 1 root   root      11 Oct  1 17:25 mkisofs -> genisoimage
-rwxr-xr-x 1 root   root     11K Jun 18  2012 mkmanifest
-rwxr-xr-x 1 root   root     16K Feb 18 13:55 mk_modmap
-rwxr-xr-x 1 root   root     23K Oct  1 17:25 mkzftree
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mlabel -> mtools
-rwxr-sr-x 1 root   mlocate  39K Feb  8 17:31 mlocate
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mmd -> mtools
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mmount -> mtools
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mmove -> mtools
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 moc -> qtchooser
lrwxrwxrwx 1 root   root      25 Feb 26 19:41 mogrify -> /etc/alternatives/mogrify
-rwxr-xr-x 1 root   root    6.2K Feb 25 19:54 mogrify.im6
lrwxrwxrwx 1 root   root      25 Feb 26 19:41 montage -> /etc/alternatives/montage
-rwxr-xr-x 1 root   root    6.2K Feb 25 19:54 montage.im6
-rwxr-xr-x 1 root   root     65K Dec 20  2011 most
-rwxr-xr-x 1 root   root     60K Sep 28 11:23 mousetweaks
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mpartition -> mtools
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mrd -> mtools
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mren -> mtools
-rwxr-xr-x 1 root   root     11K Dec  4 05:09 mscompress
-rwxr-xr-x 1 root   root     11K Dec  4 05:09 msexpand
-rwxr-xr-x 1 root   root     23K Mar  7 16:02 msgattrib
-rwxr-xr-x 1 root   root     23K Mar  7 16:02 msgcat
-rwxr-xr-x 1 root   root     23K Mar  7 16:02 msgcmp
-rwxr-xr-x 1 root   root     19K Mar  7 16:02 msgcomm
-rwxr-xr-x 1 root   root     19K Mar  7 16:02 msgconv
-rwxr-xr-x 1 root   root     19K Mar  7 16:02 msgen
-rwxr-xr-x 1 root   root     15K Mar  7 16:02 msgexec
-rwxr-xr-x 1 root   root     23K Mar  7 16:02 msgfilter
-rwxr-xr-x 1 root   root     68K Mar  7 16:02 msgfmt
-rwxr-xr-x 1 root   root     99K Mar  7 16:02 msggrep
-rwxr-xr-x 1 root   root     44K Mar  7 16:02 msginit
-rwxr-xr-x 1 root   root     52K Mar  7 16:02 msgmerge
-rwxr-xr-x 1 root   root     27K Mar  7 16:02 msgunfmt
-rwxr-xr-x 1 root   root     19K Mar  7 16:02 msguniq
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mshortname -> mtools
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mshowfat -> mtools
-rwxr-xr-x 1 root   root    178K Jun 18  2012 mtools
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mtoolstest -> mtools
-rwsr-xr-x 1 root   root     66K Jun 18  2012 mtr
-rwxr-xr-x 1 root   root    6.4K Feb  9 07:22 mtrace
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 mtvtoppm
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mtype -> mtools
-rwxr-xr-x 1 root   root     784 Jun 18  2012 mxtar
lrwxrwxrwx 1 root   root       6 Jun 18  2012 mzip -> mtools
-rwxr-xr-x 1 root   root     19K Feb  4 20:49 namei
lrwxrwxrwx 1 root   root       9 Oct  1 15:12 nano -> /bin/nano
lrwxrwxrwx 1 root   root      30 Feb 26 19:53 native2ascii -> /etc/alternatives/native2ascii
-rwxr-xr-x 1 root   root    1.4M Mar  8 16:08 nautilus
-rwxr-xr-x 1 root   root     31K Mar  8 16:08 nautilus-autorun-software
-rwxr-xr-x 1 root   root     44K Mar  8 16:08 nautilus-connect-server
-rwxr-xr-x 1 root   root     28K Jan  9 23:37 nautilus-sendto
lrwxrwxrwx 1 root   root      22 Feb 26 18:12 nawk -> /etc/alternatives/nawk
-rwxr-xr-x 1 root   root     26K Jan  8 09:54 ncal
-rwxr-xr-x 1 root   root    164K Jan  4 05:09 ncat
-rwxr-xr-x 1 root   root    5.2K Feb  8 15:33 ncurses5-config
-rwxr-xr-x 1 root   root    5.2K Feb  8 15:33 ncursesw5-config
-rwxr-xr-x 1 root   root     52K Jan  4 05:09 ndiff
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 neotoppm
-rwxr-xr-x 1 root   root     271 Feb  9 17:11 neqn
lrwxrwxrwx 1 root   root      21 Feb 26 19:29 net -> /etc/alternatives/net
-rwxr-xr-x 1 root   root     84K Dec  3 22:58 netkit-ftp
-rwxr-xr-x 1 root   root    8.3M Nov 26 09:09 net.samba3
-rwxr-xr-x 1 root   root     28K Dec  6 08:11 net-snmp-config
-rwsr-xr-x 1 root   root     32K Jan  2 17:33 newgrp
-rwxr-xr-x 1 root   root     35K Mar  7 16:02 ngettext
-rwxr-xr-x 1 root   root     31K Jan 17 07:03 nice
lrwxrwxrwx 1 root   root      31 Nov 14 23:08 ninja-ide -> ../share/ninja-ide/ninja-ide.py
-rwxr-xr-x 1 root   root     39K Jan 17 07:03 nl
-rwxr-xr-x 1 root   root     40K Feb 22 15:24 nm
-rwxr-xr-x 1 root   root    1.9M Jan  4 05:09 nmap
-rwxr-xr-x 1 root   root    293K Mar  8 17:16 nm-applet
lrwxrwxrwx 1 root   root      27 Feb 26 19:29 nmblookup -> /etc/alternatives/nmblookup
-rwxr-xr-x 1 root   root    1.6M Nov 26 09:09 nmblookup.samba3
-rwxr-xr-x 1 root   root    170K Mar  8 15:15 nmcli
-rwxr-xr-x 1 root   root    328K Mar  8 17:16 nm-connection-editor
-rwxr-xr-x 1 root   root     11K Mar  8 15:15 nm-online
-rwxr-xr-x 1 root   root     28K Mar  8 15:15 nm-tool
-rwxr-xr-x 1 root   root     31K Jan 17 07:03 nohup
-rwxr-xr-x 1 root   root     15K Feb 19 20:08 notify-send
-rwxr-xr-x 1 root   root    436K Jan  4 05:09 nping
-rwxr-xr-x 1 root   root     31K Jan 17 07:03 nproc
-rwxr-xr-x 1 root   root    3.4K Feb  9 17:11 nroff
-rwxr-xr-x 1 root   root    111K Jan 11 14:15 nslookup
-rwxr-xr-x 1 root   root     19K Dec 13 11:25 nstat
-rwxr-xr-x 1 root   root     58K Jan 11 14:15 nsupdate
-rwxr-xr-x 1 root   root     43K Feb 25 13:52 ntfsdecrypt
-rwxr-xr-x 1 root   root     270 Jan 30 11:31 nvidia-detector
-rwxr-xr-x 1 root   root      47 Dec 13 16:34 nvlc
-rwxr-xr-x 1 root   root     19K Mar  9 08:07 oakdecode
-rwxr-xr-x 1 root   root    149K Oct  8 17:12 obex-data-server
-rwxr-xr-x 1 root   root    216K Feb 22 15:24 objcopy
-rwxr-xr-x 1 root   root    312K Feb 22 15:24 objdump
-rwxr-xr-x 1 root   root     20K Jan 10 10:10 oclock
-rwxr-xr-x 1 root   root     67K Jan 17 07:03 od
-rwxr-xr-x 1 root   root    8.2K Oct  8 17:12 ods-server
-rwxr-xr-x 1 root   root    225K Oct 29 10:49 oldfind
-rwxr-xr-x 1 root   root    1.5M Feb 26 22:41 omshell
lrwxrwxrwx 1 root   root      17 Oct  3 00:57 on_ac_power -> /sbin/on_ac_power
-rwxr-xr-x 1 root   root     456 Dec 13 11:21 onboard
-rwxr-xr-x 1 root   root      78 Dec 13 11:21 onboard-settings
lrwxrwxrwx 1 root   root      30 Jan 24 07:13 oneconf-query -> ../share/oneconf/oneconf-query
-rwxr-xr-x 1 root   root    3.9K Oct  8 21:45 openshot
-rwxr-xr-x 1 root   root    2.5K Oct  8 21:45 openshot-render
-rwxr-xr-x 1 root   root    502K Mar  7 20:30 openssl
-rwxr-xr-x 1 root   root     15K Mar  9 08:07 opldecode
lrwxrwxrwx 1 root   root      22 Feb 26 19:53 orbd -> /etc/alternatives/orbd
-rwxr-xr-x 1 root   root     13K Mar  6 15:03 orca
-rwxr-xr-x 1 root   root    4.2K Feb  5 10:05 os-prober
-rwxr-xr-x 1 root   root     39K Mar  1 14:34 pacat
lrwxrwxrwx 1 root   root      25 Feb 26 19:53 pack200 -> /etc/alternatives/pack200
-rwxr-xr-x 1 root   root     15K Mar  1 14:34 pacmd
-rwxr-xr-x 1 root   root     56K Mar  1 14:34 pactl
-rwxr-xr-x 1 root   root    2.3K Mar  1 14:33 padsp
lrwxrwxrwx 1 root   root      23 Feb 26 18:12 pager -> /etc/alternatives/pager
-rwxr-xr-x 1 root   root     19K Feb  7 10:43 palmtopnm
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 pamcut
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pamdeinterlace
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pamdice
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pamfile
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pamoil
lrwxrwxrwx 1 root   root       5 Mar  1 14:34 pamon -> pacat
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pamstack
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pamstretch
-rwxr-xr-x 1 root   root    1.4K Feb  7 10:43 pamstretch-gen
-rwxr-xr-x 1 root   root     11K Feb 12 01:31 paperconf
lrwxrwxrwx 1 root   root       5 Mar  1 14:34 paplay -> pacat
lrwxrwxrwx 1 root   root       5 Mar  1 14:34 parec -> pacat
lrwxrwxrwx 1 root   root       5 Mar  1 14:34 parecord -> pacat
-rwxr-xr-x 1 root   root    8.5K May  7  2011 parsechangelog
-rwxr-xr-x 1 root   root     44K Feb  4 20:49 partx
-rwsr-xr-x 1 root   root     46K Jan  2 17:33 passwd
-rwxr-xr-x 1 root   root     31K Jan 17 07:03 paste
-rwxr-xr-x 1 root   root     15K Mar  1 14:34 pasuspender
-rwxr-xr-x 1 root   root    111K Jan  3 17:14 patch
-rwxr-xr-x 1 root   root     31K Jan 17 07:03 pathchk
-rwxr-xr-x 1 root   root     15K Mar  1 14:34 pax11publish
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmclean
-rwxr-xr-x 1 root   root    6.1K Feb  7 10:43 pbmlife
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmmake
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmmask
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 pbmpage
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 pbmpscale
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmreduce
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmtext
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 pbmtextps
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmto10x
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmtoascii
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmtoatk
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmtobbnbg
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmtocmuwm
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmtoepsi
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 pbmtoepson
-rwxr-xr-x 1 root   root     14K Feb  7 10:43 pbmtog3
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmtogem
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmtogo
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmtoicon
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmtolj
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmtomacp
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmtomda
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmtomgr
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmtonokia
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmtopgm
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmtopi3
-rwxr-xr-x 1 root   root    6.1K Feb  7 10:43 pbmtoplot
-rwxr-xr-x 1 root   root     27K Feb  7 10:43 pbmtoppa
-rwxr-xr-x 1 root   root     12K Feb  7 10:43 pbmtopsg3
-rwxr-xr-x 1 root   root    6.1K Feb  7 10:43 pbmtoptx
-rwxr-xr-x 1 root   root    6.1K Feb  7 10:43 pbmtowbmp
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmtox10bm
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmtoxbm
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmtoybm
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pbmtozinc
-rwxr-xr-x 1 root   root     23K Feb  7 10:43 pbmupc
-rwxr-xr-x 1 root   root     15K Dec  2 00:01 pcimodules
-rwxr-xr-x 1 root   root     19K Feb  7 10:43 pcxtoppm
lrwxrwxrwx 1 root   root       6 Jan 27 19:18 pdb -> pdb2.7
lrwxrwxrwx 1 root   root      23 Mar  8 08:11 pdb2.7 -> ../lib/python2.7/pdb.py
lrwxrwxrwx 1 root   root       6 Mar  6 10:36 pdb3 -> pdb3.3
lrwxrwxrwx 1 root   root      23 Mar  8 07:09 pdb3.3 -> ../lib/python3.3/pdb.py
-rwxr-xr-x 1 root   root     698 Jan 22 22:13 pdf2dsc
-rwxr-xr-x 1 root   root     909 Jan 22 22:13 pdf2ps
-rwxr-xr-x 1 root   root     19K Jan 16 15:23 pdfdetach
-rwxr-xr-x 1 root   root     15K Jan 16 15:23 pdffonts
-rwxr-xr-x 1 root   root     39K Jan 16 15:23 pdfimages
-rwxr-xr-x 1 root   root     23K Jan 16 15:23 pdfinfo
-rwxr-xr-x 1 root   root     550 Jan 22 22:13 pdfopt
-rwxr-xr-x 1 root   root     15K Jan 16 15:23 pdfseparate
-rwxr-xr-x 1 root   root    119K Jan 16 15:23 pdftocairo
-rwxr-xr-x 1 root   root     95K Jan 16 15:23 pdftohtml
-rwxr-xr-x 1 root   root     23K Jan 16 15:23 pdftoppm
-rwxr-xr-x 1 root   root     23K Jan 16 15:23 pdftops
-rwxr-xr-x 1 root   root     27K Jan 16 15:23 pdftotext
-rwxr-xr-x 1 root   root     19K Jan 16 15:23 pdfunite
-rwxr-xr-x 1 root   root     11K Nov 29 15:32 peekfd
-rwxr-xr-x 2 root   root     11K Feb 10 17:43 perl
-rwxr-xr-x 2 root   root     11K Feb 10 17:43 perl5.14.2
-rwxr-xr-x 2 root   root     45K Feb 10 17:42 perlbug
-rwxr-xr-x 1 root   root     125 Feb 10 17:43 perldoc
-rwxr-xr-x 1 root   root     13K Feb 10 17:42 perlivp
-rwxr-xr-x 2 root   root     45K Feb 10 17:42 perlthanks
-rwxr-xr-x 1 root   root     498 Jan 22 22:13 pf2afm
-rwxr-xr-x 1 root   root     516 Jan 22 22:13 pfbtopfa
lrwxrwxrwx 1 root   root      10 Dec  3 22:58 pftp -> netkit-ftp
-rwxr-xr-x 1 root   root     31K Feb  4 20:49 pg
-rwxr-xr-x 1 root   root    432K Dec  4 19:47 pgawk
-rwxr-xr-x 1 root   root    6.1K Feb  7 10:43 pgmbentley
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 pgmcrater
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pgmedge
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pgmenhance
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pgmhist
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pgmkernel
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pgmnoise
lrwxrwxrwx 1 root   root       7 Feb  7 10:43 pgmnorm -> pnmnorm
lrwxrwxrwx 1 root   root       6 Feb  7 10:43 pgmoil -> pamoil
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pgmramp
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pgmslice
-rwxr-xr-x 1 root   root     27K Feb  7 10:43 pgmtexture
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pgmtofs
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pgmtolispm
-rwxr-xr-x 1 root   root     25K Feb  7 10:43 pgmtopbm
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pgmtoppm
-rwxr-xr-x 1 root   root     23K Jan  4 16:31 pgrep
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pi1toppm
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pi3topbm
-rwxr-xr-x 1 root   root    177K Feb  9 17:11 pic
lrwxrwxrwx 1 root   root      22 Feb 26 18:15 pico -> /etc/alternatives/pico
-rwxr-xr-x 1 root   root    7.2K Feb 10 17:42 piconv
-rwxr-xr-x 1 root   root    2.3K Feb 10 15:50 pilconvert.py
-rwxr-xr-x 1 root   root     15K Feb 10 15:50 pildriver.py
-rwxr-xr-x 1 root   root    2.6K Feb 10 15:50 pilfile.py
-rwxr-xr-x 1 root   root    1.1K Feb 10 15:50 pilfont.py
-rwxr-xr-x 1 root   root    2.4K Feb 10 15:50 pilprint.py
-rwxr-xr-x 1 root   root     35K Jan 17 07:03 pinky
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 pixeltool -> qtchooser
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pjtoppm
-rwxr-xr-x 1 root   root     11K Nov  5 07:27 pkaction
-rwxr-xr-x 1 root   root     19K Nov  5 07:27 pkcheck
-rwsr-xr-x 1 root   root     23K Nov  5 07:27 pkexec
-rwxr-xr-x 1 root   root     43K Oct  8 13:52 pkg-config
lrwxrwxrwx 1 root   root       5 Jan  4 16:31 pkill -> pgrep
-rwxr-xr-x 1 root   root     11K Nov  5 07:27 pkttyagent
-rwxr-xr-x 1 root   root    4.5K Feb 10 17:42 pl2pm
-rwxr-xr-x 1 root   root     15K Feb  9 07:26 pldd
-rwxr-xr-x 1 root   root     146 Jan 22 22:13 plog
-rwxr-xr-x 1 root   root     19K Jan  4 16:31 pmap
-rwxr-xr-x 1 root   root     981 Nov 14 14:51 pm-is-supported
-rwxr-xr-x 1 root   root     23K Feb  7 10:43 pngtopnm
-rwxr-xr-x 1 root   root    614K Oct  8 17:36 pnm2ppa
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 pnmalias
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmarith
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmcat
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 pnmcolormap
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmcomp
-rwxr-xr-x 1 root   root     31K Feb  7 10:43 pnmconvol
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmcrop
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 pnmcut
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmdepth
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmenlarge
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmfile
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmflip
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmgamma
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmhisteq
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmhistmap
-rwxr-xr-x 1 root   root    4.5K Feb  7 10:43 pnmindex
lrwxrwxrwx 1 root   root      10 Feb  7 10:43 pnminterp -> pamstretch
lrwxrwxrwx 1 root   root      14 Feb  7 10:43 pnminterp-gen -> pamstretch-gen
-rwxr-xr-x 1 root   root    6.1K Feb  7 10:43 pnminvert
-rwxr-xr-x 1 root   root    1.8K Feb  7 10:43 pnmmargin
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 pnmmontage
-rwxr-xr-x 1 root   root     19K Feb  7 10:43 pnmnlfilt
lrwxrwxrwx 1 root   root      13 Feb  7 10:43 pnmnoraw -> pnmtoplainpnm
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmnorm
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmpad
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmpaste
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmpsnr
-rwxr-xr-x 1 root   root    3.2K Feb  7 10:43 pnmquant
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 pnmremap
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 pnmrotate
-rwxr-xr-x 1 root   root     19K Feb  7 10:43 pnmscale
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 pnmscalefixed
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmshear
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmsmooth
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmsplit
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmtile
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 pnmtoddif
-rwxr-xr-x 1 root   root    177K Feb  7 10:43 pnmtofiasco
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmtofits
-rwxr-xr-x 1 root   root     19K Feb  7 10:43 pnmtojpeg
-rwxr-xr-x 1 root   root     19K Feb  7 10:43 pnmtopalm
-rwxr-xr-x 1 root   root    6.1K Feb  7 10:43 pnmtoplainpnm
-rwxr-xr-x 1 root   root     27K Feb  7 10:43 pnmtopng
-rwxr-xr-x 1 root   root     19K Feb  7 10:43 pnmtops
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmtorast
-rwxr-xr-x 1 root   root     39K Feb  7 10:43 pnmtorle
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 pnmtosgi
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmtosir
-rwxr-xr-x 1 root   root     19K Feb  7 10:43 pnmtotiff
-rwxr-xr-x 1 root   root     19K Feb  7 10:43 pnmtotiffcmyk
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 pnmtoxwd
-rwxr-xr-x 1 root   root    2.4K Feb 10 17:42 pod2html
-rwxr-xr-x 1 root   root     11K Feb 10 17:42 pod2latex
-rwxr-xr-x 1 root   root     12K Feb 10 17:42 pod2man
-rwxr-xr-x 1 root   root    9.0K Feb 10 17:42 pod2text
-rwxr-xr-x 1 root   root    3.4K Feb 10 17:42 pod2usage
-rwxr-xr-x 1 root   root    3.7K Feb 10 17:42 podchecker
-rwxr-xr-x 1 root   root    2.6K Feb 10 17:42 podselect
-rwxr-xr-x 1 root   root    2.8K Jan 22 22:13 poff
lrwxrwxrwx 1 root   root      28 Feb 26 19:53 policytool -> /etc/alternatives/policytool
-rwxr-xr-x 1 root   root    1.6K Jan 22 22:13 pon
lrwxrwxrwx 1 root   root      11 Apr 30  2012 POST -> lwp-request
-rwxr-xr-x 1 root   root     19K Feb 15 11:08 ppdc
-rwxr-xr-x 1 root   root     11K Feb 15 11:08 ppdhtml
-rwxr-xr-x 1 root   root     11K Feb 15 11:08 ppdi
-rwxr-xr-x 1 root   root     15K Feb 15 11:08 ppdmerge
-rwxr-xr-x 1 root   root     11K Feb 15 11:08 ppdpo
-rwxr-xr-x 1 root   root     404 Jan 22 22:13 pphs
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 ppm3d
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmbrighten
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmchange
-rwxr-xr-x 1 root   root     23K Feb  7 10:43 ppmcie
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmcolormask
-rwxr-xr-x 1 root   root    6.1K Feb  7 10:43 ppmcolors
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmdim
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmdist
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmdither
-rwxr-xr-x 1 root   root     12K Feb  7 10:43 ppmfade
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmflash
-rwxr-xr-x 1 root   root     23K Feb  7 10:43 ppmforge
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmhist
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmlabel
-rwxr-xr-x 1 root   root    6.1K Feb  7 10:43 ppmmake
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmmix
lrwxrwxrwx 1 root   root       7 Feb  7 10:43 ppmnorm -> pnmnorm
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmntsc
-rwxr-xr-x 1 root   root     23K Feb  7 10:43 ppmpat
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 ppmquant
-rwxr-xr-x 1 root   root    2.1K Feb  7 10:43 ppmquantall
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 ppmqvga
-rwxr-xr-x 1 root   root    1.7K Feb  7 10:43 ppmrainbow
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmrelief
-rwxr-xr-x 1 root   root    6.7K Feb  7 10:43 ppmshadow
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmshift
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmspread
-rwxr-xr-x 1 root   root     16K Feb  7 10:43 ppmtoacad
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 ppmtobmp
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmtoeyuv
-rwxr-xr-x 1 root   root     19K Feb  7 10:43 ppmtogif
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmtoicr
-rwxr-xr-x 1 root   root     43K Feb  7 10:43 ppmtoilbm
lrwxrwxrwx 1 root   root       9 Feb  7 10:43 ppmtojpeg -> pnmtojpeg
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmtoleaf
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmtolj
-rwxr-xr-x 1 root   root    9.4K Feb 18 17:18 ppmtolss16
-rwxr-xr-x 1 root   root      81 Feb  7 10:43 ppmtomap
-rwxr-xr-x 1 root   root     19K Feb  7 10:43 ppmtomitsu
-rwxr-xr-x 1 root   root    587K Feb  7 10:43 ppmtompeg
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmtoneo
-rwxr-xr-x 1 root   root     19K Feb  7 10:43 ppmtopcx
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmtopgm
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmtopi1
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmtopict
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmtopj
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmtopuzz
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmtorgb3
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmtosixel
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 ppmtotga
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmtouil
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 ppmtowinicon
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 ppmtoxpm
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmtoyuv
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmtoyuvsplit
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ppmtv
-rwxr-xr-x 1 root   root     63K Jan 17 07:03 pr
-rwxr-xr-x 1 root   root    5.6K Oct  1 17:13 precat
-rwxr-xr-x 1 root   root     39K Feb  9 17:11 preconv
-rwxr-xr-x 1 root   root    3.0K Feb 10 17:43 prename
-rwxr-xr-x 1 root   root    5.6K Oct  1 17:13 preunzip
-rwxr-xr-x 1 root   root    5.6K Oct  1 17:13 prezip
-rwxr-xr-x 1 root   root     11K Oct  1 17:13 prezip-bin
lrwxrwxrwx 1 root   root      11 Jan  8 10:38 print -> run-mailcap
-rwxr-xr-x 1 root   root     395 Jan 22 22:13 printafm
-rwxr-xr-x 1 root   root     27K Jan 17 07:03 printenv
-rwxr-xr-x 1 root   root     19K Jan  8 09:54 printerbanner
-rwxr-xr-x 1 root   root    5.6K Mar  9 08:07 printer-profile
-rwxr-xr-x 1 root   root     51K Jan 17 07:03 printf
-rwxr-xr-x 1 root   root    101K Sep  8  2012 projectM-pulseaudio
-rwxr-xr-x 1 root   root     11K Jun 24  2012 protoc
-rwxr-xr-x 1 root   root     11K Feb 10 17:42 prove
-rwxr-xr-x 1 root   root     15K Nov 29 15:32 prtstat
-rwxr-xr-x 1 root   root     740 Jan 22 22:13 ps2ascii
-rwxr-xr-x 1 root   root    2.8K Jan 22 22:13 ps2epsi
-rwxr-xr-x 1 root   root     272 Jan 22 22:13 ps2pdf
-rwxr-xr-x 1 root   root     215 Jan 22 22:13 ps2pdf12
-rwxr-xr-x 1 root   root     215 Jan 22 22:13 ps2pdf13
-rwxr-xr-x 1 root   root     215 Jan 22 22:13 ps2pdf14
-rwxr-xr-x 1 root   root    1.1K Jan 22 22:13 ps2pdfwr
-rwxr-xr-x 1 root   root     647 Jan 22 22:13 ps2ps
-rwxr-xr-x 1 root   root     669 Jan 22 22:13 ps2ps2
lrwxrwxrwx 1 root   root       8 Jan 22 22:13 ps2txt -> ps2ascii
-rwxr-xr-x 2 root   root     53K Feb 10 17:42 psed
lrwxrwxrwx 1 root   root       9 Feb 18 13:55 psfaddtable -> psfxtable
lrwxrwxrwx 1 root   root       9 Feb 18 13:55 psfgettable -> psfxtable
lrwxrwxrwx 1 root   root       9 Feb 18 13:55 psfstriptable -> psfxtable
-rwxr-xr-x 1 root   root     19K Feb 18 13:55 psfxtable
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 psidtopgm
-rwxr-xr-x 1 root   root     19K Feb  7 10:43 pstopnm
-rwxr-xr-x 1 root   root     23K Nov 29 15:32 pstree
lrwxrwxrwx 1 root   root       6 Nov 29 15:32 pstree.x11 -> pstree
-rwxr-xr-x 2 root   root     36K Feb 10 17:42 pstruct
-rwxr-xr-x 1 root   root    3.0K Feb 10 17:42 ptar
-rwxr-xr-x 1 root   root    2.5K Feb 10 17:42 ptardiff
-rwxr-xr-x 1 root   root    4.2K Feb 10 17:42 ptargrep
-rwxr-xr-x 1 root   root     63K Jan 17 07:03 ptx
-rwxr-xr-x 1 root   root     83K Mar  1 14:34 pulseaudio
-rwxr-xr-x 1 root   root    8.0K Feb 28 20:59 purple-remote
-rwxr-xr-x 1 root   root     776 Feb 28 20:59 purple-send
-rwxr-xr-x 1 root   root     635 Feb 28 20:59 purple-send-async
-rwxr-xr-x 1 root   root     12K Feb 28 20:59 purple-url-handler
-rwxr-xr-x 1 root   root     11K Jan  4 16:31 pwdx
-rwxr-xr-x 1 root   root    9.8K Feb 18 17:18 pxelinux-options
-rwxr-xr-x 1 root   root    7.1K Mar  6 10:36 py3clean
-rwxr-xr-x 1 root   root     12K Mar  6 10:36 py3compile
-rwxr-xr-x 1 root   root    3.7K May  2  2012 py3_compilefiles
lrwxrwxrwx 1 root   root      31 Mar  6 10:36 py3versions -> ../share/python3/py3versions.py
-rwxr-xr-x 1 root   root     19K Mar  6 10:36 pybuild
-rwxr-xr-x 1 root   root     96K May  2  2012 pycentral
-rwxr-xr-x 1 root   root    4.1K Jan 27 19:18 pyclean
-rwxr-xr-x 1 root   root     12K Jan 27 19:18 pycompile
-rwxr-xr-x 1 root   root    3.7K May  2  2012 py_compilefiles
lrwxrwxrwx 1 root   root       8 Jan 27 19:18 pydoc -> pydoc2.7
-rwxr-xr-x 1 root   root      79 Mar  8 08:10 pydoc2.7
lrwxrwxrwx 1 root   root       8 Mar  6 10:36 pydoc3 -> pydoc3.3
-rwxr-xr-x 1 root   root      79 Mar  8 07:08 pydoc3.3
-rwxr-xr-x 1 root   root      92 Feb 14 15:50 pyflakes
lrwxrwxrwx 1 root   root      12 Jan 27 19:18 pygettext -> pygettext2.7
-rwxr-xr-x 1 root   root     22K Mar  8 08:10 pygettext2.7
lrwxrwxrwx 1 root   root      12 Mar  6 10:36 pygettext3 -> pygettext3.3
-rwxr-xr-x 1 root   root     22K Mar  8 07:08 pygettext3.3
-rwxr-xr-x 1 root   root     217 Jan 25 20:38 pyhtmlizer
lrwxrwxrwx 1 root   root       9 Jan 27 19:18 python -> python2.7
lrwxrwxrwx 1 root   root       9 Jan 27 19:18 python2 -> python2.7
-rwxr-xr-x 1 root   root    2.6M Mar  8 08:11 python2.7
lrwxrwxrwx 1 root   root       9 Mar  6 10:36 python3 -> python3.3
-rwxr-xr-x 2 root   root    3.3M Mar  8 07:09 python3.3
-rwxr-xr-x 2 root   root    3.3M Mar  8 07:09 python3.3m
lrwxrwxrwx 1 root   root      10 Mar  6 10:36 python3m -> python3.3m
-rwxr-xr-x 1 root   root     231 Mar  8 07:08 pyvenv-3.3
lrwxrwxrwx 1 root   root      29 Jan 27 19:18 pyversions -> ../share/python/pyversions.py
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 qcollectiongenerator -> qtchooser
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 qdbus -> qtchooser
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 qdbuscpp2xml -> qtchooser
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 qdbusviewer -> qtchooser
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 qdbusxml2cpp -> qtchooser
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 qdoc -> qtchooser
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 qdoc3 -> qtchooser
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 qglinfo -> qtchooser
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 qhelpconverter -> qtchooser
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 qhelpgenerator -> qtchooser
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 qmake -> qtchooser
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 qml1plugindump -> qtchooser
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 qmlbundle -> qtchooser
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 qmlmin -> qtchooser
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 qmlplugindump -> qtchooser
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 qmlprofiler -> qtchooser
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 qmlscene -> qtchooser
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 qmltestrunner -> qtchooser
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 qmlviewer -> qtchooser
-rwxr-xr-x 1 root   root     79K Mar  8 16:21 qpdf
-rwxr-xr-x 1 root   root     19K Mar  9 08:07 qpdldecode
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 qrttoppm
-rwxr-xr-x 1 root   root     23K Feb 12 15:38 qtchooser
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 qtconfig -> qtchooser
-rwxr-xr-x 1 root   root     28K Jan 24 14:22 qt-faststart
-rwxr-xr-x 1 root   root    2.4K Jan 30 11:31 quirks-handler
-rwxr-xr-x 1 root   root      43 Dec 13 16:34 qvlc
-rwxr-xr-x 1 root   root     60K Feb 22 15:24 ranlib
-rwxr-xr-x 1 root   root     11K Oct  8 22:55 rarian-example
-rwxr-xr-x 1 root   root    1.5K Oct  8 22:55 rarian-sk-config
-rwxr-xr-x 1 root   root     563 Oct  8 22:55 rarian-sk-extract
-rwxr-xr-x 1 root   root    6.2K Oct  8 22:55 rarian-sk-gen-uuid
-rwxr-xr-x 1 root   root     71K Oct  8 22:55 rarian-sk-get-cl
-rwxr-xr-x 1 root   root     399 Oct  8 22:55 rarian-sk-get-content-list
-rwxr-xr-x 1 root   root     419 Oct  8 22:55 rarian-sk-get-extended-content-list
-rwxr-xr-x 1 root   root     382 Oct  8 22:55 rarian-sk-get-scripts
-rwxr-xr-x 1 root   root    1.2K Oct  8 22:55 rarian-sk-install
-rwxr-xr-x 1 root   root     79K Oct  8 22:55 rarian-sk-migrate
-rwxr-xr-x 1 root   root     51K Oct  8 22:55 rarian-sk-preinstall
-rwxr-xr-x 1 root   root     821 Oct  8 22:55 rarian-sk-rebuild
-rwxr-xr-x 1 root   root    9.4K Oct  8 22:55 rarian-sk-update
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 rasttopnm
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 rawtopgm
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 rawtoppm
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 rcc -> qtchooser
lrwxrwxrwx 1 root   root      21 Feb 26 18:15 rcp -> /etc/alternatives/rcp
-rwxr-xr-x 1 root   root    106K Dec  6 16:53 rctest
-rwxr-xr-x 1 root   root    266K Feb 27 16:54 rdesktop-vrdp
-rwxr-xr-x 1 root   root    8.5K Jan 23 21:06 rdiffdir
-rwxr-xr-x 1 root   root    373K Feb 22 15:24 readelf
-rwxr-xr-x 1 root   root    185K Oct  1 17:25 readom
-rwxr-xr-x 1 root   root     15K Mar  7 16:02 recode-sr-latin
-rwxr-xr-x 1 root   root    3.4K Oct  8 13:49 recountdiff
lrwxrwxrwx 1 root   root       7 Jan 18 19:53 red -> /bin/ed
-rwxr-xr-x 1 root   root     35K Oct  8 13:49 rediff
-rwxr-xr-x 1 root   root    307K Jan 17 16:47 remmina
lrwxrwxrwx 1 root   root      24 Feb 26 18:13 rename -> /etc/alternatives/rename
-rwxr-xr-x 1 root   root     11K Feb  4 20:49 rename.ul
-rwxr-xr-x 1 root   root     48K Jan 10 10:10 rendercheck
-rwxr-xr-x 1 root   root     11K Feb  4 20:49 renice
-rwxr-xr-x 1 root   root    2.2K Dec 11 17:34 report-hw
lrwxrwxrwx 1 root   root       4 Feb  8 15:34 reset -> tset
-rwxr-xr-x 1 root   root     15K Sep 28 12:42 resize
-rwxr-xr-x 1 root   root     19K Feb 18 13:55 resizecons
-rwxr-xr-x 1 root   root     31K Feb  4 20:49 resizepart
-rwxr-xr-x 1 root   root     11K Feb  4 20:49 rev
-rwxr-xr-x 1 root   root     86K Dec  6 16:53 rfcomm
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 rgb3toppm
-rwxr-xr-x 1 root   root      30 Jul  6  2011 rgrep
-rwxr-xr-x 1 root   root     11K Nov 29 21:56 rhythmbox
-rwxr-xr-x 1 root   root     33K Nov 29 21:56 rhythmbox-client
-rwxr-xr-x 1 root   root     31K Feb  7 10:43 rletopnm
lrwxrwxrwx 1 root   root      24 Feb 26 18:15 rlogin -> /etc/alternatives/rlogin
lrwxrwxrwx 1 root   root      22 Feb 26 19:53 rmic -> /etc/alternatives/rmic
lrwxrwxrwx 1 root   root      22 Feb 26 19:53 rmid -> /etc/alternatives/rmid
lrwxrwxrwx 1 root   root      29 Feb 26 19:53 rmiregistry -> /etc/alternatives/rmiregistry
-rwxr-xr-x 1 root   root     173 Dec 11 17:52 routef
-rwxr-xr-x 1 root   root    1.3K Dec 11 17:52 routel
-rwxr-xr-x 1 root   root    7.4M Nov 26 09:09 rpcclient
-rwxr-xr-x 1 root   root     87K Feb  9 07:26 rpcgen
-rwxr-xr-x 1 root   root     27K Oct  1 21:29 rpl8
lrwxrwxrwx 1 root   root      21 Feb 26 18:15 rsh -> /etc/alternatives/rsh
-rwxr-xr-x 1 root   root    2.6K Oct  9 00:33 rstart
-rwxr-xr-x 1 root   root    1.5K Oct  9 00:33 rstartd
-rwxr-xr-x 1 root   root    400K Dec  2 23:36 rsync
-rwxr-xr-x 1 root   root     31K Dec  3 12:36 rtmpdump
lrwxrwxrwx 1 root   root       6 Dec 13 11:25 rtstat -> lnstat
-rwxr-xr-x 1 root   root     31K Jan 17 07:03 runcon
-rwxr-xr-x 1 root   root     17K Jan  8 10:38 run-mailcap
-rwxr-xr-x 1 root   root      57 Oct  1 17:13 run-with-aspell
lrwxrwxrwx 1 root   root      23 Feb 26 18:12 rview -> /etc/alternatives/rview
lrwxrwxrwx 1 root   root      22 Feb 26 18:49 rvim -> /etc/alternatives/rvim
-rwxr-xr-x 1 root   root      42 Dec 13 16:34 rvlc
-rwxr-xr-x 2 root   root     53K Feb 10 17:42 s2p
-rwxr-xr-x 1 root   root    100K Sep 20 01:19 sane-find-scanner
-rwxr-xr-x 1 root   root     11K Sep 18 23:47 savelog
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 sbigtopgm
-rwxr-xr-x 1 root   root     48K Sep 20 01:19 scanimage
lrwxrwxrwx 1 root   root      27 Feb 26 19:53 schemagen -> /etc/alternatives/schemagen
-rwxr-xr-x 1 root   root     63K Feb 12 10:58 scp
-rwxr-xr-x 1 root   root      90 Mar  8 15:09 scp-dbus-service
-rwxr-xr-x 1 root   root     11K Feb 18 13:55 screendump
-rwxr-xr-x 1 root   root     12M Sep 10 13:30 scribus
-rwxr-xr-x 1 root   root     15K Feb  4 20:49 script
-rwxr-xr-x 1 root   root     11K Feb  4 20:49 scriptreplay
lrwxrwxrwx 1 root   root      16 Oct  8 22:55 scrollkeeper-config -> rarian-sk-config
lrwxrwxrwx 1 root   root      17 Oct  8 22:55 scrollkeeper-extract -> rarian-sk-extract
lrwxrwxrwx 1 root   root      18 Oct  8 22:55 scrollkeeper-gen-seriesid -> rarian-sk-gen-uuid
lrwxrwxrwx 1 root   root      16 Oct  8 22:55 scrollkeeper-get-cl -> rarian-sk-get-cl
lrwxrwxrwx 1 root   root      26 Oct  8 22:55 scrollkeeper-get-content-list -> rarian-sk-get-content-list
lrwxrwxrwx 1 root   root      35 Oct  8 22:55 scrollkeeper-get-extended-content-list -> rarian-sk-get-extended-content-list
lrwxrwxrwx 1 root   root      21 Oct  8 22:55 scrollkeeper-get-index-from-docpath -> rarian-sk-get-scripts
lrwxrwxrwx 1 root   root      21 Oct  8 22:55 scrollkeeper-get-toc-from-docpath -> rarian-sk-get-scripts
lrwxrwxrwx 1 root   root      21 Oct  8 22:55 scrollkeeper-get-toc-from-id -> rarian-sk-get-scripts
lrwxrwxrwx 1 root   root      17 Oct  8 22:55 scrollkeeper-install -> rarian-sk-install
lrwxrwxrwx 1 root   root      20 Oct  8 22:55 scrollkeeper-preinstall -> rarian-sk-preinstall
lrwxrwxrwx 1 root   root      17 Oct  8 22:55 scrollkeeper-rebuilddb -> rarian-sk-rebuild
lrwxrwxrwx 1 root   root      17 Oct  8 22:55 scrollkeeper-uninstall -> rarian-sk-install
lrwxrwxrwx 1 root   root      16 Oct  8 22:55 scrollkeeper-update -> rarian-sk-update
-rwxr-xr-x 1 root   root     47K Feb 25 10:36 sdiff
-rwxr-xr-x 1 root   root    165K Dec  6 16:53 sdptool
-rwxr-xr-x 1 root   root    728K Nov 12 11:00 seahorse
lrwxrwxrwx 1 root   root      11 Jan  8 10:38 see -> run-mailcap
-rwxr-xr-x 1 root   root     474 Jan 23 17:09 select-default-iwrap
-rwxr-xr-x 1 root   root    1.2K Jul 12  2012 select-editor
-rwxr-xr-x 1 root   root    1.5K Jul 12  2012 sensible-browser
-rwxr-xr-x 1 root   root    1.1K Jul 12  2012 sensible-editor
-rwxr-xr-x 1 root   root     288 Jul 12  2012 sensible-pager
-rwxr-xr-x 1 root   root     23K Nov 14 01:56 sensors
-rwxr-xr-x 1 root   root     14K Nov 14 01:56 sensors-conf-convert
-rwxr-xr-x 1 root   root     47K Jan 17 07:03 seq
lrwxrwxrwx 1 root   root      27 Feb 26 19:53 serialver -> /etc/alternatives/serialver
lrwxrwxrwx 1 root   root      28 Feb 26 19:53 servertool -> /etc/alternatives/servertool
lrwxrwxrwx 1 root   root      17 Jan 30 12:58 service -> /usr/sbin/service
-rwxr-xr-x 1 root   root    1.1K Feb 13 10:38 session-installer
-rwxr-xr-x 1 root   root     15K Jul 19  2012 session-migration
-rwxr-xr-x 1 root   root     15K Dec  4 02:36 sessreg
-rwxr-xr-x 1 root   root     15K Feb  4 20:49 setarch
lrwxrwxrwx 1 root   root      12 Nov 29 14:51 setfacl -> /bin/setfacl
-rwxr-xr-x 1 root   root     11K Feb 18 13:55 setkeycodes
-rwxr-xr-x 1 root   root     11K Feb 18 13:55 setleds
-rwxr-xr-x 1 root   root     11K Feb 18 13:55 setlogcons
-rwxr-xr-x 1 root   root     11K Feb 18 13:55 setmetamode
-rwxr-xr-x 1 root   root     23K Dec  2 00:01 setpci
-rwxr-xr-x 1 root   root    6.2K Feb  4 20:49 setsid
-rwxr-xr-x 1 root   root     27K Feb  4 20:49 setterm
-rwxr-xr-x 1 root   root     23K May 11  2012 setxkbmap
-rwxr-xr-x 1 root   root    107K Feb 12 10:58 sftp
lrwxrwxrwx 1 root   root       6 Jan  2 17:33 sg -> newgrp
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 sgitopnm
-rwxr-xr-x 1 root   root     594 Feb 18 17:18 sha1pass
-rwxr-xr-x 1 root   root     39K Jan 17 07:03 sha1sum
-rwxr-xr-x 1 root   root     47K Jan 17 07:03 sha224sum
-rwxr-xr-x 1 root   root     47K Jan 17 07:03 sha256sum
-rwxr-xr-x 1 root   root     51K Jan 17 07:03 sha384sum
-rwxr-xr-x 1 root   root     51K Jan 17 07:03 sha512sum
-rwxr-xr-x 1 root   root    7.8K Feb 10 17:42 shasum
-rwxr-xr-x 1 root   root    3.9M Nov 30 13:35 shotwell
-rwxr-xr-x 1 root   root    1.1K Nov 30 13:34 shotwell-settings-migrator
-rwxr-xr-x 1 root   root     23K Nov 30 13:35 shotwell-video-thumbnailer
-rwxr-xr-x 1 root   root     19K Feb 18 13:55 showconsolefont
-rwxr-xr-x 1 root   root     15K May 11  2012 showfont
-rwxr-xr-x 1 root   root     15K Feb 18 13:55 showkey
-rwxr-xr-x 1 root   root    6.2K Dec  4 02:36 showrgb
-rwxr-xr-x 1 root   root     51K Jan 17 07:03 shred
-rwxr-xr-x 1 root   root     47K Jan 17 07:03 shuf
-rwxr-xr-x 1 root   root    458K Feb 27 23:04 signond
-rwxr-xr-x 1 root   root     60K Feb 27 23:04 signonpluginprocess
-rwxr-xr-x 1 root   root    206K Jan 10 16:03 signon-ui
-rwxr-xr-x 1 root   root    254K Jan 16 05:08 simple-scan
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 sirtopnm
-rwxr-xr-x 1 root   root     31K Feb 22 15:24 size
-rwxr-xr-x 1 root   root     23K Jan  4 16:31 skill
-rwxr-xr-x 1 root   root     19K Jan  4 16:31 slabtop
-rwxr-xr-x 1 root   root     19K Feb  7 10:43 sldtoppm
lrwxrwxrwx 1 root   root       3 Feb 12 10:57 slogin -> ssh
-rwxr-xr-x 1 root   root     19K Mar  9 08:07 slxdecode
-rwxr-xr-x 1 root   root    5.9M Nov 26 09:09 smbcacls
-rwxr-xr-x 1 root   root    6.0M Nov 26 09:09 smbclient
-rwxr-xr-x 1 root   root    5.9M Nov 26 09:09 smbcquotas
-rwxr-xr-x 1 root   root    6.2M Nov 26 09:09 smbget
-rwxr-xr-x 1 root   root    5.9M Nov 26 09:09 smbpasswd
-rwxr-xr-x 1 root   root    3.3M Nov 26 09:09 smbspool
-rwxr-xr-x 1 root   root    4.8K Nov 26 09:07 smbtar
-rwxr-xr-x 1 root   root    5.9M Nov 26 09:09 smbtree
-rwxr-xr-x 1 root   root     23K Oct  9 00:33 smproxy
lrwxrwxrwx 1 root   root       5 Jan  4 16:31 snice -> skill
-rwxr-xr-x 1 root   root     31K Feb  9 17:11 soelim
lrwxrwxrwx 1 root   root      34 Mar  9 03:02 soffice -> ../lib/libreoffice/program/soffice
lrwxrwxrwx 1 root   root      40 Mar  1 20:40 software-center -> ../share/software-center/software-center
lrwxrwxrwx 1 root   root      15 Mar  1 20:40 software-center-gtk3 -> software-center
-rwxr-xr-x 1 root   root    4.2K Feb 15 19:14 software-properties-gtk
-rwxr-xr-x 1 root   root    104K Jan 17 07:03 sort
-rwxr-xr-x 1 root   root    4.3K Feb  9 07:22 sotruss
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 spctoppm
-rwxr-xr-x 1 root   root     220 Aug 21  2012 spd-conf
-rwxr-xr-x 1 root   root     19K Aug 21  2012 spd-say
-rwxr-xr-x 1 root   root     27K Feb 28 02:54 speaker-test
-rwxr-xr-x 1 root   root    132K Aug 21  2012 speech-dispatcher
-rwxr-xr-x 1 root   root     18K Feb 10 17:42 splain
-rwxr-xr-x 1 root   root     64K Jan 17 07:03 split
-rwxr-xr-x 1 root   root    3.0K Oct  8 13:49 splitdiff
-rwxr-xr-x 1 root   root     11K Feb 18 13:55 splitfont
-rwxr-xr-x 1 root   root     23K Feb  9 07:26 sprof
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 sputoppm
-rwxr-xr-x 1 root   root    424K Feb 12 10:58 ssh
-rwxr-xr-x 1 root   root    143K Feb 12 10:58 ssh-add
-rwxr-sr-x 1 root   ssh     127K Feb 12 10:58 ssh-agent
-rwxr-xr-x 1 root   root    1.5K Aug 23  2010 ssh-argv0
lrwxrwxrwx 1 root   root      29 Feb 26 19:30 ssh-askpass -> /etc/alternatives/ssh-askpass
-rwxr-xr-x 1 root   root    1.5K Feb 12 10:56 ssh-copy-id
-rwxr-xr-x 1 root   root    191K Feb 12 10:58 ssh-keygen
-rwxr-xr-x 1 root   root    228K Feb 12 10:58 ssh-keyscan
-rwxr-xr-x 1 root   root    131K Feb 12 10:58 ssh-vulnkey
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 st4topgm
-rwxr-xr-x 1 root   root    1001 Mar  1 14:33 start-pulseaudio-kde
-rwxr-xr-x 1 root   root    1.2K Mar  1 14:33 start-pulseaudio-x11
-rwxr-xr-x 1 root   root    4.8K Jun 18  2012 startx
-rwxr-xr-x 1 root   root     71K Jan 17 07:03 stat
-rwxr-xr-x 1 root   root     63K Jan 17 07:03 stdbuf
-rwxr-xr-x 1 root   root    5.4K Feb 27 18:32 steam
-rwxr-xr-x 1 root   root     11K Feb 25 01:35 steamdeps
-rwxr-xr-x 1 root   root    814K Oct 29 11:53 stopmotion
-rwxr-xr-x 1 root   root    307K Oct  3 00:37 strace
lrwxrwxrwx 1 root   root      24 Feb 26 19:41 stream -> /etc/alternatives/stream
-rwxr-xr-x 1 root   root    6.2K Feb 25 19:54 stream.im6
-rwxr-xr-x 1 root   root     67K May 11  2010 streams
-rwxr-xr-x 1 root   root     27K Feb 22 15:24 strings
-rwxr-xr-x 1 root   root    216K Feb 22 15:24 strip
-rwsr-xr-x 1 root   root    119K Feb 28 14:17 sudo
lrwxrwxrwx 1 root   root       4 Feb 28 14:17 sudoedit -> sudo
-rwxr-xr-x 1 root   root     64K Feb 28 14:17 sudoreplay
-rwxr-xr-x 1 root   root     35K Jan 17 07:03 sum
-rwxr-xr-x 1 root   root    3.1K Dec  3  2011 su-to-root
-rwxr-xr-x 1 root   root      46 Dec 13 16:34 svlc
-rwxr-xr-x 1 root   root      43 Jan 30  2012 synaptic-pkexec
-rwxr-xr-x 1 root   root     23K Jan 17 11:38 synclient
-rwxr-xr-x 1 root   root     15K Jan 17 11:38 syndaemon
-rwxr-xr-x 1 root   root     51K Feb 18 13:46 syslinux
-rwxr-xr-x 1 root   root    1.4K Feb 18 17:18 syslinux2ansi
-rwxr-xr-x 1 root   root     30K Apr 16  2012 syslinux-legacy
-rwxr-xr-x 1 root   root     176 Jul  1  2012 system-config-lvm
-rwxr-xr-x 1 root   root      95 Mar  8 15:09 system-config-printer
-rwxr-xr-x 1 root   root      80 Mar  8 15:09 system-config-printer-applet
-rwxr-xr-x 1 root   root     35K Jul  2  2012 t1ascii
-rwxr-xr-x 1 root   root     40K Jul  2  2012 t1asm
-rwxr-xr-x 1 root   root     35K Jul  2  2012 t1binary
-rwxr-xr-x 1 root   root     43K Jul  2  2012 t1disasm
-rwxr-xr-x 1 root   root     47K Jul  2  2012 t1mac
-rwxr-xr-x 1 root   root     39K Jul  2  2012 t1unmac
-rwxr-xr-x 1 root   root     15K Feb  8 15:34 tabs
-rwxr-xr-x 1 root   root     31K Jan 17 07:03 tac
-rwxr-xr-x 1 root   root     63K Jan 17 07:03 tail
-rwxr-xr-x 1 root   root     237 Jan 25 20:38 tap2deb
-rwxr-xr-x 1 root   root     325 Jan 25 20:38 tap2rpm
-rwxr-xr-x 1 root   root     219 Jan 25 20:38 tapconvert
-rwxr-xr-x 1 root   root     23K Mar  6 11:53 tasksel
-rwxr-xr-x 1 root   root     19K Feb  4 20:49 taskset
-rwxr-xr-x 1 root   root    107K Feb  9 17:11 tbl
lrwxrwxrwx 1 root   root      23 Feb 26 19:40 tclsh -> /etc/alternatives/tclsh
-rwxr-xr-x 1 root   root    6.2K Dec  5 14:13 tclsh8.5
-rwxr-xr-x 1 root   root     31K Jan 17 07:03 tee
-rwxr-xr-x 1 root   root     36K Mar  1 02:17 telepathy-indicator
lrwxrwxrwx 1 root   root      24 Feb 26 18:15 telnet -> /etc/alternatives/telnet
-rwxr-xr-x 1 root   root     94K Oct  3 00:40 telnet.netkit
-rwxr-xr-x 1 root   root     35K Jan 17 07:03 test
lrwxrwxrwx 1 root   root      26 Feb 26 19:29 testparm -> /etc/alternatives/testparm
-rwxr-xr-x 1 root   root    1.5M Nov 26 09:09 testparm.samba3
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 tgatoppm
-rwxr-xr-x 1 root   root    2.3K Jun 18  2012 tgz
-rwxr-xr-x 1 root   root    2.0K Aug 17  2012 thin-client-config-agent
-rwxr-xr-x 1 root   root     19K Feb  7 10:43 thinkjettopbm
lrwxrwxrwx 1 root   root      33 Feb 27 23:26 thunderbird -> ../lib/thunderbird/thunderbird.sh
-rwxr-xr-x 1 root   root     55K Feb  8 15:34 tic
-rwxr-xr-x 1 root   root     19K Feb  7 10:43 tifftopnm
-rwxr-xr-x 1 root   root     15K Jun 29  2012 time
-rwxr-xr-x 1 root   root     52K Jan 17 07:03 timeout
-rwxr-xr-x 1 root   root     15K Jan  4 16:31 tload
lrwxrwxrwx 1 root   root      27 Feb 26 19:53 tnameserv -> /etc/alternatives/tnameserv
-rwxr-xr-x 1 root   root     15K Feb  8 15:34 toe
-rwxr-xr-x 1 root   root     71K Jan  4 16:31 top
-rwxr-xr-x 1 root   root     93K May 23  2012 toshset
-rwxr-xr-x 1 root   root     18K Feb 27 22:25 totem
-rwxr-xr-x 1 root   root     19K Feb 27 22:25 totem-audio-preview
-rwxr-xr-x 1 root   root     39K Feb 27 22:25 totem-video-thumbnailer
lrwxrwxrwx 1 root   root      10 Jan 17 07:03 touch -> /bin/touch
-rwxr-xr-x 1 root   root     15K Feb  8 15:34 tput
-rwxr-xr-x 1 root   root     43K Jan 17 07:03 tr
-rwxr-xr-x 1 root   root     15K Oct  3 00:36 tracepath
-rwxr-xr-x 1 root   root     15K Oct  3 00:36 tracepath6
lrwxrwxrwx 1 root   root      28 Feb 27 00:15 traceproto -> /etc/alternatives/traceproto
-rwxr-xr-x 1 root   root    2.9K Dec 10 23:27 traceproto.db
lrwxrwxrwx 1 root   root      28 Feb 27 00:15 traceroute -> /etc/alternatives/traceroute
lrwxrwxrwx 1 root   root      29 Feb 26 18:15 traceroute6 -> /etc/alternatives/traceroute6
lrwxrwxrwx 1 root   root      13 Dec 10 23:27 traceroute6.db -> traceroute.db
-rwsr-xr-x 1 root   root     19K Oct  3 00:36 traceroute6.iputils
-rwxr-xr-x 1 root   root     68K Dec 10 23:27 traceroute.db
-rwxr-xr-x 1 root   root    1.6K Dec 10 23:27 traceroute-nanog
-rwxr-xr-x 1 root   root    762K Feb 25 12:54 transmission-gtk
-rwxr-xr-x 1 root   root     19K Jan 10 10:10 transset
-rwxr-xr-x 1 root   root     352 Jan 25 20:38 trial
-rwxr-xr-x 1 root   root    472K Feb  9 17:11 troff
-rwxr-xr-x 1 root   root     51K Jan 17 07:03 truncate
-rwxr-xr-x 1 root   root     19K Feb  8 15:34 tset
-rwxr-xr-x 1 root   root     35K Jan 17 07:03 tsort
-rwxr-xr-x 1 root   root     11K Mar 11 06:41 ttfread
-rwxr-xr-x 1 root   root     27K Jan 17 07:03 tty
-rwxr-xr-x 1 root   root     269 Jan 25 20:38 twistd
-rwxr-xr-x 1 root   root    7.2K Feb  9 07:22 tzselect
-rwxr-xr-x 1 root   root     15K Feb 21 20:31 u1sdtool
lrwxrwxrwx 1 root   root      10 Mar  7 15:15 ubuntu-bug -> apport-bug
-rwxr-xr-x 1 root   root    5.2K Jan 30 11:31 ubuntu-drivers
-rwxr-xr-x 1 root   root    1.1K Feb 22 22:11 ubuntuone-control-panel-qt
-rwxr-xr-x 1 root   root    3.8K Feb 21 20:31 ubuntuone-launch
-rwxr-xr-x 1 root   root    7.0K Mar  6 12:51 ubuntu-support-status
-rwxr-xr-x 1 root   root     19K Mar  6 05:16 ubuntu-webapps-update-index
-rwxr-xr-x 1 root   root     38K Mar 20  2012 ucf
-rwxr-xr-x 1 root   root     19K May 30  2008 ucfq
-rwxr-xr-x 1 root   root     11K May 30  2008 ucfr
-rwxr-xr-x 1 root   root     19K May 16  2012 ucs2any
-rwxr-xr-x 1 root   root     44K Oct 29 00:17 udisks
-rwxr-xr-x 1 root   root     48K Mar  4 14:02 udisksctl
-rwxr-xr-x 1 root   root     15K Oct 29 00:17 udisks-tcp-bridge
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 uic -> qtchooser
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 uic3 -> qtchooser
-rwxr-xr-x 1 root   root     15K Jan  8 09:54 ul
-rwxr-xr-x 1 root   root    164K Sep 20 01:19 umax_pp
-rwxr-xr-x 1 root   root     41K Dec 11 18:01 unattended-upgrade
lrwxrwxrwx 1 root   root      18 Dec 11 18:01 unattended-upgrades -> unattended-upgrade
-rwxr-xr-x 1 root   root     31K Jan 17 07:03 unexpand
-rwxr-xr-x 1 root   root     530 Feb 18 13:55 unicode_stop
-rwxr-xr-x 1 root   root     920 Jun  3  2009 uniconvertor
-rwxr-xr-x 1 root   root     39K Jan 17 07:03 uniq
-rwxr-xr-x 1 root   root    7.5K Mar 11 04:17 unity
-rwxr-xr-x 1 root   root     40K Mar  6 05:16 unity-webapps-desktop-file
-rwxr-xr-x 1 root   root     15K Mar  6 05:16 unity-webapps-runner
-rwxr-xr-x 1 root   root     27K Jan 17 07:03 unlink
lrwxrwxrwx 1 root   root      24 Feb 26 18:13 unlzma -> /etc/alternatives/unlzma
-rwxr-xr-x 1 root   root      52 Mar  9 01:50 unopkg
lrwxrwxrwx 1 root   root      27 Feb 26 19:53 unpack200 -> /etc/alternatives/unpack200
-rwxr-xr-x 1 root   root    208K Feb 20 20:36 unrar
-rwxr-xr-x 1 root   root     11K Feb  4 20:49 unshare
-rwxr-xr-x 1 root   root    5.9K Oct  8 13:49 unwrapdiff
lrwxrwxrwx 1 root   root       2 Jan  3 17:36 unxz -> xz
-rwxr-xr-x 2 root   root    159K Dec 13 16:17 unzip
-rwxr-xr-x 1 root   root     75K Dec 13 16:17 unzipsfx
-rwxr-xr-x 1 root   root     43K Nov 29 15:13 update-alternatives
lrwxrwxrwx 1 root   root      26 Feb 26 18:15 updatedb -> /etc/alternatives/updatedb
-rwxr-xr-x 1 root   root     43K Feb  8 17:31 updatedb.mlocate
-rwxr-xr-x 1 root   root     19K Dec  1 03:01 update-desktop-database
-rwxr-xr-x 1 root   root    5.5K Jan 23 10:35 update-gconf-defaults
-rwxr-xr-x 1 root   root    4.5K Mar  6 12:51 update-manager
-rwxr-xr-x 1 root   root    124K Dec  3  2011 update-menus
-rwxr-xr-x 1 root   root     672 Feb 25 14:32 update-mime-database
-rwxr-xr-x 1 root   root     48K Feb 25 14:32 update-mime-database.real
-rwxr-xr-x 1 root   root     69K Feb  1 23:08 update-notifier
-rwxr-xr-x 1 root   root    2.9K Dec  2 00:01 update-pciids
-rwxr-xr-x 1 root   root    6.1K Jun  1  2012 update-perl-sax-parsers
-rwxr-xr-x 1 root   root     15K Jan 31 09:37 upower
-rwxr-xr-x 1 root   root     11K Jan  4 16:31 uptime
-rwxr-xr-x 1 root   root    3.9K Feb  8 02:16 usb-creator-gtk
-rwxr-xr-x 1 root   root    4.2K Jan  9 15:46 usb-devices
-rwxr-xr-x 1 root   root     23K Jan  9 15:46 usbhid-dump
-rwxr-xr-x 1 root   root    6.2K Mar  9 08:07 usb_printerid
-rwxr-xr-x 1 root   root     31K Jan 17 07:03 users
-rwxr-xr-x 1 root   root     11K Feb  4 20:49 uuidgen
-rwxr-xr-x 1 root   root    3.6K Sep 28 12:42 uxterm
-rwxr-xr-x 1 root   root    2.3K Jun 18  2012 uz
-rwxr-xr-x 1 root   root    3.0K Feb 27 16:53 VBox
lrwxrwxrwx 1 root   root       4 Feb 27 16:53 vboxautostart -> VBox
lrwxrwxrwx 1 root   root       4 Feb 27 16:53 VBoxAutostart -> VBox
lrwxrwxrwx 1 root   root       4 Feb 27 16:53 vboxballoonctrl -> VBox
lrwxrwxrwx 1 root   root       4 Feb 27 16:53 VBoxBalloonCtrl -> VBox
lrwxrwxrwx 1 root   root       4 Feb 27 16:53 vboxheadless -> VBox
lrwxrwxrwx 1 root   root       4 Feb 27 16:53 VBoxHeadless -> VBox
lrwxrwxrwx 1 root   root       4 Feb 27 16:53 vboxmanage -> VBox
lrwxrwxrwx 1 root   root       4 Feb 27 16:53 VBoxManage -> VBox
lrwxrwxrwx 1 root   root       4 Feb 27 16:53 vboxsdl -> VBox
lrwxrwxrwx 1 root   root       4 Feb 27 16:53 VBoxSDL -> VBox
-rwxr-xr-x 1 root   root     11K Feb 27 16:54 VBoxTunctl
lrwxrwxrwx 1 root   root       4 Feb 27 16:53 VBoxVRDP -> VBox
lrwxrwxrwx 1 root   root       4 Feb 27 16:53 vboxwebsrv -> VBox
-rwxr-xr-x 1 root   root     46K May 14  2012 vgrabbj
lrwxrwxrwx 1 root   root      20 Feb 26 18:12 vi -> /etc/alternatives/vi
lrwxrwxrwx 1 root   root      22 Feb 26 18:12 view -> /etc/alternatives/view
-rwxr-xr-x 1 root   root     24K Aug  7  2012 viewres
lrwxrwxrwx 1 root   root      21 Feb 26 18:49 vim -> /etc/alternatives/vim
-rwxr-xr-x 1 root   root    2.0M Feb 20 15:55 vim.basic
lrwxrwxrwx 1 root   root      25 Feb 26 18:49 vimdiff -> /etc/alternatives/vimdiff
-rwxr-xr-x 1 root   root    764K Feb 20 15:54 vim.tiny
-rwxr-xr-x 1 root   root    2.1K Feb 20 15:54 vimtutor
-rwxr-xr-x 1 root   root     11K Jan 18 18:03 vino-passwd
-rwxr-xr-x 1 root   root     32K Jan 18 18:03 vino-preferences
lrwxrwxrwx 1 root   root       4 Feb 27 16:53 virtualbox -> VBox
lrwxrwxrwx 1 root   root       4 Feb 27 16:53 VirtualBox -> VBox
-rwxr-xr-x 1 root   root     15K Dec 13 16:35 vlc
-rwxr-xr-x 1 root   root     11K Dec 13 16:35 vlc-wrapper
-rwxr-xr-x 1 root   root     27K Jan  4 16:31 vmstat
-rwxr-xr-x 1 root   root     11K Aug  2  2012 vmwarectrl
-rwxr-xr-x 1 root   root    111K Jul 27  2011 vnstat
-rwxr-xr-x 1 root   root     10K Dec 24 09:49 volname
-rwxr-xr-x 1 root   root     23K Feb 22 23:48 vstp
lrwxrwxrwx 1 root   root      19 Feb 26 18:12 w -> /etc/alternatives/w
-rwxr-sr-x 1 root   tty      19K Feb  4 20:49 wall
-rwxr-xr-x 1 root   root     24K Jan  4 16:31 watch
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 wbmptopbm
-rwxr-xr-x 1 root   root     39K Jan 17 07:03 wc
-rwxr-xr-x 1 root   root     286 Jan 22 22:13 wftopfa
-rwxr-xr-x 1 root   root    398K Nov  7 17:33 wget
-rwxr-xr-x 1 root   root     43K Dec 16 17:10 whatis
-rwxr-xr-x 1 root   root     15K Feb  4 20:49 whereis
lrwxrwxrwx 1 root   root      10 Feb 26 18:12 which -> /bin/which
-rwxr-xr-x 1 root   root     51K Jan 17 07:03 who
-rwxr-xr-x 1 root   root     27K Jan 17 07:03 whoami
-rwxr-xr-x 1 root   root     52K Feb 26 11:21 whoopsie
-rwxr-xr-x 1 root   root     36K Nov 26 16:17 whoopsie-preferences
-rwxr-xr-x 1 root   root     19K Feb  7 10:43 winicontoppm
lrwxrwxrwx 1 root   root      22 Feb 26 19:40 wish -> /etc/alternatives/wish
-rwxr-xr-x 1 root   root    6.2K Dec  8 08:09 wish8.5
-rwxr-xr-x 1 root   root     15K Feb 25 18:52 wmf2eps
-rwxr-xr-x 1 root   root     15K Feb 25 18:52 wmf2fig
-rwxr-xr-x 1 root   root     15K Feb 25 18:52 wmf2gd
-rwxr-xr-x 1 root   root     15K Feb 25 18:52 wmf2svg
-rwxr-xr-x 1 root   root     15K Feb 25 18:52 wmf2x
-rwxr-xr-x 1 root   root    389K Oct  1 17:25 wodim
-rwxr-xr-x 1 root   root     11K Oct  1 17:13 word-list-compress
-rwxr-xr-x 1 root   root     35K Dec  7 10:29 wpa_passphrase
-rwxr-xr-x 1 root   root     19K Jan  4 16:31 w.procps
lrwxrwxrwx 1 root   root      23 Feb 26 18:15 write -> /etc/alternatives/write
lrwxrwxrwx 1 root   root      23 Feb 26 19:53 wsgen -> /etc/alternatives/wsgen
lrwxrwxrwx 1 root   root      26 Feb 26 19:53 wsimport -> /etc/alternatives/wsimport
-rwsr-sr-x 1 root   root     10K Oct  2 15:41 X
lrwxrwxrwx 1 root   root       1 Oct  2 15:09 X11 -> .
-rwxr-xr-x 1 root   root    135K Jan 10 10:10 x11perf
-rwxr-xr-x 1 root   root    2.8K Jan 10 10:10 x11perfcomp
lrwxrwxrwx 1 root   root       7 Feb  4 20:49 x86_64 -> setarch
lrwxrwxrwx 1 root   root       7 Dec 19 10:06 x86_64-linux-gnu-cpp -> cpp-4.7
lrwxrwxrwx 1 root   root       7 Mar  7 22:48 x86_64-linux-gnu-cpp-4.7 -> cpp-4.7
lrwxrwxrwx 1 root   root       7 Dec 19 10:06 x86_64-linux-gnu-gcc -> gcc-4.7
lrwxrwxrwx 1 root   root       7 Mar  7 22:54 x86_64-linux-gnu-gcc-4.7 -> gcc-4.7
lrwxrwxrwx 1 root   root      10 Mar  7 22:54 x86_64-linux-gnu-gcc-ar-4.7 -> gcc-ar-4.7
lrwxrwxrwx 1 root   root      10 Mar  7 22:54 x86_64-linux-gnu-gcc-nm-4.7 -> gcc-nm-4.7
lrwxrwxrwx 1 root   root      14 Mar  7 22:54 x86_64-linux-gnu-gcc-ranlib-4.7 -> gcc-ranlib-4.7
-rwxr-xr-x 1 root   root     43K Oct 29 10:49 xargs
-rwxr-xr-x 1 root   root     40K Dec  4 02:47 xauth
-rwxr-xr-x 1 root   root     21K Jan 10 10:10 xbiff
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 xbmtopbm
-rwxr-xr-x 1 root   root     32K Jan 10 10:10 xcalc
-rwxr-xr-x 1 root   root     19K Jan 10 10:10 xclipboard
-rwxr-xr-x 1 root   root     42K Jan 10 10:10 xclock
-rwxr-xr-x 1 root   root     31K Dec  4 02:36 xcmsdb
-rwxr-xr-x 1 root   root     20K Jan 10 10:10 xconsole
-rwxr-xr-x 1 root   root     15K Jan 10 10:10 xcursorgen
-rwxr-xr-x 1 root   root     15K Jan 10 10:10 xcutsel
-rwxr-xr-x 1 root   root     16K Oct  4  2011 xdg-desktop-icon
-rwxr-xr-x 1 root   root     38K Oct  4  2011 xdg-desktop-menu
-rwxr-xr-x 1 root   root     21K Oct  4  2011 xdg-email
-rwxr-xr-x 1 root   root     25K Oct  4  2011 xdg-icon-resource
-rwxr-xr-x 1 root   root     34K Oct  4  2011 xdg-mime
-rwxr-xr-x 1 root   root     14K Oct  4  2011 xdg-open
-rwxr-xr-x 1 root   root     25K Oct  4  2011 xdg-screensaver
-rwxr-xr-x 1 root   root     25K Oct  4  2011 xdg-settings
-rwxr-xr-x 1 root   root     234 Oct  9 17:18 xdg-user-dir
-rwxr-xr-x 1 root   root     19K Jan 23 10:34 xdg-user-dirs-gtk-update
-rwxr-xr-x 1 root   root     19K Oct  9 17:18 xdg-user-dirs-update
-rwxr-xr-x 1 root   root    4.4K Feb 14 03:11 xdiagnose
-rwxr-xr-x 1 root   root     91K Jan 10 10:10 xditview
-rwxr-xr-x 1 root   root     32K Aug  7  2012 xdpyinfo
-rwxr-xr-x 1 root   root     11K Aug  7  2012 xdriinfo
-rwxr-xr-x 1 root   root    6.4K Feb 14 03:11 xedid
-rwxr-xr-x 1 root   root    615K Jan 10 10:10 xedit
-rwxr-xr-x 1 root   root    2.1M Mar  7 02:48 Xephyr
-rwxr-xr-x 1 root   root     27K Aug  7  2012 xev
-rwxr-xr-x 1 root   root     20K Jan 10 10:10 xeyes
-rwxr-xr-x 1 root   root    244K Jan 20 12:07 xfburn
-rwxr-xr-x 1 root   root     27K May 18  2012 xfconf-query
-rwxr-xr-x 1 root   root     29K Aug  7  2012 xfd
-rwxr-xr-x 1 root   root     37K Aug  7  2012 xfontsel
-rwxr-xr-x 1 root   root    597K Nov 17 04:42 xfreerdp
-rwxr-xr-x 1 root   root     11K May 11  2012 xfsinfo
-rwxr-xr-x 1 root   root     11K Dec  4 02:36 xgamma
-rwxr-xr-x 1 root   root     63K Jan 10 10:10 xgc
-rwxr-xr-x 1 root   root    221K Mar  7 16:02 xgettext
-rwxr-xr-x 1 root   root     15K Dec  4 02:36 xhost
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 ximtoppm
-rwxr-xr-x 1 root   root     19K Jun 18  2012 xinit
-rwxr-xr-x 1 root   root     48K Aug 15  2012 xinput
lrwxrwxrwx 1 root   root      21 Feb 26 19:53 xjc -> /etc/alternatives/xjc
-rwxr-xr-x 1 root   root     11K May 11  2012 xkbbell
-rwxr-xr-x 1 root   root    201K May 11  2012 xkbcomp
-rwxr-xr-x 1 root   root     35K May 11  2012 xkbevd
-rwxr-xr-x 1 root   root     99K May 11  2012 xkbprint
-rwxr-xr-x 1 root   root     24K May 11  2012 xkbvleds
-rwxr-xr-x 1 root   root     20K May 11  2012 xkbwatch
-rwxr-xr-x 1 root   root     15K Dec  4 02:36 xkeystone
-rwxr-xr-x 1 root   root     15K Aug  7  2012 xkill
-rwxr-xr-x 1 root   root     16K Jan 10 10:10 xload
-rwxr-xr-x 1 root   root     20K Jan 10 10:10 xlogo
-rwxr-xr-x 1 root   root     11K Aug  7  2012 xlsatoms
-rwxr-xr-x 1 root   root     15K Aug  7  2012 xlsclients
-rwxr-xr-x 1 root   root     19K Aug  7  2012 xlsfonts
-rwxr-xr-x 1 root   root     37K Jan 10 10:10 xmag
-rwxr-xr-x 1 root   root     59K Jan 10 10:10 xman
-rwxr-xr-x 1 root   root     20K Aug  7  2012 xmessage
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 xmlpatterns -> qtchooser
lrwxrwxrwx 1 root   root       9 Feb 12 15:38 xmlpatternsvalidator -> qtchooser
-rwxr-xr-x 1 root   root     31K Dec  4 02:36 xmodmap
-rwxr-xr-x 1 root   root     11K Jan 10 10:10 xmore
-rwxr-xr-x 1 root   root    2.2M Mar  7 02:47 Xorg
-rwxr-xr-x 1 root   root    2.9K Feb 14 03:11 xpci
-rwxr-xr-x 1 root   root     15K Feb  7 10:43 xpmtoppm
-rwxr-xr-x 1 root   root     37K Aug  7  2012 xprop
-rwxr-xr-x 1 root   root     15K Mar  9 08:07 xqxdecode
-rwxr-xr-x 1 root   root     51K Dec  4 02:36 xrandr
-rwxr-xr-x 1 root   root    4.0K Feb 14 03:11 xrandr-tool
-rwxr-xr-x 1 root   root     27K Dec  4 02:36 xrdb
-rwxr-xr-x 1 root   root     11K Dec  4 02:36 xrefresh
-rwxr-xr-x 1 root   root    2.8K Jan 10 02:05 xrotate
lrwxrwxrwx 1 root   root      35 Feb 26 19:31 x-session-manager -> /etc/alternatives/x-session-manager
-rwxr-xr-x 1 root   root     31K Dec  4 02:36 xset
-rwxr-xr-x 1 root   root     11K Dec  4 02:36 xsetmode
-rwxr-xr-x 1 root   root     11K Dec  4 02:36 xsetpointer
-rwxr-xr-x 1 root   root     19K Dec  4 02:36 xsetroot
-rwxr-xr-x 1 root   root     43K Jan 18 09:18 xsetwacom
-rwxr-xr-x 1 root   root     84K Oct  9 00:33 xsm
-rwxr-xr-x 1 root   root     15K Dec  4 02:36 xstdcmap
-rwxr-xr-x 1 root   root    4.0K Feb 10 17:42 xsubpp
-rwxr-xr-x 1 root   root    441K Sep 28 12:42 xterm
lrwxrwxrwx 1 root   root      37 Feb 26 19:31 x-terminal-emulator -> /etc/alternatives/x-terminal-emulator
-rwxr-xr-x 1 root   root     32K Dec  4 02:36 xvidtune
-rwxr-xr-x 1 root   root     15K Aug  7  2012 xvinfo
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 xvminitoppm
-rwxr-xr-x 1 root   root     27K Jan 10 10:10 xwd
-rwxr-xr-x 1 root   root     19K Feb  7 10:43 xwdtopnm
lrwxrwxrwx 1 root   root      34 Feb 26 19:40 x-window-manager -> /etc/alternatives/x-window-manager
-rwxr-xr-x 1 root   root     39K Aug  7  2012 xwininfo
-rwxr-xr-x 1 root   root     27K Jan 10 10:10 xwud
lrwxrwxrwx 1 root   root      31 Feb 26 19:31 x-www-browser -> /etc/alternatives/x-www-browser
-rwxr-xr-x 1 root   root     15K Feb 20 15:55 xxd
-rwxr-xr-x 1 root   root     68K Jan  3 17:36 xz
lrwxrwxrwx 1 root   root       2 Jan  3 17:36 xzcat -> xz
lrwxrwxrwx 1 root   root       6 Jan  3 17:36 xzcmp -> xzdiff
-rwxr-xr-x 1 root   root    5.4K Jan  3 17:36 xzdiff
lrwxrwxrwx 1 root   root       6 Jan  3 17:36 xzegrep -> xzgrep
lrwxrwxrwx 1 root   root       6 Jan  3 17:36 xzfgrep -> xzgrep
-rwxr-xr-x 1 root   root    5.3K Jan  3 17:36 xzgrep
-rwxr-xr-x 1 root   root    1.8K Jan  3 17:36 xzless
-rwxr-xr-x 1 root   root    2.2K Jan  3 17:36 xzmore
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 ybmtopbm
-rwxr-xr-x 1 root   root     52K Nov 12 21:50 yelp
-rwxr-xr-x 1 root   root     27K Jan 17 07:03 yes
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 yuvsplittoppm
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 yuvtoppm
-rwxr-xr-x 1 root   root     15K Feb  9 07:26 zdump
-rwxr-xr-x 1 root   root     11K Feb  7 10:43 zeisstopnm
-rwxr-xr-x 1 root   root    413K Sep  6  2012 zeitgeist-daemon
-rwxr-xr-x 1 root   root    121K Nov 13 02:29 zeitgeist-datahub
-rwxr-xr-x 1 root   root     95K Nov  6 18:12 zenity
-rwxr-xr-x 1 root   root    184K Dec  7 23:42 zip
-rwxr-xr-x 1 root   root     85K Dec  7 23:42 zipcloak
-rwxr-xr-x 1 root   root    2.9K Dec 13 16:17 zipgrep
-rwxr-xr-x 2 root   root    159K Dec 13 16:17 zipinfo
-rwxr-xr-x 1 root   root     80K Dec  7 23:42 zipnote
-rwxr-xr-x 1 root   root     80K Dec  7 23:42 zipsplit
-rwxr-xr-x 1 root   root     23K Mar  9 08:07 zjsdecode
-rwxr-xr-x 1 root   root     11K Mar  8 16:21 zlib-flate
-rwxr-xr-x 1 root   root     47K Dec 16 17:10 zsoelim
-rwxr-xr-x 1 root   root     91K Dec  5 12:53 zsync
-rwxr-xr-x 1 root   root     87K Dec  5 12:53 zsyncmake
```

---

### Post by zzllxxllzz on 2013-03-11
Aha! Thank you! 

I also found what I was looking for by going to home folder > file system (It was too easy, I feel silly now)

And thanks for correcting my typo (re: usr versus user).

---

