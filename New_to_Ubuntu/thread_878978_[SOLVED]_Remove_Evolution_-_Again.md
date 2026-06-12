---
title: "[SOLVED] Remove Evolution - Again"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by BGFG on 2008-08-03
I've come across other threads but can't seem to post to the one i want to.
Why can't i remove Evolution without screwing my machine ? I don't use it, don't want it, but when i try to remove it, it then attempts to remove the gnome-desktop among other integral parts of my system.
I removed as much as i can via synaptic but i can only get so far. also because of this, my system keeps downloading evolution updates that i do not want.
Why has one peice of software been hardwired into the Gnome-Desktop ? 
I do not find this to be in keeping with the freedom of the open-source movement.

If there is in fact a way to remove it and i simply haven't figured it out yet, then please accept my humblest apologies and edify this one.

---

### Post by UbuntuNerd on 2008-08-03
As far as I know you can't completely remove evolution b/c gnome uses some of the same packages but you can remove most of it check this link


[http://blog.mcbachmann.de/?p=4]("http://blog.mcbachmann.de/?p=4")

---

### Post by Vivaldi Gloria on 2008-08-03
> **UbuntuNerd said:**
> As far as I know you can't completely remove evolution b/c gnome uses some of the same packages but you can remove most of it check this link


[http://blog.mcbachmann.de/?p=4]("http://blog.mcbachmann.de/?p=4")

Trying to remove evolution (without removing evolution-data-server) screwed up my system. I suggest against it.

---

### Post by BGFG on 2008-08-03
> **UbuntuNerd said:**
> As far as I know you can't completely remove evolution b/c gnome uses some of the same packages but you can remove most of it check this link


[http://blog.mcbachmann.de/?p=4]("http://blog.mcbachmann.de/?p=4")

Thanks for the response man, but those are exactly the packages i'm left with :) This is most disconcerting.

---

### Post by Vorian Grey on 2008-08-03
This is really not an Ubuntu problem. This is a Gnome problem. Gnome is the one you need to ask these questions. Ubuntu only uses the Gnome desktop. They don't develop it or anything. 

My guess is that Evolution, like IE on Windows, is tied into the desktop in such a way that it is impossible to remove.

---

### Post by BGFG on 2008-08-03
> **Vorian Grey said:**
> This is really not an Ubuntu problem. This is a Gnome problem. Gnome is the one you need to ask these questions. Ubuntu only uses the Gnome desktop. They don't develop it or anything. 

My guess is that Evolution, like IE on Windows, is tied into the desktop in such a way that it is impossible to remove.

So right, i forgot and lumped everything together. Would'nt have expected this kind of redmond behavior in my preferred desktop manager.

But GNOME IS FREE, so i'm still grateful to them. And i totally take back the redmond comment.

---

### Post by Average Joe on 2008-08-03
Are you use that the Gnome-desktop environment is removed when you remove Evolution? As far as I know only the ubuntu-desktop package will be removed. This just a so-called meta-package. It doesn't contain anything itself, it is only useful if you would like to get the default ubuntu-desktop and applications back.

I removed Evolution (a long time ago) with```
sudo aptitude remove evolution
```It is always the first thing I do on a fresh Ubuntu install, since I prefer Thunderbird for my mail. I never had any problems with removing Evolution, apart from the warning that also the ubuntu-desktop package would be removed. That is fine with me since it is just a dummy package.

---

### Post by BGFG on 2008-08-03
> **Average Joe said:**
> Are you use that the Gnome-desktop environment is removed when you remove Evolution? As far as I know only the ubuntu-desktop package will be removed. This just a so-called meta-package. It doesn't contain anything itself, it is only useful if you would like to get the default ubuntu-desktop and applications back.

I removed Evolution (a long time ago) with```
sudo aptitude remove evolution
```It is always the first thing I do on a fresh Ubuntu install, since I prefer Thunderbird for my mail. I never had any problems with removing Evolution, apart from the warning that also the ubuntu-desktop package would be removed. That is fine with me since it is just a dummy package.

I still have evolution-data-server-common in synaptic. When i try to remove it, it also wants to take gnome panel and applets with it. Among others.

---

### Post by CatKiller on 2008-08-03
> **BGFG said:**
> I still have evolution-data-server-common in synaptic. When i try to remove it, it also wants to take gnome panel and applets with it. Among others.

You can remove the shortcuts and stop the Evolution Alarm Notifier from starting with your Session and just pretend that it isn't there. At least your panel will still work.

---

### Post by BGFG on 2008-08-03
Yeah, i've come to terms with it now. Besides there or not i lose absolutely no functionality, so why should i be a &*#! about it ? It may be programming, It may be novell funding. Either way it's free and works astoundingly well.
so i guess that's out of my system. ;0

---

