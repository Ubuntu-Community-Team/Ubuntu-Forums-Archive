---
title: "[SOLVED] Hardy x86 or Hardy 64?"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by KonaBean on 2008-06-18
I installed Ubuntu a while ago as a standalone OS on a new drive. (Grub allows a dualboot of XP on another drive). But, I realized only days ago that I forgot to install the 64-bit version of Ubuntu on my AMD 64 system. It works fine, despite a few hiccups that I managed to fix. I know I should switch to 64, its a pity not to, but my original install of the OS and peripherals was pretty rough. I would hate to do that again. Does anyone know if there is anyway to switch to the 64-bit version without a complete reinstall? Or do I have to just bite the bullet?

---

### Post by phoenix_abhi on 2008-06-18
No way, but I prefer x64 over x86. No problem except Java. I believe u have to do a fresh install

---

### Post by phidia on 2008-06-18
Yeah Phoenix is right there's no way AFAIK to upgrade from x86 to x86_64.
You will find plenty of help with whatever you need at the forum specific to [ubuntu 64bit]("http://ubuntuforums.org/forumdisplay.php?f=343") should you 
decide to make the leap. Good luck and hope that's useful.

---

### Post by wolfen69 on 2008-06-18
unless you're doing *serious* number crunching tasks, you will notice no difference, speed wise. i did side by side testing and there was no noticable difference in speed. if you are doing hardcore video editing, or transcoding huge files, then *maybe* it will help. i feel there is no benefit to using 64bit at this point.

---

### Post by KonaBean on 2008-06-18
Thanks for the feedback, phoenix, phidia and wolfen! I thought so. I had to hope though...

---

### Post by Pepperoni on 2008-06-18
I did a similar thing.  I started to do an install and accidentally used the x86 version.  I continued on anyway.  Then after it was done, I saw that my RAM was 3.2gigs instead of 4gigs.  It probably doesn't matter either way, but that just stuck in my craw.  I decided to re-do everything as x64.  It would be nice to do an in place switch, but I don't think that's possible.  You'd have to re-install the OS.  

My advice is to look at what you have setup and decide if you can live with it.  If everything works OK and you have less than 4gb RAM, then leave it.  Otherwise I would do it now before you get too far in.

---

### Post by stchman on 2008-06-18
> **KonaBean said:**
> I installed Ubuntu a while ago as a standalone OS on a new drive. (Grub allows a dualboot of XP on another drive). But, I realized only days ago that I forgot to install the 64-bit version of Ubuntu on my AMD 64 system. It works fine, despite a few hiccups that I managed to fix. I know I should switch to 64, its a pity not to, but my original install of the OS and peripherals was pretty rough. I would hate to do that again. Does anyone know if there is anyway to switch to the 64-bit version without a complete reinstall? Or do I have to just bite the bullet?

You have to do a complete fresh reinstall.  The 64 bit uses a completely different kernel than the 32 bit.  Fresh reinstalls are actually pretty quick so it is a no factor.

I have Hardy 64 installed on my Athlon 64 machine and everything runs perfectly except Java.

If you never visit any websites that use Java plugin then it is a non factor.  All the other Sun Java 6 packages (JDK, JRE) are 64 bit compatible.  So if you write java applications then you can use Sun Java no problem.  The plugin for Sun Java 6 is not compatible with 64 bit although there is rumors on this forum that Sun is going to make a 64 bit browser plugin this July.

I used Icedtea for my Java plugin and it works on most sites but not other.

As far as performance I don't think you will see a difference in performance unless you do something that need a lot of memory (>4GB) ro something that really needs to crunch number and uses very large arrays.

I have read that there is a up to 30% performance improvement in using 64 bit Ubuntu over 32.  I put it on my Athlon 64 machine just because I wanted to see what it was all about.

To tell you the truth if Sun Java worked perfectly I would use it on my Core 2 desktop and laptop just out of principle.

---

