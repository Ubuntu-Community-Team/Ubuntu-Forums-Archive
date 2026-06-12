---
title: "A basic building block - running/installing programs"
date: 2012-12-12
forum: New to Ubuntu
---

### Post by 3Megatons on 2012-12-12
Hi, everyone.  Newish user.  Tried Red Hat for about a week maybe a decade ago.  Currently digging into Ubuntu Studio.

After not finding anything remotely close to my phrasing in searches, online manuals, etc., I feel I must be missing the point somewhere.  Here's my problem:

How to either run, or install to be run, a program outside the package manager.

I've downloaded Xonotic, and running source on the apparent executable files yields this:
bash: source: xonotic-[any of the four choices]: cannot execute binary file

If there's a Readme among these files, I'm just not seeing it.  I haven't seen a compatibility listing that warns of particular builds that can't run this.  It's supposed to be compiled for Debian.

:confused:

---

### Post by squakie on 2012-12-12
Well, I have no clue about the software you're talking about, but I would try the following:

- make sure the binaries have execute permissions for world (or at least the group you are in)

- try "sudo xxxxxxxxxxxxx" to run your command(s)

As far as installing software, the repositories ( via apt-get or the gui'd front-end to it synaptics package manager) are the place to get software.  The package managers make sure you are getting the correct software for your release of Ubuntu, and find and install the dependencies (the software "depends" on these to run).  Going outside of the package managers usually means a lot more work and you can run into dependency heck - get 1 dependent package only to find it relies on another only to find it relies on another for many, many times.

For packages outside of the repositories and the package managers, what to download and how to install it is left to the person/group that developed the packages.  There will be no standard, and Ubuntu can't tell you what to do.  Look for a README or some such file in what you downloaded for instructions on how to install a given package.

---

### Post by capscrew on 2012-12-12
> **3Megatons said:**
> Hi, everyone.  Newish user.  Tried Red Hat for about a week maybe a decade ago.  Currently digging into Ubuntu Studio.

After not finding anything remotely close to my phrasing in searches, online manuals, etc., I feel I must be missing the point somewhere.  Here's my problem:

How to either run, or install to be run, a program outside the package manager.

I've downloaded Xonotic, and running source on the apparent executable files yields this:
bash: source: xonotic-[any of the four choices]: cannot execute binary file

If there's a Readme among these files, I'm just not seeing it.  I haven't seen a compatibility listing that warns of particular builds that can't run this.  It's supposed to be compiled for Debian.

:confused:

You have to install the deb package before you can run it.  :-)

See here for how to do the install:
**_[COLOR="DarkSlateGray"]http://www.thegeekstuff.com/2010/06/install-remove-deb-package/[/COLOR]_**

If you don't have the deb package in your download it is available here:
[**_[COLOR="DarkSlateGray"]http://pkgs.org/search/?keyword=xonotic[/COLOR]_**]("http://pkgs.org/search/?keyword=xonotic") -- Just look for your version of Ubuntu or Debian.

---

### Post by capscrew on 2012-12-12
> **squakie said:**
> Well, I have no clue about the software you're talking about, but I would try the following:

- make sure the binaries have execute permissions for world (or at least the group you are in)

- try "sudo xxxxxxxxxxxxx" to run your command(s)

As far as installing software, the repositories ( via apt-get or the gui'd front-end to it synaptics package manager) are the place to get software.  The package managers make sure you are getting the correct software for your release of Ubuntu, and find and install the dependencies (the software "depends" on these to run).  Going outside of the package managers usually means a lot more work and you can run into dependency heck - get 1 dependent package only to find it relies on another only to find it relies on another for many, many times.

The deb packages also place things as Debian (and Ubuntu) expect them to be.  

For packages outside of the repositories and the package managers, what to download and how to install it is left to the person/group that developed the packages.  There will be no standard, and Ubuntu can't tell you what to do.  Look for a README or some such file in what you downloaded for instructions on how to install a given package.

There are standards.  Debian and all its derivatives use the apt package manager which is the front end to dpkg.  That means *aptitude* and *apt-get* are really just more convenient front ends to dpkg.  

Synaptic and USC are GUI front ends to the apt system.  They are all related.  Generally speaking if the install is packaged as a deb (compiled binaries) then it will pick up the dependencies.  Packaging for deb is is setup to do that already.  The real problem comes from compiling from source code.  The user has to figure out the possible dependencies.

---

### Post by audiomick on 2012-12-12
> **capscrew said:**
> There are standards....

Squakie did say "outside the repositories and package manager". If you can get a .deb package and install with some vartiation on the apt theme, then you are not outside the package manager. Yes, there are standards for a .deb or an .rpm or whatever package. If, however, the developer doesn't go as far as making a finished .deb or whatever, there is not really any fixed rule for what might be in the file you get. It will likely be a tar.gz, it might have a read-me in it or it might not. It might be source code that you have to compile. It might have and install script or it might not.

> **3Megatons said:**
> How to either run, or install to be run, a program outside the package manager.

This is indeed a vexing question. I have searched a number of times myself, and actually never found anything definitive where I could say "ah, that explains it all".

As I indicated further up, in a file that is not a .deb package, it is a bit pot luck what you get. Compiling from source means you get the program as the developer wrote it (source code) and you have to run it through a compiler to turn it into something that the computer can run. The advantage to this is that, as far as I understand it, the compiler knows what hardware you have and compiles the program specifically for it. I believe it can theoretically allow faster operation of the program, but I believe the difference is also marginal these days.

Your best bet is, of course, to stick to what is available from the repositories of your distribution. Someone has put some effort into making sure what is in there will work with the system, so things out of the repos should not give you any bother.

The first step away from there, with Ubuntu at least, is a PPA. 
[http://en.wikipedia.org/wiki/Personal_Package_Archive]("http://en.wikipedia.org/wiki/Personal_Package_Archive")
That is a place where a developer can make packages available that are not in the main repositories. If you include a PPA in your package sources, the system updater will look there for updates.

Failing that, look for a .deb package. I think you would have realised that by now, on the strength of the previous posts. That is a package that you can install using the tools of your package management. This is desirable, as it keeps your package management up to date on what is and is not installed on the system.
Here is some reading about .deb packages and about the package management tools.
[http://en.wikipedia.org/wiki/Deb_%28file_format%29]("http://en.wikipedia.org/wiki/Deb_%28file_format%29")
[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool]("http://en.wikipedia.org/wiki/Advanced_Packaging_Tool")

For good measure, about compilers
[http://en.wikipedia.org/wiki/Compiler]("http://en.wikipedia.org/wiki/Compiler")

and a link from that page that looks interesting
[http://la-samhna.de/library/compile/index.html]("http://la-samhna.de/library/compile/index.html")

This is by no means an exhaustive listing of all your possibilities, and may even not be completely accurate, but I hope it will give you a hand hold on the whole business of installing programs on your system.

---

### Post by squakie on 2012-12-12
Thanks audiomick for clarifying my post to someone else who obviously can't read.

As an extension of what you posted on compiling - config usually sets up the make file by checking for libs, compilers, etc..  The compiler would generate the code itself in the hardware instruction set.  I know you know that and where probably making a simple explanation for the newer users, so I hope you don't mind me expanding on that a little. ;)

---

### Post by squakie on 2012-12-12
> **capscrew said:**
> There are standards.  Debian and all its derivatives use the apt package manager which is the front end to dpkg.  That means *aptitude* and *apt-get* are really just more convenient front ends to dpkg.  

Synaptic and USC are GUI front ends to the apt system.  They are all related.  Generally speaking if the install is packaged as a deb (compiled binaries) then it will pick up the dependencies.  Packaging for deb is is setup to do that already.  The real problem comes from compiling from source code.  The user has to figure out the possible dependencies.

And just what exactly didn't you read in my post?  It's there if you read it (except for dpkg - but is that really important to the OP's question?  Seems like you are trying to state again what is in my post and seemingly making me sound wrong.  Read it again,

---

### Post by audiomick on 2012-12-12
> **squakie said:**
>  I hope you don't mind me expanding on that a little. ;)

Not at all. I'm running on stuff that I learned at Uni more than 20 years ago, so there is plenty of room for expansion... ;)

---

### Post by 3Megatons on 2012-12-12
Thanks, everybody!

---

