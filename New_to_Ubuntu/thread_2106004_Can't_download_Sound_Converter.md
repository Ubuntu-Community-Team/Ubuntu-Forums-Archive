---
title: "Can't download Sound Converter"
date: 2013-01-17
forum: New to Ubuntu
---

### Post by kiwipenguin on 2013-01-17
Hi,

I'm just wondering how to find out why I can't download Sound Converter.

I tried downloading through the Ubuntu Software Centre and got this error:

Failed to download package files
Check your Internet connection.

Then I tried using Terminal (sudo apt-get install soundconverter)
and got the following result:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libutouch-geis1
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  soundconverter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 235 kB of archives.
After this operation, 1,503 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  soundconverter
Install these packages without verification [y/N]? y
Err [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) oneiric-getdeb/apps soundconverter all 2.0.3-1~getdeb1
  Could not connect to archive.getdeb.net:80 (209.105.191.78). - connect (113: No route to host)
Failed to fetch [http://archive.getdeb.net/ubuntu/pool/apps/s/soundconverter/soundconverter_2.0.3-1~getdeb1_all.deb](http://archive.getdeb.net/ubuntu/pool/apps/s/soundconverter/soundconverter_2.0.3-1~getdeb1_all.deb)  Could not connect to archive.getdeb.net:80 (209.105.191.78). - connect (113: No route to host)
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I then tried the suggestion at the end: (apt-get update)
but got the following:

N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

And also:
--fix-missing: command not found

Not sure what to do next. Any help would be much appreciated.
Thanks!

---

### Post by mc4man on 2013-01-17
Well it would seem your getdeb servers are down. So you could wait for them to come back up.

There is a way to retrieve getdeb packages from a mirror site, either directly or possibly adding to your sources. (haven't tried as don't use getdeb, maybe there's some thread about that.

As far as directly - in a terminal
```
cd Downloads && wget http://mirrors.dotsrc.org/getdeb/ubuntu/pool/apps/s/soundconverter/soundconverter_2.0.3-1~getdeb1_all.deb
```
You'll find the soundconverter package in your Downloads folder

If you d. click on it Software center may install for you - forget if 11.10's software center will allow that. If not then install gdebi, then right click on the .deb and choose gdebi, ect.

Here's a thread, mentions some  things inc. alternate source
[http://askubuntu.com/questions/51692/what-should-i-do-when-the-getdeb-repository-is-down](http://askubuntu.com/questions/51692/what-should-i-do-when-the-getdeb-repository-is-down)

---

### Post by kiwipenguin on 2013-01-20
Thanks mc4man.
I tried the direct method that you suggested and got this:

--2013-01-21 00:10:31--  [http://mirrors.dotsrc.org/getdeb/ubuntu/pool/apps/s/soundconverter/soundconverter_2.0.3-1~getdeb1_all.deb](http://mirrors.dotsrc.org/getdeb/ubuntu/pool/apps/s/soundconverter/soundconverter_2.0.3-1~getdeb1_all.deb)
Resolving mirrors.dotsrc.org... 32.1.8.120, 2001:878:346::116
Connecting to mirrors.dotsrc.org|32.1.8.120|:80... failed: Connection timed out.
Connecting to mirrors.dotsrc.org|2001:878:346::116|:80... failed: Network is unreachable.

I wonder how long the getdeb servers normally stay down for? At this stage I've been trying for at least a week.

---

### Post by howefield on 2013-01-20
You could probably download it from.... 

[http://packages.ubuntu.com/raring/soundconverter](http://packages.ubuntu.com/raring/soundconverter)

Then double click to start the install.

---

### Post by coldraven on 2013-01-20
In the meantime try getting Arista Transcoder. You can add many pre-configured settings from their web-site or edit existing ones.
[http://www.transcoder.org/](http://www.transcoder.org/)

---

### Post by GordThompson on 2013-01-20
Strange. In your initial post you reported the following error...

```
Could not connect to archive.getdeb.net:80 (209.105.191.78). - connect (113: No route to host)
```...yet when I look up that server name I get...

```
archive.getdeb.net.    86400    IN    A    216.201.78.13
```...and when I do a reverse lookup on the IP address in the error message I get...

```
78.191.105.209.in-addr.arpa. 900 IN    PTR    dsl-209-105-191-78.fairpoint.net.
```Then, in your later post your error was...

```
Connecting to mirrors.dotsrc.org|32.1.8.120|:80... failed: Connection timed out.
```...but my search of that server name returns...

```
mirrors.dotsrc.org.    9578    IN    A    130.225.254.116
```I would suggest trying the `apt-get` command again, and if you get the same error messages (with the same IP address) then try contacting your ISP to see if there is any reason why your DNS might be acting up.

---

### Post by mc4man on 2013-01-20
The direct from mirror works here, maybe you have some local issue(s)
In any event read here
[https://plus.google.com/u/0/+getdeb/posts/FF1gRuZN7pM](https://plus.google.com/u/0/+getdeb/posts/FF1gRuZN7pM)

Another thread on this (ie. set your source to a mirror
[http://ubuntuforums.org/showthread.php?t=2093565](http://ubuntuforums.org/showthread.php?t=2093565)

---

### Post by kiwipenguin on 2013-02-09
Thanks very much.
I managed to download it in the end from packages.ubuntu

---

