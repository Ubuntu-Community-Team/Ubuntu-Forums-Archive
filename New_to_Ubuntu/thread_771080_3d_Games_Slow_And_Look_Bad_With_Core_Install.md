---
title: "3d Games Slow And Look Bad With Core Install"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by ChompTheMan on 2008-04-27
Hello.  I've upgraded to Hardy and decided to do a command line base install with x-window-system-core and kde-core this time around.  While I've managed to get everything working the way I want I can't figure out why 3d games work so horribly.  The graphics look bad and the games are realy slow and laggy-like.  They worked fine with Gutsy, which was a regular install, so I must be missing something?  I have an Intel 965 chipset with the intel(i810) driver.

---

### Post by ChompTheMan on 2008-04-28
Bump

---

### Post by stchman on 2008-04-28
> **ChompTheMan said:**
> Hello.  I've upgraded to Hardy and decided to do a command line base install with x-window-system-core and kde-core this time around.  While I've managed to get everything working the way I want I can't figure out why 3d games work so horribly.  The graphics look bad and the games are realy slow and laggy-like.  They worked fine with Gutsy, which was a regular install, so I must be missing something?  I have an Intel 965 chipset with the intel(i810) driver.

The video produced by the 965 is not going to be very good for 3D games.  The 965 will play the older games from like 2002 and earlier but not the newer stuff.

Nvidia is a much better choice for a gaming card.

---

### Post by ChompTheMan on 2008-04-28
I know the 965 isn't very good for games.  However, games like Super Tux Cart and Nexuiz worked fine in Kubuntu Gutsty, so I am assuming there's something I am missing because I did a core install rather than a regular install.

---

### Post by stchman on 2008-04-29
> **ChompTheMan said:**
> I know the 965 isn't very good for games.  However, games like Super Tux Cart and Nexuiz worked fine in Kubuntu Gutsty, so I am assuming there's something I am missing because I did a core install rather than a regular install.

Are you using WINE?  I like to game as well so that is the reason I leave XP on my computer.  XP for gaming, Ubuntu for everything else.

---

### Post by ChompTheMan on 2008-04-29
I don't use wine for video games.  My problem is 3d linux games that worked perfectly fine in Gutsy Gibbon are now crap and barely function in Hardy Heron.  I'm willing to bet that if I did a regular install things would fine.  However, since I did a base install this time around I must be missing something.  Or it's a bug.  I can't stress enough that I didn't have this problem in Gutsy.  3d games worked fine in Gutsy.

---

### Post by ChompTheMan on 2008-05-03
I solved my problem so I thought I would post the solution here in case anyone else has the same problem.

```
sudo apt-get install libgl1-mesa-dri libglide3
```

---

