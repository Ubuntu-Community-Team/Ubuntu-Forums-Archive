---
title: "[SOLVED] deleting log files"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by rockerphil on 2008-10-29
ok, here's the deal. i'm currently working with minimal HDD space (a little under 50 GB), so i'm always looking for ways to free up space. so i started poking around and i'm wondering if it's safe to delete everything in /var/log, and if not, what IS safe to delete. also, any other suggestions on safely freeing up HDD space is greatly appreciated. so far i know of these commands:

```
sudo apt-get autoremove
sudo apt-get autoclean
```

much thanks in advance,

Phil

---

### Post by aktiwers on 2008-10-29
Also try:
```
sudo apt-get clean
```

Which clears apts cache entirely.

Also look here how to free space.. logfiles are text files and does not require much space.

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

### Post by handydan918 on 2008-10-29
> **rockerphil said:**
> ok, here's the deal. i'm currently working with minimal HDD space (a little under 50 GB), so i'm always looking for ways to free up space. so i started poking around and i'm wondering if it's safe to delete everything in /var/log, and if not, what IS safe to delete. also, any other suggestions on safely freeing up HDD space is greatly appreciated. so far i know of these commands:

```
sudo apt-get autoremove
sudo apt-get autoclean
```

much thanks in advance,

Phil

First, I'd be surprised to see you free up as much as 2 GB of space from dumping logfiles. 
Second, if you insist on doing this, be aware that many of the files in question are system files, and as such are owned by root. This means invoking the hazardous rm command with root privileges. 

Personally, I'd look into log rotation or some other option to keep the size down. 

Or better yet, install /var on it's own (smallish) partition, like the real sysadmins do...:lolflag:

---

### Post by gcbzzzz on 2010-09-24
> **handydan918 said:**
> First, I'd be surprised to see you free up as much as 2 GB of space from dumping logfiles. 
Second, if you insist on doing this, be aware that many of the files in question are system files, and as such are owned by root. This means invoking the hazardous rm command with root privileges. 

Personally, I'd look into log rotation or some other option to keep the size down. 

Or better yet, install /var on it's own (smallish) partition, like the real sysadmins do...:lolflag:

i need some small 100mb to do the system update on a netbook with SSDs (hell will freeze before i waste even 10mb for a var partition :)

even after aptitude autoclean i still have 30M on /var/cache/apt and 40M on /var/logs

---

### Post by gcbzzzz on 2010-09-24
> **handydan918 said:**
> First, I'd be surprised to see you free up as much as 2 GB of space from dumping logfiles. 
Second, if you insist on doing this, be aware that many of the files in question are system files, and as such are owned by root. This means invoking the hazardous rm command with root privileges. 

Personally, I'd look into log rotation or some other option to keep the size down. 

Or better yet, install /var on it's own (smallish) partition, like the real sysadmins do...:lolflag:

i need some small 100mb to do the system update on a netbook with SSDs (hell will freeze before i waste even 10mb for a var partition :)

even after aptitude autoclean i still have 30M on /var/cache/apt and 40M on /var/logs


Anyway, what i got away with was:

sudo aptitude remove --purge 2.6.31-10\*
Got 689Mb freed by this.

it will remove all the 2.6.31.1[0-9] packages that you have lying around (i'm still unsure why aptitude treats 0* as .* in it's regexp)

Just make sure you are not using any of those kernels :)

uname -r will show you the current one. i'm on .22 and left .20 and .21 there too.

---

### Post by QLee on 2010-09-24
[QUOTE=gcbzzzz]i need some small 100mb to do the system update on a netbook with SSDs (hell will freeze before i waste even 10mb for a var partition :)

even after aptitude autoclean i still have 30M on /var/cache/apt and 40M on /var/logs[/QUOTE]
autoclean deletes only the ones that are no longer available for download.

clean deletes all the packages in the cache.

If I found 40MB of files in my /var/log, rather than wanting to delete them, I would want to investigate what was dropping all the errors. But, you may do as you choose.

---

### Post by afrodeity on 2011-02-14
i have 158M sitting in /var/mail

---

