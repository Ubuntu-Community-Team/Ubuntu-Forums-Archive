---
title: "[SOLVED] sudo password lasts x minutes, how to disable?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-05-13
Already the third question today ...

When you use a sudo password in synaptic, you remain root for a few minutes, I dislike this for obvious reasons.

How do I disable this unsafe default setting in ubuntu?

*(I tried googling it, but I couldn't find the right terms to enter)*

---

### Post by eldragon on 2008-05-13
like morpheus said, you have to ask the right questions:
[http://forums.macosxhints.com/showthread.php?t=83344](http://forums.macosxhints.com/showthread.php?t=83344)

havent tried it myself, but cant see why it shouldnt work :D

---

### Post by pedro_orange on 2008-05-13
```
export EDITOR=gedit && sudo visudo
```

The sudoers man page says the following:

[HTML]timestamp_timeout

    Number of minutes that can elapse before sudo will ask for a passwd again. The default is 5. Set this to 0 to always prompt for a password. If set to a value less than 0 the user's timestamp will never expire. This can be used to allow users to create or delete their own timestamps via sudo -v and sudo -k respectively.
[/HTML]

---

### Post by Joeb454 on 2008-05-13
You can also use ```
sudo -k
``` to make sudo ask for your password next time you use it :)

I'm not sure whether this applies to graphical sudo's as well, but I use it all the time for CLI sudo sessions :)

---

### Post by mapes12 on 2008-05-13
I came across this very informative site that talks about sudo security issues:

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Go down to about half way down the page.

---

