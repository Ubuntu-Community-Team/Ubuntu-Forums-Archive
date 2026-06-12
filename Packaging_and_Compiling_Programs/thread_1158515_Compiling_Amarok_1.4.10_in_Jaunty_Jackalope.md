---
title: "Compiling Amarok 1.4.10 in Jaunty Jackalope"
date: 2009-05-13
forum: Packaging and Compiling Programs
---

### Post by kevCast on 2009-05-13
I'm trying to compile Amarok 1.4.10 in Jaunty Jackalope. I meet every dependency, however, every time I attempt to compile it, it complains about Ruby not having header files or something like that. I have ruby-dev installed. I have build-essential installed. What is going on?

---

### Post by raffraffraff on 2009-05-14
This is no help, but at least you know that you're not alone. I'm also trying to get Amarok 1.4.10 in Jaunty with libmp4v2 support but it ain't easy. (Seriously, does nobody in Jaunty land use Amarok and m4a files? How are they going to temp those Mac heads?)

---

### Post by raffraffraff on 2009-05-14
A gentoo forum reported this error (different builds of everything) but said that installing rubygems fixed it. Just FYI, it didn't fix it for me...

---

### Post by raffraffraff on 2009-05-14
Holy f... After installing every damn Ruby related package in the repository, I decided create a symbolic link from /usr/bin/ruby1.8 to /usr/bin/ruby. And it worked! I don't recommend using that method though, as it's non-standard and you can pass an alternative value to the script. This is my 'final' command line:

RUBY=/usr/bin/ruby1.8 CFLAGS=-Os ./configure --prefix=/usr --with-mp4v2 --with-libnjb --with-libmtp --enable-mysql --with-xine --without-arts --without-daap --without-ifp --without-libgpod

Notes:
Optimizing for file size gets a small boost performance because Amarok doesn't have any optimizations in its code.
If you've got m4a files, --with-libmp4v2 doesn't work! You need to use --with-mp4v2 instead.
I have a Creative Zen X-fi, but no iPod or Rio. So I enable libnjb and libmtp, and disable libgpod & ifp.

---

### Post by raffraffraff on 2009-05-14
And finally it failed to complete the build due to an incompatibility with the newer libmtp8. To get around this, download this patch:

[http://www.freshports.org/audio/amarok-kde4/files/patch-amarok_src_mediadevice_mtp_mtpmediadevice.cpp](http://www.freshports.org/audio/amarok-kde4/files/patch-amarok_src_mediadevice_mtp_mtpmediadevice.cpp)

...and apply it to [SOURCE]/amarok/src/mediadevice/mtp/mtpmediadevice.cpp

You should now be able to do a make && sudo make install.

It takes AGES to launch the first time (and it doesn't help that the splash screen was turned off! I had no idea if it worked or not.) Plus, any scripts that use python-dcop will cause trouble - I gonna miss particularly good lastfm suggestion script until I can fix that, or until they move if off DCOP.

---

### Post by kevCast on 2009-05-14
> **raffraffraff said:**
> This is no help, but at least you know that you're not alone. I'm also trying to get Amarok 1.4.10 in Jaunty with libmp4v2 support but it ain't easy. (Seriously, does nobody in Jaunty land use Amarok and m4a files? How are they going to temp those Mac heads?)

> **raffraffraff said:**
> A gentoo forum reported this error (different builds of everything) but said that installing rubygems fixed it. Just FYI, it didn't fix it for me...

> **raffraffraff said:**
> Holy f... After installing every damn Ruby related package in the repository, I decided create a symbolic link from /usr/bin/ruby1.8 to /usr/bin/ruby. And it worked! I don't recommend using that method though, as it's non-standard and you can pass an alternative value to the script. This is my 'final' command line:

RUBY=/usr/bin/ruby1.8 CFLAGS=-Os ./configure --prefix=/usr --with-mp4v2 --with-libnjb --with-libmtp --enable-mysql --with-xine --without-arts --without-daap --without-ifp --without-libgpod

Notes:
Optimizing for file size gets a small boost performance because Amarok doesn't have any optimizations in its code.
If you've got m4a files, --with-libmp4v2 doesn't work! You need to use --with-mp4v2 instead.
I have a Creative Zen X-fi, but no iPod or Rio. So I enable libnjb and libmtp, and disable libgpod & ifp.

> **raffraffraff said:**
> And finally it failed to complete the build due to an incompatibility with the newer libmtp8. To get around this, download this patch:

[http://www.freshports.org/audio/amarok-kde4/files/patch-amarok_src_mediadevice_mtp_mtpmediadevice.cpp](http://www.freshports.org/audio/amarok-kde4/files/patch-amarok_src_mediadevice_mtp_mtpmediadevice.cpp)

...and apply it to [SOURCE]/amarok/src/mediadevice/mtp/mtpmediadevice.cpp

You should now be able to do a make && sudo make install.

It takes AGES to launch the first time (and it doesn't help that the splash screen was turned off! Plus, any scripts that use python-dcop will cause trouble - I gonna miss particularly good lastfm suggestion script until I can fix that, or until they move if off DCOP.

Thank you so much! This fixed it. gcc output is scrolling as I type. One last question:  this isn't too important, but do you know how to get libvisual support in ./configure? Again, thank you.

---

### Post by raffraffraff on 2009-05-23
> **kevCast said:**
> Thank you so much! This fixed it. gcc output is scrolling as I type. One last question:  this isn't too important, but do you know how to get libvisual support in ./configure? Again, thank you.

No bother. Amarok + Jaunty + MP4 tag support was something that I absolutely require. Sharing knowledge is the thing that makes humans better than animals. (Well, a little better)

Most of the default options in ./configure should be sensible, so I'd imagine that libvisual is enabled. If you want to be 100% certain...

--with-libvisual

Read the configure script - it lists everything that it can do.
grep "\-\-with" configure

Scripts:
By the way, I've found that pydcop isn't available in Jaunty. I tried installing a .deb from launchpad, but it complains that it needs Python < 2.6. I installed Python 2.5 and changed the /usr/bin/python symlink to point to 2.5, but this error won't go away. [Edit: This also broke other stuff, so I've reverted] I'm pretty sure that this is the reason why lyrics, wiki and the scripts won't work. This is really crap because I use Amakode to convert m4a files to MP3 because my *stupid* Creative Zen X-Fi won't accept these files (though it's supposed to). Maybe I can fix the X-Fi thing without Amakode, but I'll still miss the "lastfm-similar.py" script...

(I was going to compile python-dcop under Python 2.5, but if I keep compiling stuff at this rate, I'll end up with Gentoo.)

---

### Post by SDNick484 on 2009-05-23
How did you get around:
<<<<
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE libraries installed. This will fail.
So, check this please and use another prefix!
>>>>

I'm using a slight variation of your configure line with (different CFLAGS, and enabling daap), but it's failing there every time.  I did an apt-cache search on kde3, but don't see anything that's obviously missing.

---

### Post by ssri on 2009-05-29
wow, talk about a trip through dependency hell.  Thanks for sharing your experience.  I too desire m4a playback and tag support in amarok 1.4.

---

### Post by kevCast on 2009-06-03
> **SDNick484 said:**
> How did you get around:
<<<<
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE libraries installed. This will fail.
So, check this please and use another prefix!
>>>>

I'm using a slight variation of your configure line with (different CFLAGS, and enabling daap), but it's failing there every time.  I did an apt-cache search on kde3, but don't see anything that's obviously missing.

You need to install the kdelibs-dev package.

```
sudo aptitude install kdelibs4-dev
```

---

### Post by raffraffraff on 2009-06-03
[QUOTE=SDNick484;7333917]How did you get around:
<<<<
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE libraries installed. This will fail.
So, check this please and use another prefix!
>>>>

I had that problem too, hence my prefix is hardcoded to --prefix=/usr, but that didn't work.  In the end I just took the 'kitchen sink' approach to KDE dependencies and installed all of the major KDE3 lib and dev packages I could find. That eventually worked, and I didn't narrow it down to any particular packages. Sorry, not much help.

I was thinking about building several optimized Amarok 1.4 .deb files for a variety of situations (just to practise making Debian package files with proper dependency resolution). If I do, then I'll either post them here or create an Amarok 1.4 repository for Jaunty where you can pick the version with the feature you want.

However, if I can't get scripts working on Amarok 1.4 and if Amarok 2 gets anywhere near usable, I'll bite the bullet and 'upgrade'.

---

### Post by raffraffraff on 2009-08-13
> **kevCast said:**
> You need to install the kdelibs-dev package.

```
sudo aptitude install kdelibs4-dev
```

Wow, I'm back again, this time with my netbook. I still thoroughly [HATE Amarok 2]("http://briancarper.net/blog/songbird-vs-amarok-how-not-to-design-a-gui"). Cheers kevCast, the kdelibs-dev package was indeed missing.

Seriously, does anybody have the time and skills necessary to create an Amarok14 repository for Karmic with these bells and whistles enabled by default? I don't feel like going through this all over again. And I've learned to live without the scripts. Basic AM14 will do.

---

### Post by raffraffraff on 2009-08-19
I still haven't given up.

I did get Amarok to compile perfectly well, with M4a tag and a bunch of other stuff working. But without DCOP in Jaunty, scripts don't work and that's just... not good enough.

I uninstalled Amarok and removed all KDE packages. I added the Pearson Computing PPA for KDE3.5. I installed the libraries, headers and stuff from it and now I'm trying to recompile. However, I'm told that "The program 'kde-config' is currently not installed", even though it's in /opt/kde3/bin. If I use its full path (or hardcode the prefix "/opt/kde" into my ./configure command) I am told that there are no headers.

Has ANYBODY managed to compile KDE3 apps using the dev packages from the Pearson PPA? Tips? I emailed the maintainer, but I thought I'd post here just in case...

UPDATE: Got it working. export KDEDIR=/opt/kde3 && export PATH=$PATH:/opt/kde3/bin
Now I have DCOP and M4A tagging, just like in the Hardy Medibuntu version! Wow, what a journey. Anyway, this gives me the ability to use scripts like Amakode, Web Control etc. Groovy. I'll post a script + my deb file when I get back home tonight.

---

### Post by ssri on 2009-08-19
Nice, looking forward to your compile script!

---

### Post by ssri on 2009-08-21
I figured out a way to get around the 24-bit FLAC problem for amarok14 in jaunty, and it might be applicable to you.  Apparently, there was a regression between libxine1 1.1.15 (intrepid) -> 1.1.16 (jaunty).  It is pretty easy and I'm sure you can figure it out.  Major hassles included finding out which dependencies were needed and installing Jaunty's dummy package for libcucul0.

For everyone else, here's the guide:

[http://ubuntuforums.org/showthread.php?t=1245938](http://ubuntuforums.org/showthread.php?t=1245938)

---

