---
title: "Preview of sound files not working"
date: 2011-09-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by xbxb on 2011-09-16
When I position the mouse over a sound file nothing happens: I can't  hear any sound or see any graphical indication that the system is trying  to preview the sound file.

I checked the Edit > Preferences > Preview tab and tried both 'Always' and 'Local Files Only' but neither setting works. 

I checked the indicator-sound applet and sound settings, and run  alsamixer. Everything looks correct. The desktop-login file still plays  correctly when I log in, and I can play sound files with Banshee or  Movie Player.

Sound file previews were working immediately after I did a clean beta1 installation, but stopped working after I ran the Update-Manager. 

Also, the system-ready sound file at the login screen (bongo drums) stopped working after the first update. I suspect both of these issues are related.

Does anyone else have this issue? Is this a known bug? 

If anyone can give me some help fixing this I would appreciate it.

Thanks

---

### Post by jbicha on 2011-09-17
That's a feature not a bug. ;-)

Actually in GNOME 3.2, previewing is no longer handled by Nautilus but instead by an addon/app named sushi. Unfortunately, sushi has not yet been packaged in Debian or Ubuntu and it's unlikely to be in the default 11.10 install. The sound preview preferences you stumbled across should be removed in the next Nautilus version update.

I don't know what's going on with the startup sound. It still works here at least some of the time. I'd rather it didn't actually as it's rather dated.

---

### Post by xbxb on 2011-09-17
Thanks for your reply, jbicha. I'll be watching for updates to Nautilus and looking for the sushi addon/app.

---

### Post by ioca100 on 2011-10-05
> **jbicha said:**
> That's a feature not a bug. ;-)

Actually in GNOME 3.2, previewing is no longer handled by Nautilus but instead by an addon/app named sushi. Unfortunately, sushi has not yet been packaged in Debian or Ubuntu and it's unlikely to be in the default 11.10 install. The sound preview preferences you stumbled across should be removed in the next Nautilus version update.

I don't know what's going on with the startup sound. It still works here at least some of the time. I'd rather it didn't actually as it's rather dated.

There are  sushi-plugins in synaptic. Can I install it ?

---

### Post by crdlb on 2011-10-05
> **ioca100 said:**
> There are  sushi-plugins in synaptic. Can I install it ?

That is something different.

---

### Post by Harry33 on 2011-10-05
> **jbicha said:**
> That's a feature not a bug. ;-)
...
I don't know what's going on with the startup sound. It still works here at least some of the time. I'd rather it didn't actually as it's rather dated.

So true,
I have removed gnome-session-canberra a long time ago.

---

### Post by ioca100 on 2011-10-05
> **crdlb said:**
> That is something different.

Thank you.

---

