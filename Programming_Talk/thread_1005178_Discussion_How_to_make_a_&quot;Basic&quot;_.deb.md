---
title: "Discussion: How to make a &quot;Basic&quot; .deb"
date: 2008-09-04
forum: Programming Talk
---

### Post by Diabolis on 2008-09-04
The official documentation: [https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

---

### Post by slavik on 2008-09-05
nice, thank you. :)

you've no idea how many times I've gone through the docs, but every time the number of links told me that I don't want to create packages. :)

---

### Post by LaRoza on 2008-09-05
> **slavik said:**
> nice, thank you. :)

you've no idea how many times I've gone through the docs, but every time the number of links told me that I don't want to create packages. :)

This is also very easy to use: [http://code.google.com/p/debianpackagemaker/](http://code.google.com/p/debianpackagemaker/)

---

### Post by curvedinfinity on 2008-09-05
I personally opted against a GUI because I like to integrate this into my build script. But eh, I'm really a packaging newbie, and I just wanted a deb with no frills for the particular project I researched this for. :)

---

### Post by cmay on 2008-09-05
thanks you for this post. when i as a hobbyist only used windows i could find easy and pretty nice setup installers for windows. i have been looking for something like this.

---

### Post by slavik on 2008-09-05
> **LaRoza said:**
> This is also very easy to use: [http://code.google.com/p/debianpackagemaker/](http://code.google.com/p/debianpackagemaker/)
dude, wtf ... everytime someone shows how to do something, you find some other tool that makes things easier. You really need to stop keeping secrets. :)

---

### Post by samjh on 2008-12-01
> **LaRoza said:**
> This is also very easy to use: [http://code.google.com/p/debianpackagemaker/](http://code.google.com/p/debianpackagemaker/)

What ELSE aren't you telling us? ;)

Good post, OP, and LaRoza too. :D

---

### Post by bobbocanfly on 2008-12-01
A word of warning to everyone: This method is fine for distributing your application from your website, but you will not be able to get packages built in this way into Ubuntu. If this is your aim, you need to read [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete) and get in touch with the MOTU team (#ubuntu-motu on irc.freenode.net and [email]ubuntu-motu@lists.ubuntu.com[/email]).

---

### Post by curvedinfinity on 2008-12-04
Updated to reflect bobbocanfly's warning.

---

### Post by Flimm on 2008-12-05
I've just started a [guide on preparing python applications for distribution](http://ubuntuforums.org/showthread.php?t=1002909), I'd really appreciate if you could share any suggestions you have for it.

---

### Post by drubin on 2008-12-06
> **Flimm said:**
> I've just started a [guide on preparing python applications for distribution](http://ubuntuforums.org/showthread.php?t=100290), I'd really appreciate if you could share any suggestions you have for it.

The only comment I can give is that URL is for  Nvidia drivers for Hercules Geforce3 Ti500....

---

### Post by slavik on 2008-12-08
This thread is for the discussion of the howto sticky named: How to make a "Basic" .deb, located at [http://ubuntuforums.org/showthread.php?t=910717](http://ubuntuforums.org/showthread.php?t=910717)

---

### Post by Flimm on 2008-12-08
> **drubin said:**
> The only comment I can give is that URL is for  Nvidia drivers for Hercules Geforce3 Ti500....
Looks like I accidentally deleted the last character of the URL, I've corrected it now: [the real thread on packaging a python app](http://ubuntuforums.org/showthread.php?t=1002909).

---

### Post by matmatmat on 2008-12-24
I want my .deb to create a hidden file in their home directory, how would I do it? Do i just create a folder called ~/.<hidden>?

---

### Post by matmatmat on 2008-12-24
I want my .deb to create a hidden file in the users home directory, how would I do it? Do i just create a folder called ~/.<hidden>?

---

### Post by nvteighen on 2008-12-24
> **matmatmat said:**
> I want my .deb to create a hidden file in the users home directory, how would I do it? Do i just create a folder called ~/.<hidden>?
That would probably mess everything around... unless you play with complex permission setting, the most probable is that the hidden folder will be created as owned by root... And if the system is Debian, not Ubuntu, you'll have to keep in mind that the default there is 'su', not 'sudo', so '~/blag' will be '/root/blag'...

Standard way to do this is to use /etc/your-name.

---

### Post by bobbocanfly on 2008-12-24
> **matmatmat said:**
> I want my .deb to create a hidden file in the users home directory, how would I do it? Do i just create a folder called ~/.<hidden>?

Stuff in ~/home really shouldnt be touched by packages (if at all possible). You are much better patching the upstream to create the directory when it is run as it wont mess up permissions etc.

---

### Post by curvedinfinity on 2008-12-30
> **matmatmat said:**
> I want my .deb to create a hidden file in the users home directory, how would I do it? Do i just create a folder called ~/.<hidden>?

What I did was have my installed application create the hidden user config folders when it is run. Its simple procedure in any language to check for whether a folder is created or not. :)

---

### Post by blurboy on 2009-10-10
so base on dgkp how can I create a package so that when user double clicks on it, it will unpack all the files onto the CURRENT USER desktop??

---

### Post by Flimm on 2009-10-10
> **blurboy said:**
> so base on dgkp how can I create a package so that when user double clicks on it, it will unpack all the files onto the CURRENT USER desktop??
You can't. Instead, you should follow curvedinfinity's advice:
[QUOTE=curvedinifinty]What I did was have my installed application create the hidden user config folders when it is run. Its simple procedure in any language to check for whether a folder is created or not.[/quote]

---

### Post by Penguin Guy on 2009-10-30
Nice tutorial, however you could shorten:
```
mkdir helloworld_1.0-1/usr
mkdir helloworld_1.0-1/usr/local
mkdir helloworld_1.0-1/usr/local/bin
```
Down to:
```
mkdir -p helloworld_1.0-1/usr/local/bin
```

---

### Post by Jordanwb on 2009-12-20
2 Questions: 

1) How do I target multiple arches in one deb file?
2) How do I run commands after installation? I want to create a user for my program to run under.

*Edit*

For question #2 see this: [http://www.nerdliness.com/article/2007/08/27/creating-simple-ubuntu-debian-packages](http://www.nerdliness.com/article/2007/08/27/creating-simple-ubuntu-debian-packages)

---

### Post by WitchCraft on 2009-12-31
> **Jordanwb said:**
> 2 Questions: 

1) How do I target multiple arches in one deb file?
2) How do I run commands after installation? I want to create a user for my program to run under.

*Edit*

For question #2 see this: [http://www.nerdliness.com/article/2007/08/27/creating-simple-ubuntu-debian-packages](http://www.nerdliness.com/article/2007/08/27/creating-simple-ubuntu-debian-packages)

1) You don't. 32 Bit and 64 Bit .deb files will be in different repositories. And you will make one .deb file for each architecture.

---

### Post by Jordanwb on 2010-01-28
When I install my deb package, I want dpkg to remove other packages. How would I do that? I tried "Conflicts" but gdebi won't allow the installation of my deb, since the conflicting packages are installed.

---

### Post by surabhi on 2010-04-07
Hello I am using UBUNTU 9.10

I am not  to run debianpackagemaker

it is showing an error The assembly mscorlib.dll was not found or could not be loaded.
It should have been installed in the `/usr/lib/mono/1.0/mscorlib.dll' directory.

I have installed  dpm_0.4.1~welemski1_i386.deb 

How can I run it ?

---

### Post by cai.huan on 2010-04-13
mark:popcorn:

---

### Post by ubudog on 2011-05-04
Thanks for the how-to, I go to it every time I need to package a .deb.  :-)

---

### Post by nvteighen on 2011-05-27
Not sure if this is the place to post this. But I wanted to make you all know of this really great introduction on this topic, written by Lucas Nussbaum.

[Latest PDF version]("http://git.debian.org/?p=collab-maint/packaging-tutorial.git;a=blob_plain;f=packaging-tutorial.pdf;hb=refs/heads/pdf")
[Git repo]("http://anonscm.debian.org/gitweb/?p=collab-maint/packaging-tutorial.git")

This tutorial has been included in Debian unstable's official repos as a package called packaging-tutorial. This means that it might enter Ubuntu very soon.

---

### Post by MG&amp;TL on 2011-06-27
Sorry everyone, this is going to be obvious, and I'm going to look like an idiot...again :(

This guide is good, and I understand it...but (hypothetically, I don't actually have anything that's worth publishing) do I put source code, binary executables, or both in /bin? The name of the directory would indicate binary...?

I guess I could just experiment and see what happens...:)

---

### Post by MG&amp;TL on 2011-06-27
Sticking a binary file in there works fine, and it worked the first few times, once I'd removed the "dependencies" file in "control" - didn't realize what they said :D Incidentally, how do you put dependencies like header files in there? Surely one doesn't actually put the header file source code in there?

BUT-I decided I didn't want my program to be called "hello world" so I removed the program from the directory manually, then re-built. Once I'd got rid of the error messages about capital letters not allowed, it built fine. If I tried to install it, though, it says that "apt-daemon has crashed", but then it's a standard Ubuntu error message (Don't we all love them!) saying that you should report it and then do it again.

What am I doing wrong?

---

### Post by Tony Flury on 2011-07-14
One minor gotcha for Basic Debs is that if you are building a DEB for distribution or to install a single app across a multi-user system, then you need to set the permission and possibly ownership on your executable files as appropriate before building your DEB.

I forgot to do this - and my although my DEB "worked" (app was copied to the right directory and a nice icon appeared in all users menus), the icon only worked for me, as the executable was set to my permissions only.

---

### Post by nvteighen on 2011-07-14
> **Tony Flury said:**
> One minor gotcha for Basic Debs is that if you are building a DEB for distribution or to install a single app across a multi-user system, then you need to set the permission and possibly ownership on your executable files as appropriate before building your DEB.

I forgot to do this - and my although my DEB "worked" (app was copied to the right directory and a nice icon appeared in all users menus), the icon only worked for me, as the executable was set to my permissions only.

There's the debhelper dh_fixperms script for that. Call it in the *rules* Makefile and it will do the trick.

---

### Post by Tony Flury on 2011-07-14
> **nvteighen said:**
> There's the debhelper dh_fixperms script for that. Call it in the *rules* Makefile and it will do the trick.

I don't use makefiles - well not for my simple one file Python app. I have not looked at Makefiles for python apps with multiple files.

I think i will have to investigate.

---

### Post by nvteighen on 2011-07-14
> **Tony Flury said:**
> I don't use makefiles - well not for my simple one file Python app. I have not looked at Makefiles for python apps with multiple files.

I think i will have to investigate.

The 'rules' Makefile is required for creating a Debian package; it's the file that tells dpkg how to install things. There are cases in which you can use CDBS, which automates almost everything, but everytime you build a *.deb, there's that Makefile running covertly.

---

### Post by Tony Flury on 2011-07-15
Ok - I am confused - which to be honest isn't hard to do these days.

I used this sticky as instructions to build my deb : 
[http://ubuntuforums.org/showthread.php?t=910717](http://ubuntuforums.org/showthread.php?t=910717)

No mention of a makefile - and i did not create one - I just built the directory structure - and ran dpkg-deb as instructed.

My initial comment was refering to the sticky - and the fact that the instructions don't mention permissions/ownership.

---

### Post by nvteighen on 2011-07-15
> **Tony Flury said:**
> Ok - I am confused - which to be honest isn't hard to do these days.

I used this sticky as instructions to build my deb : 
[http://ubuntuforums.org/showthread.php?t=910717](http://ubuntuforums.org/showthread.php?t=910717)

No mention of a makefile - and i did not create one - I just built the directory structure - and ran dpkg-deb as instructed.

My initial comment was refering to the sticky - and the fact that the instructions don't mention permissions/ownership.

I hadn't read that tutorial until now... It's awful. I'm not even sure such a method works for a simple single-module Python application, for example.

Sadly, creating a deb package is a horribly complex process for which IMHO there are little shortcuts available, CDBS being the most reliable. There are some tutorials available on the web that teach "simple" ways to package debs and most fail either in being really simple or in making the package work. CDBS automates a lot of things, but it's a bit complex to use too. Some changes have been made now, with the so-called quilt format and, at least on Debian 6.0, some utilities have been made easier for this.

A Debian package is an ar archive that's created according to the instructions written in a Makefile called *rules* (which is found on the debian/ metadata directory after running dh-make). That's all there is, and that's the root for a lot of troubles: it means that any change you want to do has to be done using a huge collection of highly-specific shell utilities (debhelper scripts)... you know, a Makefile is a kind of shell script... 

IMO, the best guides on deb packages are the Debian and Ubuntu official ones: 
[http://www.debian.org/doc/manuals/maint-guide/](http://www.debian.org/doc/manuals/maint-guide/) (Debian "New-Maint" guide)
[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete) (Ubuntu Packaging Guide)

Those are long and go into details, but for me they end up being much clearer than everything I've found elsewhere.

---

### Post by SevenMachines on 2011-07-15
Confusion seems to come from similar terms for 2 very different processes.

**[SIZE=3] 1. _Creating a simple deb *archive*_[/SIZE]**

- Maybe using the 'simple deb' guide or I prefer checkinstall myself

- Sometimes done to pass around your code to another debian system or to allow the systems package manager to control installing/uninstalling instead of managing it manually.

- Note,[SIZE=1]** *this is in no sense 'debianised' or 'packaged' source code***[/SIZE], its just a handy archive

** 2. _Debianised or Packaged Source Code_**

- This is not the .deb file itself, its a set of rules and other information that spells out to the packaging system [I][B]how to build deb packages from source code

[/B][/I] - This is what you need to do to upload your package to a ppa or any debian/derivative repository 

- It can be a bit complex, the guides [nvteighen]("http://ubuntuforums.org/member.php?u=273037") mentioned are the ones you want. 

- If your source code uses makefile, cmake, ant, or any number of recognised build systems that cdbs knows about then it can actually be relatively straightforward. Sometimes dh_make followed by a little editing in the automatically created debian/ directory.

In short, if you need an easy way to move around some program between debian systems then you can get away with a 'simple deb'. But if you want to do anything more meaningful such as ppa's and so on then you'll need to look into the ubuntu packaging guide link.

---

### Post by nvteighen on 2011-07-15
> **SevenMachines said:**
> Confusion seems to come from similar terms for 2 very different processes.

**[SIZE=3] 1. _Creating a simple deb *archive*_[/SIZE]**

- Maybe using the 'simple deb' guide or I prefer checkinstall myself

- Sometimes done to pass around your code to another debian system or to allow the systems package manager to control installing/uninstalling instead of managing it manually.

- Note,[SIZE=1]** *this is in no sense 'debianised' or 'packaged' source code***[/SIZE], its just a handy archive

** 2. _Debianised or Packaged Source Code_**

- This is not the .deb file itself, its a set of rules and other information that spells out to the packaging system [I][B]how to build deb packages from source code

[/B][/I] - This is what you need to do to upload your package to a ppa or any debian/derivative repository 

- It can be a bit complex, the guides [nvteighen]("http://ubuntuforums.org/member.php?u=273037") mentioned are the ones you want. 

- If your source code uses makefile, cmake, ant, or any number of recognised build systems that cdbs knows about then it can actually be relatively straightforward. Sometimes dh_make followed by a little editing in the automatically created debian/ directory.

In short, if you need an easy way to move around some program between debian systems then you can get away with a 'simple deb'. But if you want to do anything more meaningful such as ppa's and so on then you'll need to look into the ubuntu packaging guide link.

Yeah, that's a good distinction I was overlooking. Your post should be considered as an "ammendment" to the original HOWTO :D

---

### Post by JupiterV2 on 2011-07-15
I thought I would point out that once you get your first .deb created, creating subsequent ones becomes almost trivial. debuild will create a <package_name>.x.x.x.debian.tar.gz file in the parent directory your source package is in (parent/package_dir). All you need to do is retain that file. In it is a copy of the debian/ meta-directory created by dh_make for your package. Just unpack the new upstream version, unpack the debian archive into your package tree, run dch -i to add a new changelog and update the package version and run debuild again. Done!

The only thing to be aware of is to make changes if any dependencies or rules need to be updated because of changes in the upstream release.

---

### Post by mechanizedmedic on 2011-08-06
would building a .deb for my wireless driver eliminate having to recompile every time i update the kernel?

---

### Post by djsephiroth on 2011-12-06
Should this be stickied in "Packaging and Compiling Programs"?

---

