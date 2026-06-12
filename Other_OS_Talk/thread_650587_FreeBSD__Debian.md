---
title: "FreeBSD / Debian"
date: 2007-12-26
forum: Other OS Talk
---

### Post by ThRixXx on 2007-12-26
Hi I'm just wondering how does Debian compare to uBunutu ?  Is it any better ?  I've been using linux mint and uBuntu for quite a while now and I'm thinking of trying out debian.

Allso FreeBSD looks quite nice, allso uses gnome desktop.  But has anyone used it ?  Is it anygood ?  Benefits ?

Thanks..

---

### Post by Bachstelze on 2007-12-26
Moved to Other OS Talk.

---

### Post by SunnyRabbiera on 2007-12-26
well on debian, its pretty good but its a bit rough to setup and get media ready.
FreeBSD is alright, but if you need flash working its not for you

---

### Post by kellemes on 2007-12-26
I think it's all about the amount of control you want.
If you want to have a working os out of the box, with most stuff you may need.. Ubuntu is an option.. Chances are you get a lot you don't actually need..
Debian gives you the engine to build your car on so to speak.. you need to know what you want and need some time to actually build it. Debian makes it not too hard since it's one freaking toolbox, still.. **you** need to set it up.
Anyway, it may well be you start using Debian to build some shiny system with all the bells and wistles just like Ubuntu.
I can surely recommend the endeavour.

BSD I don't know a lot about..

---

### Post by ThRixXx on 2007-12-26
Oh ohk thanks for the replies, am I right if I say that most of the commands I use in uBuntu will work on debian ?  etc. sudo apt-get, sudo pppoe.

Why is debian 3dvd's big and uBuntu only 1cd ?

---

### Post by fwojciec on 2007-12-26
> **ThRixXx said:**
> Oh ohk thanks for the replies, am I right if I say that most of the commands I use in uBuntu will work on debian ?  etc. sudo apt-get, sudo pppoe.

Some will, some won't.  Each distro has it's own ways; still, there are big similarities between Debian and Ubuntu.

> **ThRixXx said:**
> Why is debian 3dvd's big and uBuntu only 1cd ?

Because Debian ships with all packages from their stable repos included.  You don't actually need all the dvds to install a basic system comparable with what you get with Ubuntu/Mint.

---

### Post by init1 on 2007-12-27
> **ThRixXx said:**
> Oh ohk thanks for the replies, am I right if I say that most of the commands I use in uBuntu will work on debian ?  etc. sudo apt-get, sudo pppoe.

Why is debian 3dvd's big and uBuntu only 1cd ?
Yes, Ubuntu is based on Debian, so apt-get will still work. By default, however, sudo is not installed so you would need to use su instead. 
The three DVD's for debian includes all of their packages. If you want a minimal system that you can build on, get the "bootable business card".

---

### Post by luckykar on 2007-12-27
If you are new to Debian you don't want a net install cd , you would be better of getting the first cd as this is all thats required to get a working desktop.

They come in 3 different flavors of cd's " Gnome , Kde or  Xfce"

Again you only need the first cd or cd-1.iso

[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/)

the kde and xfce ones are located near the bottom...

---

### Post by new2*buntu on 2007-12-27
I suggest going with a Debian testing net install CD, if you have a broadband cable (no wireless, since it may not work with the net install CD) because you don't have to download all of the CDs and you get only what you want. Also, if you type "installgui" (without quotes) at the CD boot prompt you will get a graphical installer. However, if you select "Desktop Encironment" at the package selection page you will get a Gnome desktop. So if you want KDE or XFce you will have to download the full cd isos. Hope it helps.

Edit: I just went to their site and noticed that it is very hard to navigate. I tried looking for where they put the testing netinstall but I couldn't find it. I don't know how I found it a few hours ago. They really need a redesigned download page like OpenSUSE's.

Edit2: I think that I have found it. See [Here]("http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/") if you are interested. :)

---

### Post by shadylookin on 2007-12-29
ubuntu is based off debian, but debian has a much slower release schedule.

as far as I'm aware(please correct me if i'm wrong) but freebsd doesn't use the linux kernal and is heavily based off of BSD unix. I haven't used freebsd in a long time so it might have changed, but they have less driver support since they use their own kernel.

---

### Post by zetetic on 2007-12-29
> **ThRixXx said:**
> Hi I'm just wondering how does Debian compare to uBunutu ?  Is it any better ?  I've been using linux mint and uBuntu for quite a while now and I'm thinking of trying out debian.

Allso FreeBSD looks quite nice, allso uses gnome desktop.  But has anyone used it ?  Is it anygood ?  Benefits ?

Thanks..

Off course debian is better than ubuntu. It's more free, more stable and provides much better and reliable upgrades between versions (cause it's a rolling distro).

If you choose debian lenny you will get an always up to date system so you have no reasons to care about release schedules!

Release schedules is a specific problem regarding only frozen systems like Ubuntu!

---

### Post by kellemes on 2007-12-30
Indeed..
The thing is.. you can use Debian with a "fixed" release cycle **or** you can  roll your system and be up-to-date all the time. Having a mix of both gives you the best of both worlds.. Have your critical packages as stable as possible and still use the bleeding edge version of KDE. It's pretty cool.
That's why I always come back to Debian sooner or later.

---

### Post by Bachstelze on 2007-12-30
> **zetetic said:**
> Off course debian is better than ubuntu. It's more free, more stable and provides much better and reliable upgrades between versions (cause it's a rolling distro).

If you choose debian lenny you will get an always up to date system so you have no reasons to care about release schedules!

Release schedules is a specific problem regarding only frozen systems like Ubuntu!

For your information, Debian *is* release-based, too ! If you choose Ubuntu Hardy, you will get an always up-to-date system so you have no reasons to care about release schedules.

Debian was my first Linux, but I really see no reason to run it over Ubuntu nowadays.

---

### Post by new2*buntu on 2007-12-30
> **HymnToLife said:**
> For your information, Debian *is* release-based, too ! If you choose Ubuntu Hardy, you will get an always up-to-date system so you have no reasons to care about release schedules.

Debian was my first Linux, but I really see no reason to run it over Ubuntu nowadays.

Is Debian Sid or Testing release based? All I know is that the stable version is release based.

---

### Post by Bachstelze on 2007-12-30
> **new2*buntu said:**
> Is Debian Sid or Testing release based? All I know is that the stable version is release based.

Debian is a release-based distro because there are releases of Debian, perdiod. And every OS on the planet does have releases, plus a "current" development version. This goes for Debian and for Ubuntu just as well.

---

### Post by voteforpedro36 on 2007-12-30
I don't see much reason to run Debian over Ubuntu, but if that's the case, I don't see the reason to run Ubuntu over Debian. 

I think they're pretty much the same from a user's point of view, but that's me.

Debian was harder to get wireless working, but was probably easier to install. It has no Live CD, but that was cool with me anyway. It comes with less stuff at the beginning too, I believe.

Ubuntu was less stable, but has the great community, and has the greatest support of any distro IMO.

Test both I guess if you want to really know,

---

### Post by kellemes on 2007-12-31
> **HymnToLife said:**
> If you choose Ubuntu Hardy, you will get an always up-to-date system (..)

Can you explain to me how to do this? Can I simply point my sources to Hardy repositories and update every day? Or should I go from a Hardy-ISO to begin with?

I understand it's a development release and so issues can be expected, but this applies to Debian-Testing too, still Testing is proving to be rather stable and well worth the install for desktop-use.
I searched but haven't been able to find a lot of info on using hardy, do you know about it's quality for desktop-use compared to Lenny for example?
Thanks.

---

### Post by zetetic on 2008-01-02
> **HymnToLife said:**
> For your information, Debian *is* release-based, too ! If you choose Ubuntu Hardy, you will get an always up-to-date system so you have no reasons to care about release schedules.

Debian was my first Linux, but I really see no reason to run it over Ubuntu nowadays.

Wrong: if you choose Ubuntu Hardy you will get an up-to-date system for 6 months, so you have a very good reason to care about release schedules...
If you choose Debian Testing you will get an up-to-date system for the rest of your live, so you have no reasons to care about release schedules!

Sorry, but you also don't know what a rolling release is... Every Debian stable release is the result of a continuous update of the last testing release. That's one of the main reasons why Debian is so stable.

On the contrary, every Ubuntu release is based on a snapshot of a frozen "release" (often debian sid). That's why Ubuntu is much less stable then Debian and also one of the main reasons why one can get in so much trouble when upgrading Ubuntu releases...

Ubuntu is a great distro, but only because it's a good bait for fishing ex-windows users... After knowing something more about Linux almost anybody remains on Ubuntu.

cheers,
zetetic

---

