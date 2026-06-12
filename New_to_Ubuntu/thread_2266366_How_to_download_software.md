---
title: "How to download software?"
date: 2015-02-22
forum: New to Ubuntu
---

### Post by jones5 on 2015-02-22
Hi All 

I am very new to Linux and have not got a clue how to get software when trying out different distros. They all seem different and need different ways to get applications or apps depending on what each system call them.

At the moment I am trying out Ubuntu 14.04  and Elementary OS on USB's.

Can anyone provide a really basic step by step method for getting software and actually getting it up and running? I know you can use a terminal and perhaps sudo apt. But how?  When I mean step by step I mean 
VERY SLOWLY and fully explain. I would be grateful.  I am trying to get things like firefox and basic software.

Also cannot seem to get brightness level up at all?  

If this is covered elsewhere IN DETAIL for absolute beginners please point.

---

### Post by grahammechanical on 2015-02-22
Absolute beginners in Ubuntu use the Ubuntu Software Centre. Even those who are not absolute beginners, like myself, use the Ubuntu Software Centre. There is less trouble installing software this way and we get software that is code audited to make sure it does not contain any code that will do malicious things to our computer.

I say nothing about other distributions. I do not use other distributions. I do not give support for other distributions. Linux is Free and Open Source Software (FOSS). That means that anyone is free to develop a different way of doing things. And many do go their own way in developing software. So, we have command line utilities that require us to type exact commands with the exact name of the package (software) we wish to download and install. We have utilities with a Graphical User Interface (GUI) to the command line utility.

In Linux we have, as far as I know, at least two different software package formats. RPM (Redhat Package Manager) and DEB (Debian software package format). Ubuntu is based upon Debian, which is itself a Linux distribution. So, any application has to be packaged in the DEB package format with a .deb extension to the package name. Packages with the .rpm file name extension cannot be installed in Ubuntu without first being converted into a deb package.

Software that we download from a web site is considered to be from an untrusted source because it has not been code audited. In Ubuntu we can also install software from a Personal Package Archive (PPA). Although the software package is hosted on a Canonical web site these packages are also considered from an untrusted source. In this way we, the user, are given the freedom to take responsibility for our own actions.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

[https://help.ubuntu.com/10.04/serverguide/aptitude.html](https://help.ubuntu.com/10.04/serverguide/aptitude.html)

In Ubuntu we can often use the File Manager to right click a deb package and select the option Open with Ubuntu Software Centre. Then the Software Centre will save us the trouble of using the command line. We can also use the Software Centre to remove or uninstall software as well as the command line.

Regards.

---

### Post by tgalati4 on 2015-02-22
Let's say you heard of a program called "htop".  First search the respository for it:

Open a terminal.

```
apt-cache search htop
```

It might look like:

> tgalati4@Mint17 ~ $ apt-cache search htop
aha - ANSI color to HTML converter
**htop - interactive processes viewer**
libauthen-oath-perl - Perl module for OATH One Time Passwords

So now install it:

```
sudo apt-get install htop
```

And run it:

```
htop
```

Control-C to quit the program.

For the brightness issue, what is the make and model of the laptop?

---

### Post by stalkingwolf on 2015-02-22
with Ubuntu and most of its sisters you can also use synaptic package manager.

---

### Post by buzzingrobot on 2015-02-22
Like other distributions, Ubuntu maintains software packages for downloading and installation on servers that are, collectively, known as repositories (aka repos).

It's important to remember that regardless of the tool used to download and install from these repositories, the packages are the same and they come from the same place.

Your Ubuntu system maintains a list of the repositories that are appropriate for your specific version.  It also maintains a list of all the packages currently installed. So, when you install a new package, it will identify any other packages that are required (dependencies) and automatically download and install those, as well.

An application like the Software Center focuses on applications, hiding the bits and pieces of supporting files that are also available in the repositories.  This is intentionally done to simplify things.

Tools like Synaptic, on the other hand, show a user every package in the repositories. This is useful if an experienced user needs to acquire a specific version, say, of a specific supporting package.  But, it also means that the user needs to know what he/she is doing.

Command-line tools like apt, apt-get, etc., provide similar fine-grained functionality.

It is best to install software *only* from the official repositories, or, as mentioned earlier in the thread, (carefully) from PPA's. Among other benefits, all these packages will be updated when needed. It is also best to avoid the Windows practice of downloading and installing software packages in a zip archive (or its Unix/Linux counterpart, a 'tar.gz' archive) directly from a vendor's or a developer's site. If nothing else goes wrong, you will still need to be responsible for manually updating that software in the future because your system will not record its presence.

---

### Post by jacobpratt909 on 2015-02-22
Launchpad provides many programs via sudo apt-get after you have added the ppa to the repos. Might want to find out more about that, because Launchpad helps a lot :D

-Wyz

---

### Post by newb85 on 2015-02-23
@buzzingrobot, that was the best and most well-balanced explanation I've read yet.  I hope you don't mind if I shamelessly use it verbatim in other threads.

---

### Post by jones5 on 2015-02-23
> **tgalati4 said:**
> 

For the brightness issue, what is the make and model of the laptop?

The laptop/notebook is Samsung notebook N140 32 bit XP.    Trying Elementary OS and Ubuntu 14.04 0n it.

---

### Post by jones5 on 2015-02-23
> **jacobpratt909 said:**
> Launchpad provides many programs via sudo apt-get after you have added the ppa to the repos. 

-Wyz

Sorry - haven't got a clue what that means?  Launchpad is the thing in Ubuntu where I download programs - Right?

---

### Post by jones5 on 2015-02-23
> **tgalati4 said:**
> Let's say you heard of a program called "htop".  First search the respository for it:

Open a terminal.

```
apt-cache search htop
```

It might look like:



So now install it:

```
sudo apt-get install htop
```

And run it:

```
htop
```

Control-C to quit the program.



This is how simple it has to be for some of us Linux newbies. I can just follow this and will try it. This is a good example of how to break stuff down for people who have never used Ubuntu etc. When I try to explain basic stuff to those who have never used a computer before (had to do it recently for an elderly friend) it was really instructive how basic you have to make it. I guess we all forget  how many years it took us to master these things. It takes a special type of teacher to teach from scratch. Lots of skills needed like putting yourself in their place. Almost like learning to read the alphabet before reading books?  Thanks to all the others too for suggestions.

---

### Post by jones5 on 2015-02-23
Thanks Grahammechanical - That has cleared a lot of things up. I am encouraged to try things a bit further with Ubuntu. Elementary looks nice but cannot get it to function very well and the file system seems unfathomable.

---

### Post by slickymaster on 2015-02-23
I advise you to have a read at [Installing Software]("https://help.ubuntu.com/community/InstallingSoftware")

---

### Post by buzzingrobot on 2015-02-23
> **jones5 said:**
> ... the file system seems unfathomable.

The directory structures of Linux and Windows are entirely different.  Google will turn up many explanations of the "Linux file system", but many will be not be entry-level, unfortunately.

The Linux file system is hierachical.  I.e., one top-level directory exists and all other directories are sub-directories of it.

The top level directory is simply called '/'. (Linux is a version of Unix and the original Unix developers used very terse labels.)

Immediately below '/' in the hierarchy are several standard directories. For example, one is '/etc', where system-wide configuration files are kept. Another is '/lib', where system-wide libraries of compiled code live.  The '/bin' directory houses executable files.

There is also the '/usr' directory that contains, among others, its own 'bin' and 'lib' directory.  Hence, '/usr/bin' and '/usr/lib'.  These last two directories will typically house the applications and their support libraries that are installed on the system.

A very important directory is the '/home' directory.  Linux is a multi-user system, which means it's built to allow more than one user to log in and use a machine simultaneously. Given that, it's necessary to keep the personal files of one user separate from the personal files of any other users.  So, when you install Elementary or Ubuntu or most other distributions, the installer will create a sub-directory for you in '/home' and give it your user name.  E.g., a user 'buzzingrobot' would use the '/home/buzzingrobot' directory.

This directory is usually referred to just as your 'home' directory.  When you open a file manager and see directories for things like "Downloads", "Pictures", "Music", etc., you're seeing directories created for your use in your home directory.

If you want to create a directory for something -- say, "Best Cat Videos'  -- create it in your home directory.

In addition, when you edit the preferences or settings of an application, like Firefox, that application stores that preferences in your home directory.

(BTW, file managers usually do not depict the strict hierarchical layout of the file system, but it's there.)

Also, don't try to install software directly to directories like /usr/bin or /usr/lib.  Let the software installer you use handle that.  It knows where to put stuff.

---

### Post by tgalati4 on 2015-02-23
If you want to see what is installed where, install *tree.*

```
sudo apt-get install tree
```

A tree of your home directory:

```
cd
tree
tree > my_directory_listing.txt
cat my_directory_listing.txt
```

The penultimate (next-to-last) command dumps the output of *tree* to a file called my_directory_listing.txt.
The last command simply catalogs or lists the file to your terminal.

This command will take a while:

```
cd /
tree
```

Control-C to quit.

Many GNU/Linux utilities are in /usr/bin.  Let's *tree* it.

```
cd /usr/bin
tree
tree > ~/my_listing_of_usr_bin.txt
cd
cat my_listing_of_usr_bin.txt
```

The tilda ( ~ ) is used as a shortcut for your home directory.  *cd* with no arguments takes you to your home directory.

Many of these utilities come from UNIX, an older, proprietary, operating system.  They are called GNU utilties (GNU is not UNIX), as they have been ported from UNIX in an open source fashion.  Linux consists of the kernel (the stuff in /boot) and GNU/Linux refers to the combination of the kernel and all of the utilities in /usr/bin (and elsewhere).  For simplicity, most people just call it Linux.  When you add a graphical interface and fancy packaging it's called a distribution, such as Ubuntu.

After a while, this stuff becomes second nature.

Notice I did not say, take a mouse and click in the lower left corner.  You may not have a mouse and you may not have a lower left corner.

---

### Post by deadflowr on 2015-02-23
> **jacobpratt909 said:**
> Launchpad provides many programs via sudo apt-get after you have added the ppa to the repos. Might want to find out more about that, because Launchpad helps a lot :D

-Wyz

> **jones5 said:**
> Sorry - haven't got a clue what that means?  Launchpad is the thing in Ubuntu where I download programs - Right?

Launchpad is a software collaboration platform
[https://launchpad.net/](https://launchpad.net/)

But one of the things it has, is a system known as ppa or personal package archives, which you use to get non-official packages installed on your system with ease.
[https://help.launchpad.net/Packaging/PPA/InstallingSoftware](https://help.launchpad.net/Packaging/PPA/InstallingSoftware)

---

### Post by jacobpratt909 on 2015-02-23
Launchpad is where you find a program, then do ```

sudo apt-add-repository
```
or something like that with following along ```

ppa:http://someoddwebsite.asd/somethingorother/banana
```
then you would update sudo, and download the correct package provided from that ppa.

-Wyz

---

### Post by mastablasta on 2015-02-24
> **jacobpratt909 said:**
> Launchpad is where you find a program, then do
...

copy the web adress into software center, update and program from unofficial repository ("personal" repository) will magically appear in software center. it will then get all updates automatically.

how about checking and reading the manual first? at least the intro should set you on a path...

---

### Post by jones5 on 2015-02-24
Thanks to Buzzingrobot. Now the file system seems more comprehensible. Also thanks to all others who have helped me in this first stage. I must say I am encouraged to keep  going with Ubuntu. I can see it is far more user friendly than Windows once the basics are understood and provides much more control for the user. Totally fed up with Windows dictating and ignoring users. So  I would say this after reading the Ubuntu manual quickly (thanks for the tip) it seems to make things easier,  Ubuntu have on behalf of refugees from windows and other beginners, established a graphical software download system (software center). This may have been further encouraged by the ipod generation and their app download centers. One may still use the Terminal to download packages (software) using the package management system - sudo apt - get command? Just a couple of further questions: If I did not have software center in Ubuntu how would I know what software/applications/packages are available?  Is there some list where I can see a range of common things used on the operating system. So I can choose from them. ie different email notifiers, different radio recorders, etc etc all the usual paraphanalia one adds to the OS ? How do you know they exist, how can you choose between them before using sudo apt-get to obtain them?  Very finally -  do I just put sudo apt-get into terminal or is there a GUI for sudo apt and other instructions to be put into?  Sorry if the terminology is incorrect. I will mark this thread solved as soon as I can. Thanks

---

### Post by Lars Noodén on 2015-02-24
> **jones5 said:**
>  If I did not have software center in Ubuntu how would I know what software/applications/packages are available?  Is there some list where I can see a range of common things used on the operating system. So I can choose from them. ie different email notifiers, different radio recorders, etc etc all the usual paraphanalia one adds to the OS ? How do you know they exist, how can you choose between them before using sudo apt-get to obtain them?  Very finally -  do I just put sudo apt-get into terminal or is there a GUI for sudo apt and other instructions to be put into?  Sorry if the terminology is incorrect. I will mark this thread solved as soon as I can. Thanks

As mentioned, the Software Center, Synaptic and apt-get are all front-ends to the same database of packages.  So you could use Synaptic if the Software Center UI is not your thing.  You can only know that they exist by browsing among them or, since there are so many, reading reviews online about them and then focusing your search.   You could use Synaptic, a GUI for APT, to install a package or if you wish to try apt-get you would just enter it in the terminal.  The following will install "audacity".

```

sudo apt-get update
sudo apt-get install audacity

```

Like with any other utility, it is a very good idea to skim the manual page, even [apt-get](http://manpages.ubuntu.com/manpages/trusty/en/man8/apt-get.8.html) has one.  You can see the manual page for apt-get and ls by using the [man](http://manpages.ubuntu.com/manpages/trusty/en/man1/man.1.html) tool.

```

man apt-get
man ls
man man

```

Every utility has a page, but they do vary in quality quite a bit.  But regardless of quality, it is always useful to take at least a peek to see what the program does and its many options.

---

### Post by buzzingrobot on 2015-02-24
> **jones5 said:**
> If I did not have software center in Ubuntu how would I know what software/applications/packages are available?  Is there some list where I can see a range of common things used on the operating system...

The GUI tools update themselves to show you a current list of the packages available in the repos. More often than not, installing an app will trigger the installation of other components that app requires.  A tool like Synaptic lists all those bits and pieces.  A tool like Software Center, which is more or less intended to emulate a software store, focuses on the actual applications.

You can browse through the categories in these tools. The web is full of reviews, of widely varying quality, about Linux software, usually along the lines of "Best Linux Email Apps", and that sort of thing. (Folks here are also full of opinions and recommendations. ;))

My own recommendation is to explore, but also to stay with the simplest tools that work for you, until you need to do something they can't.  E.g., if Software Center meets your needs now, stay with it. 

ON PPA's:  They are nonofficial and potentially risky because software on them is not subject to the same testing regime as software in the official repos. You're depending on the person(s) who maintain that software (often for their own personal purposes) to deal with security issues, provide updates, etc.  Sometimes installing software from a PPA also pulls in packages that conflict with other components of Ubuntu, either immediately or down the road after an update. The general advice for new users is to avoid loading up with PPA's.  (As mentioned, they're all located on launchpad.com site.  With a bit of searching there, you can usually find a PPA's page and see what that developer says about the software. Pay attention to the warnings and caveats.)

---

### Post by jones5 on 2015-03-04
Thanks to all - I now have some idea how to find and use the software/downloaders. I hope this also helps other newbies as there was not much on the Ubuntu main page (where one downloads Ubuntu OS). I know it has to be kept simple there. I will now thoroughly try out Ubuntu. Impressed so far and a good move away from Windows.

---

### Post by mastablasta on 2015-03-05
yu have official documentation available, guides and community made ubuntu manual.

---

