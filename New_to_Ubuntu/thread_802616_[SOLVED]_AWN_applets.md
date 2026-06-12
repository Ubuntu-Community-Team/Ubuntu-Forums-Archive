---
title: "[SOLVED] AWN applets"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by hellomoto on 2008-05-21
Can someone tell me were I can browse and download avant window navigator applets?

I have been to the wiki page [here]("http://wiki.awn-project.org/index.php?title=Awn_Extras"). I can view the applets information but there doesn't seam to be a link to download them.

Am I missing something?

---

### Post by shifty_powers on 2008-05-21
just look in synaptic ;)

(tpye in awn. it's part of the repo's now)

---

### Post by SunnyRabbiera on 2008-05-21
I think some can be found on gnome look.

---

### Post by SunnyRabbiera on 2008-05-21
> **shifty_powers said:**
> just look in synaptic ;)

(tpye in awn. it's part of the repo's now)

No, I think he already got it installed

---

### Post by hellomoto on 2008-05-21
AWN is already installed and working fine. 

I am looking for applets. I have been onto gnome look, There is some themes on there but thats about it.

I was trying to find some applets to browse (similar to the wiki page but with the download links!).

Also I have looked in synaptic for AWN applets and there isn't any.

---

### Post by shifty_powers on 2008-05-21
heh, no i meant the awn-applets package ;)

maybe not what he is looking for mind

---

### Post by SunnyRabbiera on 2008-05-21
> **hellomoto said:**
> AWN is already installed and working fine. 

I am looking for applets. I have been onto gnome look, There is some themes on there but thats about it.

I was trying to find some applets to browse (similar to the wiki page but with the download links!).

Also I have looked in synaptic for AWN applets and there isn't any.

Yeh I really dont know who else has stuff for AWN, your guess is as good as mine on that bit.

---

### Post by hellomoto on 2008-05-21
no problem, thank you for your help

---

### Post by hellomoto on 2008-05-21
ok solved this problem:

I downloaded and installed AWN from synaptic and whilst the program made it into the repos the applets didnt.

By adding AWN to the repos:
```

echo 'deb http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main'  |  sudo tee -a /etc/apt/sources.list
echo 'deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main'  |  sudo tee -a /etc/apt/sources.list

```

and  then downloading the applets:

```

sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

```

AWN didn't even need restarting all the applets are now available.

:)

---

