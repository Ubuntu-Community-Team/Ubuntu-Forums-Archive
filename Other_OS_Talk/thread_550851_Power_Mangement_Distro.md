---
title: "Power Mangement Distro"
date: 2007-09-14
forum: Other OS Talk
---

### Post by Kymac on 2007-09-14
I just recently bought a T61 lenovo thinkpad for college.  It has Windows Vista Home Basic installed on it (it's a 60GB harddrive and theres a 10GB partition for all the recovery stuff).

Anyway, I was curious as to how large of a partition space should I shrink Vista down to, in order to put a new distro in.  However, I haven't decided on the distro, and thought yall could help me.  I was wondering if there was a linux distribution that anyone noticed had very good power management capabilities.  I'm looking for one that is somewhat user friendly, but it doesn't need to have the prettiest GUI.

If anyone could suggest some, that would be great... Does Xubuntu use up little power?  (I'll only be using it for typing notes and such)

Thank You

---

### Post by insane_alien on 2007-09-14
Xubntu sounds good. but if you want to go even lighter(since you're only going to be typing) DSL will do. you can have it on a thumb drive as well it's so small(bout 50MB) so you won't even need to mess with your partition table. just need to tweak the BIOS to enable booting frrom USB.

---

### Post by fwojciec on 2007-09-14
I've always found that Arch Linux made it easiest for me to properly set up power management so that my laptop works longer on battery than it did in windows.  But I've always set up power management myself rather than having a distro install something automatically.

My preferences in this regard (and I think you could probably use this in just about any distro):
1) All power management (except suspend/hibernate) on my laptop is done by laptop-mode tools - properly configured it is, IMO, the ultimate, all-in-one power management solution.
2) I get rid of everything else (gnome-power-manager and such), I just uninstall it.
3) I use openbox and my system is very lightweight (under 100MB memory used after boot).  That way lots can be cached in memory (my laptop has 1GB) and hard drive doesn't have to used that often (I have it spin down very quickly when on battery).
4) I use conky to report things such as battery life, cpu frequency etc.
5) I have custom scripts, executable by keyboard shortcuts (and things like closing the lid, for example), which do things like change crufreq governors, suspend, and hibernate.

Now that I've learned how all this works, I can set it up in less than 5 minutes.  If you're serious about getting the most of your battery the best way is to learn how it works and become hands on about it.  The choice of distro is a secondary matter then.

---

### Post by schrankage on 2007-09-14
[B][SIZE="2"]I'm trying to find a way to control the fans in my laptop, they run full speed whenever the laptop is on, and I have yet to find a way to regulate and manage them. It's a Fujitsu Lifebook N Series.

Anyone have any suggestions?[/SIZE][/B]

:popcorn:

---

### Post by mips on 2007-09-15
> **schrankage said:**
> [B][SIZE="2"]I'm trying to find a way to control the fans in my laptop, they run full speed whenever the laptop is on, and I have yet to find a way to regulate and manage them. It's a Fujitsu Lifebook N Series.

Anyone have any suggestions?[/SIZE][/B]


It could be a kernel bug. I worked on a Fujitso Amilo L1310G the other where the fans would not come on at all, so the laptop ends up overheating and shutting down. The problem was not present in Dapper but Feisty just would not work. So I read up a bit and the Gutsy kernel was mentioned as a fix. I tried the Gutsy kernel and the fans worked again so I ended up doing a distribution upgrade to Gutsy and all was well.

Although my problem was the total opposite to yours a similair fix might solve the problem. Just an idea.

---

### Post by schrankage on 2007-10-01
> **schrankage said:**
> [B][SIZE="2"]I'm trying to find a way to control the fans in my laptop, they run full speed whenever the laptop is on, and I have yet to find a way to regulate and manage them. It's a Fujitsu Lifebook N Series.

Anyone have any suggestions?[/SIZE][/B]

:popcorn:

**I found out what interface my fan controller uses, and unfortunatley it isn't supported by the kernel. Which is a shame, and being as the other day my laptop got so hot if I hadn't realized it it could have started a fire, I'm going to have to re-install XP, power management is too important not to work on a laptop.**

---

### Post by MissionImpossible on 2007-10-02
> **schrankage said:**
> **I found out what interface my fan controller uses, and unfortunatley it isn't supported by the kernel. Which is a shame, and being as the other day my laptop got so hot if I hadn't realized it it could have started a fire, I'm going to have to re-install XP, power management is too important not to work on a laptop.**

I would suggest SLED 10 Sp1 or openSUSE 10.2, they have the extra YAST Power Management Configuration Utility that may work for you. Set everything to "powersave" mode and then select "passive" cooling as an option. FYI: Support for the Yast Power Management utility has been dropped in openSUSE 10.3.

Cheers

PS: You can also try Fedora 7/8 Gnome using "Frequency Scaling Configuration Applet" to lock down a set frequency (if your cpu uses them), eg 800 Mhz. IMHO, this applet should be included in Ubuntu 7.10!!

---

