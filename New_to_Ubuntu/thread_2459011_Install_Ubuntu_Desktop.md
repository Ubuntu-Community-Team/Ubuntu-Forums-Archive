---
title: "Install Ubuntu Desktop"
date: 2021-03-08
forum: New to Ubuntu
---

### Post by gadi01 on 2021-03-08
It is possible to install Ubuntu on Desktop computer's specification: 
Intel(R) Pentium(R) 4 CPU 3,20 GHZ, 496 Mo of RAM, and disk size 149 Go? I plan to install a version .Ubuntu Dessktop and win7 to make dual-boot. Is this well affect the response of the machine and the performance in compiling and running Fortran & C programs. Is it poosible to install Ubuntu from USB in the machine? Which either Ubuntu version can be installed in that machine and will perfom more than Ubuntu? Suggestions and advices would be greatly appreciated.
Thank you,

---

### Post by CatKiller on 2021-03-08
If that Pentium 4 is 32-bit, then it won't be able to install Ubuntu. 32-bit installs are no longer available. 

496 MB RAM isn't sufficient for the modern Internet. 

Windows 7 has been End-of-Life for quite some time.

---

### Post by gadi01 on 2021-03-08
Thank you for your comment,
I do not yet check if 32- or 64- bit so if is 64-bit which Ubuntu version would be installed in that machine? is the memory will affect the connection to Internet even with an internet cable?
Which version of Win do you recommend for me? and at the same time works fine with Cygwin

---

### Post by CelticWarrior on 2021-03-08
> [COLOR=#000000]I do not yet check if 32- or 64- bit so if is 64-bit[/COLOR]
Any Pentium 4 is 32-bit.

> [COLOR=#000000]s the memory will affect the connection to Internet even with an internet cable?[/COLOR]
Yes, it has little to nothing to do with the actual internet connection/service.

> [COLOR=#000000]Which version of Win do you recommend for me?[/COLOR]
NONE!
No currently supported Windows version works with so little RAM.

---

### Post by ActionParsnip on 2021-03-08
> **CelticWarrior said:**
> Any Pentium 4 is 32-bit.


*Prescott CPUs were Pentium 4 and 64bit*

[http://www.cpushack.com/2019/10/01/the-story-of-the-ibm-pentium-4-64-bit-cpu/](http://www.cpushack.com/2019/10/01/the-story-of-the-ibm-pentium-4-64-bit-cpu/)

---

### Post by Impavidus on 2021-03-08
The best use of a computer of that vintage is probably extracting raw materials for recycling, but if you insist, it can be put to some niche work. It won't run regular Ubuntu, but, if 64 bit, it may run a stripped down version. No desktop environment, no web browser, very basic graphics, but it can be used to write and compile C or fortran programs and run them if they are light enough. I wouldn't really expect computers of that vintage to boot on usb. You may need a dvd.

---

### Post by crip720 on 2021-03-08
If you can at least double the ram, then Lubuntu 18.04 should run if you take it easy(might be already out of support).  If out of support, will need to try Puppy, Tiny, or Dam small Linux or google small Linux for ones still supported.  Am running Lubuntu 18.04 on a P4, but have 1.2GBs of ram.

---

### Post by TheFu on 2021-03-08
On a system like that, you'll want a very light Linux.  Something like TinyCore.  I wouldn't load any flavor of Ubuntu desktop.
[http://tinycorelinux.net/](http://tinycorelinux.net/) to learn more.  They have versions with common desktop applications that should run well in 200MB of RAM.

---

### Post by gadi01 on 2021-03-08
can I install lUbuntu in that machine?

---

### Post by ActionParsnip on 2021-03-09
Lubuntu will install but 0.5Gb RAM is not ideal. If you can upgrade that it'll really help. I'm surprised that Windows 7 installed on so little. Does the system have a make and model?

---

### Post by guiverc on 2021-03-09
I have used a number of like systems in testing, eg.

- hp dx6120mt (pentium 4, 3gb, winfast clone of nvidia 7600gt)

though it was 1.5GB when testing Lubuntu 18.04, Lubuntu 18.10, Lubuntu 19.04 *alpha*; with the RAM only increased to 3GB when i386 ISOs were dropped mid-*disco* (19.04) cycle (so it's 3GB for later 18.04 re-spins)

It was last used to test 18.04.5 *flavors* in August-2020 (Lubuntu, Xubuntu, Kubuntu).

The last `ubuntu-desktop` however that I ran on it was Ubuntu 16.04 LTS (so Unity 7), and I don't recall ever trying (*or wanting to really try*) the GNOME desktop (*even with 3GB; it'd be no fun*).

Lubuntu *live* installation media requires you have 768MB to install; as you must be running the system live and have memory available for the installer (`ubiquity` for 18.04).  The *alternate* ISO uses the *Debian Installer* and can be used on machines with less than 768MB.  The *alternate* ISO was last created April-2018, so it'll have a lot of updates to install (unlike more recent media).

Lubuntu 18.04 LTS (2018-April release) has 3 years of full-support, which alas ends 2021-April or rather soon.  Yes your base system will still get upgrades for 5 years (until 2023-April) but many of your packages will not (only main Ubuntu desktop & server get 5 years of support), so consider that if you're online.


Other i386 systems I've tested with are

- hp d220mt (dr159p), (celeron 2ghz, 1gb (732mb useable), 82845G/GL Brookdale-G/GE (i915))
- dell latitude d610 (pentium m, 1.5gb, intel i915)
- ibm thinkpad t43 (pentium m, 1.5gb ram, radeon x300)
- ibm thinkpad t42p (pentium m, 2gb ram, amd/ati mobility firegl t2; rv350/m10 gl)
- ibm thinkpad r50p (pentium m, 1gb ram, amd/ati mobility firegl t2; rv350/m10 gl)
- asus eepc 1000HE (intel atom n270, 1gb, intel mobile 945gse integrated), wireless RT2790
- dell inspiron 6400 (c2d-t2450, 2gb, intel 945gm)

FYI:  the only system that really annoyed me was the *hp d220mt* (celeron) which maybe because it had 732MB of RAM so take note (*could also be the cpu)*.

  I also tested Debian 10 (Buster) on those systems, and actually Lubuntu 18.04 LTS was nicer to use on the *hp d220/celeron* than even Debian Buster (LXDE, LXQt, XFCE..) was (*which actually surprised me; though neither would I want to need to use!*).  I didn't explore if the issue was the celeron or lack of RAM - I just avoided the box (box has 1GB of RAM, but it's shared with video).

---

### Post by gadi01 on 2021-03-09
[COLOR=#DD4814][COLOR=#000000]@[ActionParsnip]("https://ubuntuforums.org/member.php?u=1079078")
the Win Xp is installed on that machine. How can I upgrade the RAM? I was planning to install the Xubuntu or Lubuntu to boot with a moderne version of Windiows? What do you recommend?[/COLOR][/COLOR]

---

### Post by gadi01 on 2021-03-09
@ [guiverc]("https://ubuntuforums.org/member.php?u=2074246")[COLOR=#000000] 
What do you recommend to me?? I was planning to install a Linux lightweight distro like Lubuntu or Xubuntu that boots with a moderne Windows version to install Cygwin. Please suggest to me how can I do it[/COLOR]

---

### Post by guiverc on 2021-03-09
On less than 1GB of (*available*) RAM my only real suggestion is get more RAM.

As I already stated; on the 1GB (but only **732MB** available to any OS) hp celeron d220mt device, Lubuntu 18.04 tested the best of any I tried (inc. xubuntu, debian buster..) but it was not really a device I'd want to keep using...  The pentium 4 (with 1.5gb ram), or pentium M (with 1GB) were much nicer to use. I never explored if it was the RAM or cpu (*I didn't really care that muc*h)

GTK3 based releases are slower than GTK2; eg. I used to love MATE on the pentium M laptops (with 1GB) but stopped using MATE as it switched to GTK3 using XFCE mostly instead.   XFCE likewise slowed down as it ported to GTK3 (so I switched to LXDE), ie.  with desktops, in my opinion at least, the release matters.  (you can't just say Xubuntu.. as some releases performed better than others... I kept upgrading a pentium 4 to *eoan* (19.10) allowing me to experience Xubuntu when it was finally all GTK3... Lubuntu *eoan* (19.10) using LXQt  outperformed Xubuntu *eoan*.

I would use just a WM or all terminal-based applications; in Ubuntu terms, building from a minimal install.   I'd also likely use Debian (you won't get most of the advantages of Ubuntu & *flavors*).

Repeating you need to increase your RAM !

(*I prefer sticking to talking about Ubuntu and flavors of Ubuntu on Ubuntu sites, so I'll mention others, but with fewer details; I do like my Debian* *though*)

---

### Post by mastablasta on 2021-03-12
> **guiverc said:**
> 
Repeating you need to increase your RAM !


this is the only real solution.

but on old machines it might not be feasible. btu you should know that various browsers and similar apps need quite a bit of ram these days. 

to boot at lower RAM you need to use something very basic like icevw or openbox. maybe you could give AntiX (uses Rox-IceWM)  a try or BunsenLabs Linux  (uses Openbox). both are debian based. there is also ubuntu based Bodhi Linux using E17

these are all very light options that will consume really small amounts at boot. they still have access to large array of applications.

there are also more specialized distributions that are aimed at low ram machines, old computers etc. such as Slitaz, Tiny Core, PuppyLinux, DSL and similar, but they may have other limitations. however some of them work on computers will less than 200 MB ram.

---

