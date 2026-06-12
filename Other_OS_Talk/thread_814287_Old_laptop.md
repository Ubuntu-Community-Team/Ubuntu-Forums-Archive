---
title: "Old laptop"
date: 2008-05-31
forum: Other OS Talk
---

### Post by grjemo on 2008-05-31
What would be the best distro to use on an old laptop with only 32mb of RAM and about a 2gb hard drive? It has no internet (yet).

I know there are threads on this but, they talk more about space rather than RAM.

---

### Post by LaRoza on 2008-05-31
What do you plan to do with it?

If it is just going to be a mobile web device, you can get the lightest possible setup, install a light WM and run a light browser.

---

### Post by darrelljon on 2008-05-31
Yeah, the size of the compressed image is relatively easy to measure and compare.
Memory usage/consumption would be more suitable but is much harder to measure and compare. I can only imagine having to install each distro then getting conky, then recording the result, though someone may get round to attempting it sometime. In the meantime the size of the compressed image, the experiences of users and some other factors is a good yardstick which I use with a view to guiding users of old machines.

Try Damn Small Linux.

---

### Post by LaRoza on 2008-05-31
The size of the hard drive is likely less of a problem. The RAM is the biggest limitation.

If you are already familiar with Ubuntu or Debian, you could do a base install of Debian (which I think would work) and install and use a very light window manager like Ratpoison (read up on how to use it first), and a lighter browser, perhaps Opera.

---

### Post by regomodo on 2008-05-31
> **LaRoza said:**
> The size of the hard drive is likely less of a problem. The RAM is the biggest limitation.

If you are already familiar with Ubuntu or Debian, you could do a base install of Debian (which I think would work) and install and use a very light window manager like Ratpoison (read up on how to use it first), and a lighter browser, perhaps Opera.

opera is pretty big. With 32MB you are looking at Galeon, Dillo, or kazehase.

---

### Post by LaRoza on 2008-05-31
> **regomodo said:**
> opera is pretty big. With 32MB you are looking at Galeon, Dillo, or kazehase.

Opera isn't that big.

---

### Post by grjemo on 2008-05-31
> **LaRoza said:**
> What do you plan to do with it?

If it is just going to be a mobile web device, you can get the lightest possible setup, install a light WM and run a light browser.

I'm looking to use it as something to just mess around with; I really don't care what happens to it.  I wont be using a browser, as there is no wireless OR Ethernet, but if I ever purchase an Ethernet card, I wouldn't use Opera, as it is closed source, so it won't be as good for experimenting.

---

### Post by LaRoza on 2008-05-31
> **grjemo said:**
> I'm looking to use it as something to just mess around with; I really don't care what happens to it.  I wont be using a browser, as there is no wireless OR Ethernet, but if I ever purchase an Ethernet card, I wouldn't use Opera, as it is closed source, so it won't be as good for experimenting.

Well, Firefox has been "experimented" to the point of breaking seams...

I guess you can try any distro in the sticky. Perhaps Arch might be worth trying.

---

### Post by grjemo on 2008-05-31
> **darrelljon said:**
> Try Damn Small Linux.

According to [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/), 128mb of RAM is needed.

---

### Post by ladr0n on 2008-05-31
If you just want to play around with it, I would recommend using a distro that allows you to build your system from the ground up.  This allows you to a) learn a lot more about how your system works and b) customize your system to run more efficiently on such a low-end machine.  A great distro for this is Arch.  Not only will Arch let you build your system exactly the way you want it, their wiki is very helpful and will guide you through the process of setting everything up.

---

### Post by grjemo on 2008-06-01
> **ladr0n said:**
> If you just want to play around with it, I would recommend using a distro that allows you to build your system from the ground up.  This allows you to a) learn a lot more about how your system works and b) customize your system to run more efficiently on such a low-end machine.  A great distro for this is Arch.  Not only will Arch let you build your system exactly the way you want it, their wiki is very helpful and will guide you through the process of setting everything up.

Arch needs Pentium II. This laptop (Thinkpad 385XD) has a pentium.

---

### Post by msrinath80 on 2008-06-01
If you're comfortable building things from source, try Linux From Scratch ([http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/))

---

### Post by jrusso2 on 2008-06-01
This says it works on at least 32 mb of ram and an Pentium MMX CPU

[http://www.delilinux.org/wiki/doku.php?id=announcement:generalnews:releases:deli-0.8.0](http://www.delilinux.org/wiki/doku.php?id=announcement:generalnews:releases:deli-0.8.0)

---

### Post by altariel on 2008-06-01
DeLi Linux? 
Has come out with a new version lately 
and should work with your 32 MB RAM (the new lowest RAM they recommend)

be aware though that they advise to create some swap space BEFORE INSTALLING if you have less than 48 MB of RAM!

[http://www.delilinux.de/](http://www.delilinux.de/)
[http://www.delilinux.org/wiki/doku.php?id=english:news](http://www.delilinux.org/wiki/doku.php?id=english:news)
[http://www.delilinux.org/wiki/doku.php?id=announcement:generalnews:releases:deli-0.8.0](http://www.delilinux.org/wiki/doku.php?id=announcement:generalnews:releases:deli-0.8.0)

---

### Post by regomodo on 2008-06-01
> **grjemo said:**
> According to [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/), 128mb of RAM is needed.

That is only required if you want to load the entire OS into ram. If you don't want to do that 32MB is fine.

---

### Post by darrelljon on 2008-06-01
> **regomodo said:**
> That is only required if you want to load the entire OS into ram. If you don't want to do that 32MB is fine. [The actual minimum system requirements for DSL]("http://www.damnsmalllinux.org/wiki/index.php/FAQ#Will_DSL_ever_get_bigger_than_50_MBytes.3F") with X-Windows state i486 CPU and 24Mb RAM.

---

### Post by Bungo Pony on 2008-06-02
DSL works fine with 36M of RAM on my P133, along with a 1.2G hard drive.

---

### Post by mips on 2008-06-03
> **grjemo said:**
> Arch needs Pentium II. This laptop (Thinkpad 385XD) has a pentium.

I think there is a version of Arch that does not require i686, or was that slax?

---

