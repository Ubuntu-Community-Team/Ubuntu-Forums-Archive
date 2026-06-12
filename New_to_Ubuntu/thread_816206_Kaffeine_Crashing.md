---
title: "Kaffeine Crashing"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by Beatbreaker on 2008-06-02
Hi, Kaffeine is always crashing

When i start it and try to fast forward it will crash straight away. 

Next i started it with no media, just began the program in the terminal, and it kept asking me to update a Codec, and goes into this circular loop, of trying to update, saying that i already have the Codec, and then trying to install it again.

here's the outuput, i don't know if it's linked to what's been going on with it.

```
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
michael@michael-laptop:~$ kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

```

---

### Post by cmnorton on 2008-06-02
Have you also posted a bug in Ubuntu launchpad?

---

### Post by Bodsda on 2008-06-02
Thats a bit hasty cmnorton, launchpad is already swarmed with posts about problems not bugs. first of all have you tried un-installing and re-installing both this irritating codec and kaffeine?

---

### Post by Beatbreaker on 2008-06-03
No i haven't tried that - To be honest i'm a noob and i don't know which codec to uninstall and which one would be best to install...

and in which order to do those

any ideas?

---

### Post by cmnorton on 2008-06-03
> **Bodsda said:**
> Thats a bit hasty cmnorton, launchpad is already swarmed with posts about problems not bugs. first of all have you tried un-installing and re-installing both this irritating codec and kaffeine?

I do not use Launchpad casually. That is I do not post bugs the first time I encounter a problem. Usually, if I am not sure what is going on, I'll post a question there. 

I have seen questions posted in these forums; reproduced the problem; and the original poster either did not have time or did not know about posting bugs in Launchpad, and that leads to a loss of information to improve the product. 

You can not be "hasty" as you suggest and never post a bug, or you can post a bug if you are reasonably sure there is a problem.

---

### Post by Beatbreaker on 2008-06-03
thanks for the tip on bug reporting... but i still don't know how to fix this problem.

---

### Post by SunnyRabbiera on 2008-06-03
well firstly why are you using kaffine?
secondly what version of kaffine are you using?

---

### Post by cmnorton on 2008-06-03
Have a look at this:

[http://ubuntuforums.org/showthread.php?t=134447](http://ubuntuforums.org/showthread.php?t=134447)

Other than finding your installer under System->Administration; searching for Kaffeine; completely removing it; and then re-installing it, I have no other ideas.

---

### Post by Beatbreaker on 2008-06-04
> **SunnyRabbiera said:**
> well firstly why are you using kaffine?
secondly what version of kaffine are you using?

I don't like Totem, i don't remember why - i know i should probably use Gnome based software - well what do you use? what do you suggest?



...actually i'm using Amrock too and that tends to crash more than I'd like too but it's nowhere near as dysfunctional as Kaffene

thanks for your helps, i'll check it out and see if those old archives can help me out

---

### Post by linuxisfree on 2008-06-04
> **Beatbreaker said:**
> I don't like Totem, i don't remember why - i know i should probably use Gnome based software - well what do you use? what do you suggest?



...actually i'm using Amrock too and that tends to crash more than I'd like too but it's nowhere near as dysfunctional as Kaffene

thanks for your helps, i'll check it out and see if those old archives can help me out

I would suggest you use VLC Media Player instead. But, anyway, as said earlier try to uninstall and reinstall kaffeine and that codec, first.

---

### Post by Beatbreaker on 2008-06-08
> **linuxisfree said:**
> I would suggest you use VLC Media Player instead. But, anyway, as said earlier try to uninstall and reinstall kaffeine and that codec, first.

I tried to uninstall Kaffeine and that didn't solve the problem, it still crashes. 

I've tried to use VLC but it's hopeless, when i maxamise the screen i don't get any controls, my mouse can't control anything either, I tried to update to the Nightly Updates version 0.9.xx and that didn't solve anything - i still can't configure any mouse gestures.

I want my Windows Media Player Classic back.

---

