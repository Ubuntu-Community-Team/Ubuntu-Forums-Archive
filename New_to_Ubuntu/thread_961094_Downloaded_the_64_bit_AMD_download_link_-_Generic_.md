---
title: "Downloaded the 64 bit AMD download link - Generic is installed"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by Bif Powell on 2008-10-28
Hi, I can't seem to get 64 bit ubuntu to load.  This is an AMD64 CPU so I downloaded the desktop edition, 64 bit AMD link from this page:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

I then burned that iso to a CD and booted from that and installed from it.  When I do uname -r I get:

2.6.24-19-generic

Now I did install it from a running install of Ubuntu but it was generic which is why I was doing it again...could my new install (even through it was from the 64 bit iso) have seen the generic kernel and used that instead of getting it from the new CD?

Is there anything else that might be causing this?
Is there more I can do to find out exactly what processor I have?

Thanks.

---

### Post by zvacet on 2008-10-28
```
uname -a
```

---

### Post by jerome1232 on 2008-10-28
You always get the generic kernel what's different between amd64 and i386 is this part
```
uname -m
```


that'll be i686 if you 32-bit x86_64 if your 64-bit

edit: If you want more info about your cpu then these can help, after the last one use
```
cat /proc/cpuinfo
sudo lshw -html > sysinfo.html
firefox sysinfo.html
```

---

### Post by Xiong Chiamiov on 2008-10-28
The generic kernel is what you what - it means you didn't compile it with any special options.  You can see from uname -m (or uname -a) that you're running 64-bit instead of i386, i686, or whatever.

---

### Post by Bif Powell on 2008-10-28
SOLVED!

Also, for posterity, here's what uname -m gives me

x86_64

Thanks!

---

