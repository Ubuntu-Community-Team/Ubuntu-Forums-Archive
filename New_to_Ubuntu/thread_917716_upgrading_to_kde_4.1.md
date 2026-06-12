---
title: "upgrading to kde 4.1"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by heiowge on 2008-09-12
Have been using Ubuntu for about 10 months.  Tried kubuntu, but found KDE more of a trial than Gnome, so switched.

Fancied trying KDE 4 but heard about problems, so fancied trying it when 4.1 came out.

Got better with Linux and fancied trying it.  Installed KDE4 core, and updates.  Cant seem to get 4.1 tho.

Have tried synaptic, apt-get upgrade, apt-get dist-upgrade...:confused:

Still got 4.0.3

Any ideas?

Do my repositories need changing?

---

### Post by Tatty on 2008-09-12
The official version in the ubuntu repos is 4.03.

To install 4.1 you need to add the kubuntu developers repo here:

[http://www.kubuntu.org/news/kde-4.1](http://www.kubuntu.org/news/kde-4.1)


I tried it myself but it didnt yeild that much improvement over 4.03 for me.  A few less crashes, but an even slower system.

---

### Post by heiowge on 2008-09-12
Tried it.  It crashed my system and fried my 4.0.3 install to boot:lolflag:

At least gnome wasn't affected, so I rolled back to 3.**** and reinstalled 4.0.3

Gonna try it again in a mo..

---

### Post by heiowge on 2008-09-13
Got KDE 4.0.3 back up.

Is the problem with the repositories, or just bad luck?  Can I stop it happening again?

What I ended up with was:

It loaded the screen with KDE 4.1 and the icons as it booted, then it displayed a box on a white background talking about a fatal error, with the KDE bouncing mouse pointer.  If I moved the mouse, it left a black trail onscreen - kinda like the writing with fire option.

It wouldn't display the error or let me save the log.  It merely told me that it was fatal.

---

### Post by Tatty on 2008-09-15
Im not really sure.  But perhaps, instead of just updating the changed packages, try completely removing KDE (hopefully you installed with aptitude, otherwise [this]("http://www.psychocats.net/ubuntu/puregnome") page may help) and then re-install it with the 4.1 repos enabled.

---

### Post by heiowge on 2008-09-15
Won't that erase my Gnome settings?  I'm using Gnome at the moment full time, but messing with KDE 4.0.3 on the other (less accessable) machine and making do.

---

### Post by heiowge on 2008-09-16
bump

---

### Post by HousieMousie2 on 2008-09-16
> **heiowge said:**
> Won't that erase my Gnome settings?  I'm using Gnome at the moment full time, but messing with KDE 4.0.3 on the other (less accessable) machine and making do.

I think they are two different things with their own setting locations in your Home directory.

I tried going from KDE 3.5.9 to 4.0.3 and then back to 3.5.9, it produced a lot of 'issues.'  In the end a purge and reinstall was needed.

I don't use Gnome, so it might be different, but even when I was switching back and forth between KDE versions, it maintained my original settings.

Best of luck!

---

### Post by heiowge on 2008-09-16
Cheers.

Is there any way to completely purge all KDE then install just the 4.1 version (keeping Gnome and settings in place)?

btw - I use Kopete regularly (I could remove other KDE aps without too much faff though)

---

