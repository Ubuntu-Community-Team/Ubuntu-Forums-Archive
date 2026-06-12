---
title: "Gnome 3/Gnome Shell support in Oneiric Ocelot"
date: 2011-10-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Brushstroke on 2011-10-08
I have heard differing opinions and statements on this. Some say that Gnome 3 will not be fully supported in 11.10, and some say that it will. I plan to install Oneiric with Gnome 3, but if I'm not going to get everything out of Gnome 3 that I would get if I were to, say, install the latest version of Fedora, what's the point? 

What have you guys heard about Gnome 3 and the latest upcoming Ubuntu release?

---

### Post by kaldor on 2011-10-08
You are confusing GNOME Shell with GNOME 3. Ubuntu uses Unity which is a shell for GNOME 3. The official "GNOME Shell" is what you are thinking about.

Unity is the default in 11.10. You can install the *gnome-shell* package and choose it in the login menu.

The reason that GNOME 3 caused issues in the past was due to conflicts. GNOME Shell depends on GNOME 3 dependencies, and Ubuntu 11.04 used GNOME 2. Both could not co-exist on the same system. Since Ubuntu 11.10 is totally based on GNOME 3, no conflicts will arise. 

I'm in the same boat as you; I much prefer Shell over Unity. Have fun :)

Edit: 

I should mention that this is not speculation. I use GNOME Shell without any issues at all on Oneiric. I can choose between both Unity (or Unity 2d) and GNOME Shell in the log in screen. No modifications or tweaks are needed whatsoever.

---

### Post by crdlb on 2011-10-08
There are a few places where Ubuntu has patched gnome components to work better Unity. A couple that come to mind: [list]
[*]the nautilus file transfer dialog is [patched to be skip-taskbar](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/868032), causing it to disappear easily in gnome-shell.
[*]Rhythmbox is [patched to not quit when the window is closed](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/780747), which is wrong for gnome-shell. (The linked bug report was for a mistake in the patch, but the patch is still there)[/list]

Oneiric is also missing GDM 3.2 with the new shell-based greeter, and the new gnome-documents app. Beyond that, it works pretty well.

---

### Post by Harry33 on 2011-10-09
Some Gnome applications depend on the package libunity6 (unity library) in Ubuntu Oneiric.
- libbrasero-media3-1 (Rhythmbox, Brasero)
- nautilus
- empathy
- evolution-indicator
- telepathy-indicator
- liferea

Also these depend on libunity6
- thunderbird-gnome-support
- deja-dup

---

### Post by Brushstroke on 2011-10-09
> **Harry33 said:**
> Some Gnome applications depend on the package libunity6 (unity library) in Ubuntu Oneiric.
- libbrasero-media3-1 (Rhythmbox, Brasero)
- nautilus
- empathy
- evolution-indicator
- telepathy-indicator
- liferea

Also these depend on libunity6
- thunderbird-gnome-support
- deja-dup
*Nautilus *has a Unity dependency? You've got to be kidding me... So does this mean that if I were to run a minimal install of 11.10 with Gnome 3 running on top of it, I wouldn't be able to use Nautilus without bringing in a load of Unity libraries? Such crap.

---

### Post by sgage on 2011-10-09
> **Brushstroke said:**
> I have heard differing opinions and statements on this. Some say that Gnome 3 will not be fully supported in 11.10, and some say that it will. I plan to install Oneiric with Gnome 3, but if I'm not going to get everything out of Gnome 3 that I would get if I were to, say, install the latest version of Fedora, what's the point? 

What have you guys heard about Gnome 3 and the latest upcoming Ubuntu release?

Gnome Shell works perfectly on 11.10 as far as I can tell, and I have been using it daily for several weeks now.

---

### Post by Harry33 on 2011-10-09
> **Brushstroke said:**
> *Nautilus *has a Unity dependency? You've got to be kidding me... So does this mean that if I were to run a minimal install of 11.10 with Gnome 3 running on top of it, I wouldn't be able to use Nautilus without bringing in a load of Unity libraries? Such crap.

I do not like that either.
However,
what I think it means, is that Nautilus (with the dependency on libunity6) runs a bit more better incorporated into Unity. But of course, if Unity shell is installed.

If Unity shell is not installed, the unity library is installed in vain.

---

### Post by ronacc on 2011-10-09
> **sgage said:**
> Gnome Shell works perfectly on 11.10 as far as I can tell, and I have been using it daily for several weeks now.

I agree with sgage I have been using gnome-shell since the start of oneiric and it runs great .

---

### Post by mdhollis on 2011-10-09
> **Brushstroke said:**
> *Nautilus *has a Unity dependency? You've got to be kidding me... So does this mean that if I were to run a minimal install of 11.10 with Gnome 3 running on top of it, I wouldn't be able to use Nautilus without bringing in a load of Unity libraries? Such crap.

They should release a gnome-shell-buntu to prevent that.

---

### Post by ronacc on 2011-10-09
the question is , is unity an actual dependency or just one of those things that just got marked as one , or is it due to some Ubutnu patch to nautilus .

---

