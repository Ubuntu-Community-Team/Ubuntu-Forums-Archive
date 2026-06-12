---
title: "Long delay after initial login"
date: 2014-03-02
forum: New to Ubuntu
---

### Post by DGINSD on 2014-03-02
I recently upgraded my 12.10 Ubuntu installation to 13.10, after 12.10 became unsupported. The upgrade got interrupted midway through and I managed to complete the upgrade through much goggling, though it has caused a bunch of minor issues here and there that I've had to fix.  The biggest issue and one I haven't been able to fix is a long delay between entering my login password and the display of my desktop environment.

This delay is about a minute and a half, and happens with the AMD/ATI Catalyst FGLRX driver (which is the one I normally use) or the open source driver, which is almost un-usable, but gives me a way to make sure the problem isn't the FGLRX driver. I've also tried other users and even creating a new user both have the same delay.

I'm not even sure where to look to find the problem?

---

### Post by deadflowr on 2014-03-02
12.10 is still supported

---

### Post by DGINSD on 2014-03-02
You sure about that, when ever I pulled up Software Update it always said "12.10 is no longer supported" and asked me if I wanted to upgrade to 13.10. I will admit I though it was a bit odd as it's less than a year and a half old, but I thought I read something about Ubuntu changing their release and support cycle.

---

### Post by deadflowr on 2014-03-02
Yep, I'm positive.
Support ends in April.
This is March.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Are you sure it wasn't 13.04?
That release has reached end of life.

Anyway, does anything here help
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

### Post by ibjsb4 on 2014-03-02
How bout lets verify things in terminal.

```
lsb_release -a
```

And your running kernel

```
uname -r
```

---

### Post by DGINSD on 2014-03-02
> **deadflowr said:**
> Yep, I'm positive.
Support ends in April.
This is March.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Are you sure it wasn't 13.04?
That release has reached end of life.

Anyway, does anything here help
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

You know what, your totally right, it was my 13.04 install on my other partition that was giving me that message, so I decided to do the upgrade on this older 12.10 install that I wasn't using anymore. 

As far as my delay issue, I don't think the problem is related to the video drivers, I get the delay on both proprietary or the open source ones, I've even tried differant versions of the proprietary drivers.

I haven't found anything obvious in the log files, but I'm not really sure what I'm looking for, or which log to look for the problem in. Once my DE comes up everything seems to work just fine, it's more of an annoyance knowing something isn't working how it's supposed to.

---

### Post by deadflowr on 2014-03-02
well, probably a problematic startup application.
You can try disabling those which you don't ever use.

This(though for 13.04) gives a good list of which ones do what, and whether or not you can shut 'em down.
[http://askubuntu.com/questions/310337/which-startup-applications-can-i-safely-disable](http://askubuntu.com/questions/310337/which-startup-applications-can-i-safely-disable)

See if that helps speed things up.

---

### Post by DGINSD on 2014-03-03
> **deadflowr said:**
> well, probably a problematic startup application.
You can try disabling those which you don't ever use.

This(though for 13.04) gives a good list of which ones do what, and whether or not you can shut 'em down.
[http://askubuntu.com/questions/310337/which-startup-applications-can-i-safely-disable](http://askubuntu.com/questions/310337/which-startup-applications-can-i-safely-disable)

See if that helps speed things up.

I actually have a few things I don't use already unchecked, I checked off a few others as well just to see, but it didn't change the issue.

I also have gnome3 DE installed as well, tried that to see if it had the startup delay, it did though slightly less than Unity. Not sure what that means.

There has to be some log file that has some representation of what going on during a boot and login.

---

### Post by monkeybrain20122 on 2014-03-03
> **DGINSD said:**
> You know what, your totally right, it was my 13.04 install on my other partition that was giving me that message, so I decided to do the upgrade on this older 12.10 install that I wasn't using anymore. 

As far as my delay issue, I don't think the problem is related to the video drivers, I get the delay on both proprietary or the open source ones, I've even tried differant versions of the proprietary drivers.

I haven't found anything obvious in the log files, but I'm not really sure what I'm looking for, or which log to look for the problem in. Once my DE comes up everything seems to work just fine, it's more of an annoyance knowing something isn't working how it's supposed to.

I think the isssue may be related to video driver, but it may also be related to your interrupted upgrade. So please, to spare you future problems spend 20 minutes do a clean install to whatever version and forget about "upgrade". :)

---

### Post by DGINSD on 2014-03-03
> **monkeybrain20122 said:**
> I think the isssue may be related to video driver, but it may also be related to your interrupted upgrade. So please, to spare you future problems spend 20 minutes do a clean install to whatever version and forget about "upgrade". :)

I actually always do choose clean install over upgrade. I only went with the upgrade because we're so close to the 14.04 release and didn't want to do 2 installs 3 months appart, that will show me for being lazy.

---

