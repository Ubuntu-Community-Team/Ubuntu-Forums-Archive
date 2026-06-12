---
title: "Hardy Desktop bling without Compiz"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by brommage on 2008-04-28
Hey all--

I'm running an old HP ZE4600 series laptop, and I ran into the problem of the ATI graphics card blacklist through Compiz (it's got a Radeon Mobility U1).  Rather than reverting to Gusty or waiting for Intrepid (or the $$ to buy a new laptop), I thought I'd just try and soup it up without Compiz.  Don't get me wrong--the cube is cool.  But I don't really use a heck of a lot of the features.  

The only thing I really liked on my Gusty setup was the AWN dock.  Without Compiz, it won't run.  So, can anyone recommend a good dock program that does not use Compiz (for gnome desktop)?  I ran across Cairo, but I know nothing about it.  Does anyone use it?  Can it do all the things that AWN can?  Any info would be appreciated.

Oh, also: Is there a way I can revert to an older version of Compiz, to avoid the blacklist dilemma?  That might kill the maximal amount of birds with the minimal amount of stones.

Thanks in advance.

P.S.  No birds were injured in the typing of this post.

---

### Post by LaRoza on 2008-04-28
> **brommage said:**
> 
The only thing I really liked on my Gusty setup was the AWN dock.  Without Compiz, it won't run.  So, can anyone recommend a good dock program that does not use Compiz (for gnome desktop)?  I ran across Cairo, but I know nothing about it.  Does anyone use it?  Can it do all the things that AWN can?  Any info would be appreciated.

Oh, also: Is there a way I can revert to an older version of Compiz, to avoid the blacklist dilemma?  That might kill the maximal amount of birds with the minimal amount of stones.


GNOME has its own compositing now. I don't know where it is, search around for it. (Look for "metacity" in a menu somewhere) I am not running GNOME at the moment.

You can actually unblacklist your card. There is a sticky around here for it... [http://ubuntuforums.org/forumdisplay.php?f=330](http://ubuntuforums.org/forumdisplay.php?f=330)

For lightweight eyecandy, you can try Enlightenment. OzOS is an Ubuntu based OS that uses it. Very sleek.

---

### Post by jpeddicord on 2008-04-28
> **LaRoza said:**
> GNOME has its own compositing now. I don't know where it is, search around for it. (Look for "metacity" in a menu somewhere) I am not running GNOME at the moment.

GNOME compositing right now is "meh." It enables applications to use compositing features, but it doesn't offer much and is a little slow at the moment, so I wouldn't use it just yet. That will all most likely change in the near future however, and I'm looking forward to the improvements.

---

### Post by LaRoza on 2008-04-28
> **jacobmp92 said:**
> GNOME compositing right now is "meh." It enables applications to use compositing features, but it doesn't offer much and is a little slow at the moment, so I wouldn't use it just yet. That will all most likely change in the near future however, and I'm looking forward to the improvements.

Would AWN work with it?

(I don't use GNOME. I use wmii, so I don't know what it is like)

---

### Post by brommage on 2008-04-28
> **LaRoza said:**
> You can actually unblacklist your card. There is a sticky around here for it... [http://ubuntuforums.org/forumdisplay.php?f=330](http://ubuntuforums.org/forumdisplay.php?f=330)

I saw those solutions, but they're rather inelegant.  I'd like to be able to maintain functionality on bootup without having to run commands to initialize my desktop.

> For lightweight eyecandy, you can try Enlightenment. OzOS is an Ubuntu based OS that uses it. Very sleek.

I might try that out.  I'm used to the Gnome interface (I've been using it since Edgy), and thought about trying a different interface.  Can one switch without reinstall?  If so, how?  I'm still a bit of a noob.

---

### Post by LaRoza on 2008-04-28
> **brommage said:**
> 
I might try that out.  I'm used to the Gnome interface (I've been using it since Edgy), and thought about trying a different interface.  Can one switch without reinstall?  If so, how?  I'm still a bit of a noob.

Try: [http://ruialeixopais.planetaclix.pt/linux/e17/](http://ruialeixopais.planetaclix.pt/linux/e17/)

OzOS is also a live disk, so you can try it out if you have the RAM (not a lot is needed).

---

### Post by brommage on 2008-04-28
> **jacobmp92 said:**
> GNOME compositing right now is "meh." It enables applications to use compositing features, but it doesn't offer much and is a little slow at the moment, so I wouldn't use it just yet. That will all most likely change in the near future however, and I'm looking forward to the improvements.

Ha!  Yeah.  I tried to activate it through gconfig-editor, and it crashed my system!

---

### Post by LaRoza on 2008-04-28
> **brommage said:**
> Ha!  Yeah.  I tried to activate it through gconfig-editor, and it crashed my system!

Try E17 then. I don't know if it has a dock, but it is very pretty.

---

### Post by smartboyathome on 2008-04-29
E17 has a dock named itask ng. It is great for eye candy without the bloat. :)

---

### Post by clairegrrl on 2008-04-29
> **smartboyathome said:**
> E17 has a dock named itask ng. It is great for eye candy without the bloat. :)

This is in Absolute Beginner Talk.  Funny, I have absolutely no idea what you're talking about.  Hehehe :)

---

### Post by brommage on 2008-04-30
Thanks for your help, all.  I was able to get Cairodock up and running with xcompmgr, and got my desktop up and working without having to leave gnome.  I would recommend this for those who liked AWN, but can't run it due to the Compiz blacklist!

---

### Post by fraser_m on 2008-04-30
Install compizconfig-settingsmanager and remove all the crap you don't need. you still need compiz, though.

---

### Post by Rui Pais on 2008-05-02
**Thank you LaRoza for mention OzOS and for your kind words about it! :)**


> **clairegrrl said:**
> This is in Absolute Beginner Talk.  Funny, I have absolutely no idea what you're talking about.  Hehehe :)

ItaskNG:
[http://code.google.com/p/itask-module/](http://code.google.com/p/itask-module/)
it's an application launcher and taskbar for Enlightenment (e17) desktop (purist will say Window manager/shell environment... who cares!)



> **brommage said:**
> 
I might try that out.  I'm used to the Gnome interface (I've been using it since Edgy), and thought about trying a different interface.  Can one switch without reinstall?  If so, how?  I'm still a bit of a noob.
Yes, you can install either e17 as a separate desktop without reinstall or the full OzOS, again either on your actual installation (like you would install kde or xfce4 desktop) or as a separate installation side-by-side your actual one.
:D

---

