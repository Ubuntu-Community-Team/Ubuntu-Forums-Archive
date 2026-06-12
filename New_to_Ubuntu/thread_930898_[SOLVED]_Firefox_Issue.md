---
title: "[SOLVED] Firefox Issue"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by RussW210 on 2008-09-26
Just a freak thing with my firefox... started up my Ubuntu Hardy 8.04 and clicked on firefox.  When it started, all of my bookmarks were gone along with my history of websites.  So I tried to save a bookmark and it wouldn't do anything.

So, I closed out of firefox, open the terminal, did a $ sudo firefox and everything opened fine... all my bookmarks are there along with history.

So I guess when I login under my name (I am the only user) it is not automatically giving me root privileges?  Do I need root privileges to view my bookmarks on firefox?  If so, how do I turn that off?

I have been using Ubuntu for about 3 weeks now and have never had that issue.

---

### Post by asmoore82 on 2008-09-26
check the ownership/permissions of your firefox app data ...

Open a terminal and run this:
```
ls -al .mozilla/firefox
```

---

### Post by RussW210 on 2008-09-26
drwx------ 3 myname myname 4096 2008-09-04 18:22 .
drwx------ 4 myname myname 4096 2008-09-04 18:22 ..
drwx------ 8 myname myname 4096 2008-09-26 17:21 9cq63bco.default
-rw-r--r-- 1 myname myname   94 2008-09-04 18:22 profiles.ini

That is what I get in return, how does that look?  New at this still, trying to understand the drwx rw r language.

---

### Post by asmoore82 on 2008-09-26
drwx = directory read write execute

check one level deeper:

```
ls -al ~/.mozilla/firefox/*.default
```

---

### Post by RussW210 on 2008-09-26
drwx------ 8 russell russell     4096 2008-09-26 18:04 .
drwx------ 3 russell russell     4096 2008-09-04 18:22 ..
-rw-r--r-- 1 russell russell     1561 2008-09-25 19:42 blocklist.xml
drwx------ 2 russell russell     4096 2008-09-26 00:23 bookmarkbackups
-rw-r--r-- 1 russell russell     7139 2008-09-04 18:22 bookmarks.html
drwxr-xr-x 2 root    root        4096 2008-09-26 18:04 Cache
-rw------- 1 russell russell    65536 2008-09-26 18:04 cert8.db
drwxr-xr-x 2 russell russell     4096 2008-09-04 18:22 chrome
-rw------- 1 russell russell      158 2008-09-24 07:12 compatibility.ini
-rw-r--r-- 1 russell russell   151746 2008-09-24 07:12 compreg.dat
-rw-r--r-- 1 russell russell     7168 2008-09-16 13:32 content-prefs.sqlite
-rw-r--r-- 1 russell russell   177152 2008-09-26 18:04 cookies.sqlite
-rw-r--r-- 1 russell russell    34816 2008-09-26 17:29 downloads.sqlite
drwxr-xr-x 3 russell russell     4096 2008-09-25 19:42 extensions
-rw-r--r-- 1 russell russell      489 2008-09-24 07:12 extensions.cache
-rw-r--r-- 1 russell russell      467 2008-09-24 07:12 extensions.ini
-rw-r--r-- 1 russell russell     4645 2008-09-24 07:12 extensions.rdf
-rw-r--r-- 1 russell russell    33792 2008-09-26 17:42 formhistory.sqlite
-rw------- 1 russell russell    16384 2008-09-26 18:04 key3.db
-rw-r--r-- 1 russell russell    13126 2008-09-26 18:04 localstore.rdf
lrwxrwxrwx 1 root    root          15 2008-09-26 18:04 lock -> 222.2.2.2:+8888 (for some reason it locks this section)
-rw-r--r-- 1 russell russell     4181 2008-09-24 19:16 mimeTypes.rdf
drwx------ 2 russell russell     4096 2008-09-05 19:36 OfflineCache
-rw-r--r-- 1 russell russell        0 2008-09-26 18:04 .parentlock
-rw-r--r-- 1 russell russell     2048 2008-09-17 22:49 permissions.sqlite
-rw-r--r-- 1 russell russell  2174976 2008-09-26 17:44 places.sqlite
-rw-r--r-- 1 root    root         512 2008-09-26 18:04 places.sqlite-journal
-rw------- 1 russell russell    11190 2008-09-26 17:29 pluginreg.dat
-rw------- 1 russell russell     7467 2008-09-11 19:32 pluginreg.dat~
-rw-r--r-- 1 russell russell     2603 2008-09-26 18:04 prefs.js
-rw-r--r-- 1 russell russell     2048 2008-09-04 18:22 search.sqlite
-rw------- 1 russell russell    16384 2008-09-26 18:04 secmod.db
-rw------- 1 root    root       20510 2008-09-26 18:04 sessionstore.bak
-rw------- 1 root    root       20511 2008-09-26 18:04 sessionstore.js
-rw------- 1 russell russell      711 2008-09-11 21:25 signons3.txt
-rw-r--r-- 1 russell russell 54222848 2008-09-26 18:04 urlclassifier3.sqlite
-rw-r--r-- 1 russell russell      154 2008-09-26 18:04 urlclassifierkey3.txt
drwx------ 6 russell russell     4096 2008-09-11 19:06 WiredMarker
-rw-r--r-- 1 russell russell  2068100 2008-09-24 17:36 XPC.mfasl
-rw-r--r-- 1 russell russell   110018 2008-09-24 07:12 xpti.dat
-rw-r--r-- 1 russell russell  1201461 2008-09-26 17:07 XUL.mfasl

How does that look?

---

### Post by styfle on 2008-09-26
looks like lrwxrwxrwx 1 root root 15 2008-09-26 18:04 lock -> 222.2.2.2:+8888 is only root access
that could be the problem but i'm a noob to so i'm not sure if that would affect bookmarks
i just checked mine and mine isnt restricted to root

---

### Post by justtempest on 2008-09-26
Did you update your firefox ?

---

### Post by RussW210 on 2008-09-26
No I did not update my firefox.

---

### Post by Fixman on 2008-09-26
Try doing...

```

cp -rf /root/.mozilla ~/.mozilla

```

---

### Post by RussW210 on 2008-09-26
Would updating my firefox be a bad thing or a good thing?

I have:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.2) Gecko/2008092313 Ubuntu/8.04 (hardy) Firefox/3.0.2

I am not exactly sure what that Gecko thing is... I downloaded a Gecko player a while ago but I thought I uninstalled it...

---

### Post by RussW210 on 2008-09-26
OK Fixman... I typed what you said the the terminal and it didnt come back with anything.  Was that to set me as the root user on firefox?

---

### Post by aysiu on 2008-09-26
The problem is that when you ran *sudo firefox* (a no-no, by the way), you changed ownership of some settings files to root instead of user.

Close Firefox.

Paste this command into the terminal: ```
sudo chown -R russell:russell ~/.mozilla
``` Then never run *sudo firefox* again.

More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by mike1234 on 2008-09-26
> **aysiu said:**
> The problem is that when you ran *sudo firefox* (a no-no, by the way), you changed ownership of some settings files to root instead of user.

Close Firefox.

Paste this command into the terminal: ```
sudo chown -R russell:russell ~/.mozilla
``` Then never run *sudo firefox* again.

More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

 The Devil is in the Details.....nice work. :)

M.

---

### Post by RussW210 on 2008-09-26
Thank you aysiu... that seems to have fixed the issue... I am going to restart the computer and try loading firefox regularly again just to make sure it works.

---

### Post by RussW210 on 2008-09-26
Well that seemed to fix it.  I restarted and clicked the firefox link and all my bookmarks stayed... will have to save this forum in case it happens again... but it shouldnt know that I know.

Thanks

---

