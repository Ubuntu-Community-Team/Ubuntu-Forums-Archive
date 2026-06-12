---
title: "Why do other Linux's boot faster?"
date: 2008-12-18
forum: Other OS Talk
---

### Post by Johnsie on 2008-12-18
When I got my eeepc it booted up and was usuable in about 8 seconds. about 10 seconds when I installed gnome.

So what is that makes the default Xandros boot so fast and is it possible for a user to do this with Ubuntu?

---

### Post by Vadi on 2008-12-18
Er... considered different hardware?

---

### Post by cookieofdoom on 2008-12-18
> **Johnsie said:**
> When I got my eeepc it booted up and was usuable in about 8 seconds. about 10 seconds when I installed gnome.

So what is that makes the default Xandros boot so fast and is it possible for a user to do this with Ubuntu?

Xandros is specifically designed for your eeePC. Thus it doesn't load a lot of unnecessary modules, drivers, etc. It's also much lighter in terms of software than Ubuntu is (as I understand it). I believe there are customised versions of Ubuntu for the eeePC that may be worth looking into.

---

### Post by fatality_uk on 2008-12-18
Not to sound harsh, but what the heck are you complaining about? I mean useable after about 10 seconds. Most of my Windows using office workers could only dream about a 10 second boot time.

---

### Post by Bachstelze on 2008-12-18
Moved to Other OS Talk.

---

### Post by logos34 on 2008-12-18
> **Johnsie said:**
> So what is that makes the default Xandros boot so fast and is it possible for a user to do this with Ubuntu?

you can run sys.rc.conf to disable unecessary programs from running at boot.

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

but I suspect that it's more a matter of the kernel not loading a lot of the stuff a default ubuntu setup does, as cookieofdoom said.  

here's the eee optimized ubuntu:

[http://www.ubuntu-eee.com/wiki/index.php5?title=Main_Page](http://www.ubuntu-eee.com/wiki/index.php5?title=Main_Page)

---

### Post by fistfullofroses on 2008-12-18
1. Services loaded during boot process
2. Init system chosen
3. Kernel size vs RAM size
4. Filesystem used
5. System Architecture
6. If initrd is used, its size can impact system performance as well

---

### Post by Johnsie on 2008-12-18
Thanks guys, I appreciate you're help.

---

### Post by ajcham on 2008-12-18
> **fatality_uk said:**
> Not to sound harsh, but what the heck are you complaining about? I mean useable after about 10 seconds. Most of my Windows using office workers could only dream about a 10 second boot time.

Frankly, you are being harsh.  There was no hint of complaint in the OP - it strikes me as mere curiosity as to the difference in boot times between different Linux installations. (ie. 8-10 secs on a Xandros-installed eee presumably in contrast to an unspecified boot-time for his Ubuntu desktop, which for me is approx. 40-45 secs)

---

