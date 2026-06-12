---
title: "Another Pidgin problem: not found in repository, can't build"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by pgranger on 2008-08-07
I've seen several other threads about problems with Pidgin, but I wasn't able to find a solution that worked for me. I know this isn't a Ubuntu question *per se*, but I know other people here have had similar issues, and these forums seem very well-informed.

I've been trying to install **Pidgin 2.4.3**, but I'll settle for any reasonably current version. I've tried a variety of approaches, but each time I've run into a problem of one sort or another. I am pretty new to Linux, but I am an old-time Unix user (from about ten years ago), so I'm not (too) scared by the command line.

I would LIKE to do this with the **Synaptic Package Manager**, but building from source is also acceptable, if I can find a way to do it.

**Attempt 1: Straight Package Manager install**

Simply opened Package Manager and searched (by name) for "pidgin" (without the quotes, of course). Nothing was found.

**Attempt 2: Find another repository for Package Manager to use**

Assuming that there must be a Pidgin package out there somewhere, I'll try finding a different repository. My Package Manager (freshly installed) lists only two repositories: security.debian.org/ (type = deb, distribution = etch/updates, sections = main contrib non-free) and http.us.debian.org/debian/ (type = both deb and deb-src, distribution = etch, sections = main non-free contrib). I know there are a lot of other respositories out there, but I'm having a hard time finding the right one and getting it added correctly. I find reference to Pidgin 2.4.3, listed as "unstable" at [[COLOR="Blue"]_http://packages.debian.org/sid/pidgin_[/COLOR]]("http://packages.debian.org/sid/pidgin"). I'd rather avoid "unstable" packages, but if I assume 2.4.3 is actually stable and just not verified as such yet, I'm willing to go with it.

Unfortunately, I can't find any way to tell Synaptic Package Manager to go and get this package. I tried adding packages.debian.org as a repository, but that didn't work. A pointer to a repository that has Pidgin in it, and a tip on how to add that repository to Package Manager would be a big help.

**Attempt 3: Download the package and have Package Manager install it**

Searching with Google led me to a site called GetDeb, and I found what appears to be a Debian package for Pidgin 2.4.3 at [[COLOR="Blue"]_http://www.getdeb.net/release/2883_[/COLOR]]("http://www.getdeb.net/release/2883"). I downloaded the file pidgin_2.4.3-1~getdeb1_i386.deb, but I haven't been able to find any way to get Synaptic Package Manager to use a downloaded file. When I click on "Add downloaded packages" it doesn't allow me to select this file, even though I can browse to that directory.

**Attempt 4: Build it from source**

I downloaded pidgin-2.4.3.tar.bz2 from the Pidgin site ([[COLOR="Blue"]_www.pidgin.im_[/COLOR]]("www.pidgin.im")), and extracted the archive. According to their INSTALL document, running ./configure in that directory should create a makefile, which can then be used to build the application. Unfortunately, running the configuration utility keeps on running into missing dependencies. I was able to fix a couple of them by finding the missing libraries with Synaptic Package Manager and installing them. But now it is stuck on:

[INDENT]checking for GLIB... no
no
configure: error:

You must have the GLib 2.0 development headers installed to build.[/INDENT]

Looking in Package Manager, I can find libglib2.0-dev, which sounds like the right thing. But when I mark it for installation, I get this error:

[INDENT]Depends: libglib2.0-0 (=2.12.4-2) but 2.12.6-2 is to be installed[/INDENT]

I have libglib2.0-0 and libglib2.0-data installed already, and they are both at 2.12.6-2. So the appearance is that libglib2.0-dev is looking for an OLDER version, 2.12.4-2, and complaining because it's finding a NEWER version, 2.12.6-2.

I think I've pretty much exhausted my options at this point.

Things like this are of course what turned me off Linux years ago, where every change precipitates a cascading failure of one missing dependency after another. I'd been reassured that nifty new things like the Synaptic Package Manager would take care of problems like this, and it seems that's USUALLY true, but not in this case.

Suggestions, please? Thanks.

---

### Post by spiderbatdad on 2008-08-07
how is it pidgin is not in your synaptic package manager? It doesn't even require universe/multiverse repositories...it is part of the base installation, located under the Applications>>Internet menu.

What version of Ubuntu are you running?

---

### Post by drs305 on 2008-08-07
spiderbatdad is correct if I recall correctly. Alternatively, I think this is the repository for pidgin. You can add it to your sources.list:

deb [http://ppa.launchpad.net/pidgin-developers/ubuntu](http://ppa.launchpad.net/pidgin-developers/ubuntu) hardy main

```
sudo gedit /etc/apt/sources.list
```

---

### Post by mudrain911 on 2008-08-07
Yeah Pidgin is packaged with Ubuntu. Did you uninstall it?

---

### Post by pgranger on 2008-08-07
> **drs305 said:**
> spiderbatdad is correct if I recall correctly. Alternatively, I think this is the repository for pidgin. You can add it to your sources.list:

deb [http://ppa.launchpad.net/pidgin-developers/ubuntu](http://ppa.launchpad.net/pidgin-developers/ubuntu) hardy main


Thanks, that at least got me partway there.

I added that repository, and pidgin 2.4.3 is found when I search. Unfortunately, trying to install it gets me a whole slew of unresolved dependencies, similar to what I saw in option #4 (in my original message). Although this time, at least it is looking for newer versions and failing because it finds older ones.

I'm surprised those dependencies don't update automatically, but at least it gives me something to go on.

As for what version I'm running...I honestly have no idea. I just started a new job, and the dev machine they gave me seems to be stuck together with baling twine and chewing gum. Didn't even have a Package Manager when I started, but I was able to figure out how to at least use dselect to install Synaptic.

(My home system is in much better shape, and running a new-ish version of Mint, but that doesn't help me here.)

---

### Post by spiderbatdad on 2008-08-07
It sounds like a minimal install, rather than the desktop version.
Try some of these commands:```
uname -r
```
```
cat /etc/lsb-release
```
```
cat /etc/apt/sources.list
```
If you post the results here, you can get more help on completing you sources.list of updating the package manager.

---

### Post by pgranger on 2008-08-07
> **spiderbatdad said:**
> 
If you post the results here, you can get more help on completing you sources.list of updating the package manager.

Okay, now I am both embarrassed and terrified. Embarrassed because it seems I am not even running Ubuntu here -- I'd just made a false assumption. Looks like it's actually Debian. (I know I'm running Ubuntu and Mint at home, I guess my brain just conflated home and work.)

And terrified, because I just realized how old this thing is.

To answer your questions:

[INDENT]> uname -rso
Linux 2.6.18-3-686 GNU/Linux

> cat /etc/lsb-release
cat: /etc/lsb-release: No such file or directory[/INDENT]

(Presumably because I'm not actually on Ubuntu?)

[INDENT]> cat /etc/apt/sources.list
deb [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) etch main non-free contrib
deb [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib non-free
deb-src [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) etch main non-free contrib
deb [http://ppa.launchpad.net/pidgin-developers/ubuntu](http://ppa.launchpad.net/pidgin-developers/ubuntu) hardy main[/INDENT]

That's as expected, the three I had originally plus the one I just added.

One other very interesting thing, though. sources.list is current, but there's also sources.list~ in the same directory, with a date of July 6, 2003.

[INDENT]>cat /etc/apt/sources.list~

deb cdrom:[Debian GNU/Linux 3.0 r1 _Woody_ - Official i386 Binary-1 (20021218)]/ unstable contrib main non-US/contrib non-US/main[/INDENT]

Am I *really* running a version of Debian from late 2002?

Between being non-Ubuntu, and being so old, it's not surprising that this is missing so many of the things I've come to expect.

So...my apologies for questioning the Ubuntu forums when it seems that I'm not even running Ubuntu here. I think, though, that I'm at least on the right track here, once I get those dependencies resolved.

---

### Post by drs305 on 2008-08-07
It's "lsb_release -a". That will tell you what you are running.

Come on over to ubuntu, the water's fine!

---

### Post by spiderbatdad on 2008-08-07
That falls into the category of "stuff happens." No need to apologize for a simple mistake. We're here to help. Resolving all the unmet dependencies may take some effort, but is doable, at least you have the 2.6 base kernel. Not experienced enough to know if you can just add the Hardy (gutsy may be better in this case) repos and solve your problems. Maybe someone else can advise better. But the complete list of gutsy or hardy repos is available.

---

### Post by tuxxy on 2008-08-07
lol you could always try an install of Ubuntu now its yours :)

---

### Post by pgranger on 2008-08-08
> **drs305 said:**
> It's "lsb_release -a". That will tell you what you are running.

Come on over to ubuntu, the water's fine!

Well, due to the release I'm running, I don't have an lsb_release command, or at least not anywhere on my path (another thing I'm having to re-learn after my long absence from Unix-land).

Would *love* to come over to Ubuntu, but I'm afraid I'm stuck with what they've given me here. As mentioned before, I've recently set up a pretty current Mint system at home, and I really like it. It's given me none of the trouble with missing dependencies that I've experienced with older versions.

> **spiderbatdad said:**
> No need to apologize for a simple mistake. We're here to help.

Much appreciated -- I've seen (as I'm sure everyone has) other forums where a mistake by an earnest newb would precipitate an all-out flame-fest.

> **spiderbatdad said:**
> Resolving all the unmet dependencies may take some effort, but is doable, at least you have the 2.6 base kernel. Not experienced enough to know if you can just add the Hardy (gutsy may be better in this case) repos and solve your problems. Maybe someone else can advise better. But the complete list of gutsy or hardy repos is available.

I'd taken a look at the repository list I'm using in my Package Manager at home, and it's much bigger, and presumably more up-to-date. I considered copying it down and trying to add those same repos here at work, but since most of them included "ubuntu.org" (or something similar -- I can't see them now) in the URL path, I wasn't sure about compatibility, so I didn't try it.

I expect I'll be chasing dependencies for a while, but you know, "determination and problem solving skills" were part of the reason I got this job. Maybe they're just testing me. ;)

> **tuxxy said:**
> lol you could always try an install of Ubuntu now its yours :)

Tempting, very tempting. But I don't think ops would take kindly to a new contractor blowing away the entire OS on day one. Or day three, in this case.

Thanks again, guys, for your info and courtesy.

Oh, and BTW, **Spiderbatdad** -- I couldn't help noticing your profile says you're up in the Northeast Kingdom. I'm also a Vermonster, grew up in Rutland. So they actually have electricity...and the Internets -- out in the sticks now? :D

---

### Post by ratthing on 2008-08-17
I would suggest you are best off taking a look at the Debian docs to find out what repos are appropriate for woody.  While *buntu and Debian are close enough that we use the same tools, the repos are pretty divergent, since Debian is focussed more on server stability.

Another thing I might suggest is taking the "security" and "stability" lines of argument and ask about upgrading your system based on them.  Unless there's something required in that aging release for the work you and the other developers there are doing, I can't really see why they would not let you upgrade it.

=RT=

---

