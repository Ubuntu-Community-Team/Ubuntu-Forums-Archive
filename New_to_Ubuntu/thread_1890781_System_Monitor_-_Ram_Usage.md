---
title: "System Monitor - Ram Usage"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by Glkanter on 2011-12-04
I added System Monitor to my top panel some time ago.

I have 8 GB in my PC, System Monitor reports it as 7.6 GiB and 7.7 GiB.

Right after booting up, the memory usage looks low. Then I open the System Monitor, and I could see my (user) memory usage is at about 7%. 0% swap. It doesn't graph Cache usage. With just this one instance of Firefox running, (user) memory is at 9.7%.

Over time -  and I open a lot of Firefox windows, maybe a spreadsheet and sometimes Google Earth - the memory display in the panel goes way up. (User) memory and cache each take up a quarter, or more, of the System Monitor memory display. The (user) memory will read in excess of 20%. I think swap always reads 0%.

I can't say I've had any problems. Does this seem normal?

---

### Post by 2F4U on 2011-12-04
If you have sufficient memory availabe, Linux attempts to cache as much as possible. When a program requests memory and there is not enough free memory available, Linux reduces the memory occupied by cached data. The reason behind this is that any unused RAM is wasted, therefore it will be used as cache, since that is faster than reading from the harddisk.

---

### Post by The Cog on 2011-12-04
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by Glkanter on 2011-12-04
[SIZE=2]You guys are the best!

This is what I needed to see: [/SIZE][SIZE=2]

```
glkanter@glkanter-System-Product-Name:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7749       1660       6089          0         96        517
-/+ buffers/cache:       1046       6703
Swap:         7934          0       7934
glkanter@glkanter-System-Product-Name:~$ 

```[/SIZE][SIZE=2]I'll mark this solved.[/SIZE]

---

