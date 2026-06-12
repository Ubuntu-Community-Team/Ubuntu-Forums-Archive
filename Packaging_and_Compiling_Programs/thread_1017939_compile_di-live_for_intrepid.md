---
title: "compile di-live for intrepid"
date: 2008-12-21
forum: Packaging and Compiling Programs
---

### Post by empthollow on 2008-12-21
I am making a live cd, i like to update it with each new version of ubuntu.  I like the idea of di-live by turnkeylinux.  I've found the source code here [http://code.turnkeylinux.org/di-live/](http://code.turnkeylinux.org/di-live/)  The problem is i can't figure out how to install it.  if i copy the di-live.d directory to /usr/lib, the di-live.py script runs without error, but it doesn't do anything either.  as far as i can tell, there isn't anything to compile.  I downloaded a .deb file which works on hardy but i would like to be able to install in intrepid.  If possible i would like to make a deb of it too but first thing is first.  Can anyone figure out how to make it run?:confused:


ps. 
for anyone who is not familiar with di-live, it is a live cd installer (like ubiquity) but it does not require X.  It invokes the debian installer by use of the di-live command from a running system.

---

### Post by albinootje on 2008-12-21
> **empthollow said:**
> I am making a live cd, i like to update it with each new version of ubuntu.  I like the idea of di-live by turnkeylinux.  I've found the source code here [http://code.turnkeylinux.org/di-live/](http://code.turnkeylinux.org/di-live/)
---cut---
Can anyone figure out how to make it run?:confused:

Interesting, but the documentation is very minimal. And nowhere it mentions even how to get the code via "git".

Even after reading this email : [http://www.mail-archive.com/ubuntu-server@lists.ubuntu.com/msg02113.html](http://www.mail-archive.com/ubuntu-server@lists.ubuntu.com/msg02113.html)
it's unclear to me how it works, or how to use it.

The screenshots (from Turnkey Linux) look cool however! :)
[http://www.turnkeylinux.org/screenshots](http://www.turnkeylinux.org/screenshots)

---

### Post by albinootje on 2008-12-21
Actually, the follow-up email to that previously mentioned (linked) email says that ubiquity can run without GUI by using ```
ubiquity --automatic
```
[https://lists.ubuntu.com/archives/ubuntu-installer/2008-September/000232.html](https://lists.ubuntu.com/archives/ubuntu-installer/2008-September/000232.html)

---

### Post by empthollow on 2008-12-21
It is a cool program and works very well.  I used it to install the hardy version of my livecd.

if you look in the di-live/docs directory, the README file explains about git but i didn't try that because i have never heard of git.

I'll post it below incase you can make sense of it.

```

Debian Installer for Live systems
=================================

Introduction
------------

Debian-installer (d-i) is the preferred way of installing debian based
systems. It runs in the initrd/initramfs (see notes/DebianInstaller).

Ubiquity is developed by and used in ubuntu as its graphical desktop
installer (alternative and server use pure d-i). Ubiquity uses d-i code
as its backend, is a complex beast, and unfortunately not very modular
(see notes/Ubiquity)

di-live's objective is to provide the ability to install a "live" debian
based system to the harddisk, leveraging the power/flexability of d-i,
with a completely modular implementation (least amount of assumptions)
that can be used by upstream (eg. as an ubiquity depends - seperation of
concerns).

Source structure
----------------

git-branches
    #vanilla    prestine code downloaded from upstream
    #master     patched upstream code and actual di-live code

    git-diff vanilla compat/
    git-diff vanilla d-i/


di-live     - drives the installation (similar to d-i's main-menu)
di-live.d/  - component directory (executed in alpha-numeric ordering)
d-i/        - upstream d-i source code
compat/     - compatibility scripts as d-i code assumes running in 
              initrd/initramfs

cli syntax
----------

The init script will execute di-live (on new vt) if the boot param 
"di-live" is present on /proc/cmdline. di-live may be executed manually
in a live system aswell.

Syntax: di-live [options]

Debian Installer Live

Drives the installation, executing components according to alpha-numeric
ordering, and responsible for dynamically assembling the menu and
executing components when they are selected.

Similar to d-i's main-menu, di-live's menu will only be visible when
debconf priority is low or medium. Priority is reduced when a component
fails, and returns to original level when next component completes 
successfully.

Options:
  -d --debug      Set DEBCONF_DEBUG=developer DEBIAN_FRONTEND=readline

```

---

### Post by albinootje on 2008-12-21
> **empthollow said:**
> It is a cool program and works very well.  I used it to install the hardy version of my livecd.

Looks like this can help to produce debian packages : [http://code.turnkeylinux.org/di-live/d-i/Makefile](http://code.turnkeylinux.org/di-live/d-i/Makefile)
I'd like to give this a go soonish.

---

### Post by empthollow on 2008-12-21
> **albinootje said:**
> Actually, the follow-up email to that previously mentioned (linked) email says that ubiquity can run without GUI by using ```
ubiquity --automatic
```
[https://lists.ubuntu.com/archives/ubuntu-installer/2008-September/000232.html](https://lists.ubuntu.com/archives/ubuntu-installer/2008-September/000232.html)

actually i tried that and it wouldn't run without X.  I'm not sure what that person is referring to.

---

### Post by empthollow on 2008-12-21
> **albinootje said:**
> Looks like this can help to produce debian packages : [http://code.turnkeylinux.org/di-live/d-i/Makefile](http://code.turnkeylinux.org/di-live/d-i/Makefile)
I'd like to give this a go soonish.

so that makefile.. is that for the whole di-live program or is it jsut for the debian installer.  I did see it and was confused that is was in the d-i directory.  I'll give it a whirl though, thanks for pointing that out.

---

### Post by empthollow on 2008-12-21
ok tried running make and got this error

```
for package in source/*; do \
		(cd $package && debian/rules build) || exit 1; \
	done
/bin/sh: debian/rules: Permission denied
make: *** [build] Error 1

```

i got the same error running make as root (i know, never run make as root).  it didn't matter anyhow.

here are the permissions on that file. I'm not sure what it's looking for, the permissions look good to me.

```
-rw-r--r-- 1 empthollow empthollow  664 2008-08-29 05:29 rules

```

---

### Post by albinootje on 2008-12-21
> **empthollow said:**
> ok tried running make and got this error

[CODE]for package in source/*; do \
		(cd $package && debian/rules build) || exit 1; \
	done
/bin/sh: debian/rules: Permission denied
make: *** [build] Error 1

I'm busy downloading all that source code, could take a while.
By the way, where did you get the di-live debian package for Hardy ?
Haven't found it so far.

---

### Post by empthollow on 2008-12-21
here is the url for the deb [http://archive.turnkeylinux.org/ubuntu/pool/main/d/di-live/](http://archive.turnkeylinux.org/ubuntu/pool/main/d/di-live/)

---

### Post by albinootje on 2008-12-21
> **empthollow said:**
> here is the url for the deb [http://archive.turnkeylinux.org/ubuntu/pool/main/d/di-live/](http://archive.turnkeylinux.org/ubuntu/pool/main/d/di-live/)

Thanks!

Finally got everything downloaded, but it looks like there's something missing. (And ... broader documentation is missing for sure ;-)
They mention that they're working towards version 1.0 and then things are probably a bit clearer.

Meanwhile it's an idea to install the Hardy binary in Intrepid.

I've added these in my /etc/apt/sources.list :

deb [http://archive.turnkeylinux.org/ubuntu](http://archive.turnkeylinux.org/ubuntu) hardy main universe
deb [http://archive.turnkeylinux.org/ubuntu](http://archive.turnkeylinux.org/ubuntu) hardy-security  main universe

Did a sudo apt-get update

Then installed this older (needed) library from here [http://packages.ubuntu.com/hardy-updates/libparted1.7-1](http://packages.ubuntu.com/hardy-updates/libparted1.7-1)

And now the Hardy di-live binary installs without problems in Intrepid.

Can you test it ?
I don't know yet how to proceed with working with this program :)

---

### Post by empthollow on 2008-12-21
Excellent work!  I installed the libparted1.7.1 that you had a link to.  Then i downloaded and installed the latest di-live deb from the turnkey url i provided you with.  I had to install libdebian-installer4, os-prober, and libdebconfclient0 as dependancies for di-live but they were available in my intrepid repos.  I wanted to see if i could do it without mixing repos.  It works perfectly.  

It must be ran as root at least for the prog to write to the log files.  To do a full test i will have to finish the intrepid version of my live cd.  But, so far so good.  Thanks again.

---

### Post by albinootje on 2008-12-21
> **empthollow said:**
> Excellent work!  I installed the libparted1.7.1 that you had a link to.  Then i downloaded and installed the latest di-live deb from the turnkey url i provided you with.  I had to install libdebian-installer4, os-prober, and libdebconfclient0 as dependancies for di-live but they were available in my intrepid repos.  I wanted to see if i could do it without mixing repos.  It works perfectly.  

It must be ran as root at least for the prog to write to the log files.  To do a full test i will have to finish the intrepid version of my live cd.  But, so far so good.  Thanks again.

Good. Please report back how well it's working in Intrepid, as I'm curious to try di-live myself later on.

---

### Post by empthollow on 2008-12-21
Will do.:popcorn:

---

### Post by empthollow on 2008-12-29
> **albinootje said:**
> Good. Please report back how well it's working in Intrepid, as I'm curious to try di-live myself later on.

The program does it's job.  Up and running with a working system.  The only thing you may find an inconvienience is that it does not ask for user info on anyone except root.  So, once the system is up you have to create a user and add the user to the appropriate groups manually.

---

### Post by albinootje on 2008-12-29
> **empthollow said:**
> The program does it's job.  Up and running with a working system.  The only thing you may find an inconvienience is that it does not ask for user info on anyone except root.  So, once the system is up you have to create a user and add the user to the appropriate groups manually.

Thank you!

---

### Post by alonswartz on 2010-02-11
Hey folks,

I'm one of the developers for TurnKey Linux, and developed di-live. I just found this thread, pity no one posted a question on the [projects forums]("http://www.turnkeylinux.org/forum"), I could of saved you some pain.

Anyway, the di-live git repository is now available on [github]("http://github.com/turnkeylinux/di-live")

If you have any di-live related questions, feel free to ask.

BTW, if you're interested in a simple way to customize and extend any appliance in the TurnKey Linux virtual appliance library (should work for vanilla Ubuntu as well), take a look at [TKLPatch]("http://www.turnkeylinux.org/docs/tklpatch").

Cheers,
Alon Swartz

---

