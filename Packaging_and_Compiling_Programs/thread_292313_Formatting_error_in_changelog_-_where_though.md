---
title: "Formatting error in changelog - where though?"
date: 2006-11-03
forum: Packaging and Compiling Programs
---

### Post by jamyskis on 2006-11-03
I've been trying to create Ubuntu packages for my games, but I'm stuck on following the tutorial at [http://doc.ubuntu.com/ubuntu/packagingguide/C/basic-scratch.html#id2566115](http://doc.ubuntu.com/ubuntu/packagingguide/C/basic-scratch.html#id2566115).

I've followed it exactly but when I go to create the debian package it returns with the error:

```

parsechangelog/debian: error: badly formatted heading line, at file debian/changelog line 9
dpkg-buildpackage: unable to determine source package is

```

The changelog file in question is:
```

naughts-and-crosses (0.8-0ubuntu1) edgy; urgency=low

  * Added new graphics engine, with the possibility of replacing the graphics, perhaps themes later on when level system is implemented. This includes proper graphics (256 colour) for the board and a centered board.
  * Changed resolution to 800x600, to allow for higher resolution graphics.
  * Made it possible to change the colour of the text when entering it as a parameter to the function.
  * Fixed bug whereby cursor colour was inconsistent when typing.
  * Further AI optimisations.

-- Darryl Lecount <darryl@jamyskis.net>  Thu,  2 Nov 2006 00:04:01 +0100

```

As far as I see there is nothing wrong with the formatting, but it insists there is. Am I missing something here? Thanks!

---

### Post by Jimmy_r on 2006-11-19
I am having the same problem...

---

### Post by Jimmy_r on 2006-11-19
My brain is...hurting...Bwahahahaha =P~ :-& :lol: =P~ :-& :cry: :confused:

Sorry, i need a break. Have been coding all day, and now trying to learn this...

---

### Post by mssever on 2006-11-20
> **jamyskis said:**
> I've been trying to create Ubuntu packages for my games, but I'm stuck on following the tutorial at [http://doc.ubuntu.com/ubuntu/packagingguide/C/basic-scratch.html#id2566115](http://doc.ubuntu.com/ubuntu/packagingguide/C/basic-scratch.html#id2566115).

I've followed it exactly but when I go to create the debian package it returns with the error:

```

parsechangelog/debian: error: badly formatted heading line, at file debian/changelog line 9
dpkg-buildpackage: unable to determine source package is

```The changelog file in question is:
```
[FONT=Courier New]1. naughts-and-crosses (0.8-0ubuntu1) edgy; urgency=low
2. 
3.   * Added new graphics engine, with the possibility of replacing the graphics, perhaps themes later on when level system is implemented. This includes proper graphics (256 colour) for the board and a centered board.
4.   * Changed resolution to 800x600, to allow for higher resolution graphics.
5.   * Made it possible to change the colour of the text when entering it as a parameter to the function.
6.   * Fixed bug whereby cursor colour was inconsistent when typing.
7.   * Further AI optimisations.
8. 
9. -- Darryl Lecount <darryl@jamyskis.net>  Thu,  2 Nov 2006 00:04:01 +0100
[/FONT]   
```As far as I see there is nothing wrong with the formatting, but it insists there is. Am I missing something here? Thanks!
Line 9 has to be indented, I believe. AFAIK the only line that begins in column 1 is the package name line. This is how apt distinguishes between entries.

---

### Post by Jimmy_r on 2006-11-22
Then the guide at [http://doc.ubuntu.com/ubuntu/packagingguide/C/basic-scratch.html#id2566115](http://doc.ubuntu.com/ubuntu/packagingguide/C/basic-scratch.html#id2566115) has an error:

> Here is a sample changelog file for hello:
```
hello (2.1.1-1) edgy; urgency=low

   * New upstream release with lots of bug fixes.

-- Captain Packager <packager@coolness.com>  Wed,  5 Apr 2006 22:38:49 -0700
```

---

### Post by LaserJock on 2006-11-23
> **Jimmy_r said:**
> Then the guide at [http://doc.ubuntu.com/ubuntu/packagingguide/C/basic-scratch.html#id2566115](http://doc.ubuntu.com/ubuntu/packagingguide/C/basic-scratch.html#id2566115) has an error:

Yep, that's not right. Thanks for catching that. I've fixed it in svn.

-LaserJock

---

### Post by jamyskis on 2006-12-01
That's great guys - thanks for the help. A few things it might be worth mentioning in the wiki:

[LIST]
[*][http://www.debian.org/doc/debian-policy/ch-source.html](http://www.debian.org/doc/debian-policy/ch-source.html) is a good resource
[*]Trailer line should be indented with *one space only*.
[*]It could be worth emphasising that the "rules" file should have the executable flag set. I only noticed that subtle note in the document after having googled for 20 minutes.
[*]Blank lines in the description of the control field are to be displayed as " ." and not just be left as a blank line.
[/LIST]

---

### Post by jamyskis on 2006-12-06
OK, I've decided to scrap packaging from scratch and try using Debhelper, but I'm having not much better luck.

I've unpacked the archive, run dh_make on it, created a source package with debuild -S and (attempted to) create a binary package using pbuilder.

The problems are as follows:

My game depends on liballegro4.2, but if I try to include this in the control file, pbuilder kicks up as it can't find it in the pbuilder environment.

Just ignoring the liballegro4.2 dependency and leaving it out of the control file, I can't find the source or binary debian files, only the orig.tar.gz, diff.gz and dsc files.

Can anyone help?

---

### Post by mssever on 2006-12-07
> **jamyskis said:**
> OK, I've decided to scrap packaging from scratch and try using Debhelper, but I'm having not much better luck.

I've unpacked the archive, run dh_make on it, created a source package with debuild -S and (attempted to) create a binary package using pbuilder.

The problems are as follows:

My game depends on liballegro4.2, but if I try to include this in the control file, pbuilder kicks up as it can't find it in the pbuilder environment.

Just ignoring the liballegro4.2 dependency and leaving it out of the control file, I can't find the source or binary debian files, only the orig.tar.gz, diff.gz and dsc files.

Can anyone help?

I've found this thread to be really useful when it comes to pbuilder: [http://ubuntuforums.org/showthread.php?t=206382](http://ubuntuforums.org/showthread.php?t=206382). There's a section on pbuilder hooks that allow you to include dependencies that pbuilder can't otherwise find. Also, pbuilder puts the resulting deb in its results directory, which you can configure.

By the way, Debian source packages are actually three files: the orig.tar.gz, the diff.gz, and the dsc file.

---

### Post by jamyskis on 2006-12-10
That's great - thanks for the help. I still can't get it to work - I've even installed liballegro4.2 and liballegro4.2-dev within the pbuilder environment manually (it found them so the hook config was fine) and it still came up with missing headers while compiling the binary package.

I think I'm going to have to give up on this and let someone else do the debian packaging for my games.

---

### Post by LaserJock on 2006-12-18
I don't have time to go through all the issues right now but I'd encourage everybody to try to get on IRC (irc.ubuntu.com is the server) and join #ubuntu-motu . That's where the Universe maintainers hang out and teach people to package.

It looks like one problem may be that you might not have the Universe repo in the pbuilder's sources.list .

-LaserJock

---

