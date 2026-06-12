---
title: "So, I'm just about to use Ubuntu for developing stuff."
date: 2005-07-12
forum: Programming Talk
---

### Post by the_it on 2005-07-12
Been bored, so I decided "Why not I'll use today to try and figure out what nice IDEs we have in the repositories?".  I'm trying to develop SDL applications (and learn lisp) from MSDev at home on my win98 box, but it's slow and horrible (my box).  At work, on the other hand, my machine is uber powered, and its got my favorite distro which I installed and customized.  Might as well make the most of it and start hacking here!

So I included all the way up to multiverse in synaptic, but there's still a large ton of packages to choose from.  What would you suggest would be a nice IDE (or a number of IDEs) in our repositories to start learning Lisp, Lush, and SDL in?  Since I've got unlimited fast net here, they'll download in a snap.  Any suggestions?

===

I forgot to add php/webproject management to that.  Screem, for now, looks slow and buggy (but promising).  I'm going to try Quanta, unless there's anything else you could suggest.

---

### Post by trivialpackets on 2005-07-12
[QUOTE=the_it]Been bored, so I decided "Why not I'll use today to try and figure out what nice IDEs we have in the repositories?".  I'm trying to develop SDL applications (and learn lisp) from MSDev at home on my win98 box, but it's slow and horrible (my box).  At work, on the other hand, my machine is uber powered, and its got my favorite distro which I installed and customized.  Might as well make the most of it and start hacking here!

So I included all the way up to multiverse in synaptic, but there's still a large ton of packages to choose from.  What would you suggest would be a nice IDE (or a number of IDEs) in our repositories to start learning Lisp, Lush, and SDL in?  Since I've got unlimited fast net here, they'll download in a snap.  Any suggestions?

===

I forgot to add php/webproject management to that.  Screem, for now, looks slow and buggy (but promising).  I'm going to try Quanta, unless there's anything else you could suggest.[/QUOTE]
 For a web project, I have been messing around with nvu, and that's available in the repositories.  As to lisp, I have no experience in that, however my professor works with AI in lisp, and said to pass on that he uses EMACS and says that it is very good for lisp development, due to the tools available and the configurability of it.  I've looked at it, and it's not the most user friendly at first but he assured me that it is a very powerful lisp editor and his preference.

---

### Post by the_it on 2005-07-13
What's nvu?  Can't seem to find it in the repositories.

---

### Post by m87 on 2005-07-13
nvu IS in the repositories [I'm using breezy], it's located in 'universe'

if you want some IDE's, there is anjuta2 which is by the way still a beta [or alpha] release but supports most C/C++ development and it's suitable for working with GNOME. Even KDevelop seems to be good (although I have never used it due to my KDEphobia).

emacs is the best choice ever :) it's the editor that I use for EVERYTHING, although it is a bit tricky when it comes to maintaining complex websites. for everything else, emacs is absolutely great. it has everything you need to code anything (it has code completion too!), it's more an operating system than an editor ^^

marco

---

### Post by the_it on 2005-07-14
whoa.  I think my repository listing must be old or something, coz I'm getting refusals.  Anyone care to give me a quick link to the latest (not breezy) repositories? thanks.

===

scratch that.  For some reason yesterday I was getting net problems.  I can get to the repositories now.

---

### Post by m87 on 2005-07-14
if you're not using breezy you can't ask for "newer" hoary repositories..
this may help

```
deb http://archive.ubuntu.com/ubuntu hoary main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://no.archive.ubuntu.com/ubuntu/ hoary-backports main universe multiverse restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ hoary-backports main universe multiverse restricted
```

marco

**EDIT**: oops, just read that you solved the problem.

---

### Post by the_it on 2005-07-14
Hmm?  What's the hoary-backports?  I don't seem to have that in mine... maybe that's why I still don't see nvu?

What's the full name of nvu btw.  Maybe I can query for that.

---

### Post by bored2k on 2005-07-14
[QUOTE=the_it]Hmm?  What's the hoary-backports?  I don't seem to have that in mine... maybe that's why I still don't see nvu?[/QUOTE]
[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)
> About Ubuntu Backports
Ubuntu Linux is a great distribution, but falls short in the desktop realm to Gentoo and Fedora Core. Why? Once a stable version is released, no new software updates are accepted. I subscribe to the view that a distribution can be both stable and up-to-date, so I've taken it into my own hands to recompile newer packages from Hoary and Debian Sid for Warty. They are maintained mostly by Jdong. [http://ubuntuforums.org/member.php?u=780](http://ubuntuforums.org/member.php?u=780)

Add this to your /etc/sources.list:
> ## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by the_it on 2005-07-14
I still can't seem to find nvu, although connection is good.  Here's a dump of my sources.list

```
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse #All Ubuntu normal packages
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted universe multiverse #All Ubuntu Source packages

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu/ hoary-updates main restricted universe multiverse #All Ubuntu normal updates
deb-src http://ph.archive.ubuntu.com/ubuntu hoary-updates main restricted universe multiverse #All Ubuntu source updates

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe multiverse #Security
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe multiverse #Security Source

## Other repositories not normally included in synaptic
deb http://no.archive.ubuntu.com/ubuntu/ hoary-backports main universe multiverse restricted #Hoary Backports
deb-src http://no.archive.ubuntu.com/ubuntu/ hoary-backports main universe multiverse restricted # Hoary Backports
deb http://wine.sourceforge.net/apt/ binary/  #Wine packages
```

===
wait okay now I see nvu.  It's either in the extras or the backports.  Can I get an authentication key for that so that synaptic doesn't complain? thanks.

---

### Post by m87 on 2005-07-14
no, you just have to say 'y', there is little possibility to get backdoors through official repositories  :-P

---

