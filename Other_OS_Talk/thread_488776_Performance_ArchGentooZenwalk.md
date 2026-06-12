---
title: "Performance: Arch/Gentoo/Zenwalk"
date: 2007-06-30
forum: Other OS Talk
---

### Post by ahaslam on 2007-06-30
I know others here are on a constant mission for speed, so I thought I'd share my recent experience with the new releases from the titled distro's. 

When It comes to performance I believe it's got to be balanced, it's no use booting fast only to take an age loading an application. Likewise, tools such as glxgears & super_pi only really show how good a given *component/driver* is, not how well a *system/OS* as a whole performs. 

With this in mind I benchmarked the chosen distro's with something that places my cpu, graphics, hard disk & memory under significant load. A game... Nexuis to be precise & it just happens to have a convenient timedemo benchmark tool that logs the results.

The results below are from the 32bit i686 variants (where there's a choice) with a fresh, minimal, desktop install along with the latest nvidia drivers. The Gentoo install was from the stage 3 tarball (which took long enough), using [safe cflags]("http://gentoo-wiki.com/Safe_Cflags#Intel_Core_2_Duo.2FQuad_.2F_Xeon_51xx.2F53xx"). All are using the same xorg.conf, nvidia-settings & nexuiz config upon a fresh boot into Xfce4:
```

**Arch:**
result 1910 frames 17.0337015 seconds **112.1306487** fps, one-second min/avg/max: 75 112 143
result 1910 frames 16.8586584 seconds **113.2948992** fps, one-second min/avg/max: 76 114 149
result 1910 frames 16.8626430 seconds **113.2681276** fps, one-second min/avg/max: 77 114 149

**Gentoo:**
result 1910 frames 17.3170878 seconds **110.2956815** fps, one-second min/avg/max: 66 110 141
result 1910 frames 17.1452239 seconds **111.4012865** fps, one-second min/avg/max: 75 111 149
result 1910 frames 17.1684565 seconds **111.2505366** fps, one-second min/avg/max: 73 111 149

**Zenwalk:**
result 1910 frames 17.3503367 seconds **110.0843191** fps, one-second min/avg/max: 63 110 145
esult 1910 frames 17.1959983 seconds **111.0723534** fps, one-second min/avg/max: 72 111 147
result 1910 frames 17.1852975 seconds **111.1415152** fps, one-second min/avg/max: 72 111 147
```

The min/max figures aren't absolute, rather an average over a one second period. So don't look too deeply at those, we're mainly concerned with the average figure.

As you can see Arch is the clear leader here. What's more interesting is how closely Gentoo & Zenwalk perform, especially as Zenwalk takes little more than 15 minutes to install, while Gentoo takes the best part of 15 hours.

I have an older install of Arch on another partition which is pure 64bit, this shows an extra gain:
```
**Arch x86_64:**
result 1910 frames 16.5300772 seconds **115.5469496** fps, one-second min/avg/max: 75 116 149
result 1910 frames 16.3996949 seconds **116.4655812** fps, one-second min/avg/max: 68 117 156
result 1910 frames 16.3953960 seconds **116.4961188** fps, one-second min/avg/max: 68 117 156
```

Make of this what you will, I know performance doesn't mean much to some. I just have to take my hat off to Arch & Zenwalk, two quick & simple installs that rival/beat a tailored Gentoo install.

Feel free to show any comparisons that you've made (or wish to) with any distro's, just ensure that the environments are fresh & fair ;)

---

### Post by ThinkBuntu on 2007-06-30
Arch is a great distro. I'm a little too lazy to really get it going, but I imagine that if I were to take some time to seriously track down a couple problem points, it would be the best I could get, although with its imperfections. A little automatic configuration can go a long way, and an official graphical package manager would be a nice addition. After all, it wouldn't have to be installed by default.

---

### Post by ahaslam on 2007-06-30
Maybe someone can help in the 'Arch Linux Talk' thread & don't forget the AUR for extra packages (there's a few verified pacman gui's there) ;)

---

### Post by Enverex on 2007-06-30
Hate to burst your bubble but these figures are all bogus. It's purely down to the versions of packages used. If it was due to "optimizations" then Gentoo would have come out on top. The only performance difference between distros will be down to what version(s) of software the distro is using and what programs may be resident and using system resources at the time. There is nothing that makes Arch any faster than any other distro.

---

### Post by ahaslam on 2007-06-30
> **Enverex said:**
> Hate to burst your bubble but these figures are all bogus. It's purely down to the versions of packages used. If it was due to "optimizations" then Gentoo would have come out on top. The only performance difference between distros will be down to what version(s) of software the distro is using and what programs may be resident and using system resources at the time. There is nothing that makes Arch any faster than any other distro.
Bogus? The installs were clean & *current*. If I were to have brought things in from testing it wouldn't be fair. Distro's provide package versions that fit their philosophy, it is these packages that make distributions what they are. Don't forget that newer doesn't always mean better or faster, just as older doesn't always mean slower or more stable. 

As I said, "make of this what you will." I'm only sharing my findings...

---

