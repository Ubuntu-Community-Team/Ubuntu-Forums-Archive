---
title: "Totem - lots of bugs in 11.10"
date: 2011-10-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cerda on 2011-10-09
Anyone noticed how Totem is really bad atm in 11.10 ??? The python plugins none of them seen to work (like the subtitle downloader) and i can't even save a playlist.

The first bug has been confirmed in launchpad (bug #855100), the second one i could not find there. Anyway we're 5 days to launch, any hope this could be fixed by thursday ?? Any more of you having the same problem ??

My fresh 11.10 installation wasn't that smooth, maybe it has something to do about it.

---

### Post by chazinams on 2011-10-09
Frankly, I think Totem itself is one big bug. My opinion is that the software is totally useless. I have nothing but problems with it. It is a major hassle to get it to play anything in my experience. I switched to VLC and have none of the same problems. But every now and then I run into an issue because Totem is set as default video player on a new ubuntu install.

I really wish Totem wasn't the default video player. My advice is to abandon Totem and use VLC instead. VLC is in the Universe repo.

---

### Post by cerda on 2011-10-12
The thing is, all these funcionality were okay in 11.04 and now they're missing and it's like they weren't noticed. I'm not a programmer, but, at least to save a playlist, seens to be something really easy to fix.

---

### Post by dino99 on 2011-10-12
wonder why we still not get 3.2 version with oneiric.

---

### Post by crdlb on 2011-10-12
> **dino99 said:**
> wonder why we still not get 3.2 version with oneiric.

Totem 3.2 uses clutter-gst instead of Xv, and Ubuntu apparently isn't comfortable with that.

---

### Post by jbicha on 2011-10-12
Except for the subtitle plugin which needs some more fixing, the other Python plugins are working in the proposed update.

How do you expect the save playlist bug to be fixed if nobody reports it on launchpad? ;)

We're not using Totem 3.2 in Ubuntu 11.10 because it requires clutter which requires working 3D which doesn't work for everyone.

---

### Post by BwackNinja on 2011-10-12
Totem has really shaped up in the past releases, I actually use it as my default now.

That said, the one thing that annoys me right now is when you open it up without the sidebar, then open up the sidebar, the video gets resized.

One thing I still don't like though is the ui, but I use a custom totem.ui so it wastes less space. Problem happens whether or not I'm using my custom totem.ui.

---

