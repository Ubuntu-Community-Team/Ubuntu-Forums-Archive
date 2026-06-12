---
title: "Ubuntu on Silicon Graphics O2?"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by kb8wfh on 2013-04-27
I have a Silicon Graphics O2 workstation that boot up to its OS just fine. But I have no idea the user name and password. The place I got it from is long gone. 

Is it possible to load up Ubuntu on this platform? I have googled it but can't seem to find anything that says one way or another or how to do it if it can be done. 

I have messed with Ubuntu with a PC but no idea what the hardware is for the O2 or how to install it if its even possible. 

Any suggestions on where to go next would be great. Thanks.

M

---

### Post by DuckHook on 2013-04-27
It is not possible to load Ubuntu onto this box, but according to [Wikipedia]("http://en.wikipedia.org/wiki/SGI_O2"), you can apparently load Debian or Gentoo. However, it is almost certain that you would have to compile everything from source. If you are willing to leave Linux and go with Unix (which is the 'nix it was originally designed for) then there are ports available of OpenBSD or NetBSD. Unix will probably prove your best and easiest option. You will need to learn different commands, but it isn't that hard once you get the hang of things. If you load a familiar desktop like gnome onto either BSD, you will feel right at home for everyday use. I play around with both PCBSD and Solaris (sorry, no ports of either for SGIs, I'm afraid) on a VM and it's quite fun and educational. The Unix community is every bit as vibrant as the Linux one, although you must get used to the fact that it is even more eclectic and out-there.

The SGI uses a MIPS processor, which is very different from the architecture of Intel or AMD CPUs. If interested, Wiki and Google it. It's too bad that these architectures have been largely sidetracked by the 800 lb gorilla, Intel and its 400 lb challenger, AMD. There was a time that the CPU landscape, with PPC and Alpha, was more interesting than that of today's. But that's the way it goes I suppose.

I think you have a very cool and interesting project there, if you've got the time and inclination to get it working. If you proceed, do post back and let us know how you are getting on.

[Here's]("http://www.openbsd.org/sgi.html") the link to the OpenBSD download page.
[Here's]("http://www.netbsd.org/ports/sgimips/") the one for NetBSD.

---

### Post by diesch on 2013-04-27
Ubuntu doesn't work on MIPS. See [http://www.debian.org/ports/mips/](http://www.debian.org/ports/mips/) and [http://www.cyrius.com/debian/o2/](http://www.cyrius.com/debian/o2/) for how to use Debian on MIPS.

---

### Post by DuckHook on 2013-04-27
Thanks for link @diesch

@OP

If Debian has a port, and you are a new user and used to Ubuntu, then this is by far your best option. Almost all the command lines that you learn in Ubuntu will apply to Debian, since Ubuntu is based on Debian. You will have a far easier time learning how to use Debian than either of the BSDs, although unfortunately, this means that you will have to forego the opportunity to grow a long beard and wear tie-dye tee-shirts.

---

### Post by tgalati4 on 2013-04-27
Those O2 machines were quite fast in the day.  Keep us posted on what works and what doesn't.

---

### Post by DuckHook on 2013-04-27
> **tgalati4 said:**
> Those O2 machines were quite fast in the day.

At the RISC of hijacking the thread (very, very sorry :)), RISC architecture was (and still is) a fascinating technology, but their early purveyors like SGI made the, by now, classical business mistake of positioning it for elite, specialized and business use rather than the consumer market. At least it led to ARM which is doing it right, kicking butt and taking down names these days.

---

