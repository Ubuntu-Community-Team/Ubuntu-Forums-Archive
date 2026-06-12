---
title: "Ubuntu running slow"
date: 2016-03-18
forum: New to Ubuntu
---

### Post by Christian_Smith on 2016-03-18
Hello. I work for a small business that was given a bunch of HP DC5800 computers. Now I know they are fairly old but I was hoping I could make them usable using Ubuntu. Well after putting Ubntu 14.04.4 LTS on one of them, it ran super slow. Should I use an older version?[h=2][/h]

---

### Post by v3.xx on 2016-03-18
Too many unknowns, but my guess is Unity is too much for these older boxes.  I would suggest Mate 15.10 or one of the other lighter flavors.

[ATTACH=CONFIG]267881[/ATTACH]

[http://www8.hp.com/h20195/v2/GetPDF.aspx/c04290830.pdf](http://www8.hp.com/h20195/v2/GetPDF.aspx/c04290830.pdf)

---

### Post by DuckHook on 2016-03-18
> **Christian_Smith said:**
> ...Should I use an older version?Hi Christian and welcome to the forums.

An "older version" is never a good idea. Anything that is still supported won't be appreciably faster. On the other hand, anything old enough to be reasonably fast will be so far past end of life as to be a security disaster waiting to happen.

In the 'buntu world, reducing overhead and increasing speed is addressed through selection of the 'buntu flavour (desktop GUI) and not the version (age). v3.xx is correct. Mate or Lubuntu will go much further in giving you a decent experience than regressing to some dangerous out-of-support version.

The DC5800 is not really that ancient and should run a low-graphical desktop just fine. Its bottleneck is not the CPU but the GPU and, to a lesser extent, RAM. Increasing RAM always helps, but in your case, the GPU will be the biggest limitation. It is one of those early on-board chips that steals its DRAM from system RAM, which limits the amount of system memory even further. It's usually not worth adding a standalone graphics card to such machines. You are better off adding memory and running a lean 'buntu flavour like Mate or Lubuntu.

...and stick to 14.04 and soon, 16.04. Stay with Long Term Releases.

---

### Post by v3.xx on 2016-03-18
> ...and stick to 14.04 and soon, 16.04. Stay with Long Term Releases.

Yes, I agree.  But speaking just for Mate, its 14.04 version was not an official ubuntu release and some expect this to cause upgrade problems when upgrading to 16o4.  Mate 15.10 is an official ubuntu release and should upgrade nicely next month to 16o4.

---

### Post by HermanAB on 2016-03-19
In summary, if you install a new supported version with a light weight desktop system, such as Lubuntu or Xubuntu, then your machines will run fine.

---

### Post by Christian_Smith on 2016-03-19
Thanks! I'll put Lubuntu on instead and see how that goes. Appreciate the feedback!!

---

