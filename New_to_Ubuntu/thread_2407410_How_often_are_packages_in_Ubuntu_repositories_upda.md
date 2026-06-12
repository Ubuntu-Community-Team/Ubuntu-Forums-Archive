---
title: "How often are packages in Ubuntu repositories updated ?"
date: 2018-12-03
forum: New to Ubuntu
---

### Post by automate-stuff on 2018-12-03
I want to use only the Ubuntu repositories and not PPA's, snaps or flatpaks....


I notice that in Ubuntu bionic 18.04 repository Geany has the 1.32 version.... but the latest Geany stable release is 1.33 .... When will Ubuntu repositories update Geany to 1.33 ?

---

### Post by TheFu on 2018-12-03
The basic idea for LTS is security fixes, yes!  Feature changes, no.

Security related items, if known, are backported to the LTS version, but corporate customers don't want any changes to features. They need stability more.  New is the enemy of stable.

So, in general, for people who need *newer*, they should use PPAs for the specific packages where they need it, but not for packages were it just doesn't matter.

For example, I use geany, but would rather have "stable" over "new" any day of the week.  The version on my 16.04 system is v1.27-1. But for VLC or ffmpeg, I want new and use PPAs.

At least this is how I hope it works.  There's got to be a document about this. Found it: [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by deadflowr on 2018-12-03
Ubuntu has a process for updating packages which you can read here:
[https://wiki.ubuntu.com/StableReleaseUpdates]("https://wiki.ubuntu.com/StableReleaseUpdates")

---

### Post by automate-stuff on 2018-12-04
So just to understand it better:

Right now in 18.04 Bionic, Geany 1.32 is available...So If I don't upgrade my Distro to 18.10+, Geany won't be upgraded to 1.33+ ?

---

### Post by Geoffrey_Arndt on 2018-12-04
Yes.   Software versions in each release of most distros are frozen snapshots which only receive bug fixes and security updates.   Once you actually get to have an inkling of how this all works, you have other options than upgrading the OS version.     Those options include PPA's, Stand-Alone Debs with no dependency issues (add OR remove installed core packages), Snaps, Flatpaks and AppImages.

BTW - - the two main exceptions to above are "Browsers" and "LibreOffice".     For the type of updates where your packages are updated - you need a "Rolling Release" distro like Arch or Solus.

BTW2 - - almost forgot . . the number one rolling release distro is Manjaro (based on Arch) . . . so the users can usually get the latest and greatest package releases.   (but Manjaro not as stable as Ubuntu, Suse, etc.)

---

