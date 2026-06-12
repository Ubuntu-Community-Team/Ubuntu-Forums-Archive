---
title: "how to get rid of Mint?"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by rocka on 2008-09-07
Hi,
I think I've borked my system...

I added some lines to my /etc/apt/sources.list file, but it has created some side effects:

My normal google search in FF3 has been replaced by the Mint Custom Search.
And now flash is not working properly.
Any page with flash on it immediately pings my processor to 100%, and the volume is very very low, almost off.

I have since removed those lines from the sources list and reloaded, both in update manager and Synaptic, but still the problem remains.


I asked on IRC #Ubuntu and #ubbuntuforums and I was told I would have to back up /home and reinstall...


Is there any other way?

---

### Post by phidia on 2008-09-07
Since most of the problems you listed involve ff you could remove and re-install ff and see if that changes anything.

---

### Post by rzrgenesys187 on 2008-09-07
Just adding the lines to /etc/apt/sources.list should not have done anything you could try to find out what you installed from them and remove it.  I'd try reinstalling firefox first as recommended above.  To see packages recently downloaded in Synaptic go to File>>History

---

### Post by rocka on 2008-09-07
ok, thanks for the replies, guys.


I had already tried uninstalling and reinstalling FF...

here is the paste from /file/history in Synaptic:

```
Commit Log for Mon Aug 25 17:37:12 2008

[B]Upgraded the following packages:
firefox (3.0.1+build1+nobinonly-0ubuntu0.8.04.3) to 3.0.1+build1+nobinonly-1mint1-0ubuntu0.8.04.2
firefox-2 (2.0.0.16+1nobinonly-0ubuntu0.8.04.1) to 2.0.14+2nobinonly-1mint1
firefox-3.0 (3.0.1+build1+nobinonly-0ubuntu0.8.04.3) to 3.0.1+build1+nobinonly-1mint1-0ubuntu0.8.04.2
firefox-3.0-gnome-support (3.0.1+build1+nobinonly-0ubuntu0.8.04.3) to 3.0.1+build1+nobinonly-1mint1-0ubuntu0.8.04.2
firefox-gnome-support (3.0.1+build1+nobinonly-0ubuntu0.8.04.3) to 3.0.1+build1+nobinonly-1mint1-0ubuntu0.8.04.2
flashplugin-nonfree (9.0.124.0ubuntu2) to 10.0.b218-0ubuntu3[/B]
kaffeine (0.8.6-0ubuntu8.1) to 0.8.6-0ubuntu8.1ja1
libpurple0 (1:2.4.1-1ubuntu2.1) to 1:2.4.1-1ubuntu2.1ja2
libx11-6 (2:1.1.3-1ubuntu2) to 2:1.1.3-1ubuntu2ja1
libx11-data (2:1.1.3-1ubuntu2) to 2:1.1.3-1ubuntu2ja1
libx11-xcb1 (2:1.1.3-1ubuntu2) to 2:1.1.3-1ubuntu2ja1
pidgin (1:2.4.1-1ubuntu2.1) to 1:2.4.1-1ubuntu2.1ja2
pidgin-data (1:2.4.1-1ubuntu2.1) to 1:2.4.1-1ubuntu2.1ja2
scim-bridge-agent (0.4.14-1ubuntu2) to 0.4.14-1ubuntu3
scim-bridge-client-gtk (0.4.14-1ubuntu2) to 0.4.14-1ubuntu3
unzip (5.52-10ubuntu2) to 5.52-10ubuntu2.1ja1
xchat (2.8.4-0ubuntu7) to 2.8.4-1mint1-0ubuntu7
xchat-common (2.8.4-0ubuntu7) to 2.8.4-1mint1-0ubuntu7



Commit Log for Mon Aug 25 21:15:39 2008

Installed the following packages:
libswfdec-0.6-90 (0.6.4-2)
swfdec-mozilla (0.6.0-2ubuntu1)



Commit Log for Mon Aug 25 21:18:10 2008

Installed the following packages:
gnash (0.8.2-0ubuntu3)
gnash-common (0.8.2-0ubuntu3)
libboost-date-time1.34.1 (1.34.1-4ubuntu3)
libboost-thread1.34.1 (1.34.1-4ubuntu3)
mozilla-plugin-gnash (0.8.2-0ubuntu3)



Commit Log for Tue Aug 26 19:11:03 2008

Upgraded the following packages:
linux-headers-2.6.24-19 (2.6.24-19.36) to 2.6.24-19.41
linux-headers-2.6.24-19-generic (2.6.24-19.36) to 2.6.24-19.41
linux-image-2.6.24-19-generic (2.6.24-19.36) to 2.6.24-19.41



Commit Log for Wed Aug 27 22:34:41 2008

Installed the following packages:
libglib1.2ldbl (1.2.10-19build1)
libgtk1.2 (1.2.10-18.1build2)
libgtk1.2-common (1.2.10-18.1build2)
lopster (1.2.2-4build1)



Commit Log for Thu Aug 28 20:20:38 2008

Upgraded the following packages:
yelp (2.22.1-0ubuntu2.8.04.2) to 2.22.1-0ubuntu2.8.04.3



Commit Log for Tue Sep  2 07:33:32 2008

Upgraded the following packages:
libgksu2-0 (2.0.5-1ubuntu5.1) to 2.0.5-1ubuntu5.2
libglib2.0-0 (2.16.4-0ubuntu2) to 2.16.4-0ubuntu3
libsoup2.4-1 (2.4.1-1) to 2.4.1-1ubuntu1



Commit Log for Tue Sep  2 21:24:55 2008

Upgraded the following packages:
eject (2.1.5-6) to 2.1.5-6ubuntu1



Commit Log for Wed Sep  3 18:24:16 2008

Upgraded the following packages:
libtiff4 (3.8.2-7ubuntu3) to 3.8.2-7ubuntu3.1



Commit Log for Thu Sep  4 18:54:46 2008

Upgraded the following packages:
libxml2 (2.6.31.dfsg-2ubuntu1) to 2.6.31.dfsg-2ubuntu1.1
libxml2-utils (2.6.31.dfsg-2ubuntu1) to 2.6.31.dfsg-2ubuntu1.1
python-libxml2 (2.6.31.dfsg-2ubuntu1) to 2.6.31.dfsg-2ubuntu1.1



Commit Log for Sat Sep  6 16:58:26 2008

Upgraded the following packages:
language-pack-en (1:8.04+20080708) to 1:8.04+20080805
language-pack-gnome-en (1:8.04+20080708) to 1:8.04+20080805
libsmbclient (3.0.28a-1ubuntu4.4) to 3.0.28a-1ubuntu4.5
samba-common (3.0.28a-1ubuntu4.4) to 3.0.28a-1ubuntu4.5
smbclient (3.0.28a-1ubuntu4.4) to 3.0.28a-1ubuntu4.5
winbind (3.0.28a-1ubuntu4.4) to 3.0.28a-1ubuntu4.5



Commit Log for Sat Sep  6 19:21:51 2008

[B]Removed the following packages:
firefox
firefox-3.0
firefox-3.0-gnome-support
firefox-gnome-support[/B]



Commit Log for Sat Sep  6 19:24:17 2008
[B]
Installed the following packages:
firefox-3.0 (3.0.1+build1+nobinonly-0ubuntu0.8.04.3)[/B]



Commit Log for Sun Sep  7 23:51:34 2008

[B]Removed the following packages:
flashplugin-nonfree
gstreamer0.10-ffmpeg
ubuntu-restricted-extras[/B]



Commit Log for Mon Sep  8 10:44:09 2008

[B]Installed the following packages:
flashplugin-nonfree (9.0.124.0ubuntu2)[/B]

```

there's a bunch of stuff in there that  don't think is related, but I left it there just in case. I bolded the bits that I think relate...

---

