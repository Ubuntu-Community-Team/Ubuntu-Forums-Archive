---
title: "Sys Log Error Message"
date: 2015-06-13
forum: New to Ubuntu
---

### Post by Quarkrad on 2015-06-13
Running 14.04 64bit.   The past week I keep getting error messages on my Desktop after boot - I have the choice the Cancel or Report.  Not being sure how to find out what is causing these I have had a look in **syslog(/ver/log)** - again not sure what to look for but I have a lot of these messages logged daily:  **Jun 11 17:57:54 dadubuntu kernel: [11058.451067] systemd-hostnamed[16063]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!**  Should I do something about this install or can it be ignored?

---

### Post by westie457 on 2015-06-13
From personal experience I installed 'nss-myhostname' a couple of months ago when Chromium Browser was not loading any pages. The message at the bottom of the screen was 'Resolving Host...'.
It worked for a while then something happened (can't remember exactly) then Chromium started the behaviour as before. Plugging a cable in stopped the issue. Reinstalled the wireless drivers - in my case BCMWL (somehow got corrupted), shortly after that had to reset the router. Everything worked as normal.
Now I am on a fresh installation running w/out 'nss-myhostname' with no issues. 
In syslog I get a similar warning to what you have and have come to the conclusion this can be ignored until the 'host file' is corrupted, then it becomes important.

Edit
The full name of the package is libnss-myhostname

---

### Post by abelattila83 on 2015-06-13
You can remove the "reporting software" with the following: 

apt-get remove --purge apport apport-gtk



Best regards, 
IT and IT Security news: [https://somenewsforyou.github.io/](https://somenewsforyou.github.io/)

---

### Post by Quarkrad on 2015-06-13
I'm happy to do this (purge apport) but as a newbie I'm not sure what is causing this error window to pop up (actually at boot I have two of these windows).  I chose  syslog(/ver/log) for no particular reason - there are many logs, is there a way to find out what specifically is causing these errors/windows to pop up?   If it is serious/I have to do something then purging them could be covering up something that needs to be addressed.

---

### Post by cariboo on 2015-06-13
If you click the report button, it will tell you what the problem is. I'm running wily, and get the message every time I reboot. You can also check /var/crash to see what is causing the message. This is the contents of that directory on my laptop:

> :/var/crash$ ls -l
total 63664
-rw-r----- 1 cariboo  whoopsie 53288849 Jun  7 21:04 _usr_bin_gnome-shell.1000.crash
-rw-r----- 1 root     whoopsie  1071236 Jun  5 22:58 _usr_bin_nautilus.0.crash
-rw-r--r-- 1 root     whoopsie        0 Jun  5 23:02 _usr_bin_nautilus.0.upload
-rw------- 1 whoopsie whoopsie        0 Jun  5 23:02 _usr_bin_nautilus.0.uploaded
-rw-r----- 1 cariboo  whoopsie 10829442 Jun 12 19:38 _usr_bin_nautilus.1000.crash
-rw-rw-r-- 1 cariboo  whoopsie        0 Jun 12 19:38 _usr_bin_nautilus.1000.upload
-rw------- 1 whoopsie whoopsie        0 Jun 12 19:38 _usr_bin_nautilus.1000.uploaded

---

### Post by tgalati4 on 2015-06-13
Run memtest for an hour to make sure your RAM is OK.  Something is causing an issue.  Next check the SMART parameters on your hard drive.

---

### Post by Quarkrad on 2015-06-15
I ran the tests and all is OK - I expected this as this is a new machine (only a few weeks old).  I also ran the commands and I did seem to have an issue with Virtualbox not shutting down properly as well as the Software Centre.  However, the problem has been resolved.  I knew one of my HDs was very full so I balanced my storage folders over two HDs (I have a third larger HD that I use for back up).  Since balancing and having more free space on one of the HDs (the HD contained the OS as well) I have no more reported errors.  Many thanks for your help.

---

