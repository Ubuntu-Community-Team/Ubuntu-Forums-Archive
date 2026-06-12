---
title: "Error Booting Up - Ubuntu Server"
date: 2015-12-22
forum: New to Ubuntu
---

### Post by pantera989 on 2015-12-22
Hi guys,

On booting up my computer it just stops at the following line:

```
EXT4-fs (sda1): Mounted filesystem without journal. Opts: (null)
```

[[img]https://farm6.staticflickr.com/5764/23832009081_20ef828f9d_b.jpg[/img]](https://flic.kr/p/CiXh1i)

It's an Ubuntu LAMP Server for running ZoneMinder (Security Camera Software) and has been running fine since I installed it abut a month ago. I shut it down to move it today and upon restarting it it just sits at the above line. I set it all up following an guide, and only really understood half of what I was doing.

---

### Post by DuckHook on 2015-12-26
Could be any number of things:

1. The issue may not actually have anything to do with your file system and chokes on the next item that would have shown up after file system mount. If the issue is actually file system related, then,

2. The inode is corrupt, or

3. The filesystem headers are corrupt, especially if you formatted sda1 using EXT4 in view of it now returning EXT2 mode, or

4. You have a failing HDD.

These are only the most likely suspects though other causes are too numerous to list.

You will need to boot up using a Live DVD/USB and do fsck. The best utility is actually e2fsck. Look at man pages for either. This has a good chance of diagnosing the issue and then running the proper fix. If fixed, it is critical to back up your data so that further failures do not leave you hooped. If you already back up your data, then you are sitting pretty. If not, then this is a good example of why we old-timers constantly harp about backups.

---

