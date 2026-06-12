---
title: "fresh installation: sudo apt-get hangs looking for connection"
date: 2011-12-06
forum: New to Ubuntu
---

### Post by 118118 on 2011-12-06
this thread
[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)


seems relevant but i am new and the documentation looks too complex just to try now. it's a wireless connection - and i can use the internet with it. it used to work fine. infact since the fresh install i have been able to install some items.

thanks :popcorn:

---

### Post by theozzlives on 2011-12-06
what version of Ubuntu you using?

---

### Post by 118118 on 2011-12-06
> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
is a new error message i get since starting the topic.

i have been using ctrl+z on some installations... i hope that hasn't messed anything up.

---

### Post by 118118 on 2011-12-06
11.10

must sleep now, thanks.

---

### Post by wildmanne39 on 2011-12-06
Hi, this > E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? 
usually means you have 2 applications running and trying to install packages at the same time like the terminal and software center if that is not the case restart your computer and that should clear up, then post the results from this command: 
```
sudo apt-get update
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by critin on 2011-12-06
> **118118 said:**
> is a new error message i get since starting the topic.

i have been using ctrl+z on some installations... i hope that hasn't messed anything up.

Doesn't ctrl+z pause the process?

edited to add: I don't know how reliable these commands are, so get confirmation from experts before using.  It should be a good guide though--I hope.

I found: <Ctrl>z   ---Send the current process to the background.

 to bring up the stalled processes, to use key-- fg PID Bring a background or stopped process to the foreground.

 [http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

---

### Post by 118118 on 2011-12-08
hi,

restarted computer and got the following error message trying sudo apt-get update
```

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

so i ran that command and now can update and install again!


thanks.[img]http://forum.noiseguide.com/images/smiles/shrug.gif[/img]

---

### Post by wildmanne39 on 2011-12-08
Hi, your welcome I am glad it is working, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

