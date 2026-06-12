---
title: "Lubuntu with GNOME"
date: 2021-01-14
forum: New to Ubuntu
---

### Post by jazahalka on 2021-01-14
I have installed and set GNOME on lubuntu, so do I have now ubuntu? Is between ubuntu and lubuntu any other difference?

---

### Post by howefield on 2021-01-14
Thread moved to the "*New to Ubuntu*" forum.

---

### Post by jazahalka on 2021-01-15
Thanks, I did not know, where to ask it.

---

### Post by guiverc on 2021-01-15
Personally I'd call it Ubuntu, but it would be equally correct to call it Lubuntu.  It would also depend on whom I'm talking to.

The system I'm replying to you on, was a Ubuntu install originally, on which I added `xubuntu-desktop`, `lubuntu-desktop` & `ubuntu-mate-desktop` to it. Thus what is mine?

I select (*as you likely do*) which I use during login, and as I'm currently using my Lubuntu session, I'd more likely call it Lubuntu currently online, however if speaking with friends/family or non-ubuntu people, I'd generally fall back to Ubuntu (*more people may know what it is*) or just refer to it as a GNU/Linux.

If I was using XFCE/Xubuntu, I'd likely call it Xubuntu online, or when speaking to people who know what Xubuntu is.  If using GNOME/Ubuntu, I'd just call it Ubuntu.  (*I've since removed `ubuntu-mate-desktop` so I can't use that anymore*).  

Personally I'd not call it a *Linux* machine (**1*), for me it's GNU/Linux, but that's just my choice.  Most do call it Linux - ie. there is no right answer; it's what seems most correct for you.


*1 = *Linux is the kernel, my android phone uses that kernel too*

---

### Post by jazahalka on 2021-01-15
So is there any other difference between Ubuntu and Lubuntu that different desktop?

---

### Post by howefield on 2021-01-15
> **jazahalka said:**
> ...so do I have now ubuntu?

Might help to know exactly what package(s) you have installed to "set gnome". It's unclear eg, whether you have installed purely a gnome desktop or the full ubuntu desktop.

---

### Post by jazahalka on 2021-01-15
I installed just the gnome-desktop package I think.

---

### Post by ActionParsnip on 2021-01-15
What is the output of:
```

lsb_release -a; uname -a

```
Thanks

---

### Post by jazahalka on 2021-01-15
It says:

[FONT=Arial]No LSB modules are available.[/FONT]
[FONT=Arial]Distributor ID: Ubuntu[/FONT]
[FONT=Arial]Description:    Ubuntu 20.04.1 LTS[/FONT]
[FONT=Arial]Release:        20.04[/FONT]
[FONT=Arial]Codename:       focal[/FONT]
[FONT=Arial]Linux ls-aspirea51552g 5.4.0-62-generic #70-Ubuntu SMP Tue Jan 12 12:45:47 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

So is Lubuntu just Ubuntu with different desktop?[/FONT]

---

### Post by ActionParsnip on 2021-01-15
> **jazahalka said:**
> [FONT=Arial]So is Lubuntu just Ubuntu with different desktop?[/FONT]

Essentially, yes. Ubuntu uses Gnome. Lubuntu uses LXDE. The underlying packages are identical

---

### Post by jazahalka on 2021-01-15
Ok, thank you very much.

---

### Post by jazahalka on 2021-01-15
Is there some possibility of marking comment as solution?

---

### Post by guiverc on 2021-01-15
On 20.04.1, Lubuntu desktop is LXQt  (not LXDE @ActionParsnip)

Lubuntu with LXQt uses the Qt5 toolkits; ie. libraries in your software stack.  (Q toolkit ver 5)

Ubuntu with GNOME uses the GTK+3 (or GTK3, GTK ver 3) toolkit & libraries in your software stack.
*FYI:  GTK originally was the Gimp toolkit, GTK+ was when it became Gimp+GNOME toolkit... the '+' was semi-recently dropped and it's okay to call Gimp+GNOME toolkit just GTK; GTK4 development is progressing...*

Underneath both will be the Ubuntu base system, which is identical regardless of what you're using above it (in your software stack). 

Thus applications differ too, Lubuntu comes with Qt5 applications (Qt5 applications that don't use KF5 too), as they'll use libraries already installed in your system, possibly already in memory thus you won't be wasting RAM by filling memory with multiple libraries that do the same thing, but slightly differently (ie. GTK & Qt libs in RAM at the same time).

Yes it's more than just desktop; you're changing an upper part of your software stack; but DESKTOP is the easiest bit to point to.  Above desktop are *end-user* applications (which differ), below that (& below desktop) are the toolkits & libraries (which also differ).

Just FYI.  KDE also uses Qt5, however KDE requires the use of KF5 (KDE Frameworks ver 5), which Lubuntu/LXQt doesn't require or need; result is it's lighter.  Ubuntu Studio 20.10 & later also use Qt5 but without the complete KF5 (ie. not all of KDE is installed, though users often add it in use when they add packages).

GNOME, MATE, XFCE (Xubuntu), Budgie, use the GTK3 stack.

Legacy Lubuntu (Lubuntu 18.04 LTS and before) used the older (deprecated) GTK2 stack.

---

### Post by jazahalka on 2021-01-15
So it is not the same ubuntu now? Now it uses "faster" libraries? Do I understand you correctly? Thank you.

---

### Post by guiverc on 2021-01-15
Faster libraries... maybe, but that's not the intention.

Historically, Qt was created and thus owned by a company, it was made available free of charge to open source... however the FSF & GNU projects didn't like a company still owning the rights to the Qt toolkit... this lead to the creation of GTK+  (since FSF/GNU already had created the Gimp program, Gimps libraries were  their starting point).  There is more to this history that I've summarized here..

Qt 4 had a reputation of being heavy (it was for a few versions), Qt5 however is light & fast yes.  (use 

```
lxqt-about --version

```

to see your  (LXQt & Qt) versions  for your release.

LXQt = Light X(11) & Qt, ie. **LIGHT** is a very significant goal of LXQt; just as the **L** in Lubuntu refers to Light.  Light may not mean just fast though, it may also mean lean in memory requirements... 

What's fast on one CPU maybe slower on another..  so I'd not use the "*faster*" term  (GTK3 performs better on modern CPUs than it does on older ones for example)

I'm using a 11 year old desktop (dell optiplex 960, c2q-9400) and I can run GNOME fine, but it's heavier, and not as fast as the LXQt I'm currently using (Lubuntu *hirsute* or what will be 21.04 on release). It's faster due to a combination of how written, libraries & how they run on my old cpu.

Lighter is more important in Lubuntu/LXQt, than speed.  Yes people love the *fast* effect of being being developed to be *light*, but fast was not the goal (just a side effect).

---
Some additional links

FAQ - [https://phab.lubuntu.me/w/faq/](https://phab.lubuntu.me/w/faq/)
Lubuntu links - [https://lubuntu.me/links/](https://lubuntu.me/links/)

---

### Post by guiverc on 2021-01-15
> **guiverc said:**
> Faster libraries... maybe, but that's not the intention.

What's fast on one CPU maybe slower on another..  so I'd not use the "*faster*" term  (GTK3 performs better on modern CPUs than it does on older ones for example)


I'll go off-topic here, but maybe make you understand why I made that comment.

I test Ubuntu *flavors* on i386 hardware.  

On a IBM Thinkpad t43 I still use (it runs Lubuntu 18.04 LTS), and contains a pentium M cpu, 1.5GB of RAM and is x86/i386 only (ie. 32-bit).  I really stopped using MATE on that device around 16.04, as MATE had migrated off GTK2 and was fully GTK3 by 16.04, and that CPU just doesn't run GTK3 well at all; it's slow.

Not an issue, I still had Lubuntu (LXDE using GTK2) & Xubuntu (XFCE using GTK2) for 16.04

By 18.04, Lubuntu was still on GTK2, but XFCE had started porting to GTK3, thus my use of XFCE on it had started to reduce (XFCE was slowing down in use; GTK3 is heaver).

As XFCE was slowing down due to move from GTK2 to GTK3 just as MATE had done when it ported years earlier; I feared what would happen when Lubuntu switched from LXDE to LXQt. Instead I was pleasantly surprised when Lubuntu 18.10 & 19.04 using LXQt were actually great on the old pentium M laptop :)  (*FYI: Xubuntu also had 18.10 & 19.04 ISOs*)

I also use pentium 4 machines in testing; but whilst I've run Unity (using GTK3) on pentium 4, I've **never** been tempted to use GNOME on the pentium 4 or pentium M (Unity 7 was too slow & GNOME is heaver still).

When testing using faster CPUs (eg. Core2Duo CPUs) the drop in speed from GTK2 to GTK3 was no where near as noticeable. If I wasn't looking for it (*experiencing it on really slow single-core processors*), I'd likely not have noticed it at all.

Not all CPUs are equal.  Modern cpu's cope better with modern software.

Qt5 is modern software too, but it's written in way that works for all architectures, all cpus. It's lightness really shines though when using *ancient* hardware :P

---

