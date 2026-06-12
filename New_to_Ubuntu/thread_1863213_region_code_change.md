---
title: "region code change"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by tikitikimaji on 2011-10-17
I've been trying to reset the region code for my external dvd player, but when I  follow everyone's directions for what to enter into terminal after I installed regionset, it keeps saying "error: Please ensure there is a readable cd or dvd in the drive."

But there is a DVD in the drive...

As much as I'd like to keep watching my black market bruce willis dvds from africa, I'd also like to watch some other things.

Thanks

---

### Post by tikitikimaji on 2011-10-17
figured it out.  For anyone else having trouble finding the mount point for their external dvd player, just enter 

mount|grep ^'/dev' 

into terminal, and it will spit out something like 

/dev/sr0 on /media/cdrom0

which you just copy and paste after the regionset command.

Thanks, good luck!

---

### Post by tikitikimaji on 2011-10-17
ok, it's still not working.  When I type in regionset in terminal, it gives me:

regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE

So I guess it's set for region 1, but movie player says cannot read from resource, and VLC won't play the movies either.

---

### Post by mc4man on 2011-10-17
run this in a terminal
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

When you open vlc > Media > Open Disc make sure _if need be_ to adjust the 'disc device' to correct /dev/

---

### Post by tikitikimaji on 2011-10-17
it works, thanks!!

---

