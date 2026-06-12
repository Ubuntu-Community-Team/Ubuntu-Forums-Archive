---
title: "how do I completely remove an application"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by terrykiwi83 on 2012-04-13
[SIZE=2][FONT=Century Gothic]Seems simple, but it doesn't want to work for me. Basically am trying to remove mediatomb completely, including all config files, folders...etc

I have tried

```

apt-get remove --purge mediatomb

```

That doesn't seem to remove it as I can still access it.

SO what I have done is manually deleted the folders, now the problem is when I install it via apt-get again it doesn't create the folders again :(

So as you can see I want to completely remove then reinstall it :)

?
[/FONT][/SIZE]

---

### Post by roelforg on 2012-04-13
Sudo
You forgot sudo

---

### Post by terrykiwi83 on 2012-04-13
sorry forgot to mention I was logged is as root (su) at the time, but yep I would of normally put sudo in. :)

---

### Post by roelforg on 2012-04-13
```

apt-get purge mediatomb

```
Purge ain't a command line switch

---

### Post by Azdour on 2012-04-13
Hi,

According to the man pages for apt-get:

```
apt-get remove --purge
```

is the same as

```
apt-get purge
```

So --purge is a valid parameter.

To the OP, when you ran:

```
apt-get remove --purge mediatomb
```

What feedback did you see. Was there any errors or did it just tell you it had removed it?

---

### Post by jps2012 on 2012-04-13
I used "sudo apt-get purge kalarm" to ATTEMPT to remove the pesky and user-unfriendly app kalarm (and then did the same with "alarm-clock-applet). They consumed an enormous amount of system resources (half of what firefox consumed). 

Purge doesn't seem to purge. I ran updatedb, then used locate in the terminal to check how effective purge had been. SOME files were purged, but the app folder and other files still remain. For example, this one: 

/home/me/.kde/share/apps/kalarm

The shell reported no errors during the process.

So, terrykiwi's question is a great one. If purge doesn't purge, what does?

---

### Post by anewguy on 2012-04-13
Normally the folder like that in your home folder aren't automatically deleted, mainly because these aren't installed as part of the package installation procedure but instead by the app when you run it.  You just want to be sure the purge removed any libraries, etc., it may have installed.  I know that some of the packages we install go into /usr folders so you may want to check there as well.

---

### Post by jps2012 on 2012-04-13
anewguy: You're absolutely right. There's a bunch of kalarm files remaining in the usr directory and subdirectories. Will purge work if I issue the command this way: 

sudo apt-get -r purge kalarm

---

### Post by anewguy on 2012-04-13
Don't know - to be honest I've only done a purge once or twice in many years.  I seem to install only what I need and just leave it on the system.

I would have thought sudo apt-get remove package-name would have done it, unless this was a separately downloaded .deb or other file - then I don't know if it works on those or not.

While it should have already been taken care of by just one of your previous commands, try this anyway (shouldn't need both, but do it anyway ;) ):

sudo apt-get remove mediatomb

sudo apt-get purge mediatomb


BUT.....mediatomb IS in the software center, so why not just go into the software center, select mediatomb and click the remove/uninstall there and see what happens??  You will need to do the purge after that.

That would work with the OP of this thread.


For kalarm, it also is in the software center, so I would also just use software center to uninstall it - you can do the purge after that.

Dave ;)

---

### Post by terrykiwi83 on 2012-04-13
Thanks for all the suggestions, will give it a try when I wake up a bit more :)

---

