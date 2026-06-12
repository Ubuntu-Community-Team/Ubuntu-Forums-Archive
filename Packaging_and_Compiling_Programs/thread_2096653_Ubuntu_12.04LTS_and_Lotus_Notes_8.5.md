---
title: "Ubuntu 12.04LTS and Lotus Notes 8.5"
date: 2012-12-20
forum: Packaging and Compiling Programs
---

### Post by Altispeed on 2012-12-20
Greetings,

First my apologies to the moderators if this is not posted in the correct place. Our company runs mostly on open source software. All of our workstations are using either Fedora or Ubuntu. One necessary piece of proprietary software we have is Lotus Notes. A few of our guys have tried installing it following the guide posted below. Despite much effort from the folks involved with that post, and our attempts we still do not have a usable notes client on Ubuntu. Ideally we would like to have a .deb package that we can just install.

As we are a for profit company and we try to make every effort to support the open source community and leach off of it, we would like to compensate any individual willing to help us with this project. We can supply the .deb package that IBM offers as well as the script that someone wrote on the blog post below that supposedly modifies the .deb so that it can be installed. 

Thank you all for your consideration, and again please forgive us if this is posted in the wrong section.



[http://usablesoftware.wordpress.com/2012/05/04/install-lotus-notes-8-5-3-on-ubuntu-12-04-64bit/](http://usablesoftware.wordpress.com/2012/05/04/install-lotus-notes-8-5-3-on-ubuntu-12-04-64bit/)

---

### Post by tgalati4 on 2012-12-20
The blog post is quite detailed and is titled "64-bit".  Were the problems you experienced on 32-bit machines?  In other words do you have a mixed environment of 32-bit and 64-bit machines and you can't get it running on 32-bit?

Somehow "leach" and "Open Source Community" don't belong in the same sentence.

---

### Post by Altispeed on 2012-12-20
Thank you for your prompt reply. All of our machines are 64 bit Ubuntu.

> **tgalati4 said:**
> Somehow "leach" and "Open Source Community" don't belong in the same sentence.

Agreed that's why we felt it appropriate to offer compensation since we are using open source products for profit.

---

### Post by tgalati4 on 2012-12-22
So, after following the extensive blog-post, what were the errors that you experienced?  Since I assume that you contacted the author of the blog and couldn't resolve your problem--what are the differences between the blog-post procedure and your current computing environment?

---

### Post by Altispeed on 2013-01-05
Sorry for the delayed response, Christmas etc...

Both were up to date systems. We have tried using both 12.04 and 12.10 to no avail. The problem we ran into is, after following all of the steps, it failed to resolve a few of the packages from the repos. We manually downloaded those packages and installed them. When we attempted to run the (modified) .deb package it populated in the software center but displayed an ! instead of the "install" button and had the text "gdb:i386".

---

### Post by tgalati4 on 2013-01-05
So you have experienced what we call *Dependency Hell*.  When you manually download packages (from somewhere) you don't know the history of those packages, what patches have been applied, what compilation switches were flipped to make the packages.

Sometimes you get lucky and you can mix and match packages between distros (Ubunutu and Debian for instance) and you get lucky and you get a working application.  Other times you get burned and completely bork a system.  But at least you get to keep the pieces.

Why don't you post the packages that you couldn't resolve?  And post the reasons that you couldn't resolve the packages.  Then post the locations of the manually installed packages so we can see the differences.  Sometimes packages have the same name between distros, but have slight differences (patches) so that mixing and matching becomes an exercise in frustration--*Dependency Hell*.

The detailed blog instructions looked straight-forward.  Where did it fail?

Reminds me of a Christmas story:

A couple of weeks ago, I get a call from a client that they needed help lighting their fireplace (natural gas).  So I light it and there is only a small flame.  I go outside and find that the gas meter has an earthquake shutoff valve that had tripped, shutting off the gas.  So I reset it and I get the fireplace lit.  The homeowner said they wanted to heat the house with it.  I said that this is decorative, it's really not designed to heat your whole house.  Why do you need to heat your house with the fireplace?

"Because the furnace isn't working."  Why isn't the furnace working?  I poke inside and the cables to the control board are disconnected--someone's previous troubleshooting.  I reconnect everything, check for leaks, and it works. "Hurray, we have heat for Christmas."

"My son stepped on the gas meter to get on the roof to hang the Christmas lights.  Do you think that tripped the earthquake valve?"

What does Lotus Notes have that can't be replicated with Open Source software?  Are you trying to fix the fireplace, when what you really want is heat?

---

### Post by PhilGil on 2013-01-05
It seems to me that most of your problems are coming from trying to get a working install of 32-bit Notes on a 64-bit platform. I don't know how many workstations you'd need to re-image, but why not just install 32-bit Ubuntu instead?

If you look at [IBM's system requirements]("http://www-01.ibm.com/support/docview.wss?uid=swg27019218"), they only recommend 32-bit platforms

---

### Post by niekn on 2013-01-06
latest ubuntu is miltiarch but it can cause some conflicts between 32-bit libs and 64-bit, for example: I had to install a crosscompiler for school but the compiler was only 32-bit and was 6 years old, when I tried to install it, it depended on gcc-32-bit and that tried to uninstall gcc-64-bit, luckily they had a source-repo so i compiled the compiler myself for 64-bit. but since that option won't work with lotus notes you can try the following:

```
dpkg-deb -x <package.deb> <directory>
```

this will extract all the files from the archive to a folder.
see what is installed where and search for de dependecies inside the control file, install them manually and try to launch the executable from terminal, when it shows something like "error while loading shared libraries lib<blahblah>.so" then find that file (local or on the internet) and try again with the file in the same folder as the executable OR use LD_PRELOAD=lib<blahblah>.so

this is how i usually solve these issues...

---

### Post by tgalati4 on 2013-01-06
I would build a 32-bit Ubuntu workstation and try to put Lotus Notes on that first.  If that works, then you know you have a 32-bit/64-bit problem.

---

### Post by Altispeed on 2013-01-07
Okay...from a fresh install

Below is the error copied from the terminal

```
libmotif3 was not found in your repositories
Make sure you have all repositories enabled and updated
E: No packages found
libgnome-desktop-3-0 was not found in your repositories
Make sure you have all repositories enabled and updated
Downloading ...
Installing libraries ...

```

I'm a long time RedHat user so I'm VERY familiar with dependency hell since we were still in it while you fancy Ubuntu folks were a few steps ahead ;)

Your point about open source software is well taken.

There might be a very good server based application delivery software, perhaps something like an Ulteo of sorts that would work, but I haven't really researched it as completely leaving Domino at this point isn't much of an option (see below).


A couple of reasons we are using Lotus. First and foremost because our company does Domino administration having the lotus client is a must. (I'm irritated enough that Domino Designer and the Admin client have to be run on Windows) but at least there is a webadmin client now.

The second reason is our company has spent a lot of money and time training Domino Developers so right now when we need an application it can get pawned off on anyone.

Playing devils advocate for Domino/Lotus for a minute. It's awfully nice that we can develop a piece of software in the notes client and then it simply works on the web without much alteration.

Coming full circle I guess the answer to your analogy is "We paid too much time and money for the fireplace, and have to many other people trained, and currently using the fireplace to dump it and use the furnace."


@PhilGil it's not so much reimaging alot of workstations, (there arn't that many) real problem is that the new laptops we ordered were The Dell XPS Developer Edition that ship with their own version of Ubuntu (Sputnik) which has support for this irritating new design of a mouse the Mac style clickpad. If we don't use that specific build of Ubuntu then you can't rest your thumb on the mouse pad.

Niekn & Tgalati4

Your points are also very well taken. I will install a 32bit Ubuntu build here tonight and post back results.

Again, thanks so much to everyone who is taking their time to help us solve this problem.

---

### Post by tgalati4 on 2013-01-07
Well, if you were a Unix guy, then you would recognize Motif Widgets.  It looks like you are missing a package called libmotif3.  

tgalati4@Dell600m-mint14 ~ $ apt-cache search libmotif
libmotif-dev - Open Motif - development files
libmotif4 - Open Motif - shared libraries
libmotif4-dbg - Open Motif - shared libraries

It looks like the default Ubuntu distribution only has libmotif4.

So, adding another log to the fire:

1.  Modify build scripts to point to libmotif4 and hope it works.  ln -s libmotif3 libmotif4

2.  Compile libmotif3 in a current Ubuntu build environment.  "Open Motif" should have source code available somewhere.

3.  Find precompiled binaries (*.deb) of libmotif3 from someone else who faced a similar problem.

4.  Find libmotif3 on an older version of Ubuntu and build that workstation to use for development.  I know Jaunty has it.

I love sitting by the fireplace. ](*,)

---

### Post by Altispeed on 2013-01-21
Okay, so I finally got around to installing a sacrificial Ubuntu 12.04 32 bit box.

Install goes great, no problems, and in fact it populates in Application lens. It opened a terminal and prompted for the usual agreement which I accepted. Now nothing happens.

I really wish IBM would make more Ubuntu friendly software! Valves doing it.
(I've waited five years to say that)

@tgalati4 I love sitting by the fireplace too...when it's on ;) Next up I'll try what you posted on the libmotif3 package. Thanks for your continued help!

---

### Post by Altispeed on 2013-01-21
Tried my level best for each of the solutions you suggested for a 64 bit system to no avail.

The timing of this problem couldn't be worse, just spent a while playing with Fedora 18. While I've never had a problem using Lotus in Fedora (with a little tweaking). The installer alone of Fedora 18 is practically unusable. A total switch to Ubuntu at this point seems imminent. 

Would there be a way to package libmotif3.deb WITH the lotus.deb?

---

### Post by matsbekman on 2013-08-04
Just installed Notes 9 on Ubuntu 64 without problems.
Installing it completely with no errors in the operating system


[http://wp.me/p1CuQM-hQ](http://wp.me/p1CuQM-hQ)


For reading on how to

---

