---
title: "compiz fails to load adwaita theme"
date: 2011-12-10
forum: New to Ubuntu
---

### Post by ilikelinuxitisthebest on 2011-12-10
hey guys. i have just installed compiz but whenever i launch it in the terminal it does stuff and then it says failed to load adwaita theme and then refuses to load any other settings. help is appreciated. thanks.

---

### Post by wolfen69 on 2011-12-10
Are you using gnome shell? The Adwaita theme is the default for gnome shell, which doesn't use compiz.

Edit: I just noticed you are using Xubuntu. Sorry about that.

---

### Post by lechien73 on 2011-12-10
I believe that if you install gnome-themes-standard then this problem is resolved:

```
sudo apt-get install gnome-themes-standard
```

But, as wolfen69 says, gnome doesn't use compiz, but uses mutter instead!

---

### Post by ilikelinuxitisthebest on 2011-12-10
no im on xubuntu. there for i am using xcfe.

---

### Post by ilikelinuxitisthebest on 2011-12-10
thanks that worked. but a new problem has arose. i launch the replace command in the terminal and it always just stops moving on one thing or a another. like it will apply my settings but it will say that one thing is done and then nothing else comes up. heres my output.  ```
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : ini
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing cube options...done
Initializing td options...done
Initializing rotate options...done
``` and that's it, a prompt never shows up after the rotate options thing.

---

### Post by ilikelinuxitisthebest on 2011-12-10
> **wolfen69 said:**
> 
Edit: I just noticed you are using Xubuntu. Sorry about that. No big deal.

---

### Post by bluexrider on 2011-12-10
> **ilikelinuxitisthebest said:**
> no im on xubuntu. there for i am using xcfe.
  get yourself a couple of themes here and give it a whirl

[http://xfce-look.org/](http://xfce-look.org/)

also see  [http://wiki.compiz.org/](http://wiki.compiz.org/)


for compiz control [Click here to install CCSM]("apt:compizconfig-settings-manager").

---

### Post by ilikelinuxitisthebest on 2011-12-10
sir. i don't think you know what were talking about here. i activate compiz and it dosent work. your post made no sense to me whatsoever.  I also have CCSM installed fine.

---

### Post by wildmanne39 on 2011-12-10
Hi, have a look at this link starting with post 7.
[http://ubuntuforums.org/showthread.php?t=1857423](http://ubuntuforums.org/showthread.php?t=1857423)

---

### Post by ilikelinuxitisthebest on 2011-12-10
there is no system settings

---

### Post by ilikelinuxitisthebest on 2011-12-10
ok guys. im tired of this. i have decided not to use compiz and that i will maybe try it again in the future. thank you all for your help.

---

### Post by lechien73 on 2011-12-11
If your problem with the adwaita theme is now solved - which I think it is - then maybe start a new thread about your compiz issue.

Does it happen when you launch ```
compiz --replace ccp
``` to start the compiz environment?

I found [this tutorial]("http://www.howtoforge.com/enabling-compiz-on-xubuntu-11.10-oneiric-ocelot"), which shows how to install compiz on Xubuntu 11.10, but you may have seen it already.

It does seem to be graphics card dependent - what card do you have in your machine?

---

