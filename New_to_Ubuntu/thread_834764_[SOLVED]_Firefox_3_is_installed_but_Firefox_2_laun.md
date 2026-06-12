---
title: "[SOLVED] Firefox 3 is installed but Firefox 2 launches?"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by flyingsolo on 2008-06-19
I've upgraded to FF3 on an Ubuntu laptop, iMac, Windows machine at work, Windows partition on the laptop but was not successful on my home Ubuntu desktop.  For the Ubuntu laptop, I just upgraded via repositories but this doesn't seem to work for the Desktop.  In Synaptic, it looks as though FF3 is installed but it is still FF2 that opens via the icon on task bar.  Can't understand why it is a problem with this one machine!?

---

### Post by aysiu on 2008-06-19
Can you explain a bit more about your situation?

Did you ever install Firefox from Mozilla, or have you been sticking strictly with the Ubuntu version of Firefox?

What version of Ubuntu are you using? 8.04? 7.10?

---

### Post by RequinB4 on 2008-06-19
You may need to go to edit menus (right click menu on the ubuntu logo) and check the other firefox under internet.

---

### Post by Giant Speck on 2008-06-19
It's probably because the Firefox icon on your taskbar is still pointing at Firefox 2.0.  You need to remove it and then add the icon that points toward Firefox 3.0.

I'm not sure how that's done in Ubuntu, but in Kubuntu, I'd simply right-click the Firefox 2.0 icon on the Quick Launcher applet of my panel, select "Remove," and then right click the Quick Launcher again, go to the "Add application" menu and select Firefox 3.0 under Internet.

---

### Post by flyingsolo on 2008-06-19
Sorry, guests came over so I missed the replies above.

@Aysiu:  I'm using Hardy Heron; don't know how I originally put FF on this machine b/c it's one of several I have but probably it was just installed as part of the original Ubuntu install rather than going to Mozilla for it.  This machine was on Dapper for a long time until Hardy came out and just did the upgrade, no fresh install.

As for using the Edit Menu suggestion, there is only one FF icon to choose to add to taskbar or applications and it keeps giving FF2. (that is, I don't have a choice of two FF's 2 & 3)

---

### Post by cod3rbro on 2008-06-19
Try to remove Firefox 2 first, reboot, and install Firefox 3

---

### Post by flyingsolo on 2008-06-19
By 'remove' FF 2, do you mean via Synaptic and then reboot and get FF 3 from Synaptic?  If I did this, will I be able to keep bookmarks, preferences etc? (I'd hate to start from scratch)

---

### Post by kansasnoob on 2008-06-19
I'd go to synaptic and search firefox just to see what's installed after making sure my Software Sources are correct and clicking "reload" in synaptic.

---

### Post by kansasnoob on 2008-06-19
"will I be able to keep bookmarks, preferences etc? "

Nope. You'll lose it unless you get FF3 thru updates.

I know, I did it!

Wait a minute, OK?

---

### Post by flyingsolo on 2008-06-19
When I look in Synaptic, it lists FF 3 as installed but it is really 2 that opens from App-->Internet-->FF or from FF icon on upper panel.

---

### Post by kansasnoob on 2008-06-19
First of all you can leave FF2 and FF3 both installed and choose which app to drop in the "tray" (or any app for that matter) by installing alltray from synaptic. But let's try to figure out your FF3 problem.

Do you have Hardy? That's 8.04, if so you probably just need to straighten out your Software Sources and type one simple command. BUT only if you have Ubuntu 8.04 Hardy Heron!

If you have Hardy make sure your Software Sources look like the screen shots I posted here:

[http://ubuntuforums.org/showthread.php?t=834711](http://ubuntuforums.org/showthread.php?t=834711)

Then type the command

```
sudo apt-get update
```

---

### Post by kansasnoob on 2008-06-19
> **flyingsolo said:**
> When I look in Synaptic, it lists FF 3 as installed but it is really 2 that opens from App-->Internet-->FF or from FF icon on upper panel.

So with your mouse pointer just go to Internet in your menu (mine's customized and I don't quite remember how to get there) and see if you have two Firefox's.

I ran for weeks with both FF2 and FF3 because I was waiting for the bugs to get worked out.

---

### Post by aysiu on 2008-06-19
You theoretically won't lose any settings by installing or uninstalling any particular version of Firefox, but if you're nervous about it, it never hurts to back up: ```
cp -R ~/.mozilla ~/.mozilla.backup
``` Then paste these other commands in [the terminal](http://www.psychocats.net/ubuntu/terminal) and post the output back here: ```
cd /opt
ls
sudo apt-get update && sudo apt-get remove firefox-2 && sudo apt-get install firefox-3.0
cd /usr/bin
ls -l
```

---

### Post by goggle5 on 2008-06-19
If you are nervous about losing your bookmarks & links, you can export them into a file.  In your browser (FF), go to Bookmarks -> Organize Bookmarks then File -> Export ... remember where you put this file and you can retieve it later by following the path in Bookmarks and going to File -> Import

---

### Post by flyingsolo on 2008-06-19
I followed aysiu's suggestion and the following is returned:
> Package firefox-2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox-3.0 is already the newest version.
firefox-3.0 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
michael@ubuntu-desktop:/opt$ cd /usr/bin
michael@ubuntu-desktop:/usr/bin$ ls -l



So it would seem to tell me FF2 is not installed and FF3 is but when I open FF & go to Help, About it says it is FF 2.0.0.1 and it doesn't have the features of FF3 which I have on all my other computers.

---

### Post by kansasnoob on 2008-06-19
Did you check software sources and update?

Hardy has had at least three (maybe four) kernel updates since it's release.

---

### Post by flyingsolo on 2008-06-19
Sorry, I didn't post the results of the last line, ls -l, so here it is (long!)

```
-rwxr-xr-x  1 root    root       1388 2008-03-31 18:11 sensible-browser
-rwxr-xr-x  1 root    root        616 2008-03-31 18:11 sensible-editor
-rwxr-xr-x  1 root    root        288 2008-03-31 18:11 sensible-pager
-rwxr-xr-x  1 root    root      27140 2008-04-04 03:42 seq
lrwxrwxrwx  1 root    root         27 2008-05-04 10:53 serialver -> /etc/alternatives/serialver
-rwxr-xr-x  1 root    root       6389 2008-03-31 08:44 serpentine
lrwxrwxrwx  1 root    root         28 2007-02-24 15:47 servertool -> /etc/alternatives/servertool
-rwxr-xr-x  1 root    root      61704 2008-04-21 12:48 services-admin
-rwxr-xr-x  1 root    root       7288 2007-12-13 07:46 sessreg
-rwxr-xr-x  1 root    root       6480 2008-04-29 08:57 setarch
-rwxr-xr-x  1 root    root      22664 2007-11-14 06:59 setfacl
-rwxr-xr-x  1 root    root      32036 2007-03-05 02:54 setfdprm
-rwxr-xr-x  1 root    root       5736 2008-02-06 18:49 setkeycodes
-rwxr-xr-x  1 root    root       7572 2008-02-06 18:49 setleds
-rwxr-xr-x  1 root    root       3668 2008-02-06 18:49 setlogcons
-rwxr-xr-x  1 root    root       5804 2008-02-06 18:49 setmetamode
-rwxr-xr-x  1 root    root      32856 2008-06-05 10:40 setpci
-rwxr-xr-x  1 root    root       3716 2008-04-29 08:57 setsid
-rwxr-xr-x  1 root    root      18336 2008-04-29 08:57 setterm
-rwxr-xr-x  1 root    root      16852 2007-11-07 14:55 setxkbmap
-rwxr-xr-x  1 root    root      76516 2008-05-14 11:35 sftp
lrwxrwxrwx  1 root    root          6 2008-05-04 04:31 sg -> newgrp
-rwxr-xr-x  1 root    root       9864 2008-02-11 22:49 sgitopnm
-rwxr-xr-x  1 root    root      35352 2008-04-04 03:42 sha1sum
-rwxr-xr-x  1 root    root      44188 2008-04-04 03:42 sha224sum
-rwxr-xr-x  1 root    root      44220 2008-04-04 03:42 sha256sum
-rwxr-xr-x  1 root    root      85276 2008-04-04 03:42 sha384sum
-rwxr-xr-x  1 root    root      85276 2008-04-04 03:42 sha512sum
-rwxr-xr-x  1 root    root      82632 2008-04-21 12:48 shares-admin
-rwxr-xr-x  1 root    root       5908 2008-02-06 18:49 showcfont
-rwxr-xr-x  1 root    root       9236 2007-11-07 18:13 showfont
-rwxr-xr-x  1 root    root       9244 2008-02-06 18:49 showkey
-rwxr-xr-x  1 root    root       4004 2007-12-13 07:46 showrgb
-rwxr-xr-x  1 root    root      48464 2008-04-04 03:42 shred
-rwxr-xr-x  1 root    root      33628 2008-04-04 03:42 shuf
-rwxr-xr-x  1 root    root       5044 2008-02-11 22:49 sirtopnm
-rwxr-xr-x  1 root    root      22536 2008-01-03 19:02 size
-rwxr-xr-x  1 root    root      12580 2008-03-13 19:24 skill
-rwxr-xr-x  1 root    root    9699576 2006-12-02 09:45 skype
-rwxr-xr-x  1 root    root       6904 2006-12-02 09:45 skype-action-handler
-rwxr-xr-x  1 root    root       1813 2006-09-29 11:06 skype-callto-handler
-rwxr-xr-x  1 root    root       9948 2008-03-13 19:24 slabtop
-rwxr-xr-x  1 root    root      12192 2008-02-11 22:49 sldtoppm
-rwxr-xr-x  1 root    root       4319 2006-11-10 21:16 slib
lrwxrwxrwx  1 root    root          3 2008-05-17 15:14 slogin -> ssh
-rwxr-xr-x  1 root    root      58300 2008-03-25 09:25 slxdecode
-rwxr-xr-x  1 root    root      37148 2007-08-14 15:44 smartdimmer
-rwxr-xr-x  1 root    root    2202380 2008-06-17 15:59 smbcacls
-rwxr-xr-x  1 root    root    1338340 2008-06-17 15:59 smbclient
-rwxr-xr-x  1 root    root     723684 2008-06-17 15:59 smbcontrol
-rwxr-xr-x  1 root    root    2093676 2008-06-17 15:59 smbcquotas
-rwxr-xr-x  1 root    root    2167624 2008-06-17 15:59 smbget
-rwxr-xr-x  1 root    root    2096396 2008-06-17 15:59 smbpasswd
-rwxr-xr-x  1 root    root     897272 2008-06-17 15:59 smbspool
-rwxr-xr-x  1 root    root     702788 2008-06-17 15:59 smbstatus
-rwxr-xr-x  1 root    root       4896 2008-06-17 15:59 smbtar
-rwxr-xr-x  1 root    root    1245216 2008-06-17 15:59 smbtree
-rwxr-xr-x  1 root    root      15876 2007-11-07 15:04 smproxy
lrwxrwxrwx  1 root    root          5 2008-05-04 09:20 snice -> skill
-rwxr-xr-x  1 root    root       2869 2007-10-31 15:00 SOAPsh
lrwxrwxrwx  1 root    root         11 2008-05-04 10:13 socklist -> socklist.pl
-rwxr-xr-x  1 root    root       3229 2007-05-01 03:51 socklist.pl
-rwxr-xr-x  1 root    root      22364 2008-01-28 07:51 soelim
lrwxrwxrwx  1 root    root         33 2008-06-18 22:31 soffice -> ../lib/openoffice/program/soffice
-rwxr-xr-x  1 root    root       3742 2008-03-04 19:23 software-properties-gtk
-rwxr-xr-x  1 root    root      67540 2008-04-04 03:42 sort
-rwxr-xr-x  1 root    root     164680 2008-04-09 18:30 sound-juicer
-rwxr-xr-x  1 root    root      35384 2007-11-05 11:03 sox
-rwxr-xr-x  1 root    root       5724 2008-02-11 22:49 spctoppm
-rwxr-xr-x  1 root    root      19424 2008-02-27 09:22 speaker-test
-rwxr-xr-x  1 root    root      17366 2007-11-27 07:07 splain
-rwxr-xr-x  1 root    root      32672 2008-04-04 03:42 split
-rwxr-xr-x  1 root    root       5220 2008-02-06 18:49 splitfont
-rwxr-xr-x  1 root    root      22020 2008-04-04 20:38 sprof
-rwxr-xr-x  1 root    root      88848 2008-02-27 16:31 spumux
-rwxr-xr-x  1 root    root       4256 2008-02-11 22:49 sputoppm
-rwxr-xr-x  1 root    root      20800 2008-02-27 16:31 spuunmux
-rwxr-xr-x  1 root    root       3640 2007-05-18 06:49 sq
-rwxr-xr-x  1 root    root      24080 2007-11-01 21:35 sqlite
-rwxr-xr-x  1 root    root      32424 2007-10-24 13:04 sqlite3
-rwxr-xr-x  1 root    root      12400 2006-09-28 12:53 srttool
-rwxr-xr-x  1 root    root     296252 2008-05-14 11:35 ssh
-rwxr-xr-x  1 root    root      93580 2008-05-14 11:35 ssh-add
-rwxr-sr-x  1 root    ssh       76580 2008-05-14 11:35 ssh-agent
-rwxr-xr-x  1 root    root       1452 2008-05-14 11:35 ssh-argv0
lrwxrwxrwx  1 root    root         29 2006-06-11 23:07 ssh-askpass -> /etc/alternatives/ssh-askpass
-rwxr-xr-x  1 root    root       1306 2008-05-14 11:35 ssh-copy-id
-rwxr-xr-x  1 root    root     118320 2008-05-14 11:35 ssh-keygen
-rwxr-xr-x  1 root    root     156800 2008-05-14 11:35 ssh-keyscan
-rwxr-xr-x  1 root    root      77128 2008-05-14 11:35 ssh-vulnkey
-rwxr-xr-x  1 root    root       5744 2008-02-11 22:49 st4topgm
-rwsr-xr-x  1 root    root       5968 2008-05-03 06:52 start_kdeinit
-rwxr-xr-x  1 root    root       3704 2008-05-03 06:52 start_kdeinit_wrapper
-rwxr-xr-x  1 root    root       3980 2008-02-02 00:27 startx
-rwxr-xr-x  1 root    root      43708 2008-04-04 03:42 stat
-rwxr-xr-x  1 root    root     190244 2008-01-15 07:47 strace
-rwxr-xr-x  1 root    root       4336 2008-02-19 03:08 stream
-rwxr-xr-x  1 root    root     102840 2007-11-16 20:59 streamripper
-rwxr-xr-x  1 root    root     313832 2008-03-31 18:32 streamtuner
-rwxr-xr-x  1 root    root      11772 2007-10-05 00:05 strfile
-rwxr-xr-x  1 root    root      22520 2008-01-03 19:02 strings
-rwxr-xr-x  1 root    root     181756 2008-01-03 19:02 strip
-rwxr-xr-x  1 root    root       3461 2007-10-31 15:00 stubmaker
-rwxr-xr-x  1 root    root      22668 2006-09-28 12:53 subtitle2pgm
-rwxr-xr-x  1 root    root      25548 2006-09-28 12:53 subtitle2vobsub
-rwsr-xr-x  2 root    root     107872 2008-05-14 21:41 sudo
-rwsr-xr-x  2 root    root     107872 2008-05-14 21:41 sudoedit
-rwxr-xr-x  1 root    root      31648 2008-04-04 03:42 sum
-rwxr-xr-x  1 root    root      56548 2007-03-05 02:54 superformat
lrwxrwxrwx  1 root    root          3 2008-05-04 09:25 svlc -> vlc
-rwxr-xr-x  1 root    root       2388 2008-04-30 22:59 svnpath
-rwxr-xr-x  1 root    root      14576 2007-10-24 05:28 sxpm
-rwxr-xr-x  1 root    root      11592 2008-02-27 06:20 synclient
-rwxr-xr-x  1 root    root       7536 2008-02-27 06:20 syndaemon
-rwxr-xr-x  1 root    root         78 2008-04-21 12:44 system-config-printer
-rwxr-xr-x  1 root    root         63 2008-04-21 12:44 system-config-printer-applet
-rwxr-xr-x  1 root    root      20796 2008-04-14 14:48 system-tools-backends
-rwxr-xr-x  1 root    root      28116 2008-04-04 03:42 tac
-rwxr-xr-x  1 root    root      11167 2008-04-30 22:59 tagpending
-rwxr-xr-x  1 root    root      46968 2008-04-04 03:42 tail
-rwxr-xr-x  1 root    root      19258 2008-04-09 21:23 tasksel
-rwxr-xr-x  1 root    root       9136 2008-04-29 08:57 taskset
-rwxr-xr-x  1 root    root      96144 2008-01-28 07:51 tbl
-rwxr-xr-x  1 root    root     105828 2008-02-29 19:40 tccat
-rwxr-xr-x  1 root    root      96624 2008-02-29 19:40 tcdecode
-rwxr-xr-x  1 root    root      56024 2008-02-29 19:40 tcdemux
-rwxr-xr-x  1 root    root     138020 2008-02-29 19:40 tcextract
lrwxrwxrwx  1 root    root         23 2006-06-11 23:07 tclsh -> /etc/alternatives/tclsh
-rwxr-xr-x  1 root    root       3704 2008-02-25 03:20 tclsh8.4
-rwxr-xr-x  1 root    root      18268 2008-02-29 19:40 tcmodinfo
-rwxr-xr-x  1 root    root       8148 2008-02-29 19:40 tcmp3cut
-rwxr-xr-x  1 root    root     194048 2008-02-29 19:40 tcprobe
-rwxr-xr-x  1 root    root      61120 2008-02-29 19:40 tcpvmexportd
-rwxr-xr-x  1 root    root      79676 2008-02-29 19:40 tcrequant
-rwxr-xr-x  1 root    root      87392 2008-02-29 19:40 tcscan
-rwxr-xr-x  1 root    root      30748 2008-02-29 19:40 tcxmlcheck
-rwxr-xr-x  1 root    root      12252 2008-02-29 19:40 tcxpm2rgb
-rwxr-xr-x  1 root    root      47028 2008-06-17 15:59 tdbbackup
-rwxr-xr-x  1 root    root      24192 2008-04-04 03:42 tee
lrwxrwxrwx  1 root    root         24 2006-06-11 23:07 telnet -> /etc/alternatives/telnet
-rwxr-xr-x  1 root    root      77504 2006-12-17 22:16 telnet.netkit
-rwxr-xr-x  1 root    root      23012 2008-04-04 03:42 test
-rwxr-xr-x  1 root    root     638948 2008-06-17 15:59 testparm
lrwxrwxrwx  1 root    root          9 2008-05-04 09:45 testrb -> testrb1.8
-rwxr-xr-x  1 root    root        150 2007-11-23 12:04 testrb1.8
-rwxr-xr-x  1 root    root      18148 2007-09-29 23:11 testrec
-rwxr-xr-x  1 root    root      12960 2008-02-11 08:10 test-speech
-rwxr-xr-x  1 root    root      27060 2008-04-03 10:10 text2pcap
-rwxr-xr-x  1 root    root       6444 2008-04-08 14:19 text2wave
-rwxr-xr-x  1 root    root       9892 2008-02-11 22:49 tgatoppm
-rwxr-xr-x  1 root    root      29204 2008-04-30 05:26 themus-theme-applier
-rwxr-xr-x  1 root    root      13984 2008-02-11 22:49 thinkjettopbm
-rwxr-xr-x  1 root    root      47976 2008-02-23 19:38 tic
-rwxr-xr-x  1 root    root      12392 2008-02-11 22:49 tifftopnm
-rwxr-xr-x  1 root    root      10640 2007-08-02 04:08 time
-rwxr-xr-x  1 root    root      95172 2008-04-21 12:48 time-admin
-rwxr-xr-x  1 root    root       5776 2008-03-13 19:24 tload
lrwxrwxrwx  1 root    root         27 2007-02-24 15:47 tnameserv -> /etc/alternatives/tnameserv
-rwxr-xr-x  1 root    root     203492 2008-02-24 06:36 toc2cddb
-rwxr-xr-x  1 root    root     206144 2008-02-24 06:36 toc2cue
lrwxrwxrwx  1 root    root          7 2008-05-04 10:14 todos -> fromdos
-rwxr-xr-x  1 root    root       8668 2008-02-23 19:38 toe
-rwxr-xr-x  1 root    root        823 2008-04-08 11:42 tomboy
-rwxr-xr-x  1 root    root        377 2008-04-08 11:42 tomboy-panel
-rwxr-xr-x  1 root    root     154808 2007-04-29 23:40 toolame
-rwxr-xr-x  1 root    root      52336 2008-03-13 19:24 top
-rwxr-xr-x  1 root    root      82192 2007-11-16 07:54 toshset
lrwxrwxrwx  1 root    root         23 2008-05-04 13:12 totem -> /etc/alternatives/totem
lrwxrwxrwx  1 root    root         37 2008-05-04 13:12 totem-audio-preview -> /etc/alternatives/totem-audio-preview
-rwxr-xr-x  1 root    root     364416 2008-04-11 13:56 totem-gstreamer
-rwxr-xr-x  1 root    root     131440 2008-04-11 13:56 totem-gstreamer-audio-preview
-rwxr-xr-x  1 root    root     135568 2008-04-11 13:56 totem-gstreamer-video-indexer
-rwxr-xr-x  1 root    root     134816 2008-04-11 13:56 totem-gstreamer-video-thumbnailer
lrwxrwxrwx  1 root    root         37 2008-05-04 13:12 totem-video-indexer -> /etc/alternatives/totem-video-indexer
lrwxrwxrwx  1 root    root         10 2008-05-04 09:42 touch -> /bin/touch
-rwxr-xr-x  1 root    root       9428 2008-02-23 19:38 tput
-rwxr-xr-x  1 root    root      38672 2008-04-04 03:42 tr
-rwxr-xr-x  1 root    root       8140 2007-12-10 13:33 tracepath
-rwxr-xr-x  1 root    root       9356 2007-12-10 13:33 tracepath6
lrwxrwxrwx  1 root    root         29 2008-05-04 13:00 traceroute6 -> /etc/alternatives/traceroute6
-rwsr-xr-x  1 root    root      12296 2007-12-10 13:33 traceroute6.iputils
-rwxr-xr-x  1 root    root      33756 2008-06-10 02:44 tracker-applet
-rwxr-xr-x  1 root    root     409392 2008-06-10 02:44 trackerd
-rwxr-xr-x  1 root    root      11460 2008-06-10 02:44 tracker-extract
-rwxr-xr-x  1 root    root      35792 2008-06-10 02:44 tracker-preferences
-rwxr-xr-x  1 root    root      98460 2008-06-10 02:44 tracker-search-tool
-rwxr-xr-x  1 root    root      12724 2008-06-10 02:44 tracker-thumbnailer
-rwxr-xr-x  1 root    root     313820 2008-02-29 19:40 transcode
-rwxr-xr-x  1 root    root       6284 2007-09-29 23:11 transist.flt
-rwxr-xr-x  1 root    root     503044 2008-05-09 12:49 transmission
-rwxr-xr-x  1 root    root     350676 2008-01-28 07:51 troff
-rwxr-xr-x  1 root    root     251832 2007-09-17 15:17 truecrypt
-rwxr-xr-x  1 root    root       4309 2007-05-18 06:49 tryaffix
-rwxr-xr-x  1 root    root      89068 2008-03-29 16:17 tsclient
-rwxr-xr-x  1 root    root      14620 2008-02-23 19:38 tset
-rwxr-xr-x  1 root    root      30408 2008-04-04 03:42 tsort
-rwxr-xr-x  1 root    root      22556 2008-04-04 03:42 tty
-rwxr-xr-x  1 root    root       6894 2008-04-04 20:27 tzselect
-rwxr-xr-x  1 root    root       1105 2008-05-17 07:54 ubuntu-bug
-rwxr-xr-x  1 root    root      32634 2008-02-21 03:22 ucf
-rwxr-xr-x  1 root    root      19290 2008-02-21 03:22 ucfq
-rwxr-xr-x  1 root    root      10405 2008-02-21 03:22 ucfr
-rwxr-xr-x  1 root    root      14324 2007-11-13 05:53 ucs2any
lrwxrwxrwx  1 root    root         13 2008-05-04 09:43 udevinfo -> /sbin/udevadm
lrwxrwxrwx  1 root    root         13 2008-05-04 09:43 udevtest -> /sbin/udevadm
lrwxrwxrwx  1 root    root         21 2007-12-29 14:52 uic -> /etc/alternatives/uic
-rwxr-xr-x  1 root    root     305928 2008-04-09 13:28 uic-qt3
-rwxr-xr-x  1 root    root       9848 2007-12-12 09:59 ul
-rwxr-xr-x  1 root    root      18384 2007-12-05 13:04 unace
-rwxr-xr-x  1 root    root      11417 2008-03-10 12:24 unattended-upgrade
-rwxr-xr-x  1 root    root      27188 2008-04-04 03:42 unexpand
-rwxr-xr-x  1 root    root       1538 2008-02-06 18:49 unicode_start
-rwxr-xr-x  1 root    root       1003 2008-02-06 18:49 unicode_stop
-rwxr-xr-x  1 root    root      31196 2008-04-04 03:42 uniq
lrwxrwxrwx  1 root    root          7 2008-05-04 10:14 unix2dos -> fromdos
-rwxr-xr-x  1 root    root      22728 2008-04-04 03:42 unlink
lrwxrwxrwx  1 root    root          4 2008-05-04 09:20 unlzma -> lzma
-rwxr-xr-x  1 root    root         50 2008-06-13 19:08 unopkg
lrwxrwxrwx  1 root    root         27 2006-06-14 23:14 unpack200 -> /etc/alternatives/unpack200
lrwxrwxrwx  1 root    root         23 2008-05-04 13:09 unrar -> /etc/alternatives/unrar
-rwxr-xr-x  1 root    root     183332 2007-11-27 21:02 unrar-nonfree
-rwxr-xr-x  1 root    root       3996 2007-05-18 06:49 unsq
-rwxr-xr-x  1 root    root       5728 2007-10-05 00:05 unstr
-rwxr-xr-x  2 root    root     121680 2008-03-21 07:29 unzip
-rwxr-xr-x  1 root    root      55864 2008-03-21 07:29 unzipsfx
lrwxrwxrwx  1 root    root         26 2008-05-04 13:00 updatedb -> /etc/alternatives/updatedb
-rwxr-xr-x  1 root    root      28120 2008-03-08 14:22 updatedb.mlocate
-rwxr-xr-x  1 root    root      11464 2008-05-29 09:23 update-desktop-database
-rwxr-xr-x  1 root    root        210 2008-03-27 09:37 update-gnucash-gconf
-rwxr-xr-x  1 root    root       4126 2008-05-09 12:50 update-manager
-rwxr-xr-x  1 root    root      32504 2008-03-21 12:24 update-mime-database
-rwxr-xr-x  1 root    root      50112 2008-04-04 18:34 update-notifier
-rwxr-xr-x  1 root    root       1228 2008-06-05 10:40 update-pciids
-rwxr-xr-x  1 root    root       4698 2007-10-24 05:21 update-perl-sax-parsers
-rwxr-xr-x  1 root    root       3428 2008-03-13 19:24 uptime
-rwxr-xr-x  1 root    root       3988 2008-03-25 09:25 usb_printerid
-rwxr-xr-x  1 root    root      54113 2008-04-30 22:59 uscan
-rwxr-xr-x  1 root    root      24056 2008-04-04 03:42 users
-rwxr-xr-x  1 root    root      94248 2008-04-21 12:48 users-admin
-rwxr-xr-x  1 root    root       3352 2006-06-21 20:18 utf8tolatin1
-rwxr-xr-x  1 root    root       4148 2008-03-27 14:25 uuidgen
-rwxr-xr-x  1 root    root      22377 2008-04-30 22:59 uupdate
-rwxr-xr-x  1 root    root       2147 2008-04-09 18:28 uxterm
-rwxr-xr-x  1 root    root      69056 2007-11-26 01:06 v4l2-ctl
-rwxr-xr-x  1 root    root      20140 2007-11-26 01:06 v4l2-dbg
-rwxr-xr-x  1 root    root     136172 2007-12-02 20:06 vcdimager
-rwxr-xr-x  1 root    root      38960 2007-12-02 20:06 vcd-info
-rwxr-xr-x  1 root    root     163260 2007-12-02 20:06 vcdxbuild
-rwxr-xr-x  1 root    root     143636 2007-12-02 20:06 vcdxgen
-rwxr-xr-x  1 root    root     134604 2007-12-02 20:06 vcdxminfo
-rwxr-xr-x  1 root    root      38988 2007-12-02 20:06 vcdxrip
-rwxr-xr-x  1 root    root      11948 2008-05-07 18:41 vcut
lrwxrwxrwx  1 root    root         20 2006-06-11 23:07 vi -> /etc/alternatives/vi
lrwxrwxrwx  1 root    root         22 2006-06-11 23:07 view -> /etc/alternatives/view
-rwxr-xr-x  1 root    root      18704 2007-11-07 14:59 viewres
lrwxrwxrwx  1 root    root         21 2006-06-11 23:07 vim -> /etc/alternatives/vim
-rwxr-xr-x  1 root    root    1536508 2008-01-31 08:07 vim.basic
lrwxrwxrwx  1 root    root         25 2007-10-03 22:53 vimdiff -> /etc/alternatives/vimdiff
-rwxr-xr-x  1 root    root     593412 2008-01-31 08:07 vim.tiny
-rwxr-xr-x  1 root    root       1776 2008-01-31 08:06 vimtutor
-rwxr-xr-x  1 root    root      77176 2008-04-07 15:38 vinagre
-rwxr-xr-x  1 root    root      24780 2008-04-07 14:10 vino-preferences
-rwxr-xr-x  1 root    root       4744 2008-04-15 14:15 vlc
-rwxr-xr-x  1 root    root       3432 2008-04-14 19:51 vmmouse_detect
-rwxr-xr-x  1 root    root      18564 2008-03-13 19:24 vmstat
-rwxr-xr-x  1 root    root      31880 2006-09-28 12:53 vobsub2pgm
-rwxr-xr-x  1 root    root       3704 2007-11-05 16:48 volname
-rwxr-xr-x  1 root    root      19936 2008-05-07 18:41 vorbiscomment
-rwxr-xr-x  1 root    root       3258 2008-05-07 18:41 vorbistagedit
-rwxr-xr-x  1 root    root       5740 2008-02-06 18:49 vt-is-UTF8
-rwxr-xr-x  1 root    root      18504 2008-04-09 08:21 vumeter
lrwxrwxrwx  1 root    root         19 2006-06-11 23:07 w -> /etc/alternatives/w
-rwxr-xr-x  1 root    root    1173640 2007-01-22 16:51 w3m
-rwxr-xr-x  1 root    root       1132 2007-01-22 16:51 w3mman
-rwxr-xr-x  1 root    root      35416 2008-03-30 02:42 wacdump
-rwxr-sr-x  1 root    tty        9960 2008-04-29 08:57 wall
-rwxr-xr-x  1 root    root       9204 2008-03-13 19:24 watch
-rwxr-xr-x  1 root    root       4704 2008-02-11 22:49 wbmptopbm
-rwxr-xr-x  1 root    root      31840 2008-04-04 03:42 wc
-rwxr-xr-x  1 root    root        323 2008-04-09 11:10 wftopfa
-rwxr-xr-x  1 root    root     218032 2007-06-18 06:45 wget
-rwxr-xr-x  1 root    root      87792 2008-03-12 10:24 whatis
-rwxr-xr-x  1 root    root       7648 2008-04-29 08:57 whereis
lrwxrwxrwx  1 root    root         10 2008-05-04 04:31 which -> /bin/which
-rwxr-xr-x  1 root    root      20956 2008-03-24 11:23 whiptail
-rwxr-xr-x  1 root    root      33180 2008-04-04 03:42 who
-rwxr-xr-x  1 root    root      22736 2008-04-04 03:42 whoami
-rwxr-xr-x  1 root    root       1579 2008-04-30 22:59 whodepends
-rwxr-xr-x  1 root    root      33736 2007-11-06 15:02 whois
-rwxr-xr-x  1 root    root       6650 2008-04-30 22:59 who-uploads
-rwxr-xr-x  1 root    root      12336 2008-02-11 22:49 winicontoppm
-rwxr-xr-x  1 root    root    1365808 2008-04-03 10:10 wireshark
lrwxrwxrwx  1 root    root         22 2006-06-11 23:07 wish -> /etc/alternatives/wish
-rwxr-xr-x  1 root    root       4056 2008-02-25 14:24 wish8.4
-rwxr-xr-x  1 root    root       4737 2008-04-30 22:59 wnpp-alert
-rwxr-xr-x  1 root    root     359116 2008-03-01 02:22 wodim
-rwxr-xr-x  1 root    root       4668 2008-01-26 17:50 word-list-compress
-rwxr-xr-x  1 root    root     644140 2008-02-24 06:35 workrave
-rwxr-xr-x  1 root    root      14464 2008-03-12 18:28 wpa_passphrase
-rwxr-xr-x  1 root    root      10020 2008-03-13 19:24 w.procps
lrwxrwxrwx  1 root    root         23 2008-05-04 10:55 write -> /etc/alternatives/write
-rwxr-xr-x  1 root    root     103068 2008-01-03 15:28 wvdial
-rwxr-xr-x  1 root    root      46932 2008-01-03 15:28 wvdialconf
lrwxrwxrwx  1 root    root         29 2006-06-11 23:07 www-browser -> /etc/alternatives/www-browser
lrwxrwxrwx  1 root    root          3 2008-05-04 09:25 wxvlc -> vlc
-rwsr-sr-x  1 root    root       7460 2008-04-15 22:20 X
lrwxrwxrwx  1 root    root          6 2006-06-11 23:07 X11 -> ../bin
-rwxr-xr-x  1 root    root     104856 2007-11-07 15:05 x11perf
-rwxr-xr-x  1 root    root       2703 2007-11-07 15:05 x11perfcomp
-rwxr-xr-x  1 root    root      23848 2008-04-02 11:22 xargs
-rwxr-xr-x  1 root    root      31012 2007-10-31 17:42 xauth
-rwxr-xr-x  1 root    root      12036 2007-11-07 15:05 xbiff
-rwxr-xr-x  1 root    root       6156 2008-02-11 22:49 xbmtopbm
-rwxr-xr-x  1 root    root      48280 2008-03-27 20:25 xbrlapi
-rwxr-xr-x  1 root    root        117 2007-12-05 09:26 xbsh
-rwxr-xr-x  1 root    root      22936 2007-11-07 15:05 xcalc
-rwxr-xr-x  1 root    root     694280 2008-03-06 19:43 xcdroast
-rwxr-xr-x  1 root    root      14232 2007-11-07 15:05 xclipboard
-rwxr-xr-x  1 root    root      32568 2007-11-07 15:05 xclock
-rwxr-xr-x  1 root    root      23976 2007-12-13 07:46 xcmsdb
-rwxr-xr-x  1 root    root      12520 2007-11-07 15:05 xconsole
-rwxr-xr-x  1 root    root      10000 2007-11-07 15:05 xcursorgen
-rwxr-xr-x  1 root    root      10128 2007-11-07 15:05 xcutsel
-rwxr-xr-x  1 root    root      13072 2007-03-05 02:54 xdfcopy
lrwxrwxrwx  1 root    root          7 2008-05-04 10:09 xdfformat -> xdfcopy
-rwxr-xr-x  1 root    root      14806 2008-01-09 06:43 xdg-desktop-icon
-rwxr-xr-x  1 root    root      39267 2008-01-09 06:43 xdg-desktop-menu
-rwxr-xr-x  1 root    root      16526 2008-01-09 06:43 xdg-email
-rwxr-xr-x  1 root    root      24129 2008-01-09 06:43 xdg-icon-resource
-rwxr-xr-x  1 root    root      28015 2008-01-09 06:43 xdg-mime
-rwxr-xr-x  1 root    root      10029 2008-01-09 06:43 xdg-open
-rwxr-xr-x  1 root    root      19303 2008-01-09 06:43 xdg-screensaver
-rwxr-xr-x  1 root    root        242 2008-02-12 18:49 xdg-user-dir
-rwxr-xr-x  1 root    root      14680 2008-02-13 06:51 xdg-user-dirs-gtk-update
-rwxr-xr-x  1 root    root      14436 2008-02-12 18:49 xdg-user-dirs-update
-rwxr-xr-x  1 root    root      57404 2007-11-07 15:05 xditview
-rwxr-xr-x  1 root    root      23212 2007-11-07 14:59 xdpyinfo
-rwxr-xr-x  1 root    root       5300 2007-11-07 14:59 xdriinfo
-rwxr-xr-x  1 root    root     509820 2007-11-07 15:05 xedit
-rwxr-xr-x  1 root    root      17504 2007-11-07 14:59 xev
-rwxr-xr-x  1 root    root      12056 2007-11-07 15:05 xeyes
-rwxr-xr-x  1 root    root       6131 2008-04-02 22:48 xfailsafedialog
-rwxr-xr-x  1 root    root      20272 2007-11-07 14:59 xfd
-rwxr-xr-x  1 root    root      27572 2007-11-07 14:59 xfontsel
-rwxr-xr-x  1 root    root       4620 2007-11-07 18:13 xfsinfo
-rwxr-xr-x  1 root    root       1652 2008-04-09 18:23 xft-config
-rwxr-xr-x  1 root    root       7200 2007-12-13 07:46 xgamma
-rwxr-xr-x  1 root    root     189104 2007-12-13 02:22 xgettext
-rwxr-xr-x  1 root    root      10976 2007-12-13 07:46 xhost
-rwxr-xr-x  1 root    root      19144 2008-03-30 02:42 xidump
-rwxr-xr-x  1 root    root       9396 2008-02-11 22:49 ximtoppm
-rwxr-xr-x  1 root    root      11544 2008-02-02 00:27 xinit
-rwxr-xr-x  1 root    root       8472 2007-11-07 14:55 xkbbell
-rwxr-xr-x  1 root    root     177924 2007-11-07 14:55 xkbcomp
-rwxr-xr-x  1 root    root      28584 2007-11-07 14:55 xkbevd
-rwxr-xr-x  1 root    root      90000 2007-11-07 14:55 xkbprint
-rwxr-xr-x  1 root    root      15932 2007-11-07 14:55 xkbvleds
-rwxr-xr-x  1 root    root      13052 2007-11-07 14:55 xkbwatch
-rwxr-xr-x  1 root    root       8888 2007-11-07 14:59 xkill
-rwxr-xr-x  1 root    root      11320 2007-11-07 15:05 xload
-rwxr-xr-x  1 root    root      12592 2007-11-07 15:05 xlogo
-rwxr-xr-x  1 root    root       5744 2007-11-07 14:59 xlsatoms
-rwxr-xr-x  1 root    root       6736 2007-11-07 14:59 xlsclients
-rwxr-xr-x  1 root    root      17368 2007-11-07 14:59 xlsfonts
-rwxr-xr-x  1 root    root      29024 2007-11-07 15:05 xmag
-rwxr-xr-x  1 root    root      49608 2007-11-07 15:05 xman
-rwxr-xr-x  1 root    root      13440 2007-11-07 14:59 xmessage
-rwxr-xr-x  1 root    root       1247 2007-06-04 21:59 xmkmf
-rwxr-xr-x  1 root    root      28660 2008-03-10 20:32 xml2po
-rwxr-xr-x  1 root    root      12112 2008-03-12 08:40 xmlcatalog
-rwxr-xr-x  1 root    root      48056 2008-03-12 08:40 xmllint
-rwxr-xr-x  1 root    root       3255 2008-04-09 08:53 xmlproc_parse.python-xml
-rwxr-xr-x  1 root    root       4287 2008-04-09 08:53 xmlproc_val.python-xml
-rwxr-xr-x  1 root    root       2872 2007-10-31 15:00 XMLRPCsh
-rwxr-xr-x  1 root    root      24592 2007-12-13 07:46 xmodmap
-rwxr-xr-x  1 root    root       6172 2007-11-07 15:05 xmore
-rwxr-xr-x  1 root    root    1693212 2008-06-12 22:22 Xorg
lrwxrwxrwx  1 root    root         29 2008-06-18 22:32 xpcshell-1.9 -> ../lib/xulrunner-1.9/xpcshell
-rwxr-xr-x  1 root    root      14008 2008-02-11 22:49 xpmtoppm
-rwxr-xr-x  1 root    root      27608 2007-11-07 14:59 xprop
-rwxr-xr-x  1 root    root      54300 2008-03-25 09:25 xqxdecode
-rwxr-xr-x  1 root    root      33948 2007-12-13 07:46 xrandr
-rwxr-xr-x  1 root    root      22340 2007-12-13 07:46 xrdb
-rwxr-xr-x  1 root    root       7492 2007-12-13 07:46 xrefresh
-rwxr-xr-x  1 root    root     653384 2007-12-03 07:53 xsane
-rwxr-xr-x  1 root    root     114888 2008-04-10 22:15 xscreensaver-getimage
-rwxr-xr-x  1 root    root      16142 2008-04-10 22:14 xscreensaver-getimage-file
-rwxr-xr-x  1 root    root       5008 2008-04-10 22:14 xscreensaver-getimage-video
-rwxr-xr-x  1 root    root      16328 2008-04-10 22:15 xscreensaver-gl-helper
-rwxr-xr-x  1 root    root      25084 2008-04-10 22:14 xscreensaver-text
lrwxrwxrwx  1 root    root         35 2008-05-04 13:12 x-session-manager -> /etc/alternatives/x-session-manager
-rwxr-xr-x  1 root    root      27252 2007-12-13 07:46 xset
-rwxr-xr-x  1 root    root       4876 2007-12-13 07:46 xsetmode
-rwxr-xr-x  1 root    root       5744 2007-12-13 07:46 xsetpointer
-rwxr-xr-x  1 root    root      11920 2007-12-13 07:46 xsetroot
-rwxr-xr-x  1 root    root      28524 2008-03-30 02:42 xsetwacom
-rwxr-xr-x  1 root    root      16508 2007-11-19 11:04 xsltproc
-rwxr-xr-x  1 root    root      70076 2007-11-07 15:04 xsm
-rwxr-xr-x  1 root    root       8812 2007-12-13 07:46 xstdcmap
-rwxr-xr-x  1 root    root      51838 2007-11-27 07:07 xsubpp
-rwxr-sr-x  1 root    utmp     309780 2008-04-09 18:28 xterm
lrwxrwxrwx  1 root    root         37 2006-06-11 23:07 x-terminal-emulator -> /etc/alternatives/x-terminal-emulator
-rwxr-xr-x  1 root    root      13156 2007-12-13 07:46 xtrapchar
-rwxr-xr-x  1 root    root       6200 2007-12-13 07:46 xtrapin
-rwxr-xr-x  1 root    root       4164 2007-12-13 07:46 xtrapinfo
-rwxr-xr-x  1 root    root       7436 2007-12-13 07:46 xtrapout
-rwxr-xr-x  1 root    root       5316 2007-12-13 07:46 xtrapproto
-rwxr-xr-x  1 root    root       3812 2007-12-13 07:46 xtrapreset
-rwxr-xr-x  1 root    root       5084 2007-12-13 07:46 xtrapstats
lrwxrwxrwx  1 root    root         27 2008-06-18 22:32 xulrunner -> /etc/alternatives/xulrunner
lrwxrwxrwx  1 root    root         30 2008-06-18 22:32 xulrunner-1.9 -> ../lib/xulrunner-1.9/xulrunner
-rwxr-xr-x  1 root    root      27460 2007-12-13 07:46 xvidtune
-rwxr-xr-x  1 root    root       8560 2007-11-07 14:59 xvinfo
-rwxr-xr-x  1 root    root       5152 2008-02-11 22:49 xvminitoppm
-rwxr-xr-x  1 root    root      21456 2007-11-07 15:05 xwd
-rwxr-xr-x  1 root    root      13484 2008-02-11 22:49 xwdtopnm
lrwxrwxrwx  1 root    root         34 2006-06-11 23:07 x-window-manager -> /etc/alternatives/x-window-manager
-rwxr-xr-x  1 root    root      22332 2007-11-07 14:59 xwininfo
-rwxr-xr-x  1 root    root      22228 2007-11-07 15:05 xwud
lrwxrwxrwx  1 root    root         31 2006-06-11 23:07 x-www-browser -> /etc/alternatives/x-www-browser
-rwxr-xr-x  1 root    root      11868 2008-01-31 08:07 xxd
-rwxr-xr-x  1 root    root       8472 2007-09-29 23:11 y4mblack
-rwxr-xr-x  1 root    root      14876 2007-09-29 23:11 y4mcolorbars
-rwxr-xr-x  1 root    root     117048 2007-09-29 23:11 y4mdenoise
-rwxr-xr-x  1 root    root       5756 2007-09-29 23:11 y4mhist
-rwxr-xr-x  1 root    root       7320 2007-09-29 23:11 y4minterlace
-rwxr-xr-x  1 root    root      10764 2007-09-29 23:11 y4mshift
-rwxr-xr-x  1 root    root      10892 2007-09-29 23:11 y4mspatialfilter
-rwxr-xr-x  1 root    root      24728 2007-09-29 23:11 y4mstabilizer
-rwxr-xr-x  1 root    root      14340 2007-09-29 23:11 y4mtopnm
-rwxr-xr-x  1 root    root      14004 2007-09-29 23:11 y4mtoppm
-rwxr-xr-x  1 root    root       4768 2007-09-29 23:11 y4mtoyuv
-rwxr-xr-x  1 root    root      12136 2007-09-29 23:11 y4munsharp
-rwxr-xr-x  1 root    root       4536 2008-02-11 22:49 ybmtopbm
-rwxr-xr-x  1 root    root     236188 2008-05-29 09:00 yelp
-rwxr-xr-x  1 root    root      22532 2008-04-04 03:42 yes
-rwxr-xr-x  1 root    root       6812 2007-09-29 23:11 ypipe
-rwxr-xr-x  1 root    root      11900 2007-09-29 23:11 yuv2lav
-rwxr-xr-x  1 root    root       7668 2007-09-29 23:11 yuv4mpeg
-rwxr-xr-x  1 root    root      29732 2007-09-29 23:11 yuvcorrect
-rwxr-xr-x  1 root    root      39248 2007-09-29 23:11 yuvcorrect_tune
-rwxr-xr-x  1 root    root      18116 2007-09-29 23:11 yuvdeinterlace
-rwxr-xr-x  1 root    root      14240 2007-09-29 23:11 yuvdenoise
-rwxr-xr-x  1 root    root       7708 2007-09-29 23:11 yuvfps
-rwxr-xr-x  1 root    root      12160 2007-09-29 23:11 yuvinactive
-rwxr-xr-x  1 root    root      35864 2007-09-29 23:11 yuvkineco
-rwxr-xr-x  1 root    root      13064 2007-09-29 23:11 yuvmedianfilter
-rwxr-xr-x  1 root    root       9980 2007-09-29 23:11 yuvplay
-rwxr-xr-x  1 root    root      49272 2007-09-29 23:11 yuvscaler
-rwxr-xr-x  1 root    root       6772 2008-02-11 22:49 yuvsplittoppm
-rwxr-xr-x  1 root    root       4924 2008-02-11 22:49 yuvtoppm
-rwxr-xr-x  1 root    root      16168 2007-09-29 23:11 yuvycsnoise
-rwxr-xr-x  1 root    root       7344 2007-09-29 23:11 yuyvtoy4m
-rwxr-xr-x  1 root    root       9620 2008-04-04 20:38 zdump
-rwxr-xr-x  1 root    root       5728 2008-02-11 22:49 zeisstopnm
-rwxr-xr-x  1 root    root      58068 2008-04-08 11:18 zenity
-rwxr-xr-x  1 root    root      66532 2006-07-10 11:47 zip
-rwxr-xr-x  1 root    root      27620 2006-07-10 11:47 zipcloak
-rwxr-xr-x  1 root    root       1188 2008-03-21 07:29 zipgrep
-rwxr-xr-x  2 root    root     121680 2008-03-21 07:29 zipinfo
-rwxr-xr-x  1 root    root      23296 2006-07-10 11:47 zipnote
-rwxr-xr-x  1 root    root      27392 2006-07-10 11:47 zipsplit
-rwxr-xr-x  1 root    root      62396 2008-03-25 09:25 zjsdecode
-rwxr-xr-x  1 root    root      63664 2008-03-12 10:24 zsoelim

```
This is what you wanted me to post, right?

---

### Post by flyingsolo on 2008-06-19
Yes, kansasnoob, I've done as you suggested also.  All is up to date.

---

### Post by aysiu on 2008-06-19
Unfortunately, I just got the tailend of that input. I was mainly looking for /usr/bin/firefox

Can you post the output of these two commands? ```
ls /usr/bin/firefox -l
ls /opt/
```

---

### Post by flyingsolo on 2008-06-19
As requested:
```
michael@ubuntu-desktop:~$ ls /usr/bin/firefox -l
lrwxrwxrwx 1 root root 20 2007-01-23 12:00 /usr/bin/firefox -> /opt/firefox/firefox
michael@ubuntu-desktop:~$ ls /opt/
azureus  CastPodder  firefox  picasa
michael@ubuntu-desktop:~$
```

---

### Post by aysiu on 2008-06-20
I think I see the problem.

Paste these commands in the terminal ```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm -r /opt/firefox
``` Then the *firefox* command should launch Firefox 3.0

---

### Post by flyingsolo on 2008-06-20
Great! and many thanks!  Now, hopefully I'm not overtaxing your patience to ask for a brief analysis of what the problem was or why the usual updating process didn't work as it did with my other Ubuntu machine (laptop).  What problem did you spot?
(don't get me wrong, it's great to have a solution but since I'm just copy/pasting your suggestions, I don't know if I've learned anything in this process)

---

### Post by aysiu on 2008-06-20
Sure thing.

There is Firefox from Ubuntu.

And then there is Firefox from Mozilla.

The standard way to install the Firefox from Mozilla is to place it in the /opt directory and then link it to the launcher for Firefox (/usr/bin/firefox).

So at some point, you probably installed the Mozilla version of Firefox 2 into /opt and symlinked to /usr/bin/firefox. So when you launched Firefox, you were launching the Mozilla Firefox (2) from /opt/firefox/firefox instead of the Ubuntu Firefox (which is now 3).

So we removed the Mozilla Firefox (2) from /opt and restored the /usr/bin/firefox to the Ubuntu Firefox (3).

Does that make sense?

---

### Post by kansasnoob on 2008-06-20
> **aysiu said:**
> Sure thing.

There is Firefox from Ubuntu.

And then there is Firefox from Mozilla.

The standard way to install the Firefox from Mozilla is to place it in the /opt directory and then link it to the launcher for Firefox (/usr/bin/firefox).

So at some point, you probably installed the Mozilla version of Firefox 2 into /opt and symlinked to /usr/bin/firefox. So when you launched Firefox, you were launching the Mozilla Firefox (2) from /opt/firefox/firefox instead of the Ubuntu Firefox (which is now 3).

So we removed the Mozilla Firefox (2) from /opt and restored the /usr/bin/firefox to the Ubuntu Firefox (3).

Does that make sense?

Hats off to aysiu!

Thanks for being here! SERIOUSLY!

---

### Post by flyingsolo on 2008-06-20
Thanks again--this helps alot b/c each incremental bit of knowledge maybe avoids a future trip to the forums to sort something out.

---

