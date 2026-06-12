---
title: "Ubuntu installation timing out"
date: 2013-08-07
forum: New to Ubuntu
---

### Post by b_shah2 on 2013-08-07
Hey guys, 

As the title says, my computer cannot finish the installation of ubuntu onto my computer because the installation times out before it can finish. To elaborate for you, the standard "Welcome To Installation" screen shows up, then I click "Install Ubuntu", and... nothing. The computer will then not respond for say an hour or so, and then if Im lucky (Ive tried this installation multiple times), it moves onto the next screen about "Preparing to Install Ubuntu", where all the requirements are meet except the internet isn't connected. The computer isn't able to connect to the internet... this might be the issue, but if it is, then I need help installing ubuntu without an internet connection. Anyhow, I **don't** click "Install third party software", and click next. And nothing happens. Ive left the computer at that screen for hours before yet, no further progress is made. Also FYI i was using the CD-ROM to perform the installation, not a USB port.

As for a little information about the computer:
The computer is Sony Vaio Desktop Computer **Model # [COLOR=#000000]PCV-RZ24G. [/COLOR]**[COLOR=#000000]Here is the support page: [http://esupport.sony.com/US/p/model-home.pl?mdl=PCVRZ24G&template_id=1&region_id=1&tab=manuals#/manualsTab](http://esupport.sony.com/US/p/model-home.pl?mdl=PCVRZ24G&template_id=1&region_id=1&tab=manuals#/manualsTab)
The computer is currently running Windows XP, 32 bit.
The computer has a 100 gigabyte HD, and a 256 Megabyte RAM.
The computer has a Pentium 4 microprocessor, running at 2.4 GHz

Im sorry if i gave too much information, i don't know what will be useful to solve the problem. And if there is any other information needed, just ask. Any help would be appreciated, Thank You.[/COLOR]

---

### Post by Petro Dawg on 2013-08-07
As a first step, I would try re-downloading and re-burning the Ubuntu ISO image to a new CD.  It's possible there is an issue with a corrupted installation disk, lets find that out before troubleshooting further.

I'm not sure which version you are trying to install, but make sure you are installing the 32 bit version of Ubuntu (I would suggest using 12.04.2 for now).

---

### Post by Cheesemill on 2013-08-08
256MB of RAM probably isn't enough to run the live installer, let alone an installed copy of Ubuntu.

If you really want to get a Ubuntu derivative on that machine then try installing Lubuntu using the alternative CD as this uses a text mode installer. You can download the iso from here...
[http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/)

However, 256MB of RAM will still be to little to give you a usable installation, as soon as you fire up a browser you'll have no memory left.

---

### Post by Boab1993 on 2013-08-08
I agree with cheesemill, lubuntu is a bit hard going for your computer.

Check out Debian:

[http://www.debian.org/](http://www.debian.org/)

Its pretty much a precursor to ubuntu, and only requires a minimum of 8MB of RAM and 512MB of diskspace to run and you can still have all the popular applications on it.

Hope this helps

---

### Post by 3rdalbum on 2013-08-08
256 megabytes of RAM is nowhere near enough for Ubuntu. That's why it's taking an hour to get to the next screen in the installer. You definitely can't run Ubuntu on that. If you increased the RAM to a gigabyte you'd be able to run Ubuntu, but that computer's a bit too old to be running a recent full-featured Linux distro. Ubuntu requires 3D acceleration as well to run its GUI and your laptop is probably not up to that.

However, there is a lighter derivative of Ubuntu, called Lubuntu. It's not as attractive, and it runs a different desktop environment (GUI) to normal Ubuntu. However it will run on 256 megabytes of RAM with no 3D acceleration, and you can install any software that can be installed on normal Ubuntu. Same repositories, and mostly the same software running underneath the GUI. I can't promise it will be fast, but apparently even with 256mb of RAM it will be usable.

For a bit more information, check out: [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

You might be thinking "Oh, but since my computer is old, maybe I could run an old version of Ubuntu...". The earliest version of Ubuntu that's still supported is 12.04, which was only released last year and will still be too heavy for your machine. You will be unable to install any software on an earlier version of Ubuntu, so it's not worth you even trying. Go with Lubuntu 13.04.

---

### Post by Werne on 2013-08-08
> **3rdalbum said:**
> ...but that computer's a bit too old to be running a recent full-featured Linux distro.
Not really, it's all about what you use and how much you're willing to fiddle with it. I was running Debian Squeeze LXDE on 256MB RAM and AMD Athlon 64 3200+ 2.0GHz (the single-core one) and it worked quite well, used 68MB on idle. That changed a bit after upgrading to Wheezy though, uses 82MB on idle and Iceweasel is more RAM demanding so I swapped it for Midori, but that's about it.

And now that I think about it, the latest Debian stable release is an oldtimer compared to half of Linux distributions, so it's not really recent.

Also, I don't think Lubuntu would work, especially 13.04. It may say 256MB on the system requirements but it uses 120-150MB on idle alone, fire up a web browser and it ate all the RAM. I have a 512MB RAM HP NX6310 that gets tortured by it, but it's my wife's laptop so I can't say I care much.

---

### Post by Cheesemill on 2013-08-08
> **Werne said:**
> And now that I think about it, the latest Debian stable release is an oldtimer compared to half of Linux distributions, so it's not really recent.

I wouldn't really call 3 months old 'not recent' :)

Another distro you could try is [#!]("http://crunchbang.org/") (CrunchBang), it's always the first thing I go for on older low-spec machines.

---

### Post by Werne on 2013-08-08
> **Cheesemill said:**
> I wouldn't really call 3 months old 'not recent'
Leave sources.list as-is and it becomes pretty old, pretty soon. A lot of the stuff designed for desktop usage is a bit aged and will be that aged (sometimes stays the same version) untill EOL. Luckily, all I need is a mozilla team repo and I'm good, even Squeeze is new enough for me then (plus, I prefer GNOME 2).;)

But I digress...

Anyway, yup, CrunchBang is pretty good on old machines, Openbox is not really my thing (I prefer Fluxbox) but it's decent once you get used to it. With 256MB RAM there aren't many choices, with any more demanding DE (GNOME, KDE, Unity, XFCE is a big maybe) it would either swap like crazy and be slow as sloth (partly due to swapping, partly due to old CPU), or wouldn't work at all, and neither of those is good.

---

### Post by Rob Sayer on 2013-08-08
When you hear that linux runs well on computers with limited memory, well, that's true.  Technically 'linux' is the kernel itself as far as I've been able to tell.  That's the part that controls the hardware and allows the OS and apps to run.  It indeed runs in a small memory space

What they don't tell you is that the desktop GUI environment that ship with various linux distros *doesn't* run in a very small space.

As mentioned by others here who know a hell of a lot more than I do, 256M ram is a stretch even for lubuntu.

---

### Post by Petro Dawg on 2013-08-08
I didn't see the 256M RAM spec when I first commented.  I agree that is probably a little low to run any 'buntu version at a usable speed (even Lubuntu would be iffy).

A small investment in RAM would definately be worth it.  I have 2 Pentium4 PCs running Ubuntu just fine, but I did max out RAM first.

It looks like you can upgrade to 1G for under $30 (if you shop carefully), which should be enough to use Xubuntu or Ubuntu2D.

Otherwise you might give [puppy linux]("http://puppylinux.org/main/Download%20Latest%20Release.htm") a try, I've had the current slacko puppy (5.5) running well on machines far weaker than yours (and keep an encrypted installation of it on USB on my keychain at all times).  Using [UNetbootin]("http://unetbootin.sourceforge.net/") to create a bootable puppy USB from which you can save and boot your puppy distribution is easy and prevents you from having to mess with the partitions on your Windows harddrive.  If I wasn't using Ubuntu, I would use puppy.

---

### Post by Rob Sayer on 2013-08-09
An upgrade to at 1Gb memory (at least) would be a very good idea for the OP.

I'm not sure, however, I'd recommend unity 2D or even gnome-fallback for 2Gb or less.  They still use compiz.  On my 4Gb i3 based laptop they were speedier than standard unity 3D but still too slow for me.  I went to xubuntu and then setted on kubuntu.

Kubuntu is often not recommended here for less than 2Gb ram, but I use it on my 1Gb netbook.  It's not quite as fast as xubuntu in hardware terms.  But it has so many more features that it speeds *me* up to the the point it's faster overall.

KDE is endlessly tweakable ... which may be seen as a good or bad thing ... and you can make it run a lot faster on slower hardware with 1-2Gb.  First install kubuntu-low-fat-settings.  This will turn off graphic effects and disable a number of startup services that slow everything down and I don't need.

Then go to settings->application appearance->style.  Select 'cleanlooks' for widget style.  This makes a surprisingly large difference.

Also settings->desktop effects->advanced.  Set compositing type to xrender and qt graphics to raster.  This also makes a big difference on older gpu's.

I'm not saying the OP shouldn't use xubuntu with some added ram.  I used to use it and xfce is a good gui environment.  But I find kde is way more powerful - more so than unity IMO - and can be configured for slower machines.  The only downside for me is that with all that power comes a ton of settings.  This may frustrate newbies.

---

### Post by b_shah2 on 2013-08-09
Hey guys,

I just wanted to thank all of you for the responses. All the suggestions for alternate distros were great, even though I feel like they would downgrade in comparison to WinXP Pro, (but then again, i havent tried them so i wouldnt know). Anyhow i actually ended up stripping an ram disk from another computer by Sony, and luckily, it fit! Adding an extra 128 MB of Ram to the original 256 for a total of 384. I know, its not a huge difference, but enough to take me through the installation in an half an hour. Which is a huge improvement over the hours it was taking before.

Anyhow, i just wanted to thank everybody, so Thank You.

---

### Post by Rob Sayer on 2013-08-10
With 384Mb you may be able to run lubuntu.  I wouldn't even try any other ubuntu version.  Good luck.

---

### Post by Boab1993 on 2013-08-10
Glad your happy with result on the forum, be sure to keep in touch with community.

Remember to mark the thread as solved so other users can find the infomation!

---

