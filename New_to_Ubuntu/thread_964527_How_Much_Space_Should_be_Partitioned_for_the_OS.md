---
title: "How Much Space Should be Partitioned for the OS?"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by psyoptic on 2008-10-31
I'm about to go through with my first Ubuntu installation and was wondering what a good size for the OS or /root partition should be?

This is what I have down so far:

_250 gb hard drive (232 gb of actual space)_
200 gb for Windows XP (NTFS)
22 gb for / root for Ubuntu (ext3)
2 gb for swap 
8 gb for /home (ext 3)

I was thinking about shrinking the /root partition down to 15 gb and maybe increasing the size of the /home partition to 13 gb but I'm not so sure. Should I keep as much space as possible for the OS and put any data files on an external hard drive and just leave configuration settings on the /home partition? 

I'm assuming that the bulk of /home files would be data files and that configuration files don't leave a large footprint. I'd appreciate any thoughts or advice on this.

---

### Post by InfinityCircuit on 2008-10-31
You will probably never need more than 10G for /.  Personally I use 4G for / with no issues, including maintaining a cowbuilder chroot in /var.

---

### Post by hellion0 on 2008-10-31
As a rule, I run 10GB for / and the rest of it (that isn't already taken up by Windows) for /home. Rarely, if ever, do you need more than 10GB on a root partition. The only exception is if you use a lot of giant apps or if you burn lots of dual-layer DVDs (which may use a good deal of space in /tmp), then you may need more.

---

### Post by Zzl1xndd on 2008-10-31
I have 30gigs, but I have a Tera byte drive so I can spare the extra.

---

### Post by bumanie on 2008-10-31
Usually 8-10gb is ample for / and 1-2gb for swap - you can use the extra 10-12gb for /home. If it were me, I'd steal a little more off windows to make /home a little larger.

---

### Post by Nepherte on 2008-10-31
[LIST]
[*]root : 12Gb should be enough
[*]swap: If you have 512Mb ram or less, take 2 x ram. If you have 1024 ram, you can take the amount of ram for your swap. If you have more ram, then you basically don't need a swap but some distributions have issues with it, so perhaps it is better to take a swap. If you want to use suspend, you'll need at least the amount of your ram as swap and you sure want to take a margin of 15% extra.
[*]home: this is totally up to you[/LIST]

---

### Post by Paqman on 2008-10-31
> **bumanie said:**
> If it were me, I'd steal a little more off windows to make /home a little larger.

So would I. Extra space in /home is useful, since a lot of stuff like Windows apps (installed through Wine) and virtual machines will eat up big chunks of space in /home.

The only time you'll need tons of space in / is if you're doing anything that creates massive temporary files, such as copying DVDs. If you can see yourself doing that then 15-20GB would be handy, otherwise 10GB is fine.

---

### Post by PierreDeKat on 2008-10-31
One thing you want to plan for is any media you might want to work with. 

For instance, a dual-layer DVD ISO can run up around 8.5 gb and a blu-ray disk ISO might be up around 50 gb.

The point being, if you have a 20 gb /root or /home partition, you're sure not going to be able to drop a 50 gb file there.

Me, I've got a roughly 20 gb Windows partition, a roughly 20 gb /root partition, a minuscule /swap partition that I have little use for with 2 gb of memory, and a 250 gb NTFS partition that Windows and Ubuntu share.

---

### Post by redbob on 2008-10-31
I ought to partition my Disc by this way:
20gb to /, 20gb to Home, 1gb to swap and the rest for opt. 
If you have just one user account you could decrease home space. In my case, my desktops have five users, so 20gb to home is not so large.

---

