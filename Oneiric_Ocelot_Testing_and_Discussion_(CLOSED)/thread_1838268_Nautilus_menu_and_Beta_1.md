---
title: "Nautilus menu and Beta 1"
date: 2011-09-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by makitso on 2011-09-03
Don't know what I did but now the nautilus "File Edit View..." menu is always on the top panel even with no files open.  Not a problem in Unity but I installed the gnome 3 shell for testing and it conflicts gnome and locks up the system.

---

### Post by sammiev on 2011-09-03
> **makitso said:**
> Don't know what I did but now the nautilus "File Edit View..." menu is always on the top panel even with no files open.  Not a problem in Unity but I installed the gnome 3 shell for testing and it conflicts gnome and locks up the system.

+1 same here and I even did a fresh install and after the updates it went the same way. It's a bug to say the least.

---

### Post by mc4man on 2011-09-03
Unity (3d) has been displaying the [wrong appmenu on the desktop]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/805252") for some time
That shouldn't matter in GS, if you're seeing that menu then GS has likely crashed, ck. /var/crash, lately GS does crash here on about 15% of log in attempts

---

### Post by sammiev on 2011-09-03
I get the GS menu until I move my mouse to the left hand top of the screen. I can go any where else without a problem until then.

---

### Post by tekstr1der on 2011-09-03
This issue is being discussed in the following bug:

[https://bugs.launchpad.net/ubuntu/oneiric/+source/nautilus/+bug/805252](https://bugs.launchpad.net/ubuntu/oneiric/+source/nautilus/+bug/805252)

Perhaps you should chime in with your GS woes.

---

### Post by Quackers on 2011-09-03
> **sammiev said:**
> I get the GS menu until I move my mouse to the left hand top of the screen. I can go any where else without a problem until then.

Me too :-)
I've regressed to unity for the moment

---

### Post by mc4man on 2011-09-03
Not too sure the appmenu on desktop focus has anything to do w/ GS crashing, (other than when it does it usually shows just the nautilus menu
So slightly OT - 
Seeing here about a 60% chance of getting a good GS login. When it does crash a couple of different crashes though by far the most common one is this one

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/840715](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/840715)

As far as the appmenu on Desktop focus in Unity, even in it's improper state atm find it very useful - would hate to see it removed as was recently suggested

---

### Post by xebian on 2011-09-03
I got around this issue by accident when I was checking out gnome tweak tool.  INstall it and turn off the option for Nautilus to manage the desktop.

---

### Post by sammiev on 2011-09-03
> **xebian said:**
> I got around this issue by accident when I was checking out gnome tweak tool.  INstall it and turn off the option for Nautilus to manage the desktop.

That maybe the option for now but i must add i was able to get back in a few times now without that. I will change my settings and try a few reboots to see if that is the cause. 
Thanks. :)

---

### Post by sammiev on 2011-09-03
> **xebian said:**
> I got around this issue by accident when I was checking out gnome tweak tool.  INstall it and turn off the option for Nautilus to manage the desktop.

TY, I tried a few reboots and it seemed to work. After reboot I finally got a system error and went to report it to find it was reported many times. TY sir! :)

---

