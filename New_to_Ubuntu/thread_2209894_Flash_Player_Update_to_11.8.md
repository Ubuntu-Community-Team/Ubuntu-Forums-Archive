---
title: "Flash Player Update to 11.8?"
date: 2014-03-07
forum: New to Ubuntu
---

### Post by GUZZLR on 2014-03-07
Hello All...
I cant watch videos from XFinity Comcast because it tells me the minimum required flash player is 11.8, and I have  11.2.  Is it possible to update to 11.8?
Thanks for the help

---

### Post by QIII on 2014-03-07
The short answer, unfortunately, is "No".

Adobe has chosen to end support for Linux and you have the most recent Linux version available.

Not that it matters much, since comcast doesn't bother with Linux.  You can pass traffic, but can't view streaming content from their website.

---

### Post by monkeybrain20122 on 2014-03-07
Install Chrome. Adobe has stopped updating flash for Linux except for security updates. Chrome on the other hand has the latest flash bundled with it because of some deal with Adobe.

Edited: Alternatively you can get Windows' flash working in Firefox with a wine workaround
[http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)

---

### Post by QIII on 2014-03-07
But you still can't access Comcast's content.

---

### Post by monkeybrain20122 on 2014-03-07
> **QIII said:**
> But you still can't access Comcast's content.

I don't know what Comcast is. :) But with pipelight flash you probably can because it is the same as Windows' (so can access drmed contents). May need a user agent switcher too

---

### Post by QIII on 2014-03-07
I've been trying for several years to watch Comcast's content on my Linux machines.

---

### Post by monkeybrain20122 on 2014-03-07
Try pipelight, maybe it will work. :)

---

### Post by GUZZLR on 2014-03-07
Pipelight?  I don't see this in Software Center.  Is there code for it?
Thanks for the help

---

### Post by QIII on 2014-03-07
It's not in the repo.

Take a look [here]("http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html").

Works pretty well with Netflix.  Good luck with Comcast, though.

---

### Post by slooksterpsv on 2014-03-07
Pipelight is silverlight. You'll have to run a VM using VirtualBox with Windows or Wine. Adobe stopped at 11.2 for Linux. I feel Flash is dying out due to HTML5's robust set of features.

---

### Post by jawilljr2 on 2014-03-07
> **slooksterpsv said:**
> Pipelight is silverlight. You'll have to run a VM using VirtualBox with Windows or Wine. Adobe stopped at 11.2 for Linux. I feel Flash is dying out due to HTML5's robust set of features.

[Pipelight Flash]("http://fds-team.de/cms/pipelight-installation.html#section_2_3")

Pipelight flash is like pipelight silverlight, it uses M$'s version of flash in a linux browser.

---

### Post by slooksterpsv on 2014-03-07
Thank you jawill I didn't know of Pipelight Flash. I'll remember that =D

---

### Post by monkeybrain20122 on 2014-03-07
If you use Pipelight flash you would want to set up a way to switch between it and native flash. After all wine has is limitations and when native flash works, it usually works better.

For Debian systems such as Ubuntu it is really easy. 
```
sudo apt-get install galternatives
```
Then open it, enter your password and navigate to Mozilla flash plugin on the side pane, then enter the path to pipelight flash, look for libpipelight-flash.so, it may be in your ~/.mozilla/plugins folder or /usr/lib/mozilla/plugins, depending on whether you install it without or with sudo. You can then choose which version to use with a simple click, then restart Firefox, that's it (glaternatives is a graphic front end to update-alternatives, but it is easier to use than having to remember the command and type it everytime you try to switch)

---

### Post by neslertom on 2014-03-21
Sadly, that does not help for applications that still require it.  I just left windows to come to Ubuntu and now I have to run WINE to emulate Windows?

---

