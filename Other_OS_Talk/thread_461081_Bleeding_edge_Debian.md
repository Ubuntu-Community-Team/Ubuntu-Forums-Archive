---
title: "Bleeding edge Debian?"
date: 2007-06-01
forum: Other OS Talk
---

### Post by miggols99 on 2007-06-01
I've looked around in the Debian repos and found that kdebase is version 3.5.5 for stable. I like to have bleeding edge packages, but I saw the unstable version has 3.5.7, the most up to date version. Is the sid version (unstable) more stable than it says? I've looked at sidux, but it doesn't have a net install cd, which I want, so I can build ground up. Also, is there a "command line install" for Debian? Is it a server install? If there is one, where can I find it? I've been looking around for it, but haven't been able to find it.

---

### Post by Bachstelze on 2007-06-01
For most users, Sid is perfectly stable. Having ran it for several years, I can recall facing only a couple of functionality-critical bugs and a dozen of minor annoyances. And moreover, problems that arise are usually fixed in a matter of days (but feel free to file a bug report if you spot one !). 

One of the reasons Sid is stil labelled unstable is that before apackage can move to testing, then to stable, it must have been given enough testing on the *eleven* architectures Debian supports. And given that i386 is by far the most common and the best supported, chances are that some "unstable" stuff will be rock-stable for it, but won(t have been tested enough or will give problems on other, more obscure ones.

Long story short : go with Sid, there's no reason not to on an i386 desktop.

---

### Post by justin whitaker on 2007-06-01
> **miggols99 said:**
> I've looked around in the Debian repos and found that kdebase is version 3.5.5 for stable. I like to have bleeding edge packages, but I saw the unstable version has 3.5.7, the most up to date version. Is the sid version (unstable) more stable than it says? I've looked at sidux, but it doesn't have a net install cd, which I want, so I can build ground up. Also, is there a "command line install" for Debian? Is it a server install? If there is one, where can I find it? I've been looking around for it, but haven't been able to find it.

There is a minimal install ISO here:

[http://www.debian.org/CD/netinst/](http://www.debian.org/CD/netinst/)

Three minutes on Google and the Debian website. 

As far as Debian+bleeding edge: that's Ubuntu. Debian tends to be very slow in moving things from unstable to stable status, partly because of philosophy, partly due to politics, and partly because Debian is used in alot of mission critical settings. That is why there are all of these Debian based distributions that try to keep the packages up to date. 

Have you tried Kubuntu? Mepis? Freespire (Alpha)? All of these are KDE centric, and fairly up to date with their package set.

---

### Post by ThinkBuntu on 2007-06-01
Debian + Bleeding edge = Ubuntu? What a joke. I'm not even sure that Debian + cutting edge = Ubuntu. You're looking for Sidux, which is a distro that bases itself off Debian Sid, the most "bleeding-edge" set of packages available for any distro. They take these packages that are supposed to be unstable and do their very best to stabilize them.

---

### Post by miggols99 on 2007-06-01
Ok. Where do I find it? Is it the daily builds? Weekly builds? Or something completely different. I don't want to download the wrong iso...

---

### Post by Rodneyck on 2007-06-01
Sidux is what you want. These guys take great care in making sure Sid is usable and what is downloaded to your computer will not break it, which sometimes happens when running pure Sid.

Download Sidux:
[http://debian.tu-bs.de/project/sidux/release/](http://debian.tu-bs.de/project/sidux/release/)

After installing, from then on out, you need to run the fabulous du-fixes script which keeps you "safely" updated to the most cutting-edge apps, kernels, xorgs and all the goodie apps, plus a lot more. That script is the best thing to happen to any distro.  Follow the directions on the du-fixes page below.

Script:
[http://techpatterns.com/forums/about736.html](http://techpatterns.com/forums/about736.html)

---

### Post by miggols99 on 2007-06-01
Is there a ultra lite install, with only kde-core? Or a command line only install? Because I looked at the live cd and it had loads of programs. This is actually the only thing pushing me away from sidux.

---

### Post by Rodneyck on 2007-06-01
> **miggols99 said:**
> Is there a ultra lite install, with only kde-core? Or a command line only install? Because I looked at the live cd and it had loads of programs. This is actually the only thing pushing me away from sidux.

I don't think there is a command line only install, but there is a kde-lite version using just kdebase. This would be your best option. Even if you had to remove some of the apps, it would not be that many. 

BTW, Sidux is also one of the fastest distros around running KDE.

---

### Post by miggols99 on 2007-06-01
Sounds good. I'm downloading the lite version now...

---

### Post by Bachstelze on 2007-06-01
Get a weekly build of Debian "testing". Install. Change your sources.list to "unstable". Upgrade. You're there.

---

### Post by happy-and-lost on 2007-06-03
Sid's fine. A bit of dependancy hell once in a while, but it's better than running the old buggy-er KDE in Etch.

---

### Post by miggols99 on 2007-06-03
I've looked at sidux. It installs some sidux programs, an _**UGLY**_ colour theme and bootsplash. Red and black? Ew. I heard that a lot of people like it. Looks like it's not going to change...

I've installed sid now. Let's hope I don't get too much trouble with it...

---

### Post by ThinkBuntu on 2007-06-03
> **miggols99 said:**
> I've looked at sidux. It installs some sidux programs, an _**UGLY**_ colour theme and bootsplash. Red and black? Ew. I heard that a lot of people like it. Looks like it's not going to change...

I've installed sid now. Let's hope I don't get too much trouble with it...
So you didn't use Sidux because of the ugly theme? One minute of tweaking frow the Control Center would give you a nice, standard KDE...

---

### Post by notwen on 2007-06-03
I run my servers off a sidux box, have had 0 issues what so ever for the past 3ish months.  I dig it for what I need from it. =]

---

### Post by miggols99 on 2007-06-03
> So you didn't use Sidux because of the ugly theme? One minute of tweaking frow the Control Center would give you a nice, standard KDE...
No, actually, there were a few problems. I tried installing neverball. But it didn't appear in the menus. But it did in Kubuntu/Ubuntu! Also, there are some sidux programs. Will it do anything if I remove them? Do you remove the grub theme by removing some lines from the menu.lst file?

---

### Post by kerry_s on 2007-06-03
kde-> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-kde-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-kde-CD-1.iso)

xfce4-> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)

net-> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso)

add testing/lenny and unstable/sid repos, then apt-get dist-upgrade, bam you are now bleeding edge with pure debian.

---

### Post by juxtaposed on 2007-06-03
> For most users, Sid is perfectly stable.

You convinced me to upgrade to sid from lenny :P

Seems stable so far, and it seemed to fix a problem with GDM...

---

### Post by Pobega on 2007-06-03
> **juxtaposed said:**
> You convinced me to upgrade to sid from lenny :P

Seems stable so far, and it seemed to fix a problem with GDM...

Almost makes me consider upgrading to Sid...I've been contemplating it, but I can't really afford downtime on my laptop (Will be used for college come September, and I'll need it to be working at all times).

But it's still so tempting.

---

