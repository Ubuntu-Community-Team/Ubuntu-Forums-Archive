---
title: "Launching HTTP cache cleaner"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Gonz_91 on 2008-09-13
Hi fellow 'buntu lovers ;)

I've been noticing sometimes the appearance of a taskbar item named "Launching HTTP cache cleaner", which sits there for a while, and then just goes away.


Can anyone provide some more info, please?

Thank you all very much :D

---

### Post by ptn107 on 2008-09-13
I think it's associated with KDE.  GNOME is my desktop environment, and I sometimes see that at the bottom on my panel when I'm working with KDE programs.

---

### Post by IntuitiveNipple on 2008-09-13
When you've got Apache web-server utilities installed (apache2-utils) it will set up a cron job to run /usr/sbin/htcacheclean to check and clean the apache **mod_cache_disk** directories. This is to prevent them consuming all available disk space since the apache cache module don't check disk space during caching to ensure it is as fast as possible.

If apache isn't using mod_cache_disk, or the cache is almost empty, htcacheclean will run for a short time and then exit. If there was an active cache you'd know about it since when htcacheclean runs it can slow the PC down to a crawl because of disk access contention.

---

### Post by ptn107 on 2008-09-13
I do not have apache stuff installed, and nothing in my crontab files (for myself or root).  I see the cache cleaner box come up occasionally when Amarok is running.

Update:
I see what you mean though.  I found the script 'apache2' in my /etc/cron.daily/ that apparently cleans out /var/cache/apache2/mod_disk_cache.  However I do not have apache installed.

---

### Post by Gonz_91 on 2008-09-15
> **ptn107 said:**
> I do not have apache stuff installed, and nothing in my crontab files (for myself or root).  I see the cache cleaner box come up occasionally when Amarok is running.


This is exactly what happens to me

:)

---

### Post by Darkshade on 2008-10-30
That happens when you use KDE programs in GNOME (like Amarok in the most common case).

Solution: [http://ubuntuforums.org/showthread.php?t=962982](http://ubuntuforums.org/showthread.php?t=962982)

---

