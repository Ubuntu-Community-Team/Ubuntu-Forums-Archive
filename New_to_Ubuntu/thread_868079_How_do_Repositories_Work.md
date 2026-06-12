---
title: "How do Repositories Work?"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by sonicskywalker on 2008-07-23
How do the repositories work? Is it possible to put your own projects into a repository? If so, how do you do it?

---

### Post by LowSky on 2008-07-23
hope this helps

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)
[http://www.nongnu.org/synaptic/](http://www.nongnu.org/synaptic/)
[http://www.debian.org/doc/manuals/apt-howto/index.en.html](http://www.debian.org/doc/manuals/apt-howto/index.en.html)

---

### Post by dca on 2008-07-23
Easiest is to create your own for your project if it's hosted on your own server.  You provide instructions to end users how to add the repo to their package manager so that way the only thing they need to do is type the name in their search bar.  The only down side, the more people that hit your server the longer it will take to install or refresh repos, etc...
 
Then again if it's on sourceforge you can just release the source and let us compile and install on our own?

---

### Post by sonicskywalker on 2008-07-23
No way! if I release software, I want it to actually install properly and actually work! (this tarball garbage is a waste of time!)

Thanks!

---

### Post by LowSky on 2008-07-23
how to create a deb
[https://wiki.ubuntu.com/PackagingGuide/Basic?action=show&redirect=HowToBuildDebianPackagesFromScratch](https://wiki.ubuntu.com/PackagingGuide/Basic?action=show&redirect=HowToBuildDebianPackagesFromScratch)
[http://wiki.freegeek.org/index.php/Basic_Debian_Packaging](http://wiki.freegeek.org/index.php/Basic_Debian_Packaging)

---

### Post by Oldsoldier2003 on 2008-07-23
You can always publish your packages to your launchpad PPA as you are learning how to package.

[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

---

