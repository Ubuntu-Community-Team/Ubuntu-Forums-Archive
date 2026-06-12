---
title: "Mono 2.0"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by GNURULZ on 2008-11-12
Hello 

Is there any easy way or repo for Ubuntu to install Mono 2.0 i know it works straight out of the box for SUSE i tried compiling mono 2.0 and it failed for some reason i was just wondering if there was an easier way to install it on Ubuntu 8.04LTS. I would like to do some C# development work for Ubuntu rather then booting up XP with visual studio on it.

Thanks in advance.

---

### Post by sonicb00m on 2008-11-12
I don't think you can install Mono 2 without compiling it yourself.

Alternatively, you can run XP in virtual box and develop visual studio there. I use the seamless windows feature and install the Ubuntu theme in my XP environment and program there.

If you are looking to program natively then you'll have to figure out how to compile it yourself. I had very little success porting a VS project into Mono though and decided to start over with Java.

---

### Post by igknighted on 2008-11-12
[https://launchpad.net/~tlbdk/+archive](https://launchpad.net/~tlbdk/+archive)

Add this PPA (add the lines indicated to your /etc/apt/sources.list file), then run 'sudo apt-get update && sudo apt-get upgrade'.

EDIT: If you ever find yourself wanting something not in the repo's, chances are someone else wanted it too, so google search the application/driver and version + the ubuntu version + PPA and chances are someone has built it and it is in a PPA (like the community repo's you search on suse's website for packages for the online install)

---

### Post by GNURULZ on 2008-11-12
Thanks guys for your help but you are probably right about only being able to install it by compiling it. I guess i will have to leave windows xp inside a virtual Environment for C# work and continue to learn Python for Linux development work. I have been trying to install mono 2.0 on Ubuntu since it first got released I will try and compile it one more time if anyone has successfully installed it please post cheers.

---

### Post by directhex on 2008-11-12
So many PPAs by people who really haven't grasped the magnitude of the changes to Mono packaging (or indeed packaging, by the look of it). You won't get any support regarding problems with the above PPA from anyone at Debian or Ubuntu. The above packages ARE broken, but at a push they might install. Maybe.

There are three reasons you haven't seen Mono 2.0 packages any where official (or semi-official) yet.

1) You can't "just" update Mono, you need to produce updated packages for the entire "Mono stack" - XSP, monodoc, libgdiplus, gluezilla, etc etc etc. It comes to about ten source packages (making about a hundred binary packages), I think.

```
directhex@mortos:~/Projects/pkg-mono$ head -1 */trunk/debian/changelog
==> cli-common/trunk/debian/changelog <==
cli-common (0.5.8) UNRELEASED; urgency=low

==> gluezilla/trunk/debian/changelog <==
gluezilla (2.0-1) UNRELEASED; urgency=low

==> libgdiplus/trunk/debian/changelog <==
libgdiplus (2.0-1) UNRELEASED; urgency=low

==> mod-mono/trunk/debian/changelog <==
mod-mono (2.0-1) UNRELEASED; urgency=low

==> mono-basic/trunk/debian/changelog <==
mono-basic (2.0+dfsg-1) UNRELEASED; urgency=low

==> mono-debugger/trunk/debian/changelog <==
mono-debugger (0.60+dfsg-4) unstable; urgency=medium

==> monodoc/trunk/debian/changelog <==
monodoc (2.0-1) UNRELEASED; urgency=low

==> mono-tools/trunk/debian/changelog <==
mono-tools (1.9-2) unstable; urgency=medium

==> mono/trunk/debian/changelog <==
mono (2.0-2~pre1) experimental; urgency=low

==> moon/trunk/debian/changelog <==
moon (0.8.1+dfsg-1) unstable; urgency=low

==> xsp/trunk/debian/changelog <==
xsp (2.0-1) UNRELEASED; urgency=low
```

2) We're taking this opportunity to introduce some significant packaging changes. These changes will allow for a shrunken installation - new Jaunty installs should have 20-40% less space taken up by Mono than Intrepid and earlier

3) Testing and coherency. Putting something "unready" into a PPA is... risky. It can break users' systems. We want to ensure that the Mono 2.0 transition is as smooth as possible (it WILL introduce packaging changes, so you will not be able to compile mono-related packages after the transition without updating the package's build dependencies), which means we need a coherent single-point for the entire stack to be "sourced from" before it goes into a PPA. In this case, that means Debian Experimental. Mono 2.0 has been uploaded to Experimental, but due to the changes in point (2) above, it is waiting in the Debian NEW queue for ftpmaster approval. Once that lands, we can upload the remaining packages relating to the migration to Experimental (most of which should not suffer from any delays as they don't include new binary packages). Once THAT happens, and all of the Mono stack is in Experimental, then I'll request a sync of the lot into Jaunty - and upload packages to my semi-official repository for Hardy.

---

