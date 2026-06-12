---
title: "HOW-TO: sources.list"
date: 2005-10-14
forum: Outdated Tutorials &amp; Tips
---

### Post by humanity_to_others on 2005-10-14
You can acces your sources.list with that command in terminal:
```
sudo gedit /etc/apt/sources.list
```
or in kubuntu,
```
sudo kwrite /etc/apt/sources.list
```
just in terminal,
```
sudo nano /etc/apt/sources.list
```
Then you can just copy below repositories. You can change country code from de to your country code or the country code of a country near you.... You can also check out source-o-matic script page, too: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic). 

Some users need programs like latest wine, final OO2 and Opera Web Browser . If you actually want use these programs you can uncomment (remove **#** in front of their addresses) their repositories. 

_Some repositories:_
```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

deb http://de.archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse
deb http://de.archive.ubuntu.com/ubuntu/ breezy-security universe main restricted multiverse
deb http://de.archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse

#backports
deb http://de.archive.ubuntu.com/ubuntu breezy-backports main universe multiverse restricted

#backports-extras
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main universe multiverse restricted

#Penguin Liberation Front 
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

#wine
#deb http://wine.sourceforge.net/apt/ binary/

#opera web browser
#deb http://deb.opera.com/opera/ etch non-free

#OO2 final
#deb http://people.ubuntu.com/~doko/OOo2 ./

```

You can also find  ubuntu_demon's sources.list useful, which is in there: [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

Another tips from wiki: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

This How-to also in Ubuntu Document Storage Facility: [http://doc.gwos.org/index.php/Sources.list](http://doc.gwos.org/index.php/Sources.list)

---

### Post by majikstreet on 2005-10-14
Of course you want to substitute de for your country code or the country code of a country near you...

:KS  Great guide, thanks.

---

### Post by poofyhairguy on 2005-10-14
I just want everyone to know that this line:

> deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main

Should NOT be in there after you install the w32codecs and whatever. Put it in, get the codecs, then delete it out. Upgrading your system with that line left it can cause big problems.

---

### Post by Sav on 2005-10-15
Breezy backports?
Where?

---

### Post by Perfect Storm on 2005-10-15
There's is not breezy backports yet.

---

### Post by Annagul on 2005-10-15
(Sorry for my english...)

>  deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main 

What Debian-dist we must use on marillat's repos? Etch or Sid?

---

### Post by imagine on 2005-10-15
Etch is the name of the next release of Debian (the current is Sarge). You can compare it to Dapper.
Sid is just a synonym for the development version. Sid will never get released and will always be called Sid.

So you'll usually want to go for Sarge or Etch.

---

### Post by The Headhunter on 2005-10-15
Just for clarification...backports = multiverse?  Because when I try to enable multiverse, I see nothing other than the backports...

---

### Post by poofyhairguy on 2005-10-15
[QUOTE=Annagul](Sorry for my english...)



What Debian-dist we must use on marillat's repos? Etch or Sid?[/QUOTE]

Etch. But as soon as you install the codecs, delete the line! It CAN mess up your computer BAD if you upgrade with that line in your sources.list.

---

### Post by pelago on 2005-10-15
[QUOTE=The Headhunter]Just for clarification...backports = multiverse?  Because when I try to enable multiverse, I see nothing other than the backports...[/QUOTE]
No, backports and multiverse and different things.

---

### Post by Annagul on 2005-10-16
> But as soon as you install the codecs, delete the line! It CAN mess up your computer BAD if you upgrade with that line in your sources.list.


Ok. I commented that line after install the codecs. 

Thank you for all

From the very-south of Spain :razz: 

Luis

---

### Post by Jenda on 2005-10-16
[QUOTE=pelago]No, backports and multiverse and different things.[/QUOTE]
backports:
Because Ubuntu never upgrades the software in the stable version, as a policy to ensure stability, someone made the BACKPORTS - repos where you can uprade these packages, that are otherwise held back

multiverse:
Officially unsupported repositories (i.e. containing unsupported packages), that may include proprietary SW.

[QUOTE=poofyhairguy]I just want everyone to know that this line:

Quote:
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main

Should NOT be in there after you install the w32codecs and whatever. Put it in, get the codecs, then delete it out. Upgrading your system with that line left it can cause big problems.[/QUOTE]
WHOA
This aught'a be posted somewhere in big bright shiny letters!!!

---

### Post by celticmonkey on 2005-10-16
People waiting for the unoffical backports at mirrormax that contain things like win32 codecs should be aware that the unofficial backports have been closed. Permanently, if I'm not mistaken.

Read this sticky post at the backports forum:
[http://www.ubuntuforums.org/showthread.php?t=69681]("http://www.ubuntuforums.org/showthread.php?t=69681")

If I read it right, the official backport will open when there are more up-to-date dapper drake packages that can be backported to breezy, which ofcourse won't be for sometime. Non GPL stuff like win32 codecs and much other dubious material will not be in the official backports. It will be missing many things that we have come to expect from the unofficial backports.

The practical implication of this is that the information at the [unofficial ubuntu guide]("http://ubuntuguide.org/") is not useful for hoary or breezy. 

I don't think that this is popularly known among ubuntu users yet. Maybe I'm a bit thick, but I didn't realize this until after I'd tried to do a clean install of breezy. Ah well.

---

### Post by poofyhairguy on 2005-10-16
[QUOTE=celticmonkey]People waiting for the unoffical backports at mirrormax that contain things like win32 codecs should be aware that the unofficial backports have been closed. Permanently, if I'm not mistaken.

Read this sticky post at the backports forum:
[http://www.ubuntuforums.org/showthread.php?t=69681]("http://www.ubuntuforums.org/showthread.php?t=69681")

If I read it right, the official backport will open when there are more up-to-date dapper drake packages that can be backported to breezy, which ofcourse won't be for sometime. Non GPL stuff like win32 codecs and much other dubious material will not be in the official backports. It will be missing many things that we have come to expect from the unofficial backports.

The practical implication of this is that the information at the [unofficial ubuntu guide]("http://ubuntuguide.org/") is not useful for hoary or breezy. 

I don't think that this is popularly known among ubuntu users yet. Maybe I'm a bit thick, but I didn't realize this until after I'd tried to do a clean install of breezy. Ah well.[/QUOTE]


Actually, I have knowledge that this might not be as dead as you state. Its just not ready.

---

### Post by jetpeach on 2005-10-17
Whoa, this is bad - how do I enable mp3 support again?  I hate proprietary formats and all, but I have to be able to use them to make ubuntu worthwile.  Is anyone updating the guides/howtos on how in the world I can enable things like mp3 support?

---

### Post by r0nin on 2005-10-17
[QUOTE=poofyhairguy]Etch. But as soon as you install the codecs, delete the line! It CAN mess up your computer BAD if you upgrade with that line in your sources.list.[/QUOTE]

Why does this cause problems? Is Ubuntu so much different to Debian?

---

### Post by poofyhairguy on 2005-10-17
[QUOTE=jetpeach]Whoa, this is bad - how do I enable mp3 support again?  I hate proprietary formats and all, but I have to be able to use them to make ubuntu worthwile.  Is anyone updating the guides/howtos on how in the world I can enable things like mp3 support?[/QUOTE]


[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by poofyhairguy on 2005-10-17
[QUOTE=r0nin]Why does this cause problems? Is Ubuntu so much different to Debian?[/QUOTE]


Yes. That repo is meant for Debian. Updating with it in can make your apt-get break because its confused. Apt-get is the same program in Ubuntu and Debian. The sources.list tells it what it is, what distro its on, and what it needs to do.

When you have that line in and you upgrade, you computer's like "what am I, Debian or Ubuntu?" and it might refuse to do anything.

If fact, I'm so worried about it I think I'll edit this thread.

---

### Post by r0nin on 2005-10-17
[QUOTE=poofyhairguy]Yes. That repo is meant for Debian. Updating with it in can make your apt-get break because its confused. Apt-get is the same program in Ubuntu and Debian. The sources.list tells it what it is, what distro its on, and what it needs to do.

When you have that line in and you upgrade, you computer's like "what am I, Debian or Ubuntu?" and it might refuse to do anything.

If fact, I'm so worried about it I think I'll edit this thread.[/QUOTE]

Is this the same with any Debian repo (like Opera, Skype, Rarewares, ...) or just a specific Marillat problem?

---

### Post by manicka on 2005-10-17
This sources list created by one of the mods (aysiu) is well set out. Up to date Breezy and hoary versions available

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

---

### Post by poofyhairguy on 2005-10-17
[QUOTE=r0nin]Is this the same with any Debian repo (like Opera, Skype, Rarewares, ...) or just a specific Marillat problem?[/QUOTE]


Any Debian repo might cause problems, but using the main ones and Marillat are almost guarenteed to cause problems.

Stick to Ubuntu repos if you can.

---

### Post by samjam on 2005-10-17
[QUOTE=Annagul](Sorry for my english...)



What Debian-dist we must use on marillat's repos? Etch or Sid?[/QUOTE]

You can add THIS to your sources.list

deb-src [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main

and then build from source for breezy with

apt-get -b source libdvdcss
instead of just trying to install other folks binaries!

if the source won't build, try:
apt-get -b build-deps libdvdcss
apt-get -b source libdvdcss

replace the "libdvdcss" with whatever package you want to build.

There really is no need to install binaries from other debian distros when you can build the binary to fit your own.

Sam

---

### Post by manicka on 2005-10-17
This libdvdcss deb is built for ubuntu

[ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/libd/libdvdcss/libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb](ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/libd/libdvdcss/libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb)

I'd leave the marillat repo alone, it will break your system

---

### Post by samjam on 2005-10-17
[QUOTE=manicka]This libdvdcss deb is built for ubuntu

[ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/libd/libdvdcss/libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb](ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/libd/libdvdcss/libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb)

I'd leave the marillat repo alone, it will break your system[/QUOTE]

Well, I'd rather build my own debs from a source I trust than some random binary repository I never heard of, without source. (All thanks to the cipherfunk guy, but why should I trust it)

It can't break your system if you only have it in as a deb-src, it will only be used when building from source.

---

### Post by manicka on 2005-10-17
You are clearly someone who is comfortable with deb based distros knows how to take more advanced steps to maintain his system :) I don't believe that building debs from the marillat repos is the way to go for new users. If they stick with solutions that are made for ubuntu there will be fewer problems in the long run.

---

### Post by NeTo on 2005-10-17
[QUOTE=samjam]Well, I'd rather build my own debs from a source I trust than some random binary repository I never heard of, without source. (All thanks to the cipherfunk guy, but why should I trust it)

It can't break your system if you only have it in as a deb-src, it will only be used when building from source.[/QUOTE]

I follow a similar rule before adding a repository to the sources.list file. The repository should contain Ubuntu binaries (ideally) along with sources for all of the packages. Simply put, I don't trust a .deb if the source can't be downloaded along with it, even if I am not going to compile the package myself :p

For example, intead of downloading that deb from cipherfunk.org, I would rather add to sources.list:```

deb ftp://cipherfunk.org/pub/packages/ubuntu/ breezy main
deb-src ftp://cipherfunk.org/pub/packages/ubuntu/ breezy main
```

Well, if I wrote those correctly :p

That way, I can install the binaries which is easier. But if anything fails, I can always checkout the source for the cause :KS

---

### Post by poofyhairguy on 2005-10-17
[QUOTE=NeTo]I follow a similar rule before adding a repository to the sources.list file. The repository should contain Ubuntu binaries (ideally) along with sources for all of the packages. Simply put, I don't trust a .deb if the source can't be downloaded along with it, even if I am not going to compile the package myself :p

For example, intead of downloading that deb from cipherfunk.org, I would rather add to sources.list:```

deb ftp://cipherfunk.org/pub/packages/ubuntu/ breezy main
deb-src ftp://cipherfunk.org/pub/packages/ubuntu/ breezy main
```

Well, if I wrote those correctly :p

That way, I can install the binaries which is easier. But if anything fails, I can always checkout the source for the cause :KS[/QUOTE]


NICE! I edited and added that to the first post.

---

### Post by kedar85 on 2005-10-18
Just to be very sure ...
The main debian repos won't work with breezy badger?

Kedar

---

### Post by fut21 on 2005-10-18
If you wanna help, keyes who made "easy ubuntu, try to create a "ubuntu P.L.F" mirror. 
[http://placelibre.ath.cx/keyes/index.php/2005/10/03/48-depot-plf-ubuntu](http://placelibre.ath.cx/keyes/index.php/2005/10/03/48-depot-plf-ubuntu)

---

### Post by manicka on 2005-10-18
[QUOTE=kedar85]Just to be very sure ...
The main debian repos won't work with breezy badger?

Kedar[/QUOTE]

Yes, they will break your system

---

### Post by Arathorn on 2005-10-18
So it's impossible now to get mp3 files to work in 5.10? At least the method described in RestrictedFormats doesn't work anymore.

---

### Post by NeTo on 2005-10-18
Check the edited first post. You can download the w32codecs package using Synaptic if you add the two last lines of the sources.list shown there.

That means you can have mp3 support with a package built for breezy :D

---

### Post by poofyhairguy on 2005-10-18
[QUOTE=kedar85]Just to be very sure ...
The main debian repos won't work with breezy badger?

Kedar[/QUOTE]


They might, just like a car wheel might work or a big truck.

---

### Post by majed on 2005-10-19
[QUOTE=Arathorn]So it's impossible now to get mp3 files to work in 5.10? At least the method described in RestrictedFormats doesn't work anymore.[/QUOTE]
sudo apt-get install xmms and it will play MP3s right away.. :)

i like this better bcz its just as easy as winamp and it just works and its light too.. good luck!

---

### Post by manicka on 2005-10-19
[QUOTE=Arathorn]So it's impossible now to get mp3 files to work in 5.10? At least the method described in RestrictedFormats doesn't work anymore.[/QUOTE]
Try the method described here for breezy

[http://doc.ubuntu.com/gnome/faqi386/C/ch03.html#codecs](http://doc.ubuntu.com/gnome/faqi386/C/ch03.html#codecs)

---

### Post by Arathorn on 2005-10-19
Adding the multiverse and universe helped... thank all of you.

---

### Post by humanity_to_others on 2005-10-30
Thanks for your additions and I added Opera repository.

---

### Post by ubuntu_demon on 2005-11-08
My sources.list (I use it and recommend it) :
[http://www.ubuntuforums.org/showthread.php?t=87946](http://www.ubuntuforums.org/showthread.php?t=87946)

---

### Post by humanity_to_others on 2005-11-17
I added staging for backports, extras with extras staging and final OpenOffice2 for Ubuntu, thx.

---

### Post by ubuntu_demon on 2005-11-17
[QUOTE=humanity_to_others]I added staging for backports, extras with extras staging and final OpenOffice2 for Ubuntu, thx.[/QUOTE]
you should also add plf :
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

---

### Post by humanity_to_others on 2005-11-18
Added **plf** and **source-o-matic**, thank you.

---

### Post by humanity_to_others on 2005-11-18
I added some commands for editing sources.list and some deb-src repos.

---

### Post by christooss on 2005-11-18
[QUOTE=ubuntu_demon]you should also add plf :
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)[/QUOTE]

So with plf its safe to upgrade with and you can install codecs to? Right?

---

### Post by ubuntu_demon on 2005-11-18
[QUOTE=humanity_to_others]Added **plf** and **source-o-matic**, thank you.[/QUOTE]
good.Now you can remove cipherfunk because plf replaces it.

Also remove or comment backports-staging since this repo is intended for testing(instead of general use by the average desktop user).

I apreciate your efforts to clear things up for people. IMHO most people will like my sources.list. Some users need things like wine,OO2 and opera. But not everyone so you should comment them by default and recommend users to only uncomment them if they actually use them.

---

### Post by ubuntu_demon on 2005-11-18
[QUOTE=christooss]So with plf its safe to upgrade with and you can install codecs to? Right?[/QUOTE]
plf is not official supported but IMHO it's the safest way to install codecs and "restricted software".

---

### Post by manicka on 2005-11-18
I have added this how-to, to the 
Ubuntu Document Storage Facility

---

### Post by ubuntu_demon on 2005-11-18
[QUOTE=manicka]I have added this how-to, to the 
Ubuntu Document Storage Facility[/QUOTE]
please incorporate (some of) those tips of mine on there (you can also check my sources.list in my signature).

You guys are doing great work on the Document Storage Facility !

---

### Post by manicka on 2005-11-19
[QUOTE=ubuntu_demon]please incorporate (some of) those tips of mine on there (you can also check my sources.list in my signature).

You guys are doing great work on the Document Storage Facility ![/QUOTE]

Thanks, have made adjustments as suggested. 

I agree that the plf is the best source at the moments for codecs etc. I hope they sort out there server issues soon.

Thanks also for the comments on the Doc Facility. It's coming along nicely.

---

### Post by ubuntu_demon on 2005-11-19
[QUOTE=manicka]Thanks, have made adjustments as suggested. 

[/QUOTE]

great!

[QUOTE=manicka]
I agree that the plf is the best source at the moments for codecs etc. I hope they sort out there server issues soon.
[/QUOTE]

I've never had troubles with the mirror in my sources.list (yet?).

[QUOTE=manicka]
Thanks also for the comments on the Doc Facility. It's coming along nicely.[/QUOTE]

Yeah I really like it and I think Ubuntu users can benefit greatly from it. That's why I put it in my signature :).

---

### Post by humanity_to_others on 2005-11-19
All suggestions now in this How-to, thank you majikstreet, poofyhairguy (8 times), Sav, Artificial Intelligence, Annagul (2 times), imagine, The Headhunter, pelago, Jenda, celticmonkey, jetpeach, r0nin (2 times), manicka (7 times), samjam (2 times), NeTo (2 times), kedar85, fut21, Arathorn (2 times), majed, ubuntu_demon (6 times), christooss.

---

### Post by ubuntu_demon on 2005-11-20
I would not only comment the staging repo's but remove them to make it easier for the average desktop user.

Regarding the commented src repos. What's the thought behind this ? I don't think it speeds up stuff very much to comment them. And they can't hurt if they are uncommented.

---

### Post by humanity_to_others on 2005-11-22
You are right, removed deb-src and staging.

---

### Post by ubuntu_demon on 2005-11-23
[QUOTE=humanity_to_others]You are right, removed deb-src and staging.[/QUOTE]
I said uncomment src instead of remove :-P

I adapted my sources.list and included the wine,OOo2 and opera repositories (commentented) :

IMHO it's a good thing if we both recommend the same sources.list to the forum users. Would you use mine ?

[http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

### Post by frodon on 2005-11-23
I have a question regarding backports.

I already got some problems using backports under hoary, for example at the time when i updated gaim to the hoary backport version it broke my firefox.
So my question is, does the concept of the breezy backport is still the same ? I want to know if there're still some risks to use backports.

By the way, What is the breezy-extras repository ?

---

### Post by ubuntu_demon on 2005-11-23
here is some information about the backports  and the extras repo :
[http://www.ubuntuforums.org/showthread.php?t=40291](http://www.ubuntuforums.org/showthread.php?t=40291)

The backports are offical now so there should be less problems than previously. I wouldn't recommend backports for important servers though and I don't know whether I would use backports if I had to maintain a lot of workstations.

For more information about the backports you should go to the backports section and search/read/ask there.

---

### Post by humanity_to_others on 2005-11-24
[QUOTE=ubuntu_demon]I said uncomment src instead of remove :-P

I adapted my sources.list and included the wine,OOo2 and opera repositories (commentented) :

IMHO it's a good thing if we both recommend the same sources.list to the forum users. Would you use mine ?

[http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)[/QUOTE]
Misunderstood, feel free to edit this thread. Or removing this thread can be better.

---

### Post by ubuntu_demon on 2005-11-24
No I won't edit or remove this thread.

-It's a good thing to have a discussion about sources.list's
-the howto section is a place where people look. your idea to start a howto sources.list is good!
-I added opera,OOo2 and wine (all commented) to my sources.list. I got the idea from this thread.

My suggestion (but that is just my opinion) is that you use the sources.list I have here :

[http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

In the end users can and should make their own informed decision about what they put in their sources.list.

---

### Post by aznboi on 2005-11-24
Here is a new sources list for Ubuntu 5.10 Breezy
in terminal type:
```
sudo gedit /etc/apt/sources.list
```
in the new text editor, select all delete and copy and paste this into their:
```
# Ubuntu supported packages (packages)
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu supported packages (sources)
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages)
deb http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://us.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse

# Ubuntu community supported packages (sources)
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

# Seveas' packages (packages)
deb http://seveas.ubuntulinux.nl breezy-seveas all

# Seveas' packages (sources)
deb-src http://seveas.ubuntulinux.nl breezy-seveas all

# Ubuntu backports project (packages)
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# Ubuntu backports project (sources)
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# Cipherfunk multimedia packages (packages)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ breezy main

# Cipherfunk multimedia packages (sources)
deb-src ftp://cipherfunk.org/pub/packages/ubuntu breezy main

# Bleeding edge wine packages (packages)
deb http://wine.sourceforge.net/apt/ binary/

# Bleeding edge wine packages (sources)
deb-src http://wine.sourceforge.net/apt/ source/

# OpenOffice.org 2 final packages (packages)
deb http://people.ubuntu.com/~doko/OOo2/ /

# OpenOffice.org 2 final packages (sources)
deb-src http://people.ubuntu.com/~doko/OOo2/ /

# Penguin Liberation Front (packages)
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

# Penguin Liberation Front (sources)
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

# PlanetMirror (packages)
deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

# Backport-Staging (packages)
deb http://ubuntu-backports.mirrormax.net/ breezy-backports-staging main universe multiverse

# Extras-Staging (packages)
deb http://ubuntu-backports.mirrormax.net/ breezy-extras-staging main universe multiverse

# Extras (packages)
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main universe multiverse

```
save, exit and then in terminal type:
```
apt-get update
```
and it will update all the packages, (there are a ton of them) there should  be two errors at the end but thats ok.

---

### Post by ubuntu_demon on 2005-11-24
aznboi : I merged your thread with this one.

I didn't know about seveas's repo. I'll talk to him .. see whether it's intended for the average desktop user or not.

edit :
I talked to seveas. His repo is not intended for the average desktop user :

-his repo is kind of his personal repo playing ground
-he hasn't got the bandwith if we go announcing everybody should use his repo

---

### Post by ubuntu_demon on 2005-12-14
breezy-extras is empty and probably will stay empty according to jdong. So I removed the repository from my sources.list because it doesn't serve any function. In a way plf is the new breezy-extras.

---

