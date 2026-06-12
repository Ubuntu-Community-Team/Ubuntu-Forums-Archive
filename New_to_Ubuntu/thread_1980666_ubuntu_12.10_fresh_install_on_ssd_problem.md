---
title: "ubuntu 12.10 fresh install on ssd problem"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by hollywoodpete on 2012-05-15
I just installed 12.10 64-bit on a new ssd. For some reason update manager doesn't work. I tried sudo apt-get clean, update and upgrade but it either freezes or I get errors. Any help would be appreciated

---

### Post by Lisiano on 2012-05-15
Have you tried pointing it at a different server? Press Alt+F2 and type ```
software-properties-gtk
``` then change the server from a local one to Main Server. Then close it and drop back to a terminal (Ctrl+Alt+T) and type ```
sudo apt-get update
sudo apt-get upgrade
```

Also a list of the errors you get would be very helpful.

---

### Post by hollywoodpete on 2012-05-15
nighthawk@Core4:~$ software-properties-gtk
gpg: /tmp/tmp26Gy0B/trustdb.gpg: trustdb created
nighthawk@Core4:~$ software-properties-gtk
gpg: /tmp/tmpa10leP/trustdb.gpg: trustdb created
nighthawk@Core4:~$ sudo apt-get update
[sudo] password for nighthawk: 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security InRelease
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg [198 B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg [198 B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg [198 B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release [49.6 kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release [49.6 kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release [49.6 kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages [1,273 kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages [4,786 kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages [8,452 B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse amd64 Packages [119 kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages [1,274 kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages [8,431 B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex [3,706 B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex [2,676 B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex [2,596 B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex [2,922 B]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main amd64 Packages [107 kB]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe amd64 Packages [30.9 kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted amd64 Packages [757 B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse amd64 Packages [1,142 B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [108 kB]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages [31.1 kB]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages [770 B]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages [1,393 B]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex [73 B]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex [71 B]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex [71 B]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex [73 B]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main amd64 Packages [33.6 kB]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe amd64 Packages [8,581 B]
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted amd64 Packages [14 B]
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse amd64 Packages [1,142 B]
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages [33.6 kB]
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages [8,594 B]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted i386 Packages [14 B]
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse i386 Packages [1,393 B]
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main TranslationIndex [73 B]
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted TranslationIndex [70 B]
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex [72 B]
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en [726 kB]
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en [2,395 B]
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en [3,341 kB]
Get:47 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en [52.0 kB]
Get:48 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en [587 B]
Get:49 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en [267 B]
Get:50 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en [19.4 kB]
Get:51 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en [14.3 kB]
Get:52 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en [587 B]
Get:53 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en [14 B]
Get:54 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en [6,261 B]
Fetched 17.2 MB in 6s (2,634 kB/s)                                             
nighthawk@Core4:~$ ts... 45%

---

### Post by westie457 on 2012-05-15
> **hollywoodpete said:**
> I just installed 12.10 64-bit on a new ssd. For some reason update manager doesn't work. I tried sudo apt-get clean, update and upgrade but it either freezes or I get errors. Any help would be appreciated

 sincerely hope you have not installed 12.10 as your main system. It is in the very early stages of deveopment and consequently very buggy and will break very often.

Looking at your terminal output you have 12.04 (Precise Pangolin).

Did you run both commands that were suggested because the output from the second one ```
sudo apt-get upgrade 
``` will tell us what the errors are.

---

### Post by ajgreeny on 2012-05-15
> **hollywoodpete said:**
> I just installed 12.10 64-bit on a new ssd. For some reason update manager doesn't work. I tried sudo apt-get clean, update and upgrade but it either freezes or I get errors. Any help would be appreciated
An absolute beginner using 12.10!  Surely not?

If I'm wrong on both these and you are a new user, and you really are using 12.10, you are very brave, or extremely foolish, or most probably did it accidentally in some strange way.

Try 12.04, or 10.04 and leave 12.10 for those who know how to deal with problems like this.

---

### Post by hollywoodpete on 2012-05-15
> **westie457 said:**
> sincerely hope you have not installed 12.10 as your main system. It is in the very early stages of deveopment and consequently very buggy and will break very often.

Looking at your terminal output you have 12.04 (Precise Pangolin).

Did you run both commands that were suggested because the output from the second one ```
sudo apt-get upgrade 
``` will tell us what the errors are.

Sorry. I have 12.04. My mistake. It froze up after sudo apt-get update. It is actually working now after a couple of restarts and using the main server as you suggested. Thank you

---

