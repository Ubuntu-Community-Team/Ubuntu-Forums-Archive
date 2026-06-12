---
title: "Why /proc has nosuid mount option"
date: 2018-05-15
forum: New to Ubuntu
---

### Post by chengpan on 2018-05-15
[COLOR=#242729][FONT=Arial]I notice /proc and /dev is mounted differently on ubuntu than other linux distribution as follows:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Ubuntu:[/FONT][/COLOR]
[INDENT][FONT=inherit]udev on /dev type devtmpfs (rw,nosuid,relatime,size=4079136k,nr_inodes=1019784,mode=755) proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)[/FONT]
[/INDENT][COLOR=#242729][FONT=Arial]ALinux:[/FONT][/COLOR]
[INDENT][FONT=inherit]devtmpfs on /dev type devtmpfs (rw,relatime,size=1015576k,nr_inodes=253894,mode=755) proc on /proc type proc (rw,relatime)[/FONT]
[/INDENT][COLOR=#242729][FONT=Arial]I know nosuid is a security option to disallow files that contain setuid flag. But isn't /proc is a virtual file system already, and /proc serves as a interface to query kernal information. Why is /proc still needed to be mounted with **nosuid**? Similarly to /dev.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Please let me know.[/FONT][/COLOR]

---

### Post by TheFu on 2018-05-15
Belts AND suspenders.

---

### Post by kerry_s on 2018-05-15
apples AND oranges

---

### Post by kerry_s on 2018-05-15
sorry, couldn't help myself. fu did it first.

comparing the way 1 distro is different from another is silly. they all do it there own way.

> ALinux:
devtmpfs on /dev type devtmpfs (rw,relatime,size=1015576k,nr_inodes=253894,mode=7 55) proc on /proc type proc (rw,relatime)

is mounted in ram using devtmpfs

> Ubuntu:
udev on /dev type devtmpfs (rw,nosuid,relatime,size=4079136k,nr_inodes=101978 4,mode=755) proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)

is mounting a location into ram using udev

different ways of doing the same thing.

---

### Post by TheFu on 2018-05-16
> **TheFu said:**
> Belts AND suspenders.

Actually, my meaning was that to hold your pants up (pants in the US form, not UK), that having 2 methods is good.  Both noexec AND nosuid mount options. This is a common theme throughout Unix security. Never trust just 1 level of protection, always have 2+, just in case 1 fails.

---

