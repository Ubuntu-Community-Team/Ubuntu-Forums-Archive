---
title: "zoneminder install not working"
date: 2014-10-09
forum: New to Ubuntu
---

### Post by jeffjohn2 on 2014-10-09
try as i might, I can not install Zoneminder using apt-get.  In terminal, I get the response:

invoke-rc.d: initscript zoneminder, action "start" failed.
dpkg: error processing package zoneminder (--configure):
 subprocess installed post-installation script returned error exit status 255
Errors were encountered while processing:
 zoneminder
E: Sub-process /usr/bin/dpkg returned an error code (1)

I did previously have it running but subsequently would not run so 'removed' and attempted new install.

Any suggestions, please, thanks, Jeff

---

### Post by Vladlenin5000 on 2014-10-09
How exactly have you "removed" it? Knowing that may give us a clue about why it isn't installing now...
Anyway, it looks like a sources problem. I would check if there are other errors with *sudo apt-get update*.

---

### Post by tgalati4 on 2014-10-09
Zoneminder uses a lot of frameworks:

```
apt-cache depends zoneminder
```

It requires a working mysql server to store the video clips.  It logs events with rsyslog.  It uses Apache to serve up the web pages.  So during the post-installation configuration script, an error happened.  My guess is that one of those services was not installed or not started.  You can search for the post-installation script and run it manually to see where it dumps out.

zm requires quite a bit of setup.  It is not plug-and-play.  This is an old tutorial:  [http://www.howtoforge.com/video_surveillance_zoneminder_ubuntu](http://www.howtoforge.com/video_surveillance_zoneminder_ubuntu), but it gives the basic steps.  You will want to find a newer tutorial--something from this century.

I don't have it installed, but try again and examine its status:

```
dpkg-query -l zoneminder
```

---

### Post by jeffjohn2 on 2014-10-10
Many thanks indeed for support. Is the last line here the problem on my AMD64  install:

Depends: libsys-mmap-perl
  Depends: zip
    zip:i386
  Depends: javascript-common
  Depends: libnet-sftp-foreign-perl
  Conflicts: zoneminder:i386


I am 10 days new to Ubuntu so probably well out of my depth here!  I used the Synaptic Pkg Manager for download so assumed all would be plain sailing. Now however zm won't run.  Any advice, however basic, greatfully received! Jeff

---

### Post by jeffjohn2 on 2014-10-10
p.s. apache2 LAMP running with php webserver fine.

---

### Post by jeffjohn2 on 2014-10-10
removed Zm using Synaptic and tried apt-get (re)install with following result:-

jeff@jeff-Dell-DM051:~$ sudo apt-get install zoneminder
[sudo] password for jeff: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  zoneminder
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1 230 kB of archives.
After this operation, 10,5 MB of additional disk space will be used.
Selecting previously unselected package zoneminder.
(Reading database ... 164150 files and directories currently installed.)
Preparing to unpack .../zoneminder_1.26.5-1ubuntu3_amd64.deb ...
Unpacking zoneminder (1.26.5-1ubuntu3) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Setting up zoneminder (1.26.5-1ubuntu3) ...
ZoneMinder is stopped
invoke-rc.d: initscript zoneminder, action "status" failed.
Starting ZoneMinder: failure

invoke-rc.d: initscript zoneminder, action "start" failed.
dpkg: error processing package zoneminder (--configure):
 subprocess installed post-installation script returned error exit status 255
Processing triggers for ureadahead (0.100.0-16) ...
Errors were encountered while processing:
 zoneminder
E: Sub-process /usr/bin/dpkg returned an error code (1)
jeff@jeff-Dell-DM051:~$ 


Can anyone interpret/advise, please?  Thanks Jeff

---

### Post by tgalati4 on 2014-10-10
Yes, zm requires some linux knowledge.  The message "Conflicts: zoneminder:i386" simply means that you have the 64-bit version installed.  Any package with i386 is a 32-bit package and it will break any 64-bit installation.  You will see that with most packages.

Again, your error is happening in the post installation configuration script.  You need to step through the zoneminder control script and see where it fails.

There are also log files in /var/log.  Page through dpkg.log.

Here's some documentation to read:  [http://www.zoneminder.com/documentation](http://www.zoneminder.com/documentation)

Manually run this file until it fails:  /etc/init.d/zoneminder.

---

### Post by jeffjohn2 on 2014-10-12
I am immensely grateful for the level of support offered on this issue.  As you surmised, it was a question of matching my camera settings and the URL link. I have the DCS-920 working now and expect to tackle the DCS-5300Gs next!  Thanks to all !!

---

