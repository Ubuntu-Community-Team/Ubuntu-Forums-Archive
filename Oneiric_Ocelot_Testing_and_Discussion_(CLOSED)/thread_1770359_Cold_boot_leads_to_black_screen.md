---
title: "Cold boot leads to black screen"
date: 2011-05-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-05-29
I don't turn off my laptop very often I usually either leave it on or suspend it.
I've found though that twice this week when the laptop has been turned off for a few hours and I come to cold boot it everything proceeds normally up to the point of the login screen appearing.
I get just a black screen with a pointer. The pointer is movable and the disc actuivity light goes on and off. There is no panel or anything. 
It's as if everything is normal except it forgot to load the graphics :-)
At this point ctrl+alt+f1/f2 do nothing, ctrl+alt+del does nothing. I have to REISUB and on reboot everything is fine.
This is on my gnome3/gnome-shell OO install.
This has happened 3 times in the last 10 days or so.
It only happens from a cold boot.
Anybody seeing anything similar?

---

### Post by Harry33 on 2011-05-29
> **Quackers said:**
> I don't turn off my laptop very often I usually either leave it on or suspend it.
I've found though that twice this week when the laptop has been turned off for a few hours and I come to cold boot it everything proceeds normally up to the point of the login screen appearing.
I get just a black screen with a pointer. The pointer is movable and the disc actuivity light goes on and off. There is no panel or anything. 
It's as if everything is normal except it forgot to load the graphics :-)
At this point ctrl+alt+f1/f2 do nothing, ctrl+alt+del does nothing. I have to REISUB and on reboot everything is fine.
This is on my gnome3/gnome-shell OO install.
This has happened 3 times in the last 10 days or so.
It only happens from a cold boot.
Anybody seeing anything similar?

Right, It happens every now and then, but not so often that mentioned.
I think gdm does not start properly then. For me it is also SysRq R-E-I-S-U-B that only helps.

---

### Post by Quackers on 2011-05-29
Thanks for that confirmation Harry33.
That's it, exactly. Only on a cold boot and only now and again.
I also just remembered something from about 2 weeks ago. On one cold boot gdm took about 3 minutes to start. I have a conky display, which shows the cpu usage, and on that occasion it had both processors pegged at 100%, but the system was usable.
System monitor showed nothing unusual, but top showed that gdm was using all the cpu. I rebooted and all was fine.
So, I'm sure you are right about it being a gdm problem.

---

### Post by ronacc on 2011-05-29
I ran into that for awhile in NN , haven't  had it in OO yet .

---

### Post by lucazade on 2011-05-29
> **ronacc said:**
> I ran into that for awhile in NN , haven't  had it in OO yet .

I can confirm ronacc`s experience. IIRC it was due to a wrong identification of motherboard brand and pci slots by the kernel.. There were more info in a old thread in natty forum section.

---

### Post by Quackers on 2011-05-29
> **lucazade said:**
> I can confirm ronacc`s experience. IIRC it was due to a wrong identification of motherboard brand and pci slots by the kernel.. There were more info in a old thread in natty forum section.

Interesting, thanks :-)

---

### Post by lucazade on 2011-05-29
> **Quackers said:**
> Interesting, thanks :-)

Tried to search that old thread but without success.. althought re-reading your report is probably different because the one i'm referring was a kernel panic on a cold boot.

---

### Post by Harry33 on 2011-05-29
Just remembered one more thing.
I am currently using new gdm (v. 3.0.2) from Gnome3 PPA.
That gdm fails more often than the GTK+2 version.

---

### Post by Quackers on 2011-05-30
I'm using gdm 3.0.2-0ubuntu1

---

### Post by dino99 on 2011-05-30
looks at changes with:

sudo update-usbids && sudo update-pciids

---

### Post by Harry33 on 2011-05-30
> **Quackers said:**
> I'm using gdm 3.0.2-0ubuntu1

Yes, and from the Gnome3 PPA (which is, however, build for Natty)?
In Oneiric repos the newest version is 2.32.1-0ubuntu4.
And it just may be that Oneiric will switch to LightDM. there already is the version 0.3.5 in official repos.

Anyway, that is exactly the version of Gdm, that sometimes gets stuck.

---

### Post by Quackers on 2011-05-30
Ok thanks Harry. (Yes it's from the gnome3team.ppa)
I'll be watching :-)

---

### Post by Harry33 on 2011-05-30
> **Quackers said:**
> Ok thanks Harry. (Yes it's from the gnome3team.ppa)
I'll be watching :-)

Yes I have that gdm version myself too. It works well, only occasional probelms but rebooting always helps.

---

### Post by Quackers on 2011-06-16
This "problem" has disappeared for the last week or so.
Cold boots and reboots have been faultless in that time.
However after yesterday's and today's updates on reboot evrything loads as it should do except that the desktop is empty, having no top panel and cairo dock has a black box round it and conky reports that one cpu is maxed out at 100%.
On entering top in terminal it shows that gdm is using 100%cpu.
On REISUBing things return to normal next time.
This is happening every second boot/reboot, or has been today.
This is still using OO/gnome-shell.

---

### Post by Harry33 on 2011-06-16
> **Quackers said:**
> This "problem" has disappeared for the last week or so.
Cold boots and reboots have been faultless in that time.
However after yesterday's and today's updates on reboot evrything loads as it should do except that the desktop is empty, having no top panel and cairo dock has a black box round it and conky reports that one cpu is maxed out at 100%.
On entering top in terminal it shows that gdm is using 100%cpu.
On REISUBing things return to normal next time.
This is happening every second boot/reboot, or has been today.
This is still using OO/gnome-shell.

What if you switch to LightDM.
I have used it more than a week now without any issues.
I also have removed (purged) the Gdm from my system.

---

### Post by Quackers on 2011-06-16
Lol, if I have lightdm installed it was by accident :-)
I can't use Unity on this sytem but I can go to Classic, which is fine.
I'm very happy with gnome-shell and haven't really tried anything else.

---

### Post by Harry33 on 2011-06-16
> **Quackers said:**
> Lol, if I have lightdm installed it was by accident :-)
I can't use Unity on this sytem but I can go to Classic, which is fine.
I'm very happy with gnome-shell and haven't really tried anything else.

I use only Gnome-shell with the fallback option Gnome-panel.
And LightDM.

---

### Post by Quackers on 2011-06-16
Thanks again, Harry33. I'll see if things develop over the next couple of days.
With a few spare moments I'll look at LightDM too :-)

---

### Post by jfernyhough on 2011-06-16
I've got exactly the same issue on my 1749 - glad it's not just me!

I put it down to an incompatibility with the natty GNOME3 team packages, but it only happens when I run kernel 3.0 - if I boot with 2.6.39 I can log in fine using GDM. For me, LightDM combined with kernel 3.0 also ends up with a stalled login.

I'm downloading and installing 3.0-1 now and will see if that makes any difference.

On my 311c (running Natty but with GNOME3) I've found that gnome-session-daemon sometimes runs at 100% CPU. It will let me reboot, though.

---

### Post by Quackers on 2011-06-16
Hokey cokey :-)  Let us know please, thanks.

---

### Post by jfernyhough on 2011-06-16
Nope, same thing, though I also did an update-usbids. It does get a little further, but then as soon as I press a key it freezes. I think the system is still running as the HDD is active, but X is definitely unresponsive.

Hmm.

---

### Post by Quackers on 2011-06-16
Ah, not what we'd hoped then!
Perseverance (and multiple boots) is the key for the moment :-)

---

### Post by jfernyhough on 2011-06-20
After spending a while searching around I haven't found many solutions to this, other than a clean install. So I grabbed a Daily oneiric LiveCD, reinstalled, and everything works.

I reckon there were a few packages hanging around from previous releases (seeing as I haven't clean installed since... karmic? lucid?) and these likely created a problem. Not ideal as it's pretty much impossible to reproduce.

I had to use x-edgers for mesa packages that allow fglrx to install, but other than that all is good.

Oh, apart from having to create a link to applications.menu after installing gnome-panel so I had an applications menu in GNOME:

$ sudo ln -s /etc/xdg/menus/gnome-applications.menu /etc/xdg/menus/applications.menu

---

### Post by jerrylamos on 2011-06-20
The "dread update" strikes again??  

I always have other partitions with Narwhal, Meerkat, Lynx, etc. and I do run Ocelot live before trying an install.  BTW I've installed 19 June daily build on a netbook, a laptop, and a desktop O.K. Two of the instgalls were on USB hard drives - left over laptop hard drive in a $10 or $20 case.  

On Alpha's I've had Install wipe out my hard drives when there was a screw up on partitioning, or Grub either fails on boot or fouls up the boot menu.

Usually somewhere in Alpha the "dread update" strikes & I do a re-install.

Running O.K. at the moment, occasional crash, bring on the next dread update!

Jerry

---

