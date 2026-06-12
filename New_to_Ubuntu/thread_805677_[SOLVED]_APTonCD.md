---
title: "[SOLVED] APTonCD"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by leftfootleashed on 2008-05-24
Hi,

I'm trying to use APTonCD to backup my installed packages before I upgrade from Gutsy to Hardy to save me downloading everything again under Hardy. However, when it scan, it doesn't pick up all my packages. I've tried searching the whole filesystem for .deb files to add them, but I can't find them for most of the packages I have. Does this mean I have to download the packages again? Or is there a different type of file I should be looking for?

Any advice would be much appreciated,

Thanks,

Dave

---

### Post by angry_johnnie on 2008-05-24
I think it looks for packages in /var/cache/apt/archives.

If you've run **sudo apt-get autoclean** in the past, you most likely don't have anything in there.

---

### Post by leftfootleashed on 2008-05-24
Yeah, that makes sense. I don't remember doing that, but then I don't remember everything I do ;). Looks like I'll have to download them again. Cheers for your help.

---

### Post by plucky on 2008-05-24
> I'm trying to use APTonCD to backup my installed packages before I upgrade from Gutsy to Hardy to save me downloading everything again under Hardy


Don't use AptonCD to save your packages,as the Hardy packages will probably be more up to date versions.If you do an upgrade from Gutsy to Hardy,the packages will also be upgraded.If you do a clean install then you have to install all your extra packages yourself.

AptonCd is good to save your packages if you ever have to reinstall the Operating System and don't want to download them again.

Good Luck

---

