---
title: "Help me find a new distro!"
date: 2008-10-19
forum: Other OS Talk
---

### Post by Istonian on 2008-10-19
I am trying to find a distro that is up to date. I also want it to have a huge repository. Gnome preferably. Anyone know any good distros?

---

### Post by cardinals_fan on 2008-10-19
Arch would fulfill those requirements.

---

### Post by smartboyathome on 2008-10-19
If you don't mind setting it up, Arch is great for being up to date.

---

### Post by Istonian on 2008-10-19
I have always had trouble setting Arch up. I might give it a go. Suggest some more while I try Arch.

---

### Post by SuperSonic4 on 2008-10-19
[Mandriva 2009.0 GNOME version]("http://torrent.mandriva.com/public/")
[Linux Mint]("http://www.linuxmint.com/download.php")
[Ubuntu]("http://www.ubuntu.com/getubuntu/download")

---

### Post by Istonian on 2008-10-19
Mandriva doesn't have very big repos. I like access to a lot of software. I know Arch has AUR so that has to make the software choices plentiful.

I am looking at Arch and the beginners guide is scaring me. So much stuff to do to get your system working. I don't know if I can handle it.

---

### Post by cardinals_fan on 2008-10-19
> **Istonian said:**
> 
I am looking at Arch and the beginners guide is scaring me. So much stuff to do to get your system working. I don't know if I can handle it.
Did you read the first heading: "DON'T PANIC!"?

Arch is **much** easier to set up than most people think, provided that your hardware plays along.  Trust me, it isn't hard - Pacman does all the legwork.

---

### Post by Istonian on 2008-10-19
Ok, ok. I don't have a printer though so I will have to find a way to have the guide with me while I install and configure Arch.

---

### Post by cardinals_fan on 2008-10-19
> **Istonian said:**
> Ok, ok. I don't have a printer though so I will have to find a way to have the guide with me while I install and configure Arch.
The live CD includes the beginners guide (I think it's in /arch, but I'm not sure).

---

### Post by -grubby on 2008-10-19
> **cardinals_fan said:**
> The live CD includes the beginners guide (I think it's in /arch, but I'm not sure).

it's located at /arch/beginnersguide.txt

---

### Post by wolfen69 on 2008-10-19
go out and buy a stack of blank cd's and hit up distrowatch.com. if you ask for opinions about what to try next, you'll get many different opinions.

---

### Post by chucky chuckaluck on 2008-10-19
arch isn't as scarey as it sounds. i've installed it three different times (to try different file systems) and i had relatively few minor issues that were quickly cleared up. and i'm just a humble end user who finds most documentation tl/dr.

---

### Post by wolfen69 on 2008-10-19
i'm glad i'm over that phase. i've tried over 30 distros. mandriva and ubuntu work *for me*.

---

### Post by d_skillz on 2008-10-19
I'd say try Mandriva 09 OpenSuse 11 they both are great options Arch can be daunting for a newbie.

---

### Post by brucenduane on 2008-10-19
If you want a huge repository, try Ubuntu with ~25,000 packages not counting source in the Synaptic package manager.  It is a Live CD and comes in several flavors, Ubuntu, Kubuntu, Edubuntu, Xubuntu, and non-live DVD UbuntuStudio.

A fun simple distribution is Puppy Linux by Barry Kauler & friends out of Australia.  No big repository but a hand-coded simple yet very complete Linux in less than 90 MB and runs in memory.  Barry's development blog is worth checking out at [http://puppylinux.com/blog](http://puppylinux.com/blog).

---

### Post by Sorivenul on 2008-10-20
I would suggest tying Arch, as well.  It is far from as scary as it seems at first, IMO.

Mandriva 2009 GNOME is great, and the repository has plenty of applications.  What applications or types of applications are you looking for that something like Mandriva wouldn't have?

If you're looking for something simple and GNOME based, paldo might be for you.  No "huge" repository, but again, everything the average user needs.  And you can always create your own packages.

Slackware may also be an option, if you don't mind doing a little bit of setup.  It's a great system to learn, IMO, and again you can make your own packages.

Good luck!

---

### Post by NullHead on 2008-10-20
Gentoo, or Debian-Sid.

---

### Post by SomeGuyDude on 2008-10-20
True story about setting up Arch. The ONLY hard part is getting Alsa/users/X going on and even that's just time consuming. The installation part is just a breeze. During the entirety of the setup (before the reboot), here was ALL I had to do:

- Change the size of my swap partition (I did auto-prepare)
- Add a few packages from base that I know I need (wireless stuff, sudo, ntfs support)
- Edit rc.conf to put in my timezone and throw 'etho="dhcp"' under network
- Open and close the locales thing so it generated whatever it generates
- Set my root password.

That was literally all. I'm pretty positive you can install Arch from the CD without actually changing any options aside from specifying your network connection.

---

### Post by coxy on 2008-10-20
Debian Lenny or even Debian Sid (won't be as stable as Lenny).

You won't find many distros with bigger repos than Debian.

---

### Post by ghodkiller on 2008-10-20
Debian works for me as a wonder

[Linux Archive]("http://www.linux-archive.org/")

---

### Post by phoenix_snake on 2008-10-20
> **Istonian said:**
> I am trying to find a distro that is up to date. I also want it to have a huge repository. Gnome preferably. Anyone know any good distros?

I just tried openSUSE recently and I think its good according to the requirements you listed.

Huge repos, loads of packages after adding the repos.

Up to date, programs were up to date after adding all those repos.

Yes, it has gnome as well.

Oh yeah another thing, its easy to use, looks good as well.

Hope this helps.

[http://en.opensuse.org](http://en.opensuse.org)

---

### Post by Istonian on 2008-10-20
I think the biggest thing for me is setting up configuration files and setting up for users and sound. I have did a Debian base install and built my system from that. How much different is Arch?

---

### Post by Sorivenul on 2008-10-21
> **Istonian said:**
> I have did a Debian base install and built my system from that. How much different is Arch?
Really, not much.  It's still Linux, so most of the same tools are there.  Read the Arch Beginner's Guide to get a taste of what's in store both during and post-install.  If you can build a Debian system from the ground up, you can do Arch, in my estimation.  The big difference you'll run into is Arch's pacman vs. Debian's apt-get/aptitude as far as the "building" goes.  I've never really heard an Arch user complain about pacman, and as one myself, I find it a joy to work with.

---

