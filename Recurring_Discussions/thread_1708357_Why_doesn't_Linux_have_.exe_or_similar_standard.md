---
title: "Why doesn't Linux have .exe or similar standard?"
date: 2011-03-16
forum: Recurring Discussions
---

### Post by Perpetual_Bliss on 2011-03-16
As many things as may be wrong with Windows, one of the greatest things about installing programs in Windows is the ability to double-click and let the computer install all by itself. All computer programs - from any third party, etc. - use an .exe installer. Why isn't there a similar standard in Linux/Ubuntu? I know there's a lot of diversity across the board in terms of software, but don't they use the same base?  

I've been trying to install 3rd party apps on Ubuntu for the last day, and it's frustrating and many times, doesn't work.

---

### Post by tgm4883 on 2011-03-16
> **Perpetual_Bliss said:**
> As many things as may be wrong with Windows, one of the greatest things about installing programs in Windows is the ability to double-click and let the computer install all by itself. All computer programs - from any third party, etc. - use an .exe installer. Why isn't there a similar standard in Linux/Ubuntu? I know there's a lot of diversity across the board in terms of software, but don't they use the same base?  

I've been trying to install 3rd party apps on Ubuntu for the last day, and it's frustrating and many times, doesn't work.

Debian based distros have .deb files for installation. RPM based distros have the .rpm extension.

---

### Post by LowSky on 2011-03-16
Could you at least tell us what applications you are tring to install?

---

### Post by matt_symes on 2011-03-16
Hi

> **Perpetual_Bliss said:**
> As many things as may be wrong with Windows, one of the greatest things about installing programs in Windows is the ability to double-click and let the computer install all by itself. All computer programs - from any third party, etc. - use an .exe installer. Why isn't there a similar standard in Linux/Ubuntu? I know there's a lot of diversity across the board in terms of software, but don't they use the same base?  

I've been trying to install 3rd party apps on Ubuntu for the last day, and it's frustrating and many times, doesn't work.

What about .deb files ? The software repros are a safe way to distribute software.

Kind regards

---

### Post by uRock on 2011-03-16
> **LowSky said:**
> Could you at least tell us what applications you are tring to install?
+1 For Ubuntu/Linux you need to find .deb packages for easy install. Also, you may be able to find the package in the Ubuntu Software Center where you may just click and install softwares.

---

### Post by kellemes on 2011-03-16
Indeed there is no universal package format for Linux, simply because distributions have there own idea regarding how software needs to be managed within the system.
Not sure if it's undesirable anyway..
I can imagine coming from windows all seems somewhat complicated.

---

### Post by Joshun on 2011-03-16
The equivalent for a .exe installer for ubuntu would be a .deb package. However, most people tend to use repositorys for installing third party software (which you can add in software sources), as these ensure that programs are kept up to date. In Windows, when you update it only updates the Windows Operating System, and not any other programs - some programs have auto updaters (like flash and java), but in ubuntu most programs are integrated into the package management system.

There is also [autopackage]("http://www.autopackage.org/"), which allows you to install third party software easily. Usually though, you are just better off using repositorys and deb packages.

If you want to actually run windows exe files, then try using [wine]("http://winehq.org") (you can install it in the software centre), it works on quite a few things with a bit of tweaking.

---

### Post by tkelito on 2011-03-16
As stated .exe is very similar in Linux to .rpm or .deb.  They are all just containers designed to to install the program automatically using a package manager like Add/Remove Programs, Synaptics, etc.

Not every developer compiles their software into these easy to use packages, which can have benefits or detriments depending on the use.   A major detriment would be to new users not knowing how to unzip a tar and make/compile it correctly.  A major benefit though is when you want to choose the specific locations that something installs or see exactly where a file is failing to install instead of just random error codes.  Do remember a lot of *nix users are going command line only which a .deb provides them no extra benefit.

Great example of this is Java, if you don't have root/sudo access you will need to install it into your home directory and create symlinks for the plugin to function properly in your browser. I prefer to hone more control over my OS and choose where things go so for most apps I prefer they aren't in .deb containers.  

In Windows you have zero control over what an .exe does, where it installs (we all hated apps that installed in C:\).  That is the nice side of linux, you control your experience and your OS.  Linux as I said is also run a lot at the command line where Windows is used more predominantly in a GUI environment.

---

### Post by Joeb454 on 2011-03-16
> **kellemes said:**
> Indeed there is no universal package format for Linux, simply because distributions have there own idea regarding how software needs to be managed within the system.
Not sure if it's undesirable anyway..
I can imagine coming from windows all seems somewhat complicated.

It does, but even pre-compiled .tar.gz releases, such as those used by Mozilla, aren't too difficult once you have a bit of experience :)

Admittedly, a .deb or .rpm file or repository installation would be easier for beginners. I know I was confused when I first started out.

---

### Post by Tweak42 on 2011-03-16
> **Joshun said:**
> The equivalent for a .exe installer for ubuntu would be a .deb package. However, most people tend to use repositorys for installing third party software (which you can add in software sources), as these ensure that programs are kept up to date. In Windows, when you update it only updates the Windows Operating System, and not any other programs - some programs have auto updaters (like flash and java), but in ubuntu most programs are integrated into the package management system. centre), it works on quite a few things with a bit of tweaking.

The packaging and repository system is SO superior for linux that I've been waiting for MS to implement something similar since Windows 98 (95 brought installshield).  Just imagine not having to search net, save download, find where saved download went, unzip, run installer, click accept X times.  Not to mention updates .... yuck. 13 years and counting and MS still does installs the same inferior/infuriating way. Apple is doing pretty successful with their app store model, so I wonder if MS will finally get a clue.

---

### Post by cariboo on 2011-03-16
This has been discussed countless times before, moved to recurring.

---

### Post by GWBouge on 2011-03-16
> **Perpetual_Bliss said:**
> All computer programs - from any third party, etc. - use an .exe installer.

Or an .msi ... or a simple .zip so you can put it where you want it ... there isn't much of a standard aside from everything (with the exception of an archive) likes to hide stuff somewhere without your knowledge.

> **Joeb454 said:**
> Admittedly, a .deb or .rpm file or repository installation would be easier for beginners. I know I was confused when I first started out.

Agreed.  It's a bit to take in at first, but once you get the hang of it, you'll (I, at least) find that the Linux methods are *much* better at finding software, keeping track of what's installed, not bogging down with lots of software installed, and cleaning up remnants of software that you remove.

---

### Post by Mark Phelps on 2011-03-16
> **Perpetual_Bliss said:**
> ... All computer programs - from any third party, etc. - use an .exe installer...

Actually ... no, they do NOT.

Older Windows apps would often use .BAT files, some even used .COM files.  Newer Windows apps often use .MSI files.

Ubuntu, with its use of .deb files for pre-packaged installations, is actually far more consistent.

---

### Post by kellemes on 2011-03-16
> **Mark Phelps said:**
> Actually ... no, they do NOT.

Older Windows apps would often use .BAT files, some even used .COM files.  Newer Windows apps often use .MSI files.

Ubuntu, with its use of .deb files for pre-packaged installations, is actually far more consistent.

OP is talking about Linux, not Ubuntu.
And there is nothing consistent in Linux package management.
It's just not possible with 400+ brands of Linux..

---

### Post by Perpetual_Bliss on 2011-03-16
> **LowSky said:**
> Could you at least tell us what applications you are tring to install?
I tried quite a few. I was successful in installing Jupiter and Mendeley; unsuccessful with Foxit Reader and Granola

> **tgm4883 said:**
> Debian based distros have .deb files for installation. RPM based distros have the .rpm extension.
I guess you do have a point there.

---

### Post by bruce89 on 2011-03-17
It's called source code.

I realise that's not good enough, just kidding.

---

### Post by wojox on 2011-03-17
Programs built in C# use the .exe extension. Look in your filesystem.

---

### Post by handy on 2011-03-17
I've read somewhere in the not too distant past that there is genuinely a combined .deb .rpm repo' going to be put together in the future.

Such a repo' will save the distros that use it a great deal of time in package management. At least Ubuntu, Debian & Red Hat were involved I believe.

I don't remember the details & I have no idea where I read it.

Perhaps someone else can post a link for us?

---

### Post by DuckHook on 2011-03-17
The reason that Linux doesn't have a single installation standard is because, by its very nature, it is not possible to impose a monoculture on its community. In contrast, proprietary software can be forced to adhere to single standards because "proprietary" is, by definition, monocultural. If we want the freedom and variety that comes from a multicultural community such as Linux, then the price that we have to pay comes in the form of increased complexity and the rejection of any single standard. The alternative is the comfort of simplicity and standards at the cost of lock-in and exclusion. It's a decision that each of us makes as individual consumers, but, speaking only for myself, I prefer the complicated freedom of Linux to the simplified lock-in of proprietary software.

When I look at the hundreds of programs alone which are there for the asking in Ubuntu's software centre, not a one of which requires an activation key or a validation number or, indeed, a single dime for the dubious benefit of an "upgrade", I wouldn't go back to my old Windows world for all the wheat in Kansas.

---

### Post by weasel fierce on 2011-03-17
As far as I figure, the Debian system is pretty much as good as its ever going to get.

---

### Post by kellemes on 2011-03-17
> **weasel fierce said:**
> As far as I figure, the Debian system is pretty much as good as its ever going to get.

You must be joking.. :)
But well, I've seen worse..

---

### Post by handy on 2011-03-17
So no one is aware of this project for the future, which will apparently serve both .deb & .rpm distros from one grand repo, thus saving all that multiple handling regarding package management?

---

### Post by kellemes on 2011-03-17
> **handy said:**
> So no one is aware of this project for the future, which will apparently serve both .deb & .rpm distros from one grand repo, thus saving all that multiple handling regarding package management?

Nope, never heard of it.. and searching gives me nothing..

---

### Post by ikt on 2011-03-17
> **handy said:**
> I've read somewhere in the not too distant past that there is genuinely a combined .deb .rpm repo' going to be put together in the future.

There was some big hype over AppStream:

[http://ubuntuforums.org/showthread.php?t=1680786](http://ubuntuforums.org/showthread.php?t=1680786)

[http://distributions.freedesktop.org/wiki/AppStream](http://distributions.freedesktop.org/wiki/AppStream)

It now looks deadish, apptools looks slightly more alive

[http://code.google.com/p/apptools-dist/](http://code.google.com/p/apptools-dist/)

But even then, combined they both appear dead, guess there will never be a unified package manager unless someone like Red Hat or Canonical push for it.

---

### Post by handy on 2011-03-17
Never is too big a word for this problem. Solving it benefits all concerned & allows that much more time for so many involved in package management to be doing more productive things.

Everybody wins.

---

### Post by wojox on 2011-03-17
> **handy said:**
> So no one is aware of this project for the future, which will apparently serve both .deb & .rpm distros from one grand repo, thus saving all that multiple handling regarding package management?

I remember reading something similar. They want all distro's to conform to using the same package manager. Pacman and AUR's makepkg would fit that nicely.

---

### Post by tgm4883 on 2011-03-17
> **handy said:**
> Never is too big a word for this problem. Solving it benefits all concerned & allows that much more time for so many involved in package management to be doing more productive things.

Everybody wins.

You want a unified package manager that can install rpm or deb (or whatever the unified format has). This is not the same as what you are talking about, as the backend for the repo would contain the source, and the frontend would contain each distros packaging (including changes). There would still exist .deb and .rpm files and they would still not be compatible between distros.

---

### Post by handy on 2011-03-17
> **tgm4883 said:**
> You want a unified package manager that can install rpm or deb (or whatever the unified format has). This is not the same as what you are talking about, as the backend for the repo would contain the source, and the frontend would contain each distros packaging (including changes). There would still exist .deb and .rpm files and they would still not be compatible between distros.

What I read about solved the problem between .rpm & .deb . They would coexist & feed from the same source.

I can't for the life of me remember where I read it. But Shuttleworth & co. As well as Red Hat & Debian were satisfied enough with the project not to veto.

---

