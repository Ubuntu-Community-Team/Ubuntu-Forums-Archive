---
title: "Builds are fine, can't install"
date: 2011-01-05
forum: Packaging and Compiling Programs
---

### Post by randyrando on 2011-01-05
Hi there, new to this forum.  I use Ubuntu on my laptop.  Our app, fossology is developed on debian systems (Lenny) and we build unofficial .debs for users to use and a Debian developer builds and uploads into the Debian stream.  We have a lot of users who try to install the .debs on Ubuntu, most of the time it doesn't work.  

I read up on how to build in ubuntu and then created chroots for 9.10, 10.04 and 10.10 on vm's of the same OS (e.g. 9.10 chroot is on a 9.10 vm etc...).

Using the same process I do for Debian builds, I used the chroot to build 32bit versions of fossology.  The builds are fine.  I made the Pakages and Sources files.  When I do a sudo apt-get update I get:

```

W: GPG error: [http://fossology.org](http://fossology.org) ./ Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch [http://fossology.org/ubuntu/karmic/./Packages.bz2](http://fossology.org/ubuntu/karmic/./Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

```

These are unofficial packages why is the Release file and the GPG signatures needed?

There is a Packages.bz2, what is going on with this? The man page for bzip2 doesn't mention error codes that I can find.

---

### Post by randyrando on 2011-01-05
A little clarification, when I try to apt-get update, I am doing this on a 9.10 system (which is what the packages were built for).

---

### Post by MadCow108 on 2011-01-05
you have created a own repository?

your Releases.gpg seems to contain no signatures, but that should be no problem, apt-get will just ask you if you want to install from an "untrusted" source

the second error is the problem. Can the Packages.bz2 be extracted manually? is the data in it ok (it should be what apt-cache show displays normally)?

---

### Post by randyrando on 2011-01-05
> **MadCow108 said:**
> you have created a own repository?

your Releases.gpg seems to contain no signatures, but that should be no problem, apt-get will just ask you if you want to install from an "untrusted" source

the second error is the problem. Can the Packages.bz2 be extracted manually? is the data in it ok (it should be what apt-cache show displays normally)?

Yes I created my own repository.  Ah, thank you!  After checking, the repository location is not reachable.  When I moved the bits to a reachable place the above errors went away.

I could extract the contents of the Packages file, it was not corrupt, I think the not  being able to reach it was the issue.  Thanks for your reply and questions it helped me figure out what was wrong.

---

