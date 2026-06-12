---
title: "No Firefox menus in Gnome Shell"
date: 2011-08-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sgage on 2011-08-10
Is anyone else experiencing this? FF menus work fine in Unity, but in GS, nothing, nada. I can log out/log in many times, reboot, etc., but no joy. Kind of a showstopper. 

Then, on a whim, I'll try GS again later or the next day, and the menus will be working again. 

How utterly bizarre.

---

### Post by chrisccoulson on 2011-08-10
Are you sure you haven't just hidden the menu (to display the Firefox button instead)?

---

### Post by pferraro on 2011-08-10
This could be due to interference by appmenu (that was my experience).  Try removing the appmenu packages (if you aren't using unity at all).

---

### Post by sgage on 2011-08-10
> **chrisccoulson said:**
> Are you sure you haven't just hidden the menu (to display the Firefox button instead)?

No. The menu is showing, it's just that clicking on any of the items does nothing at all.

---

### Post by sgage on 2011-08-10
> **pferraro said:**
> This could be due to interference by appmenu (that was my experience).  Try removing the appmenu packages (if you aren't using unity at all).

I do switch between Unity and GS, but I removed firefox-globalmenu some time ago. When this problem started cropping up, I reinstalled it, thinking maybe there was some weird interaction going on, but it didn't help so I removed it again.

I'll try removing appmenu altogether, just to see...

---

### Post by chrisccoulson on 2011-08-10
If the menu is displayed, then it's nothing to do with the appmenu (especially seeing as you already uninstalled firefox-globalmenu, which incidentally, is completely benign outside of Unity). It sounds more like a gnome-shell bug

---

### Post by brazov on 2011-08-10
> **sgage said:**
> Is anyone else experiencing this? FF menus work fine in Unity, but in GS, nothing, nada. I can log out/log in many times, reboot, etc., but no joy. Kind of a showstopper. 

Then, on a whim, I'll try GS again later or the next day, and the menus will be working again. 

How utterly bizarre.

In my case those menus do work correctly. (Using GNOME classic, no effect).

---

### Post by wazupwiop on 2011-08-10
I am not experiencing any bugs.  I am using Gnome Classic on 11.04 with no issues.

---

### Post by sgage on 2011-08-10
> **sgage said:**
> I'll try removing appmenu altogether, just to see...

I logged into GS to experiment with removing appmenu, but I checked FF first, and now menus are work.

This is the weirdest thing - sometimes they work fine, and sometimes they just don't. I can't detect any pattern. The next time they don't work, I'll try removing appmenu...

---

### Post by sgage on 2011-08-10
> **chrisccoulson said:**
> If the menu is displayed, then it's nothing to do with the appmenu (especially seeing as you already uninstalled firefox-globalmenu, which incidentally, is completely benign outside of Unity). It sounds more like a gnome-shell bug

Could be, though pferraro felt he detected an interaction there...

---

### Post by sgage on 2011-08-10
> **brazov said:**
> In my case those menus do work correctly. (Using GNOME classic, no effect).

I'm talking about Gnome Shell...

---

### Post by sgage on 2011-08-10
> **wazupwiop said:**
> I am not experiencing any bugs.  I am using Gnome Classic on 11.04 with no issues.

I'm talking about Gnome Shell, in 11.10 (Oneiric), so it's a rather different situation...

---

