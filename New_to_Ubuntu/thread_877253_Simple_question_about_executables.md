---
title: "Simple question about executables"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by CujoQuarrel on 2008-08-01
I believe this to be true but just checking to be sure.

Are executables made for one version of Linux usable in another version (i.e. SUSE -> Ubuntu) if they have the same kernel (and the appropriate libraries). I can't think why they wouldn't be but need to check to make sure.

Thanks

---

### Post by bks on 2008-08-01
Ubuntu uses *.deb files, where some other may use *.rpm, but it is possible to convert other file types to *.deb with alien.

---

### Post by eightmillion on 2008-08-01
For the most part yes. It really depends on how the program interacts with the system. Different distributions can be set up very differently.

---

### Post by loboc on 2008-08-01
> Ubuntu uses *.deb files, where some other may use *.rpm, but it is possible to convert other file types to *.deb with alien.

That wasnt what he was asking.  Binary executables work fine and should on any POSIX complient system BSD, Linux OSX.  Installing them so you can remove them concerns the packaging format.  If you download some stand alone program in a tarball it will work but you lose all the automatic magic of apt, it has super cow powers.

---

### Post by Thelasko on 2008-08-01
For the sake of this being the "Absolute Beginner Talk" no, there are differences.  Mostly because I don't want noobs trying to install RPM or tgz files.

The differences between the files can sometimes be very small, such as one is a .deb and one is a .rpm.  Other times, files and folders are located in different directories, and some parts of the source code have been changed.  It really depends on how the software was compiled, and what the differences are in the systems.

Usually, from distribution to distribution, the source code is the same.  Anything else can vary.

That being said, I have run RPM files on my Ubuntu machine.  I don't recommend it for beginners.

> Are executables made for one version of Linux usable in another version (i.e. SUSE -> Ubuntu) if they have the same kernel (and the appropriate libraries).

The directory structure needs to be the same, but with all of those caveats (there are a lot of them) they are the same.

---

### Post by scorp123 on 2008-08-01
> **CujoQuarrel said:**
>  Are executables made for one version of Linux usable in another version (i.e. SUSE -> Ubuntu) if they have the same kernel (and the appropriate libraries).  Usually yes, e.g. it should not be a big problem to install programs which only exist as SUSE *.rpm files on Ubuntu (you can convert such archives with "alien"), usually those binaries should run no matter what. BUT: as soon as the program does "funny things" e.g. it wants to use the "rpm" packet manager (which Ubuntu doesn't have) to check for the presence of a certain library (I've seen commercial apps who did that!! Bummer!) or as soon as it expects certain config files in certain locations (every Linux distro is a slight bit different in that regard) you may run into unexpected troubles.

---

### Post by scorp123 on 2008-08-01
> **Thelasko said:**
>  That being said, I have run RPM files on my Ubuntu machine.  I don't recommend it for beginners. I second that. You have to know what you do.

Best thing for a beginner is to use the repositories and the nice packet managers (e.g. Synaptic) and get your software from there.

---

### Post by CujoQuarrel on 2008-08-04
It was the binary executables I was asking about. Didn't phrase the question very well.

Thanks

---

