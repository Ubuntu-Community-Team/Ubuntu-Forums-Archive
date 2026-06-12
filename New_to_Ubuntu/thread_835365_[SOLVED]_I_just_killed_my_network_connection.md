---
title: "[SOLVED] I just killed my network connection"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by drunkardivan on 2008-06-20
OK, running Hardy on a Dell Vostro 1000 with a Broadcom BCM4310 card.

I was really struggling to get wireless up and running, was having no luck with ndiswrapper, and was generally getting frustrated. So, I installed Wicd. 

That was a mistake. Now, I can't connect via ethernet, and my Wifi light on my box has gone off. When I enter ifconfig in terminal, I get this:
```

 lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:312 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:312 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:15600 (15.2 KB)  TX bytes:15600 (15.2 KB)

```

What have I done? And what can I do from here?

---

### Post by drunkardivan on 2008-06-20
Oh, and just to clarify, it's not my primary laptop, so it's not an absolute emergency. I also have a 2 GB thumb drive, if I need to download something and transfer it over, I have that capability... as long as it's nothing larger than 2 gigs, obviously.

---

### Post by drunkardivan on 2008-06-20
Figured out a solution... kinda.

I rebooted with the Live CD, used gparted to wipe my Ubuntu partition, installed Hardy 64 to "largest contiguous free space", opened up the software repositories, updated, enabled the restricted drivers, and now I have wireless.

It's an inelegant solution, and I wouldn't recommend it to anyone who had been using their Ubuntu partition longer than a few hours, but it was effective.

---

