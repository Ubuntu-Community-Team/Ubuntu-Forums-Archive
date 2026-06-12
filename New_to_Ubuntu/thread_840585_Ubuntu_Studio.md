---
title: "Ubuntu Studio?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by joey129 on 2008-06-25
Ubuntu studio is just like the regular one but with more apps geared towards multimedia editing pre-installed, right?

---

### Post by Inxsible on 2008-06-25
Right !

---

### Post by billgoldberg on 2008-06-25
And some better looking themes/wallpapers.

---

### Post by ad_267 on 2008-06-25
And a "real time" kernel... I think that's what it's called. From wikipedia:
> The kernel included with Ubuntu Studio is modified for intensive audio, video or graphics work. The scheduler allows applications to request immediate CPU time, which can drastically reduce audio latency. Ubuntu Studio also includes custom artwork, a blue-on-black theme as opposed to Ubuntu's default brown and orange.

---

### Post by bluepowder7 on 2008-06-25
yeah, tons of apps and the rt (realtime) kernel.  you can still use the generic kernel without worry.

if you're looking at adding the ubuntustudio-... packages to your normal ubuntu install, note that it's a BIG install to add the audio/video/graphics apps, so if you're low on space or even just marginal you may see it interrupt itself, and tell you to manually run a command (cuz the temp files it makes use up every last picobyte of space you had).  open terminal and run that command, and it'll sort itself out usually.

---

### Post by joey129 on 2008-06-26
> **bluepowder7 said:**
> if you're looking at adding the ubuntustudio-... packages to your normal ubuntu install, note that it's a BIG install to add the audio/video/graphics apps, so if you're low on space or even just marginal you may see it interrupt itself, and tell you to manually run a command (cuz the temp files it makes use up every last picobyte of space you had).  open terminal and run that command, and it'll sort itself out usually.

So, is studio more efficient at running tose kinds of apps?
And i wanna get you guys' opinion on this: I kinda just installed ubuntu (so there's really nothing here yet). What I'm thinking of doing is installing some of the apps that come with studio so i dont have to reinstall the OS. But if the kernel (i duno what i'm talking about.. its just what i got from the previous posters:confused:) is like better, is it worth the reinstall?

---

### Post by ad_267 on 2008-06-26
> **joey129 said:**
> So, is studio more efficient at running tose kinds of apps?
And i wanna get you guys' opinion on this: I kinda just installed ubuntu (so there's really nothing here yet). What I'm thinking of doing is installing some of the apps that come with studio so i dont have to reinstall the OS. But if the kernel (i duno what i'm talking about.. its just what i got from the previous posters:confused:) is like better, is it worth the reinstall?

I don't know how much better the kernel is so you want to wait for someone else's opinion on that. But I'm pretty sure you can just install the realtime kernel from an Ubuntu installation by installing the linux-rt package. Then you can select which kernel you want from your GRUB menu. I'm not sure if there will be any issues with this compared to a fresh Ubuntu Studio installation.

---

### Post by bluepowder7 on 2008-06-29
> **joey129 said:**
> So, is studio more efficient at running tose kinds of apps?
And i wanna get you guys' opinion on this: I kinda just installed ubuntu (so there's really nothing here yet). What I'm thinking of doing is installing some of the apps that come with studio so i dont have to reinstall the OS. But if the kernel (i duno what i'm talking about.. its just what i got from the previous posters:confused:) is like better, is it worth the reinstall?

more efficient?  dunno.  i think it just loads some fairly good apps - nearly all of which i never got around to using since i ended up borking my system anyways.  i think (and guess that) the real efficiency boost comes from the realtime (-rt) kernel, which from what i read allcates 95% of the CPU to the active task, and leaves the rest for everything else.

---

