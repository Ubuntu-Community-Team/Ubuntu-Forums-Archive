---
title: "Too much information, too little experience in packaging (none)"
date: 2012-07-12
forum: Packaging and Compiling Programs
---

### Post by Jacobonbuntu on 2012-07-12
**Dear people, **

Forgive me for asking a question that might be asked some times before, but I simply cannot find a simple answer, and I am sure it must be easyer than creating the application itself.

I made a Quicklist editor (used launchpad, [here]("https://launchpad.net/jonb.homelauncher")) which can be installed and used locally, for the time being, which was ok, as long as it was in an experimental stage. I believe it is time to create a ppa now; I know the dependencies (python3 / python3-tk) I decided what should be installed where and I can easily make a script for it, to make it appear like any other "normal" application.  Most important thing to me is that people would get automatic updates.

Remember I am completely new to this, and every time I try to find out what to do, the problem is that I find a HUGE amount of information with a lot of jargon.

Is there somewhere a simple instruction for newbees on this like me?
please HELP!


[CENTER][IMG]https://dl.dropbox.com/u/1155139/screenshot.png[/IMG]
[/CENTER]

---

### Post by Jacobonbuntu on 2012-07-13
OK, I can be a bit more specific now,
I found a sympathetic howto (-make a .deb file) [here]("http://www.youtube.com/watch?v=nhoRyd2CEVs"), but the part about the rules- file is quite summary, apart from the fact that I cannot look into the example file to do some studying, because in my /usr/share/doc/debhelper directory, there is only 1 ("tiny") example. 

as said, I do not believe it should be complicated as I just need to copy some files to the right directories and set permissions etc.

can anyone point me out where I can find information on how to set up the rules- file?

---

### Post by SevenMachines on 2012-07-13
```
$ cat /usr/share/doc/debhelper/examples/rules.tiny 
#!/usr/bin/make -f
%:
	dh $@

```
This is all the rules file you need, it simply calls debhelper scripts to do all the tasks that might have been done in rules. To see how to use debhelper and for a list of debhelper tools and what they do see
```
$ man debhelper

```The one you'll probably want to see first is
```
$ man dh_install
```
In particular notice the 'FILES' section, this tells you how to create a 'debian/<package>.install' file (where <package> is changed to a real package name from your control file) which will install files to directories on a system

---

### Post by Jacobonbuntu on 2012-07-13
> **SevenMachines said:**
> ```
$ cat /usr/share/doc/debhelper/examples/rules.tiny 
#!/usr/bin/make -f
%:
    dh $@

```This is all the rules file you need, it simply calls debhelper scripts to do all the tasks that might have been done in rules. To see how to use debhelper and for a list of debhelper tools and what they do see
```
$ man debhelper

```The one you'll probably want to see first is
```
$ man dh_install
```In particular notice the 'FILES' section, this tells you how to create a 'debian/<package>.install' file (where <package> is changed to a real package name from your control file) which will install files to directories on a system


Ah, thanks this is good information!
I'll get into it
thanks!

---

### Post by Jacobonbuntu on 2012-07-13
I am sure I am missing something, -I am probably thinking too complicated- but where to define the destinations of the different files? I thought that was the rules -file?
[B]
edit: ooops, forget my question, I did not read  the man pages [/B]**well, found it  ****......**

---

### Post by Jacobonbuntu on 2012-07-14
> **SevenMachines said:**
> ```
$ cat /usr/share/doc/debhelper/examples/rules.tiny 
#!/usr/bin/make -f
%:
    dh $@

```This is all the rules file you need, it simply calls debhelper scripts to do all the tasks that might have been done in rules. To see how to use debhelper and for a list of debhelper tools and what they do see
```
$ man debhelper

```The one you'll probably want to see first is
```
$ man dh_install
```In particular notice the 'FILES' section, this tells you how to create a 'debian/<package>.install' file (where <package> is changed to a real package name from your control file) which will install files to directories on a system

Well, I managed to create a shockingly straightforward .deb file that  installs an equally shockingly simple testprogram, including desktop  file and icon. Although ubuntu software complains about the "bad  quality" and I still have to find out how to do some  scripting to prepare (some) files, I think I get the picture.

Once again, thanks for the tip that pointed me in the right direction!

---

### Post by SevenMachines on 2012-07-14
> **Jacobonbuntu said:**
> Well, I managed to create a shockingly straightforward .deb file that  installs an equally shockingly simple testprogram, including desktop  file and icon. Although ubuntu software complains about the "bad  quality"
Congratulations, you're now a better packager than me :)

The packaging build uses lintian to check for mistakes and warn about things you might want to improve on (many packages in the repository will still have many warnings just to put things in perspective) Don't know if it was you I mentioned it to recently but if not, you can look up these lintian warnings at [http://lintian.debian.org/tags.html](http://lintian.debian.org/tags.html) to give you more of a description of what the warning might mean

---

### Post by Jacobonbuntu on 2012-07-14
AHA!
I did something wrong with my email adres, the warning has gone!
nice when things start to work...

---

### Post by Cheesemill on 2012-07-14
If you are going to use a PPA on Launchpad you don't create the .deb file yourself, instead you upload the source code to Launchpad and the package gets built on their servers.

[https://help.launchpad.net/Packaging/PPA/BuildingASourcePackage](https://help.launchpad.net/Packaging/PPA/BuildingASourcePackage)
[http://developer.ubuntu.com/packaging/html/](http://developer.ubuntu.com/packaging/html/)

---

### Post by SevenMachines on 2012-07-14
As a general process I'd say,
(1) Get 'debuild -b -us -uc' working
(2) Then 'debuild -S' to create source business
(3) Set up pbuilder environment with, for example
$ pbuilder-dist precise create
(4) Test build in clean environment
$ pbuilder-dist precise build somepackage.dsc
(5) Upload to launchpad ppa

Packaging so you can get the binary built is the major part, and the bit people often have the most trouble getting to grips with. Theres also bzr for packaging if you want it and a whole host of things, but best to focus on step (1) first

---

### Post by Jacobonbuntu on 2012-07-14
> **Cheesemill said:**
> If you are going to use a PPA on Launchpad you don't create the .deb file yourself, instead you upload the source code to Launchpad and the package gets built on their servers.

[https://help.launchpad.net/Packaging/PPA/BuildingASourcePackage](https://help.launchpad.net/Packaging/PPA/BuildingASourcePackage)
[http://developer.ubuntu.com/packaging/html/](http://developer.ubuntu.com/packaging/html/)

Good heavens, I really should start reading, looks good! still nice if you *can *do things, even if it were  to understand what is actually happening :)
@ sevenmachines: I will try to figure out all you write , although I am still celebrating my very first succes :)

---

### Post by SevenMachines on 2012-07-14
> **Jacobonbuntu said:**
> @ sevenmachines: I will try to figure out all you write , although I am still celebrating my very first succes :)
Don't worry too much about it, I'm sure it'll come to you when you need it, the hard parts done

---

