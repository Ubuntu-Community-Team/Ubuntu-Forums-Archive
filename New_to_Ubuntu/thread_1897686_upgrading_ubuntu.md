---
title: "upgrading ubuntu"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by *^kyfds( on 2011-12-19
hi.


this thread will probably be moved to recurring discussions, but i thought i might as well ask anyway.

i'm currently running ubuntu 11.10, and i was wondering how to update my version (when ubuntu 12.something comes out).

how does this sort of thing go?

will i have to reformat my drive?

thanks in advance, 

thehumorouscheese.

---

### Post by kanikilu on 2011-12-19
There is more than one way to do a distro upgrade, but here are the instructions straight from ubuntu.com:

[http://www.ubuntu.com/download/ubuntu/upgrade](http://www.ubuntu.com/download/ubuntu/upgrade)

---

### Post by critin on 2011-12-19
It will show at the top of your update notification in April, giving you a choice to upgrade from there.  No, you don't have to do anything except let it install.

I suggest waiting a few days and pay attention on the forums though, see what problems others are having with upgrading.  You may decide to download the iso and do a clean install instead.  Start backing up your personal stuff so you don't lose anything if you do a clean install. (or upgrade)

---

### Post by *^kyfds( on 2011-12-19
thanks for your help.

i'll probably be going for the update manager instead of the clean install.

---

### Post by guyver_dio on 2011-12-19
You can upgrade to the alpha release but I would wait until the full LTS version gets released. If you want to see how the alpha and development versions are going install them in a VM, I made the mistake of upgrading to the alpha release and it screwed everything (had to reinstall ubuntu so I tried the alpha off a cd and it wasn't worth it anyway, not very usable atm).

I'd definitely go with a clean install over an upgrade when it gets released too. 

Just incase you were thinking of doing that ;)

---

### Post by QIII on 2011-12-20
If you have the ATI proprietary graphics driver installed, it used to be best to uninstall it before upgrading.

For several upgrades (before I took to just doing clean installs) I had a bugger of a time unless I uninstalled them first and reinstalled after the update.

May be different these days.  One would hope.

---

### Post by bodhi.zazen on 2011-12-20
> **Thehumorouscheese said:**
> hi.


this thread will probably be moved to recurring discussions, but i thought i might as well ask anyway.

i'm currently running ubuntu 11.10, and i was wondering how to update my version (when ubuntu 12.something comes out).

how does this sort of thing go?

will i have to reformat my drive?

thanks in advance, 

thehumorouscheese.

It is a valid question.

The general process is

1. Back up your data and a list of currently installed applications.

2. Disable any and all third party repos, including ppa.

3. Remove all third party drivers (video, wireless) from outside the ubuntu repositories.

4. fully update your system.

5. READ THE RELEASE NOTES

6. Boot your system with the new desktop iso, this allows you to identify and obvious problems.

7. Upgrade.

8. re-enable third party repos, re-install any third party video or wireless drivers.

If all that seems too much hassle, back up your data and do a fresh install.

---

### Post by *^kyfds( on 2011-12-21
thanks again.

marking as solved ^_^

---

