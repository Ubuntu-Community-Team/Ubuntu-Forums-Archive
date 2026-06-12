---
title: "Title Bar Missing minimize &amp; X"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by oldtrout on 2008-09-30
[SIZE="3"][B]Using Firefox V3.0.3
On the title bar all the icons on the right such as minimize & X have disappeared?
Help and thanks. [/B][/SIZE]

---

### Post by mwalimu54 on 2008-09-30
Yeah, me too, only not just in FF.  I think it's compiz or the emerald theme manager that's causing my problem but I don't know how to fix it.  Any help would be appreciated.

PS.  Sometimes they show but other times they mysteriously disappear.

---

### Post by nhasian on 2008-09-30
See if this resolves the issue for you. If it does, dont forget to "thank" me :)

```
metacity --replace
```

---

### Post by wilsong on 2008-09-30
I had this problem when i tried to upgrade to 8.10 Intrepid, it was happening in KDE, but wouldnt happen in enlightenment ... if you can tell us what window manager your using, and tell us any steps you have tried that have or haven't worked, and when you started noticing this problem?

---

### Post by mwalimu54 on 2008-10-01
using Gnome on 7.10. I've had this problem ever since I started using emerald and compiz which was about the same time.  It corrects itself if I drag the problematic windows around a bit.  It seems to be that a refresh helps them out.

---

### Post by Therion on 2008-10-01
This issue almost drove me insane.  Short answer:  Remove Emerald.  

Problem solved.  Permanently.

```
sudo apt-get remove emerald
```
You can disable it in the Session manager, but I just removed it since I wasn't using it anyway.

---

### Post by mwalimu54 on 2008-10-01
ok, not a fix but an explanation anyway.  is there another windows manager that will do the effects like clear title bars besides emerald that you could recommend?

---

### Post by Therion on 2008-10-01
> **mwalimu54 said:**
> ok, not a fix but an explanation anyway.  is there another windows manager that will do the effects like clear title bars besides emerald that you could recommend?
You may not like it, but I assure you it VERY much fixes the problem.

My other best suggestion if you've simply GOT to have clear titlebars... Use the [Compiz-Fusion Icon](http://wiki.compiz-fusion.org/CompizFusionIcon).  It will help minimize your frustration at least.  It's in Synaptic or you can use apt-get.

---

### Post by Locke_99GS on 2008-10-01
I had the same issues. The latest Compiz from git cured it for me.

---

### Post by ogunduz on 2008-10-15
im having the same problem and i dont want to remove compiz. i was not having any problem till this morning. is there any way to fix it?

---

### Post by hatman on 2008-11-10
> **ogunduz said:**
> im having the same problem and i dont want to remove compiz. i was not having any problem till this morning. is there any way to fix it?

I found this post on the Compiz Fusion site, 
> open ccsm which is compizconfig-settings-manager and you open that either through the terminal with ccsm or under system/preferences/compizconfig settings manager.
Then look under the effects category... click on the window decoration plugin... and in the "Command" field... remove what is there and if emerald is installed type either emerald --replace or just emerald.... on the other hand if emerald is not installed type gtk-window-decorator --replace there.
I went into ccsm and in the command there was emerald, so I removed it and placed the ```
gtk-window-decorator --replace
``` there instead, it worked for me.

---

