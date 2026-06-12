---
title: "Distributions that keep up with updating packages?"
date: 2007-08-07
forum: Other OS Talk
---

### Post by Apewall on 2007-08-07
Former Gentoo user here, so I'm used to being able to compile a program via portage down to the latest alpha.

I'm finding that Ubuntu annoys me to no end with not supporting new packages, programs are left out of date in the repositories and I'm constantly having to find new repositories.

Furthermore half of the time I cannot update programs because Ubuntu lists them essential, and it breaks the distro if I update one essential program.

Basicly I want the latest and greatest, not the "Hey this is our stable release list, see you again when we make it to Gutsy."  Any other -simple- Linux distrobution capable of this, or am I moving back to compiling all my programs out of portage in Gentoo.

---

### Post by eentonig on 2007-08-07
If you want the latest and the greatest... I'd say go back to Gentoo.

Ubuntu is not aimed towards tech geeks who want to fine tune untill the latest detail. Or want to be up to date to the very last bit.

Ubuntu is created around the idea "ease of use and stability for the general computer user". As such, they have to make sacrifices. 

Personally, I don't mind not running the very latest alpha release. If programs do what I expect them to do, why should I introduce the possibilities of undiscovered bugs in my system? except if I need this or that new feature. But that rarely happens.

But if this is what you want. By all means, nobody said you have to use ubuntu.

---

### Post by anaconda on 2007-08-07
Yep.
the same thing is starting to annoy me too. Until now I have always moved to the newest release just to get new versions of the programs, but this is really too much work just for that.

There are distros that hadnle this better. I will be looking into Mepis 7 when it comes.

---

### Post by Frak on 2007-08-07
You can still compile programs in Ubuntu just as you did in Gentoo, I do it alot, not for the same reasons, but you can do it. Thanks to having handy dpkg tools, you can also with a simple command install all needed dependencies.

---

### Post by Apewall on 2007-08-07
I'm considering Sabayon, it sounds more like what I'm looking for, but I've not heard any user experiences personally.

> **Frak said:**
> You can still compile programs in Ubuntu just as you did in Gentoo, I do it alot, not for the same reasons, but you can do it. Thanks to having handy dpkg tools, you can also with a simple command install all needed dependencies.
Ofcourse you can, but you'll still need to find each and every package since the repositories are not kept up, unless you want to use the unstable testing repo.

---

### Post by Frak on 2007-08-07
I like Sabayon, Works great, give it a shot if you want. I prefer it over regular Gentoo, as IMHO, it is a pain in the a** to install Gentoo. At least Sabayon is pre-configured.

---

### Post by Apewall on 2007-08-07
> **Frak said:**
> I like Sabayon, Works great, give it a shot if you want. I prefer it over regular Gentoo, as IMHO, it is a pain in the a** to install Gentoo. At least Sabayon is pre-configured.

Never had a problem installing gentoo.  But I am mostly wondering how Sabayon deals with portage, and if I will still be compiling packages all the time to update.

---

### Post by Frak on 2007-08-07
It derives everything from Gentoo as I know.
And as for me installing Gentoo, 9/10 times it won't install for me, and if you could point to some reasons why, please tell me, because I do like Gentoo. I did get it back in '99, but it'd be nice to try it out now.
It usually fails during installation of programs such as OO.o, firefox, evolution, etc.
Any ideas?

---

### Post by Apewall on 2007-08-07
> **Frak said:**
> It derives everything from Gentoo as I know.
And as for me installing Gentoo, 9/10 times it won't install for me, and if you could point to some reasons why, please tell me, because I do like Gentoo. I did get it back in '99, but it'd be nice to try it out now.
It usually fails during installation of programs such as OO.o, firefox, evolution, etc.
Any ideas?

I do think I would much prefer a binary distribution that just keeps up to date with all of its packages.

They've recently created a GUI installer for the LiveCD, while not as good as manual installation it gets the job done, failure to compile is usually caused by a broken dependency-in most cases.

---

### Post by Frak on 2007-08-07
ok, thanks
As stated above, you might want to try Mepis 7, they are usually bleeding edge

---

### Post by miggols99 on 2007-08-07
Arch Linux is bleeding edge. To update all you have to type is:

pacman -Syu

Which downloads the package lists and upgrades out of date packages. It is also is rolling release (is Gentoo?) so you don't have to dist-upgrade or use update manager to upgrade to a new Ubuntu release. I don't know about Mepis though. Debian stable isn't very bleeding edge.

---

### Post by Erunno on 2007-08-07
openSUSE offers many [repositories]("http://download.opensuse.org/repositories/") for a wide range of software via their Build Service. The advantage compared to a rolling distro is that you can choose to update only the software which matters to you most without compromising the stability of the base system.

---

### Post by SunnyRabbiera on 2007-08-07
PCLOS does the same too, its a bit faster on the uptake then ubuntu but  it doesnt have as large of a library as ubuntu.

---

### Post by kerry_s on 2007-08-07
try straight debian, you can use all the repos, etch, lenny, and sid and be up to date, there's is also a experimental repo, for the truly hard core got to have the newest one people. nothing like living on the edge.

kde> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-kde-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-kde-CD-1.iso)
xfce4> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)
gnome> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-netinst.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-netinst.iso)
for custom, building> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso)

i always do mine custom, i install the base, then build up from there. haven't used a full DE in almost a year.

my current> apt-get install xorg gdm synaptic jwm menu mc
is what i started this build with, freshly built this mourning. :)
nothing much to look at, i'm keeping it simple.

---

### Post by hogweed on 2007-08-07
It sounds like you might want to take a look at Sidux ([http://www.sidux.com]("http://www.sidux.com")), which is Debian Sid (Unstable) but with a live-cd installer and a set of tools and scripts to minimize the "Unstable" attributes of Sid without losing the up to date package list. You can just add in the multimedia repos, and even the Debian "Experimental" repo for a few programs, if you want. Should be pretty much what you are looking for.

I have not used it, but likely will give it a try fairly soon. Like you, I like having the most recent releases of all programs, but I got a bit bored with the compile-times of Gentoo (that was three years ago -- but I can't imagine that that aspect has changed much). I used to run straight Debian Sid before Kubuntu, and I *really* miss never having to re-install or do a massive upgrade from version to version -- it was just incremental upgrades forever, and always the latest stuff. (I'm trying to remember why I switched, but can't recall -- it was probably just curiosity...).

So, I'd suggest exploring Sidux, fwiw.

--
hogweed

---

### Post by raul_ on 2007-08-07
Arch Linux

---

### Post by Apewall on 2007-08-09
Does Arch Linux keep up to date thoroughly? I would think so with allowing user made packages to be moved to the repository.

I've been sitting here compiling a gentoo system for 6-8 hours and thought, I could have probably at least tried another distro in this amount of time.

---

### Post by miggols99 on 2007-08-09
Arch Linux updates most packages within a few days or a week at the most. Some packages may be out of date though.

---

### Post by igknighted on 2007-08-09
Sidux and Fedora are both great binary distros that keep up to date.  Sidux will update EVERYTHING, Fedora not as much, but still a lot (for example, FF2 never made it into FC6, but apps like pidgin upgrade within days of release...).

---

### Post by raul_ on 2007-08-09
> **Apewall said:**
> Does Arch Linux keep up to date thoroughly? I would think so with allowing user made packages to be moved to the repository.

I've been sitting here compiling a gentoo system for 6-8 hours and thought, I could have probably at least tried another distro in this amount of time.

Yes, sometimes you can find packages in the repositories befores they were officially released. What you can't find in the repositories you can find in the AUR (Arch User Repository), and voting for your favorite packages in the AUR, promotes them to the official repositories.

Arch is bleeding edge

---

### Post by Nikron on 2007-08-09
However, Arch is a smaller distro, so you will probably have a package or two that's been neglected.  But, ABS is beyond awesome, and simply changing version numbers and compiling will get you up to date if a package gets out of date.

---

### Post by omns on 2007-08-09
I'd agree, Arch and ABS make for nice bleeding edge distro that's reasonably stable. Zenwalk also does a nice job and is developing tools similar to ABS. It's a much smaller distro but really slick.

---

