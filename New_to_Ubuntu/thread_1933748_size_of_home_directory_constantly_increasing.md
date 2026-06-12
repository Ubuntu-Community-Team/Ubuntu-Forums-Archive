---
title: "size of home directory constantly increasing"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by devendram on 2012-03-01
Hi,
     Size of /home directory is constantly increasing without doing anything. But when I checked the list in that directory with ll command I could not find any file or directory which takes  more than 55 kilo bytes. When I used du -sh command it shows 4.9 GB its so strange. What could be the problem ? What is eating up disk space constantly in /home directory ?

~$du -sh
4.9G    

~$ll
total 396[HTML]
drwxr-xr-x 44 devendra devendra  4096 2012-03-01 10:21 ./
drwxr-xr-x  3 root     root      4096 2012-02-29 19:30 ../
drwx------  4 devendra devendra  4096 2012-02-06 17:53 .adobe/
-rw-------  1 devendra devendra 30670 2012-02-29 21:58 .bash_history
-rw-r--r--  1 devendra devendra   220 2012-01-15 16:20 .bash_logout
-rw-r--r--  1 devendra devendra  3353 2012-01-15 16:20 .bashrc
drwxrwxr-x  2 devendra devendra  4096 2012-02-29 10:45 bin/
drwxr-xr-x  3 devendra devendra  4096 2012-02-16 16:47 .bluefish/
drwx------ 17 devendra devendra  4096 2012-02-29 15:12 .cache/
drwxrwxr-x  3 devendra devendra  4096 2012-01-16 13:32 .compiz-1/
drwx------ 28 devendra devendra  4096 2012-02-21 13:48 .config/
drwx------  3 devendra devendra  4096 2012-01-15 16:27 .dbus/
drwxr-xr-x  3 devendra devendra  4096 2012-02-29 22:18 Desktop/
-rw-rw-r--  1 devendra devendra    33 2012-03-01 10:21 .dmrc
drwxr-xr-x  2 devendra devendra  4096 2012-02-17 19:47 Documents/
drwxr-xr-x  4 devendra devendra  4096 2012-02-29 11:31 Downloads/
-rw-------  1 devendra devendra    16 2012-01-15 16:27 .esd_auth
-rw-r--r--  1 devendra devendra   179 2012-01-15 16:20 examples.desktop
drwx------  2 devendra devendra  4096 2012-02-29 19:42 .filezilla/
drwxr-xr-x  2 devendra devendra  4096 2012-02-07 19:10 .fontconfig/
drwx------  6 devendra devendra  4096 2012-03-01 10:21 .gconf/
drwx------  5 devendra devendra  4096 2012-02-16 16:31 .gnome2/
drwx------  2 devendra devendra  4096 2012-02-04 16:57 .gnome2_private/
-rw-------  1 devendra devendra     0 2012-02-17 19:50 .goutputstream-72BK9V
-rw-------  1 devendra devendra     0 2012-01-26 11:23 .goutputstream-GMSP8V
drwxrwxr-x  3 devendra devendra  4096 2012-02-16 16:51 .gphpedit/
drwxrwxr-x  2 devendra devendra  4096 2012-02-25 15:38 .gstreamer-0.10/
-rw-rw-r--  1 devendra devendra   152 2012-03-01 10:21 .gtk-bookmarks
dr-x------  2 devendra devendra     0 2012-03-01 10:21 .gvfs/
-rw-------  1 devendra devendra 38866 2012-03-01 10:21 .ICEauthority
-rw-rw-r--  1 devendra devendra 45805 2012-02-07 17:09 IMG_07022012_152307.png
drwxrwxr-x  3 devendra devendra  4096 2012-01-25 10:48 .java/
drwxrwxr-x  4 devendra devendra  4096 2012-02-16 12:45 .komodoedit/
drwxrwxr-x  3 devendra devendra  4096 2012-01-15 21:47 .libreoffice/
drwxr-xr-x  3 devendra devendra  4096 2012-01-15 16:27 .local/
drwx------  3 devendra devendra  4096 2012-01-22 17:25 .macromedia/
drwx------  8 devendra devendra  4096 2012-02-05 14:31 Matrixrate/
drwx------  3 devendra devendra  4096 2012-01-15 16:27 .mission-control/
drwx------  4 devendra devendra  4096 2012-01-15 16:28 .mozilla/
drwxr-xr-x  2 devendra devendra  4096 2012-01-15 16:27 Music/
drwx------  4 devendra devendra  4096 2012-02-04 16:59 .mysqlgui/
-rw-------  1 devendra devendra   463 2012-02-05 18:41 .mysql_history
-rw-------  1 root     root        42 2012-02-07 13:09 .nano_history
drwxrwxr-x  3 devendra devendra  4096 2012-01-23 12:37 .netbeans/
drwxrwxr-x  4 devendra devendra  4096 2012-01-28 15:50 .onboard/
drwxr-xr-x  2 devendra devendra  4096 2012-02-29 20:59 Pictures/
-rw-r--r--  1 devendra devendra   797 2012-01-24 10:02 .profile
drwxr-xr-x  2 devendra devendra  4096 2012-01-15 16:27 Public/
drwx------  2 devendra devendra  4096 2012-03-01 10:21 .pulse/
-rw-------  1 devendra devendra   256 2012-01-15 16:27 .pulse-cookie
-rw-------  1 root     root      1024 2012-02-05 13:18 .rnd
-rw-rw-r--  1 devendra devendra    66 2012-02-29 17:57 .selected_editor
-rw-rw-r--  1 devendra devendra  1235 2012-02-06 18:53 shipping.1.txt
-rw-rw-r--  1 devendra devendra  1183 2012-02-06 18:30 shipping.txt
drwx------  5 devendra devendra  4096 2012-02-29 21:38 .Skype/
drwx------  4 devendra devendra  4096 2012-02-27 15:54 .speech-dispatcher/
drwx------  2 devendra devendra  4096 2012-02-21 14:05 .ssh/
-rw-rw-r--  1 devendra devendra  2086 2012-02-07 16:25 stockstatus.php
-rw-rw-r--  1 devendra devendra  2121 2012-02-06 15:51 stockstatus.php~
-rw-r--r--  1 devendra devendra     0 2012-01-15 21:36 .sudo_as_admin_successful
-rw-rw-r--  1 devendra devendra  1369 2012-02-06 15:19 superduper.1.php
-rw-rw-r--  1 devendra devendra  1312 2012-02-06 14:54 superduper.1.php~
-rw-rw-r--  1 devendra devendra   917 2012-02-06 14:48 superduper.php
drwxr-xr-x  2 devendra devendra  4096 2012-01-15 16:27 Templates/
drwx------  5 devendra devendra  4096 2012-01-16 13:32 .thumbnails/
drwx------  4 devendra devendra  4096 2012-02-07 17:40 .thunderbird/
drwxrwxr-x  2 devendra devendra  4096 2012-01-21 19:10 Ubuntu One/
drwxr-xr-x  2 devendra devendra  4096 2012-01-15 16:27 Videos/
-rw-------  1 devendra devendra   696 2012-02-16 16:33 .viminfo
-rw-------  1 devendra devendra    64 2012-03-01 10:21 .Xauthority
drwxr-xr-x  4 devendra devendra  4096 2012-01-22 16:19 .xmms/
-rw-------  1 devendra devendra 12397 2012-03-01 10:40 .xsession-errors[/HTML]

---

### Post by jerome1232 on 2012-03-01
enclose the output in code tags to increase readability. (go to advanced mode, highlight all of the output, and click the number symbol on the toolbar)

what do these look like? Do you have an automatic backup solution? (I've seen forgotten automatic backups cause this kind of thing more times then I can count so I'm asking)

```
df -h
du -hx --max-depth=1 ~
```

---

### Post by devendram on 2012-03-01
> **jerome1232 said:**
> enclose the output in code tags to increase readability. (go to advanced mode, highlight all of the output, and click the number symbol on the toolbar)

what do these look like? Do you have an automatic backup solution? (I've seen forgotten automatic backups cause this kind of thing more times then I can count so I'm asking)

```
df -h
du -hx --max-depth=1 ~
```

Backup is not enabled.

:~$ du -hx --max-depth=1 ~```

40K    /home/devendra/.pulse
176K    /home/devendra/.macromedia
40K    /home/devendra/.speech-dispatcher
396K    /home/devendra/.gstreamer-0.10
12K    /home/devendra/.dbus
284K    /home/devendra/.java
57M    /home/devendra/.netbeans
32K    /home/devendra/.mysqlgui
64K    /home/devendra/.compiz-1
71M    /home/devendra/.mozilla
56M    /home/devendra/.komodoedit
12K    /home/devendra/.onboard
1.6M    /home/devendra/.config
4.0K    /home/devendra/.gnome2_private
3.3M    /home/devendra/.Skype
840K    /home/devendra/.adobe
1.1M    /home/devendra/.libreoffice
4.0K    /home/devendra/Templates
12K    /home/devendra/.bluefish
276K    /home/devendra/Matrixrate
4.0K    /home/devendra/Ubuntu One
12K    /home/devendra/.gphpedit
4.0K    /home/devendra/Music
12K    /home/devendra/.mission-control
9.7M    /home/devendra/.cache
8.0K    /home/devendra/.ssh
48K    /home/devendra/.gnome2
28K    /home/devendra/.xmms
4.0K    /home/devendra/Videos
996K    /home/devendra/Pictures
6.5M    /home/devendra/.thumbnails
0    /home/devendra/.gvfs
3.3M    /home/devendra/.gconf
92K    /home/devendra/.fontconfig
4.3G    /home/devendra/.thunderbird
4.0K    /home/devendra/Public
14M    /home/devendra/.local
64K    /home/devendra/.filezilla
112M    /home/devendra/Downloads
136K    /home/devendra/Documents
528K    /home/devendra/Desktop
12K    /home/devendra/bin
4.7G    /home/devendra
```Thanks [jerome1232]("http://ubuntuforums.org/member.php?u=453029") , Here I can see thunderbird is taking 4.3G, I have only about 500 emails in inbox with less sized attachments. I have deleted all mails but still showing same size . How to free that space ?

---

### Post by winh8r on 2012-03-01
run the following command to refresh everything:


```
sudo updatedb
```

then check again, all should be correctly displayed now.

Hope this helps.

---

### Post by devendram on 2012-03-01
> **winh8r said:**
> run the following command to refresh everything:


```
sudo updatedb
```then check again, all should be correctly displayed now.

Hope this helps.

I run that command but nothing changed, size of thunderbird is still the same. How to delete .thunderbird in /home ?

---

### Post by SlugSlug on 2012-03-01
I'd find out why its 4gig before deleting it...


ls -Rlh ~/.thinderbird

---

### Post by devendram on 2012-03-01
> **SlugSlug said:**
> I'd find out why its 4gig before deleting it...


ls -Rlh ~/.thinderbird

sudo ls -Rlh ~/.thunderbird
```

/home/devendra/.thunderbird:
total 16K
-rw-rw-r-- 1 devendra devendra  335 2012-02-07 17:40 appreg
drwx------ 4 devendra devendra 4.0K 2012-02-29 13:41 Crash Reports
-rw-rw-r-- 1 devendra devendra   94 2012-02-07 17:40 profiles.ini
drwx------ 7 devendra devendra 4.0K 2012-03-01 16:30 tkmlitpn.default

/home/devendra/.thunderbird/Crash Reports:
total 24K
-rw-rw-r-- 1 devendra devendra   42 2012-02-29 13:40 crashreporter.ini
-rw------- 1 devendra devendra   10 2012-02-07 17:40 InstallTime20110929181644
-rw------- 1 devendra devendra   10 2012-02-29 13:40 LastCrash
drwx------ 2 devendra devendra 4.0K 2012-02-29 13:41 pending
-rw-rw-r-- 1 devendra devendra   70 2012-02-29 13:41 submit.log
drwx------ 2 devendra devendra 4.0K 2012-02-29 13:41 submitted

/home/devendra/.thunderbird/Crash Reports/pending:
total 0

/home/devendra/.thunderbird/Crash Reports/submitted:
total 4.0K
-rw-rw-r-- 1 devendra devendra 50 2012-02-29 13:41 bp-0bd50fa7-6724-4192-8827-dc7dd2120229.txt

/home/devendra/.thunderbird/tkmlitpn.default:
total 30M
-rw-rw-r--  1 devendra devendra 1.4K 2012-02-23 10:34 abook.mab
-rw-r--r--  1 devendra devendra 256K 2012-03-01 15:51 addons.sqlite
-rw-r--r--  1 devendra devendra  11K 2012-03-01 15:53 blocklist.xml
drwxrwxr-x 18 devendra devendra 4.0K 2012-03-01 15:37 Cache
-rw-------  1 devendra devendra  64K 2012-03-01 16:30 cert8.db
-rw-------  1 devendra devendra  170 2012-02-07 17:41 compatibility.ini
-rw-r--r--  1 devendra devendra 512K 2012-02-24 08:37 cookies.sqlite
-rw-r--r--  1 devendra devendra  64K 2012-02-28 22:13 downloads.sqlite
-rw-r--r--  1 devendra devendra  354 2012-02-07 17:40 extensions.ini
-rw-r--r--  1 devendra devendra 384K 2012-02-24 10:34 extensions.sqlite
-rw-rw-r--  1 devendra devendra   69 2012-03-01 16:30 folderTree.json
-rw-r--r--  1 devendra devendra  14M 2012-03-01 16:14 global-messages-db.sqlite
-rw-rw-r--  1 devendra devendra 2.7K 2012-02-29 21:35 history.mab
drwx------  3 devendra devendra 4.0K 2012-02-24 07:13 ImapMail
-rw-------  1 devendra devendra  16K 2012-03-01 16:30 key3.db
-rw-rw-r--  1 devendra devendra 8.6K 2012-03-01 16:12 localstore.rdf
drwx------  6 devendra devendra 4.0K 2012-03-01 15:52 Mail
-rw-r--r--  1 devendra devendra  482 2012-02-23 10:32 mailViews.dat
-rw-rw-r--  1 devendra devendra  607 2012-02-29 22:01 mimeTypes.rdf
drwx------  2 devendra devendra 4.0K 2012-02-29 13:40 minidumps
-rw-rw-r--  1 devendra devendra 9.1K 2012-03-01 16:30 panacea.dat
-rw-r--r--  1 devendra devendra  64K 2012-03-01 15:53 permissions.sqlite
-rw-r--r--  1 devendra devendra  10M 2012-02-28 22:13 places.sqlite
-rw-------  1 devendra devendra 6.0K 2012-02-23 10:32 pluginreg.dat
-rw-------  1 devendra devendra 7.9K 2012-03-01 16:30 prefs.js
-rw-r--r--  1 devendra devendra   74 2012-02-24 07:09 search.json
-rw-------  1 devendra devendra  16K 2012-02-23 10:32 secmod.db
-rw-rw-r--  1 devendra devendra   86 2012-03-01 16:17 session.json
-rw-r--r--  1 devendra devendra 288K 2012-03-01 15:39 signons.sqlite
drwxrwxr-x  2 devendra devendra 4.0K 2012-02-07 17:41 startupCache
-rw-r--r--  1 devendra devendra 5.0M 2012-02-23 10:44 urlclassifier3.sqlite
-rw-rw-r--  1 devendra devendra  178 2012-03-01 16:30 virtualFolders.dat

/home/devendra/.thunderbird/tkmlitpn.default/Cache:
total 196K
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 0
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 1
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 2
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 3
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 4
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 5
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 6
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 7
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 8
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 9
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 A
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 B
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 C
-rw------- 1 devendra devendra  21K 2012-03-01 16:12 _CACHE_001_
-rw------- 1 devendra devendra 7.7K 2012-03-01 16:12 _CACHE_002_
-rw------- 1 devendra devendra  87K 2012-03-01 16:12 _CACHE_003_
-rw------- 1 devendra devendra 8.3K 2012-03-01 16:12 _CACHE_MAP_
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 D
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 E
drwx------ 3 devendra devendra 4.0K 2012-03-01 15:38 F

/home/devendra/.thunderbird/tkmlitpn.default/Cache/0:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/1:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/2:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/3:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/4:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/5:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/6:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/7:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/8:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/9:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/A:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/B:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/C:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/D:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/E:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/F:
total 4.0K
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:38 7F

/home/devendra/.thunderbird/tkmlitpn.default/Cache/F/7F:
total 64K
-rw------- 1 devendra devendra 62K 2012-03-01 15:38 34E7Ed01

/home/devendra/.thunderbird/tkmlitpn.default/ImapMail:
total 8.0K
drwxr-xr-x 3 devendra devendra 4.0K 2012-03-01 15:38 imap.googlemail.com
-rw-rw-r-- 1 devendra devendra 1.2K 2012-02-24 08:37 imap.googlemail.com.msf

/home/devendra/.thunderbird/tkmlitpn.default/ImapMail/imap.googlemail.com:
total 3.2G
-rw-rw-r-- 1 devendra devendra 1.3K 2012-02-24 07:14 Archives.msf
-rw-rw-r-- 1 devendra devendra 1.2K 2012-02-24 07:13 Drafts.msf
-rw-rw-r-- 1 devendra devendra 1.4K 2012-02-29 14:34 [Gmail].msf
drwx------ 2 devendra devendra 4.0K 2012-02-29 15:15 [Gmail].sbd
-rw------- 1 devendra devendra 3.2G 2012-03-01 11:04 INBOX
-rw-rw-r-- 1 devendra devendra 332K 2012-03-01 16:11 INBOX.msf
-rw-r--r-- 1 devendra devendra   25 2012-02-24 07:13 msgFilterRules.dat
-rw------- 1 devendra devendra 3.9K 2012-02-28 15:45 Personal
-rw-rw-r-- 1 devendra devendra 2.4K 2012-02-28 15:45 Personal.msf
-rw-rw-r-- 1 devendra devendra 1.6K 2012-02-24 09:02 Receipts.msf
-rw-rw-r-- 1 devendra devendra 1.2K 2012-02-24 07:13 Sent.msf
-rw-rw-r-- 1 devendra devendra 1.3K 2012-02-24 07:14 Templates.msf
-rw-rw-r-- 1 devendra devendra 1.9K 2012-03-01 16:11 Trash.msf
-rw-rw-r-- 1 devendra devendra 1.6K 2012-02-24 08:48 Travel.msf
-rw-rw-r-- 1 devendra devendra 1.6K 2012-02-24 08:48 Work.msf

/home/devendra/.thunderbird/tkmlitpn.default/ImapMail/imap.googlemail.com/[Gmail].sbd:
total 1.2G
-rw------- 1 devendra devendra 377M 2012-03-01 15:41 All Mail
-rw-rw-r-- 1 devendra devendra 736K 2012-03-01 16:11 All Mail.msf
-rw------- 1 devendra devendra 1.2M 2012-02-29 21:00 Drafts
-rw-rw-r-- 1 devendra devendra  15K 2012-03-01 15:41 Drafts.msf
-rw------- 1 devendra devendra  87M 2012-03-01 10:32 Important
-rw-rw-r-- 1 devendra devendra 193K 2012-03-01 16:11 Important.msf
-rw------- 1 devendra devendra 485M 2012-03-01 11:04 Sent Mail
-rw-rw-r-- 1 devendra devendra 256K 2012-03-01 15:41 Sent Mail.msf
-rw------- 1 devendra devendra  18M 2012-03-01 10:23 Spam
-rw-rw-r-- 1 devendra devendra 7.3K 2012-03-01 15:40 Spam.msf
-rw-rw-r-- 1 devendra devendra 1.7K 2012-02-24 18:34 Starred.msf
-rw------- 1 devendra devendra 250M 2012-03-01 15:51 Trash
-rw-rw-r-- 1 devendra devendra 693K 2012-03-01 16:11 Trash.msf

/home/devendra/.thunderbird/tkmlitpn.default/Mail:
total 24K
drwxr-xr-x 2 devendra devendra 4.0K 2012-02-07 17:41 Feeds
-rw-rw-r-- 1 devendra devendra 1.3K 2012-02-23 10:34 Feeds.msf
drwxr-xr-x 2 devendra devendra 4.0K 2012-02-23 13:06 Local Folders
drwxr-xr-x 2 devendra devendra 4.0K 2012-02-23 13:06 pop.googlemail.com
-rw-rw-r-- 1 devendra devendra 1.2K 2012-02-24 07:11 pop.googlemail.com.msf
drwxr-xr-x 2 devendra devendra 4.0K 2012-03-01 15:52 smart mailboxes

/home/devendra/.thunderbird/tkmlitpn.default/Mail/Feeds:
total 8.0K
-rw-r--r-- 1 devendra devendra  321 2012-02-07 17:41 feeds.rdf
-rw-r--r-- 1 devendra devendra    0 2012-02-07 17:41 Trash
-rw-rw-r-- 1 devendra devendra 1.8K 2012-03-01 16:11 Trash.msf

/home/devendra/.thunderbird/tkmlitpn.default/Mail/Local Folders:
total 8.0K
-rw-r--r-- 1 devendra devendra    0 2012-02-07 17:41 Trash
-rw-rw-r-- 1 devendra devendra 2.1K 2012-03-01 15:49 Trash.msf
-rw-r--r-- 1 devendra devendra    0 2012-02-07 17:41 Unsent Messages
-rw-rw-r-- 1 devendra devendra 2.1K 2012-03-01 15:49 Unsent Messages.msf

/home/devendra/.thunderbird/tkmlitpn.default/Mail/pop.googlemail.com:
total 25M
-rw-r--r-- 1 devendra devendra  13M 2012-02-23 13:44 Inbox
-rw-rw-r-- 1 devendra devendra  43K 2012-02-24 08:34 Inbox.msf
-rw-r--r-- 1 devendra devendra   25 2012-02-23 10:43 msgFilterRules.dat
-rw------- 1 devendra devendra  14K 2012-02-23 13:44 popstate.dat
-rw------- 1 devendra devendra  578 2012-02-23 11:05 Sent
-rw-rw-r-- 1 devendra devendra 2.7K 2012-02-24 07:11 Sent.msf
-rw-r--r-- 1 devendra devendra  13M 2012-02-23 11:21 Trash
-rw-rw-r-- 1 devendra devendra 174K 2012-02-23 12:21 Trash.msf

/home/devendra/.thunderbird/tkmlitpn.default/Mail/smart mailboxes:
total 4.0K
-rw-r--r-- 1 devendra devendra    0 2012-03-01 15:52 Trash
-rw-rw-r-- 1 devendra devendra 1.6K 2012-03-01 16:30 Trash.msf

/home/devendra/.thunderbird/tkmlitpn.default/minidumps:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/startupCache:
total 2.0M
-rw-rw-r-- 1 devendra devendra 2.0M 2012-03-01 15:54 startupCache.4.little
devendra@devendra-Vostro1510:~$ clear screen

devendra@devendra-Vostro1510:~$ sudo ls -Rlh ~/.thunderbird
/home/devendra/.thunderbird:
total 16K
-rw-rw-r-- 1 devendra devendra  335 2012-02-07 17:40 appreg
drwx------ 4 devendra devendra 4.0K 2012-02-29 13:41 Crash Reports
-rw-rw-r-- 1 devendra devendra   94 2012-02-07 17:40 profiles.ini
drwx------ 7 devendra devendra 4.0K 2012-03-01 16:30 tkmlitpn.default

/home/devendra/.thunderbird/Crash Reports:
total 24K
-rw-rw-r-- 1 devendra devendra   42 2012-02-29 13:40 crashreporter.ini
-rw------- 1 devendra devendra   10 2012-02-07 17:40 InstallTime20110929181644
-rw------- 1 devendra devendra   10 2012-02-29 13:40 LastCrash
drwx------ 2 devendra devendra 4.0K 2012-02-29 13:41 pending
-rw-rw-r-- 1 devendra devendra   70 2012-02-29 13:41 submit.log
drwx------ 2 devendra devendra 4.0K 2012-02-29 13:41 submitted

/home/devendra/.thunderbird/Crash Reports/pending:
total 0

/home/devendra/.thunderbird/Crash Reports/submitted:
total 4.0K
-rw-rw-r-- 1 devendra devendra 50 2012-02-29 13:41 bp-0bd50fa7-6724-4192-8827-dc7dd2120229.txt

/home/devendra/.thunderbird/tkmlitpn.default:
total 30M
-rw-rw-r--  1 devendra devendra 1.4K 2012-02-23 10:34 abook.mab
-rw-r--r--  1 devendra devendra 256K 2012-03-01 15:51 addons.sqlite
-rw-r--r--  1 devendra devendra  11K 2012-03-01 15:53 blocklist.xml
drwxrwxr-x 18 devendra devendra 4.0K 2012-03-01 15:37 Cache
-rw-------  1 devendra devendra  64K 2012-03-01 16:30 cert8.db
-rw-------  1 devendra devendra  170 2012-02-07 17:41 compatibility.ini
-rw-r--r--  1 devendra devendra 512K 2012-02-24 08:37 cookies.sqlite
-rw-r--r--  1 devendra devendra  64K 2012-02-28 22:13 downloads.sqlite
-rw-r--r--  1 devendra devendra  354 2012-02-07 17:40 extensions.ini
-rw-r--r--  1 devendra devendra 384K 2012-02-24 10:34 extensions.sqlite
-rw-rw-r--  1 devendra devendra   69 2012-03-01 16:30 folderTree.json
-rw-r--r--  1 devendra devendra  14M 2012-03-01 16:14 global-messages-db.sqlite
-rw-rw-r--  1 devendra devendra 2.7K 2012-02-29 21:35 history.mab
drwx------  3 devendra devendra 4.0K 2012-02-24 07:13 ImapMail
-rw-------  1 devendra devendra  16K 2012-03-01 16:30 key3.db
-rw-rw-r--  1 devendra devendra 8.6K 2012-03-01 16:12 localstore.rdf
drwx------  6 devendra devendra 4.0K 2012-03-01 15:52 Mail
-rw-r--r--  1 devendra devendra  482 2012-02-23 10:32 mailViews.dat
-rw-rw-r--  1 devendra devendra  607 2012-02-29 22:01 mimeTypes.rdf
drwx------  2 devendra devendra 4.0K 2012-02-29 13:40 minidumps
-rw-rw-r--  1 devendra devendra 9.1K 2012-03-01 16:30 panacea.dat
-rw-r--r--  1 devendra devendra  64K 2012-03-01 15:53 permissions.sqlite
-rw-r--r--  1 devendra devendra  10M 2012-02-28 22:13 places.sqlite
-rw-------  1 devendra devendra 6.0K 2012-02-23 10:32 pluginreg.dat
-rw-------  1 devendra devendra 7.9K 2012-03-01 16:30 prefs.js
-rw-r--r--  1 devendra devendra   74 2012-02-24 07:09 search.json
-rw-------  1 devendra devendra  16K 2012-02-23 10:32 secmod.db
-rw-rw-r--  1 devendra devendra   86 2012-03-01 16:17 session.json
-rw-r--r--  1 devendra devendra 288K 2012-03-01 15:39 signons.sqlite
drwxrwxr-x  2 devendra devendra 4.0K 2012-02-07 17:41 startupCache
-rw-r--r--  1 devendra devendra 5.0M 2012-02-23 10:44 urlclassifier3.sqlite
-rw-rw-r--  1 devendra devendra  178 2012-03-01 16:30 virtualFolders.dat

/home/devendra/.thunderbird/tkmlitpn.default/Cache:
total 196K
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 0
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 1
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 2
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 3
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 4
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 5
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 6
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 7
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 8
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 9
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 A
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 B
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 C
-rw------- 1 devendra devendra  21K 2012-03-01 16:12 _CACHE_001_
-rw------- 1 devendra devendra 7.7K 2012-03-01 16:12 _CACHE_002_
-rw------- 1 devendra devendra  87K 2012-03-01 16:12 _CACHE_003_
-rw------- 1 devendra devendra 8.3K 2012-03-01 16:12 _CACHE_MAP_
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 D
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:37 E
drwx------ 3 devendra devendra 4.0K 2012-03-01 15:38 F

/home/devendra/.thunderbird/tkmlitpn.default/Cache/0:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/1:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/2:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/3:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/4:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/5:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/6:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/7:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/8:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/9:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/A:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/B:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/C:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/D:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/E:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/Cache/F:
total 4.0K
drwx------ 2 devendra devendra 4.0K 2012-03-01 15:38 7F

/home/devendra/.thunderbird/tkmlitpn.default/Cache/F/7F:
total 64K
-rw------- 1 devendra devendra 62K 2012-03-01 15:38 34E7Ed01

/home/devendra/.thunderbird/tkmlitpn.default/ImapMail:
total 8.0K
drwxr-xr-x 3 devendra devendra 4.0K 2012-03-01 15:38 imap.googlemail.com
-rw-rw-r-- 1 devendra devendra 1.2K 2012-02-24 08:37 imap.googlemail.com.msf

/home/devendra/.thunderbird/tkmlitpn.default/ImapMail/imap.googlemail.com:
total 3.2G
-rw-rw-r-- 1 devendra devendra 1.3K 2012-02-24 07:14 Archives.msf
-rw-rw-r-- 1 devendra devendra 1.2K 2012-02-24 07:13 Drafts.msf
-rw-rw-r-- 1 devendra devendra 1.4K 2012-02-29 14:34 [Gmail].msf
drwx------ 2 devendra devendra 4.0K 2012-02-29 15:15 [Gmail].sbd
-rw------- 1 devendra devendra 3.2G 2012-03-01 11:04 INBOX
-rw-rw-r-- 1 devendra devendra 332K 2012-03-01 16:11 INBOX.msf
-rw-r--r-- 1 devendra devendra   25 2012-02-24 07:13 msgFilterRules.dat
-rw------- 1 devendra devendra 3.9K 2012-02-28 15:45 Personal
-rw-rw-r-- 1 devendra devendra 2.4K 2012-02-28 15:45 Personal.msf
-rw-rw-r-- 1 devendra devendra 1.6K 2012-02-24 09:02 Receipts.msf
-rw-rw-r-- 1 devendra devendra 1.2K 2012-02-24 07:13 Sent.msf
-rw-rw-r-- 1 devendra devendra 1.3K 2012-02-24 07:14 Templates.msf
-rw-rw-r-- 1 devendra devendra 1.9K 2012-03-01 16:11 Trash.msf
-rw-rw-r-- 1 devendra devendra 1.6K 2012-02-24 08:48 Travel.msf
-rw-rw-r-- 1 devendra devendra 1.6K 2012-02-24 08:48 Work.msf

/home/devendra/.thunderbird/tkmlitpn.default/ImapMail/imap.googlemail.com/[Gmail].sbd:
total 1.2G
-rw------- 1 devendra devendra 377M 2012-03-01 15:41 All Mail
-rw-rw-r-- 1 devendra devendra 736K 2012-03-01 16:11 All Mail.msf
-rw------- 1 devendra devendra 1.2M 2012-02-29 21:00 Drafts
-rw-rw-r-- 1 devendra devendra  15K 2012-03-01 15:41 Drafts.msf
-rw------- 1 devendra devendra  87M 2012-03-01 10:32 Important
-rw-rw-r-- 1 devendra devendra 193K 2012-03-01 16:11 Important.msf
-rw------- 1 devendra devendra 485M 2012-03-01 11:04 Sent Mail
-rw-rw-r-- 1 devendra devendra 256K 2012-03-01 15:41 Sent Mail.msf
-rw------- 1 devendra devendra  18M 2012-03-01 10:23 Spam
-rw-rw-r-- 1 devendra devendra 7.3K 2012-03-01 15:40 Spam.msf
-rw-rw-r-- 1 devendra devendra 1.7K 2012-02-24 18:34 Starred.msf
-rw------- 1 devendra devendra 250M 2012-03-01 15:51 Trash
-rw-rw-r-- 1 devendra devendra 693K 2012-03-01 16:11 Trash.msf

/home/devendra/.thunderbird/tkmlitpn.default/Mail:
total 24K
drwxr-xr-x 2 devendra devendra 4.0K 2012-02-07 17:41 Feeds
-rw-rw-r-- 1 devendra devendra 1.3K 2012-02-23 10:34 Feeds.msf
drwxr-xr-x 2 devendra devendra 4.0K 2012-02-23 13:06 Local Folders
drwxr-xr-x 2 devendra devendra 4.0K 2012-02-23 13:06 pop.googlemail.com
-rw-rw-r-- 1 devendra devendra 1.2K 2012-02-24 07:11 pop.googlemail.com.msf
drwxr-xr-x 2 devendra devendra 4.0K 2012-03-01 15:52 smart mailboxes

/home/devendra/.thunderbird/tkmlitpn.default/Mail/Feeds:
total 8.0K
-rw-r--r-- 1 devendra devendra  321 2012-02-07 17:41 feeds.rdf
-rw-r--r-- 1 devendra devendra    0 2012-02-07 17:41 Trash
-rw-rw-r-- 1 devendra devendra 1.8K 2012-03-01 16:11 Trash.msf

/home/devendra/.thunderbird/tkmlitpn.default/Mail/Local Folders:
total 8.0K
-rw-r--r-- 1 devendra devendra    0 2012-02-07 17:41 Trash
-rw-rw-r-- 1 devendra devendra 2.1K 2012-03-01 15:49 Trash.msf
-rw-r--r-- 1 devendra devendra    0 2012-02-07 17:41 Unsent Messages
-rw-rw-r-- 1 devendra devendra 2.1K 2012-03-01 15:49 Unsent Messages.msf

/home/devendra/.thunderbird/tkmlitpn.default/Mail/pop.googlemail.com:
total 25M
-rw-r--r-- 1 devendra devendra  13M 2012-02-23 13:44 Inbox
-rw-rw-r-- 1 devendra devendra  43K 2012-02-24 08:34 Inbox.msf
-rw-r--r-- 1 devendra devendra   25 2012-02-23 10:43 msgFilterRules.dat
-rw------- 1 devendra devendra  14K 2012-02-23 13:44 popstate.dat
-rw------- 1 devendra devendra  578 2012-02-23 11:05 Sent
-rw-rw-r-- 1 devendra devendra 2.7K 2012-02-24 07:11 Sent.msf
-rw-r--r-- 1 devendra devendra  13M 2012-02-23 11:21 Trash
-rw-rw-r-- 1 devendra devendra 174K 2012-02-23 12:21 Trash.msf

/home/devendra/.thunderbird/tkmlitpn.default/Mail/smart mailboxes:
total 4.0K
-rw-r--r-- 1 devendra devendra    0 2012-03-01 15:52 Trash
-rw-rw-r-- 1 devendra devendra 1.6K 2012-03-01 16:30 Trash.msf

/home/devendra/.thunderbird/tkmlitpn.default/minidumps:
total 0

/home/devendra/.thunderbird/tkmlitpn.default/startupCache:
total 2.0M
-rw-rw-r-- 1 devendra devendra 2.0M 2012-03-01 15:54 startupCache.4.little

```

---

### Post by SlugSlug on 2012-03-01
you may want to expunge your inbox. Your setup with IMAP so your emails are still there after you delete until you expunge.

This can be done automatically on exit

[http://kb.mozillazine.org/Compacting_folders](http://kb.mozillazine.org/Compacting_folders)

---

### Post by devendram on 2012-03-01
> **SlugSlug said:**
> you may want to expunge your inbox. Your setup with IMAP so your emails are still there after you delete until you expunge.

This can be done automatically on exit

[http://kb.mozillazine.org/Compacting_folders](http://kb.mozillazine.org/Compacting_folders)

I have deleted .thunderbird because I found it bit inefficient while sending and receiving emails. So I am moving to Evolution.

Would deleting .thunderbird be problem ?

---

### Post by pootan on 2012-03-01
Check the size of .xsession-errors in your home folder once you have show hidden files active. It is often a cause of alarm for people.

---

### Post by jerome1232 on 2012-03-01
> **devendram said:**
> 
Would deleting .thunderbird be problem ?

As long as the emails are still on your email server, I don't see why it would be.

---

