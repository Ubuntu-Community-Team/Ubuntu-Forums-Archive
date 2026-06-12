---
title: "Distro Hopping - *buntu-like, but update like Arch?"
date: 2008-07-21
forum: Other OS Talk
---

### Post by Xiong Chiamiov on 2008-07-21
Hmm, I wonder how well that title got the point across.  Oh well.

I haven't settled on a distro yet.  I started with Kubuntu, and it served me well, but I really don't like the way the repositories work.  For instance, my roommate had to upgrade to Hardy 3 weeks before release because an update broke compatability with his wireless card.  I also am one of the many who require the newer NVIDIA drivers to get things working with the kernel that shipped with Hardy, yet (last I checked) it hasn't been updated.  Sigh.

So, I've been using Arch for about a month (perhaps closer to 2 now), and I like several things about it.  However, I sometimes have errors that, well, take forever to iron out, and while I enjoy doing that sometimes, I don't want to have to for my main desktop OS.

So, I'm trying to find something that "just works" like *buntu *mostly* does, yet has the latest stable releases of applications in the repos at most a day or two after release.  While I don't want the latest alpha (or even beta), I'm ok with something being broken if I know that I'll get the fix as soon as it's out.

I would also prefer something that's fairly "start from scratch and add only what you need" like Arch, but it's not necessary.  Source-based installation is also ok, although I'm not particularly fond of it, considering my tendency to install packages on a whim.

Aside from the 2 mentioned, I've played around with a few others on another partition:
* PC-BSD - FreeBSD with a "user-friendly" top on it.  Couldn't get my screen res bigger than 800x600, and the PBI installation system was *way* too much like Windows; I've never going back to google-download-next-next-next-finish again.
* Debian Etch - far too stable for me, and I wasn't particularly excited about Sid, but haven't tried it
* Crux - wanted to use my prexisting GRUB, couldn't get the right parameters to get it to boot, and documentation sucked so I dumped it and installed
* Gentoo - although I'm not particularly fond of source-based installations (see above), I've used it's wiki quite a bit, and decided to try it out.  Haven't had a chance to use it yet.
* FreeBSD - very brief experience on a side-project of mine.  Haven't had the chance to use in a desktop environment.

EDIT: I suppose I should clarify a little more what I want as far as "easiness".  From [this excellent article]("http://www.over-yonder.net/~fullermd/rants/userfriendly/userfriendly1.php"), I've begun to think of the term "user-friendly" really meaning three different things:
* easy to use
* easy to learn
* easy to use without learning

I'm looking for the first two fairly well-balanced.  I like being able to pick up on things quickly as long as they don't restrict me later on.  I also don't like spending forever getting something working, unless there is no easier way, and it's a project.

---

### Post by zmjjmz on 2008-07-21
Sidux is a possibility, and so is Sabayon.

---

### Post by L815 on 2008-07-22
I'm looking for the same. Sidux doesn't play well for some reason with my hardware, were Debian does o_O

---

### Post by Xiong Chiamiov on 2008-07-22
> **zmjjmz said:**
> Sidux is a possibility, and so is Sabayon.
Thanks, I'll look into those.

I should also note that, although I like things to work easily, as I said, there are many things that I prefer doing through the terminal.  For instance, I haven't used a graphical package manager frontend in quite some time, as I find it faster to use the CLI (plus I can tuck it away in Yakuake).

Mm, and I don't count KDE4 to be stable yet.  Maybe at 4.1...

---

### Post by Bachstelze on 2008-07-22
> **L815 said:**
> I'm looking for the same. Sidux doesn't play well for some reason with my hardware, were Debian does o_O

Then use Debian ;)

---

### Post by perlluver on 2008-07-22
You look pretty well versed in Linux, try Slackware.

---

### Post by L815 on 2008-07-22
> **HymnToLife said:**
> Then use Debian ;)


I have the CD ready, just gotta take the plunge :guitar:

---

### Post by jkeyes0 on 2008-07-22
You might try out [Foresight Linux]("http://www.foresightlinux.org/"). Rolling release distro, based on rPath Linux. Users can create and upload packages to their own repos, which could eventually be included in the main repos.

Small community in #foresight on freenode, but someone's always willing to help out.

---

### Post by Rumor on 2008-07-22
Zenwalk can be made to be a rolling release like Arch but still maintain a more Ubuntu-like simplicity. 

More info in this post: [http://ubuntuforums.org/showpost.php?p=3455794&postcount=9](http://ubuntuforums.org/showpost.php?p=3455794&postcount=9)

---

### Post by SunnyRabbiera on 2008-07-22
Well you can try Linux mint, its ubuntu based but only updates what is needed.

---

### Post by Twitch6000 on 2008-07-22
PclinuxOS might work for you,but you might wanna change the package manager.

Maybe even try to put everything in one with Linux from scratch?

---

### Post by RedSquirrel on 2008-07-22
> **Xiong Chiamiov said:**
> * Gentoo - although I'm not particularly fond of source-based installations (see above), I've used it's wiki quite a bit, and decided to try it out.  Haven't had a chance to use it yet.

Gentoo is my current favourite. It may meet your needs quite well, but there's only one way to find that out. ;)

I generally stick to stable packages with a few from the testing branch. 

Most of the packages don't take that long to compile. There are binaries for some of the larger programs (for example, Firefox, Thunderbird, OpenOffice).

The documentation is very good. It isn't that hard to learn and once you learn it, it's easy to use (IMHO).

---

### Post by rsambuca on 2008-07-22
> **Xiong Chiamiov said:**
> So, I'm trying to find something that "just works" like *buntu *mostly* does, yet has the latest stable releases of applications in the repos at most a day or two after release.  While I don't want the latest alpha (or even beta), I'm ok with something being broken if I know that I'll get the fix as soon as it's out.


Wow, you are willing to wait an entire day or two to get a new release???  Dream on.  No distro does that.  Sometimes it takes some time to test that there is no breakage!

For your needs, stick with Debian Sid, Arch, Foresight, or Gentoo.

---

### Post by RedSquirrel on 2008-07-22
> **Xiong Chiamiov said:**
> * Debian Etch - far too stable for me, and I wasn't particularly excited about Sid, but haven't tried it

Yeah, Debian stable is like a software museum (but there is a good reason for this).

I think most "Desktop" users of Debian go with either testing or unstable (or mix branches).

I've used Sid in the past and I thought it was nice. I used to upgrade it daily and it didn't cause much trouble. However, there is a possibility that your system could break at some point when you upgrade. It didn't happen to me, but that **warning** is mentioned throughout the Debian docs and elsewhere.

One thing I do recall is that I had OpenOffice installed on Sid and it seemed there were new OpenOffice packages every day, which amounted to at least 100 MB to download each time. :shock:

Anyway, if you decide to try Sid, you can install it directly but you have to use expert mode when you run the installer (I used Debian's "business card" image).

---

### Post by Hallvor on 2008-07-23
> **Xiong Chiamiov said:**
> Hmm, I wonder how well that title got the point across.  Oh well.

I haven't settled on a distro yet.  I started with Kubuntu, and it served me well, but I really don't like the way the repositories work.  For instance, my roommate had to upgrade to Hardy 3 weeks before release because an update broke compatability with his wireless card.  I also am one of the many who require the newer NVIDIA drivers to get things working with the kernel that shipped with Hardy, yet (last I checked) it hasn't been updated.  Sigh.

So, I've been using Arch for about a month (perhaps closer to 2 now), and I like several things about it.  However, I sometimes have errors that, well, take forever to iron out, and while I enjoy doing that sometimes, I don't want to have to for my main desktop OS.

So, I'm trying to find something that "just works" like *buntu *mostly* does, yet has the latest stable releases of applications in the repos at most a day or two after release.  While I don't want the latest alpha (or even beta), I'm ok with something being broken if I know that I'll get the fix as soon as it's out.

I would also prefer something that's fairly "start from scratch and add only what you need" like Arch, but it's not necessary.  Source-based installation is also ok, although I'm not particularly fond of it, considering my tendency to install packages on a whim.

Aside from the 2 mentioned, I've played around with a few others on another partition:
* PC-BSD - FreeBSD with a "user-friendly" top on it.  Couldn't get my screen res bigger than 800x600, and the PBI installation system was *way* too much like Windows; I've never going back to google-download-next-next-next-finish again.
* Debian Etch - far too stable for me, and I wasn't particularly excited about Sid, but haven't tried it
* Crux - wanted to use my prexisting GRUB, couldn't get the right parameters to get it to boot, and documentation sucked so I dumped it and installed
* Gentoo - although I'm not particularly fond of source-based installations (see above), I've used it's wiki quite a bit, and decided to try it out.  Haven't had a chance to use it yet.
* FreeBSD - very brief experience on a side-project of mine.  Haven't had the chance to use in a desktop environment.

EDIT: I suppose I should clarify a little more what I want as far as "easiness".  From [this excellent article]("http://www.over-yonder.net/~fullermd/rants/userfriendly/userfriendly1.php"), I've begun to think of the term "user-friendly" really meaning three different things:
* easy to use
* easy to learn
* easy to use without learning

I'm looking for the first two fairly well-balanced.  I like being able to pick up on things quickly as long as they don't restrict me later on.  I also don't like spending forever getting something working, unless there is no easier way, and it's a project.


I`d say PCLinuxOS. It is very easy. They also have a community Gnome edition. New software is sent to a testing server for a week or so, before you get it as an upgrade to your system. It offers a very good comprimise between ease of use and bleeding edge software.

---

### Post by Hallvor on 2008-07-23
> **Twitch6000 said:**
> PclinuxOS might work for you,but you might wanna change the package manager.


Change synaptic?

---

### Post by enlightenment now on 2008-07-23
> **Xiong Chiamiov said:**
> Hmm, I wonder how well that title got the point across.  Oh well.

I haven't settled on a distro yet.  I started with Kubuntu, and it served me well, but I really don't like the way the repositories work.  For instance, my roommate had to upgrade to Hardy 3 weeks before release because an update broke compatability with his wireless card.  I also am one of the many who require the newer NVIDIA drivers to get things working with the kernel that shipped with Hardy, yet (last I checked) it hasn't been updated.  Sigh.

So, I've been using Arch for about a month (perhaps closer to 2 now), and I like several things about it.  However, I sometimes have errors that, well, take forever to iron out, and while I enjoy doing that sometimes, I don't want to have to for my main desktop OS.

So, I'm trying to find something that "just works" like *buntu *mostly* does, yet has the latest stable releases of applications in the repos at most a day or two after release.  While I don't want the latest alpha (or even beta), I'm ok with something being broken if I know that I'll get the fix as soon as it's out.

I would also prefer something that's fairly "start from scratch and add only what you need" like Arch, but it's not necessary.  Source-based installation is also ok, although I'm not particularly fond of it, considering my tendency to install packages on a whim.

Aside from the 2 mentioned, I've played around with a few others on another partition:
* PC-BSD - FreeBSD with a "user-friendly" top on it.  Couldn't get my screen res bigger than 800x600, and the PBI installation system was *way* too much like Windows; I've never going back to google-download-next-next-next-finish again.
* Debian Etch - far too stable for me, and I wasn't particularly excited about Sid, but haven't tried it
* Crux - wanted to use my prexisting GRUB, couldn't get the right parameters to get it to boot, and documentation sucked so I dumped it and installed
* Gentoo - although I'm not particularly fond of source-based installations (see above), I've used it's wiki quite a bit, and decided to try it out.  Haven't had a chance to use it yet.
* FreeBSD - very brief experience on a side-project of mine.  Haven't had the chance to use in a desktop environment.

EDIT: I suppose I should clarify a little more what I want as far as "easiness".  From [this excellent article]("http://www.over-yonder.net/%7Efullermd/rants/userfriendly/userfriendly1.php"), I've begun to think of the term "user-friendly" really meaning three different things:
* easy to use
* easy to learn
* easy to use without learning

I'm looking for the first two fairly well-balanced.  I like being able to pick up on things quickly as long as they don't restrict me later on.  I also don't like spending forever getting something working, unless there is no easier way, and it's a project.

Actually it sounds like [OzOS]("http://cafelinux.org/OzOs/") would be perfect for you, it is based on Xubuntu but with an e17 WM, the distro is compiled from CVS so it is as update as you want it to be. 

If you want to stay with a Gnome desktop, the developers have an [B][oz-gnome-desktop]("http://cafelinux.org/forum/index.php/topic,1578.0.html"):

[/B] > The new one, kind of strange, it's a Ubuntu like Gnome Desktop: [**oz-gnome-desktop**]("http://cafelinux.org/forum/index.php/topic,1578.0.html"). 
My wife uses gnome, and although ubuntu-desktop is full compatible with oz-desktop/OzOS, it fills my installations with unneeded stuff... 
So i decided make a metapackage for a Gnome implemented *à la* Ubuntu (easy and very complete) but more flexible and without the fat and cholesterol.
I guess it may interest other users, that may want to have all comfort of Ubuntu but keeping things light
Essentially it won't force ubuntu-artwork, bluetooth and avahi support only on users choice, no brtty nor evolution installed. 
More gnome-ish apps are installed by recommend list, that means they can be skipped or removed without system require remove of the oz-gnome-desktop.[http://cafelinux.org/forum/index.php/topic,1578.0.html](http://cafelinux.org/forum/index.php/topic,1578.0.html)

Also I have found the [OzOS Forums]("http://cafelinux.org/forum/index.php") completely helpful, and the developers are accessible and friendly.

---

