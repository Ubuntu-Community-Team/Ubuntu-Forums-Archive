---
title: "after resetting fglrx, X login screen repeating?"
date: 2012-09-18
forum: New to Ubuntu
---

### Post by Jmob on 2012-09-18
So, I've been playing around with fglrx, trying to find a setup that I like on my box.  I was having some trouble with the install from the repositories (on a Lenovo T500), and so I reset back to normal.  I then tried a more manual method used here:

[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

The process caused X to fail to load, so I followed the removal procedures.  With one exception: it called for the following line:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```which I couldn't do as there are several files (xorg.conf.fglrx-[0-3], and xorg.conf.original-[0-3], xorg.conf.failsafe, and xorg.conf-backup-[four different 12 digit numerical codes which appear to be timecodes].  There are also a few other files.

Anyway, at this point X *does* appear to load in a normal boot, but when my login credentials are entered (only when they're correct), the screen goes to black for a moment, some terminal information pops up too briefly to read...and I'm back at the login screen as if it reset, or I'd done an alt-prtsc-k.

I can log in on a different tty, and authentication is fine.  I have what appears to be normal terminal control from there.  I can switch back to the gui, but the problem is still there.

Obviously I've screwed up something here, but I'm not sure how to attack it.  Any recommendations?

---

### Post by NikTh on 2012-09-18
Hi , 
try to check the permissions of .Xauthority file inside your /home directory . 

```
ls -l ~/.Xauthority
```

If you see root as owner , then change it to your username. 
```
sudo chown username:username ~/.Xauthority
``` 

Thanks

---

### Post by Jmob on 2012-09-18
Yes, that seems to have worked.  Thanks for the information.  

What, exactly, went on such that the ownership changed on the file?

---

### Post by steeldriver on 2012-09-18
Probably in order to generate an xorg.conf file, the installer started the X server (as Xorg -configure); if you ran the installer using sudo (rather than dropping to a true root shell in the recovery console) that would have created a root-owned Xauthority file in your home dir

---

### Post by Jmob on 2012-09-19
Thanks.

Interesting.  So, what's the lesson here?  I'm learning about various things (.Xauthority, for instance), but not really putting together a clear picture of what went wrong.  That's a sad thing to say, I admit, but it's better than acting like I get it when I don't, I guess.

---

### Post by steeldriver on 2012-09-19
I'm really only guessing about what happened, I'm no expert

I guess you could say the lesson is to do graphics driver upgrades from the root console rather than sudo - OTOH the root-owned .Xauthority seems to be a generic problem so I don't know what the 'bigger' answer is

---

