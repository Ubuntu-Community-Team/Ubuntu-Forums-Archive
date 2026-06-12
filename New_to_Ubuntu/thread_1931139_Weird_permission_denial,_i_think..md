---
title: "Weird permission denial, i think."
date: 2012-02-24
forum: New to Ubuntu
---

### Post by Jake5 on 2012-02-24
So here is my problem,    whenever i enter any terminal command to remove Wine from my machine.     this is the response i get...every time.     any help is more than awesome.    not sure what to do      jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ apt-get autoremove E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied) E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?   jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ sudo apt-get autoremove [sudo] password for jake:  E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable) E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by HeroOfCanton on 2012-02-24
Looks like something is locking your package installer. Try rebooting and using sudo on the first try.

Please use the code tag (pound sign in editor) when posting terminal code. Makes it easier for all to read.

---

### Post by enjoijesus94 on 2012-02-24
like stated above 
use 
"sudo" at Beginning when installing packages.

if that dosnt help make sure synaptic aint open:P

---

### Post by cortman on 2012-02-24
> **Jake5 said:**
> So here is my problem,    whenever i enter any terminal command to remove Wine from my machine.     this is the response i get...every time.     any help is more than awesome.    not sure what to do      jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ apt-get autoremove E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied) E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?   jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ sudo apt-get autoremove [sudo] password for jake:  E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable) E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I assume you ran this as

```
**sudo **apt-get remove wine
```

Emphasis on sudo.
The other problem is that you have another apt process running. I have full details on how to fix this simple issue in [this blog post]("http://cortman.wordpress.com/2012/02/24/unable-to-obtain-lock-for-software-installation/"). If you can't access it for whatever reason I can post it verbatim as well.
Good luck!

---

### Post by Jake5 on 2012-02-24
Thanks guys, I tried the   #sudo apt-get remove wine  after a reboot.  the terminal told me that wine was not installed and then asked to install another program. I was hesitant but i had an idea as to what it was.  Sure enough it was the EULA for wine. It will run the dialogue and post an accept button on the bottom, but i cannot press the button, hitting enter does nothing, even (y) enter does not work. I have a feeling that you have to accept this agreement in order for the system to see that the program is actually there. I can run wine with no issues and even have found a way to run the infamous fruity loops program that so many windows users are clinging onto their machines for. I hate windows and only wanted to run wine to see if i could get fruity loops to work. So without accepting this EULA i think the only way to purge the file is to do a fresh install...How sad.  tried killing the process's per cortman's suggestion, but there were like four hundred of them running and i was unable to find the one not to kill...didnt want to mess anything up so i gave up.

---

### Post by Jake5 on 2012-02-24
I also have a problem with my enter key obviously not inserting a line space on this forum... not just me. I promise im typing this correctly.  If it works correctly this post should read on six seperate lines.

---

### Post by Jake5 on 2012-02-24
> **Jake5 said:**
> I also have a problem with my enter key obviously not inserting a line space on this forum... not just me. I promise im typing this correctly.  If it works correctly this post should read on six seperate lines.

and it didnt.

---

### Post by 3rdalbum on 2012-02-25
Wine doesn't have a EULA, I imagine you're talking about msttcorefonts or some other package like that.

You need to press Tab and then the spacebar to accept the license. If you'd installed the package with Software Center it would have been a simple "click on OK" affair, but no harm done.

---

### Post by Jake5 on 2012-02-25
> **3rdalbum said:**
> Wine doesn't have a EULA, I imagine you're talking about msttcorefonts or some other package like that.

You need to press Tab and then the spacebar to accept the license. If you'd installed the package with Software Center it would have been a simple "click on OK" affair, but no harm done.

That was it exactly...I already re-installed ubuntu 11.10 on the laptop in question...so wine is definitely gone now...But I will remember that shortcut, thank you.

---

### Post by cortman on 2012-02-25
> **Jake5 said:**
> tried killing the process's per cortman's suggestion, but there were like four hundred of them running and i was unable to find the one not to kill...didnt want to mess anything up so i gave up.

Just FTR, killing the grep process is no problem. It's just not related to apt at all, so killing it will not release the lock file.

---

### Post by prasaadsj on 2013-01-24
> **enjoijesus94 said:**
> like stated above 
use 
"sudo" at Beginning when installing packages.

if that dosnt help make sure synaptic aint open:P

This worked as charm. Use **sudo apt-get install -f** after u restart linux.

---

