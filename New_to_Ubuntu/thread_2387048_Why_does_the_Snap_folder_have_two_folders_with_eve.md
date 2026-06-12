---
title: "Why does the Snap folder have two folders with every root folder?"
date: 2018-03-14
forum: New to Ubuntu
---

### Post by jimijives on 2018-03-14
Hi, I ran a anti-virus scan with Sophos and it reported no viruses but said 47 errors and they were all messages saying could not open folders.  Here is a small sample:

Could not open /snap/core/4110/etc/alternatives/awk
Could not open /snap/core/4110/etc/alternatives/jsondiff
Could not open /snap/core/4110/usr/sbin/dpkg-divert
Could not open /snap/core/4110/usr/sbin/dpkg-statoverride
Could not open /snap/core/current/etc/hostname
Could not open /snap/core/current/etc/mtab
Could not open /snap/core/current/usr/sbin/dpkg-statoverride
Could not open /snap/core/current/usr/share/doc/openssl/copyright

Because Sophos said no virus detected I feel quite confident there is nothing wrong but this is just bugging me.  I read about the Snap folder and it's supposed to be somewhere files go for programs you install go?

What is puzzling me is inside the Snap folder are another three /bin   /chromium   /core  and a README file.
The chromium folder has quite a small copy of root folders.  However the /bin and /core folders have absolutely everything that is in the root folder.

Is this normal?  It seems like a lot of duplication for no specific program because chromium is the only thing I installed from Ubuntu Software.

Thanks for any advice, I appreciate your time.

---

### Post by Holger_Gehrke on 2018-03-14
This is completely normal and part of the way snaps work. The 'real' snap-packages are compressed file system images  (squashfs files residing in /var/lib/snapd/snaps/), which get mounted into subdirectories of /snap. Quite a few of the files in the snaps duplicate files which are already on the system, but might be different versions of these files. The ideas is for a snap to be as self-contained as possible and to deliver everything a program needs along in the package without relying on other packages. In some cases there are symbolic links in the snap to files which exist on the system on which the snaps was created but which don't necessarily exist on your system, which is what causes the warnings by your anti-virus. It tries to follow the link and finds no file for it. The error message is somewhat misleading and makes it seem to me like the authors of that software are more used to windows on which symbolic links are rarely if ever used while they are used extensively on almost all Linux systems.

Holger

---

