---
title: "HOWTO: Anjuta DevStudio 2.0.2 for Dapper"
date: 2006-06-25
forum: Outdated Tutorials &amp; Tips
---

### Post by mlind on 2006-06-25
[INDENT]To build [anjuta]("http://anjuta.sourceforge.net/") 2.0.2 for Dapper, you also need to build newer versions of two additional libraries,
**[COLOR="Blue"]libgdl-1-0[/COLOR]** and **[COLOR="Blue"]libgbd-1-0[/COLOR]**, to satisfy the build-time requirements.
[/INDENT]




[SIZE="4"]Initial setup[/SIZE]
[LIST]
[*]Suggested procedure before starting is to install **debfoster** and run it once and answer *yes* (or no if you know what you're doing) asked questions. 
[*]This way you set *default* state for installed packages and can easily uninstall **all** anjuta build dependencies after building. 
[*]You can later "reset" debfoster using **-n** parameter after the whole buildprocess is complete and installed dependencies have been removed.
[/LIST]



[SIZE="3"]Setup build environment[/SIZE]
[LIST]
[*]Install required tools for building process
```

sudo aptitude install build-essential cdbs devscripts dh-make fakeroot

```
[/LIST]

[SIZE="3"]Setup APT repositories[/SIZE]
[LIST]
[*]Add Debian unstable repository to /etc/apt/sources.list
```

deb-src http://ftp.uk.debian.org/debian unstable main contrib non-free

```

[*]After adding, update
```

sudo aptitude update

```
[/LIST]



[SIZE="4"][COLOR="Blue"]libgdl[/COLOR][/SIZE]
[LIST]
[*]Get the source
```

mkdir -p ~/packages/gdl
cd ~/packages/gdl
apt-get source libgdl-1-0
cd gdl-0.6.1

```

[*]Insert new changelog entry
```

dch -iDdapper

```
```

gdl (0.6.1-**2ubuntu1**) dapper; urgency=low

  * Adopted for Dapper

 -- Firstname Lastname <youralias@yourmail.org>  Sun, 25 Jun 2006 13:23:33 +0300

```

[*]Install required build-time dependencies
```

sudo aptitude install libgconf2-dev libglade2-dev libgnomeui-dev

```

[*]Build and install
```

dpkg-buildpackage -rfakeroot -us -uc
sudo dpkg -i ../libgdl-1-*.deb

```
[/LIST]

[SIZE="4"][COLOR="Blue"]libgbf[/COLOR][/SIZE]
[LIST]
[*]Get the source
```

mkdir -p ~/packages/gnome-build
cd ~/packages/gnome-build
sudo aptitude update
apt-get source libgbf-1-0
cd gnome-build-0.1.3

```

[*]Insert new changelog entry
```

dch -iDdapper

```
```

gnome-build (0.1.3-**3ubuntu1**) dapper; urgency=low

  * Adopted for Dapper

 -- Firstname Lastname <youralias@yourmail.org>  Sun, 25 Jun 2006 13:16:43 +0300

```

[*]Build and install
```

dpkg-buildpackage -rfakeroot -us -uc
sudo dpkg -i  ../libgbf-1-*.deb

```
[/LIST]


[SIZE="4"][COLOR="Green"]anjuta[/COLOR][/SIZE]
[LIST]
[*]Get the source
```

mkdir -p ~/packages/anjuta
cd ~/packages/anjuta
apt-get source anjuta
cd anjuta-2.0.2

```

[*]Insert new changelog entry
```

dch -iDdapper

```
```

anjuta (2.0.2-**3ubuntu1**) dapper; urgency=low

  * Adopted for Dapper

 -- Firstname Lastname <youralias@yourmail.org> Sun, 25 Jun 2006 13:41:15 +0300

```

[*]Install required build-time dependencies
```

sudo aptitude install libpcre3-dev libgnomeprintui2.2-dev libgnomeprint2.2-dev libvte-dev libzvt2.0-dev automake libxslt1-dev autogen libdevhelp-1-dev libwnck-dev

```

[*]Build and install
```

dpkg-buildpackage -rfakeroot -us -uc
sudo dpkg -i ../anjuta_2.0.2-**3ubuntu1**_i386.deb ../anjuta-common_2.0.2-**3ubuntu1**_all.deb

```
[/LIST]



[SIZE="4"]Removing the build dependencies[/SIZE]
[LIST]
[*]If you installed **debfoster** as suggested in the beginning, you can now clear all build dependencies.
Answer **p** (as purge) for all questions regarding to applications and libraries installed on build process.


[*]Remove/comment debian source repository from /etc/apt/sources.list

[/LIST]

---

### Post by mlind on 2006-06-25
If someone has alternative for usage of deprecated **debfoster**, it would be great.

---

### Post by dabear on 2006-06-25
Someone wanna provide me the deb, so I don't have to go through the compile process? thanks.

---

### Post by mlind on 2006-06-27
[QUOTE=dabear]Someone wanna provide me the deb, so I don't have to go through the compile process? thanks.[/QUOTE]

Sure, I can upload the .debs for you if you say where. Personally I was quite
disappointed for this release, found few "not so nice" bugs laying around.

---

### Post by vasdee on 2006-06-27
i wouldn't mind some debs :) , try [http://www.freefilehoster.com]("http://www.freefilehoster.com") for hosting the packages.I've put some anjuta2 debs there from another thread ([http://www.ubuntuforums.org/showthread.php?t=191252]("http://www.ubuntuforums.org/showthread.php?t=191252")) however I really want to see if another build has the the 'project manager' option enabled and working, every deb i've tried so far has it greyed out or unselectable from the plugins menu :(

I think anjuta2 will be a damn fine program when it matures past its alpha status at the moment.

---

### Post by mlind on 2006-06-27
[QUOTE=vasdee]i wouldn't mind some debs :) , try [http://www.freefilehoster.com]("http://www.freefilehoster.com") for hosting the packages.I've put some anjuta2 debs there from another thread ([http://www.ubuntuforums.org/showthread.php?t=191252]("http://www.ubuntuforums.org/showthread.php?t=191252")) however I really want to see if another build has the the 'project manager' option enabled and working, every deb i've tried so far has it greyed out or unselectable from the plugins menu :(

I think anjuta2 will be a damn fine program when it matures past its alpha status at the moment.[/QUOTE]

okay, i uploaded .debs [here]("http://www.freefilehoster.com/uploads/1151419381anjuta-2.0.2_dapper.tar.gz")

I didn't get that "Project manager" -plugin working either. I'm not sure, but I  think
this feature needs glade-3, which is currently only on GNOME CVS. It smells so
fresh that I wouldn't go building it just yet. I didn't manage to build valgrind
plugin either, but other goodies should be there.


/edit
ah, file went AWOL.. reuploaded.

---

### Post by Hanj on 2006-07-04
Does anyone have a list of changes/new features for Anjuta 2 so I know if it's worth looking forward to? I'm currently using KDevelop since Anjuta simply doesn't have the features I need. I would be really nice with a good Gnome IDE though.

---

### Post by mlind on 2006-07-04
[QUOTE=Hanj]Does anyone have a list of changes/new features for Anjuta 2 so I know if it's worth looking forward to? I'm currently using KDevelop since Anjuta simply doesn't have the features I need. I would be really nice with a good Gnome IDE though.[/QUOTE]

You should try looking anjuta's home page and look for changelogs between
versions and roadmap they have. There was "What's new on 2.0" article, but I
couldn't find it anymore..

[http://anjuta.sourceforge.net/](http://anjuta.sourceforge.net/)
[http://sourceforge.net/news/?group_id=14222](http://sourceforge.net/news/?group_id=14222)

---

### Post by Hanj on 2006-07-04
Thanks, mlind. I was hoping for a better class generator and better code completion, but that doesn't seem to be happening. Sounds like it's still worth checking out though.

---

### Post by Hanj on 2006-07-04
I tried it and overall it looks really good. Clean, nice interface without any loss of usability. The class generator seems to be missing altogether though, which isn't good. Also, I couldn't find anywhere to edit linker options, what's up with this? I really hope a stable and usable version gets out soon.

---

### Post by mlind on 2006-07-04
[QUOTE=Hanj]I tried it and overall it looks really good. Clean, nice interface without any loss of usability. The class generator seems to be missing altogether though, which isn't good. Also, I couldn't find anywhere to edit linker options, what's up with this? I really hope a stable and usable version gets out soon.[/QUOTE]

I just tried compiling anjuta and tested it briefly, so I can't help you with this sorry.
Is that class generator feature that should be there?

---

### Post by vasdee on 2006-07-04
The class generator is there for me when I select "new >" from the menu, as for the automake options they are within the disabled "project manager" plugin :(

Hopefully the next release will have this enabled and bring anjuta to a usable state.

---

### Post by Hanj on 2006-07-04
> Is that class generator feature that should be there?Well, it was there in the earlier verision (from the repositories), but only as a quite unfinished plugin. Kdevelop has a much better generator, where you can simply pick a class name and an ancestor class and it will generate all the necessary files for you.

EDIT: Ah, there it is. Thanks vasdee! Look pretty ok, though not as powerful as the one in KDevelop.

---

### Post by mlind on 2006-07-04
[QUOTE=vasdee]The class generator is there for me when I select "new >" from the menu, as for the automake options they are within the disabled "project manager" plugin :(

Hopefully the next release will have this enabled and bring anjuta to a usable state.[/QUOTE]

That project management had something to do with glade3 which is still on
experimenatal state on Gnome CVS. I'll try rebuilding this to see if I can get it enabled somehow.

---

### Post by mlind on 2006-07-04
Well I just found out that 2.0.2 is still on alpha stage :-s 
So I don't think I'm going to bother.

I was able to include other features exept Valgrind and Glade plugins. I had to build
newer graphvitz too. If anyone wants packages, just say so.

---

### Post by Hanj on 2006-07-10
mlind: I take it you managed to get the project manager to work, so that Anjuta is actually usable? In that case I'd love to have the packages and try it out. Sorry for the late reply, btw.

---

### Post by mlind on 2006-07-10
> **Hanj said:**
> mlind: I take it you managed to get the project manager to work, so that Anjuta is actually usable? In that case I'd love to have the packages and try it out. Sorry for the late reply, btw.

Nope, couldn't get the project manager enabled, sorry. :( 
Maybe when next alpha/beta comes out..

---

### Post by Hanj on 2006-07-10
Ah, ok. I'll have to wait then :|

---

### Post by rko618 on 2006-08-19
> **mlind said:**
> Nope, couldn't get the project manager enabled, sorry. :( 
Maybe when next alpha/beta comes out..

Something tells me thats going to be a while.  According to their website version 2.0.1 came out 2005-06-27 and 2.0.2 was released 2006-05-15.  A good 11 months later.  Talk about a slow development cycle.

---

### Post by punkrockguy318 on 2007-03-31
anjuta 2.1.2 is out, and it's in BETA.  Perhaps someone could make some packages?

---

### Post by Nirro on 2007-04-01
I tried to ./configure it on Feisty (the 2.1.2 version).
The problem is that it wants libgdl-1 0.7.3. 
In Feisty it is still 0.6.1, and Debian unstable only has 0.7.2-1.
So I'm stuck.

---

### Post by punkrockguy318 on 2007-04-01
i just compiled libgdl and installed it to /usr/local and it worked alright

---

### Post by newen on 2007-05-19
There's a repository for installing Anjuta 2.1.3

> 1) Add 'deb [http://anjuta.org/apt](http://anjuta.org/apt) ./' in your /etc/apt/sources.list
2) Create a file called /etc/apt/preferences and enter the following:

Package: anjuta
Pin: version 2.*
Pin-Priority: 990

Package: anjuta-common
Pin: version 2.*
Pin-Priority: 990

Package: anjuta-dev
Pin: version 2.*
Pin-Priority: 990

3) sudo apt-get update
4) sudo apt-get install anjuta
(anjuta-dev, if you want to write anjuta plugins)

[http://ubuntuforums.org/showthread.php?t=441113](http://ubuntuforums.org/showthread.php?t=441113)

---

### Post by miggl on 2007-07-19
> **newen said:**
> There's a repository for installing Anjuta 2.1.3



[http://ubuntuforums.org/showthread.php?t=441113](http://ubuntuforums.org/showthread.php?t=441113)

Thanks for this! :)

---

