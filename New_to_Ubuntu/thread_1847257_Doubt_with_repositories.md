---
title: "Doubt with repositories"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by morle on 2011-09-20
Hi,

I've just installed Ubuntu 10.04 a few days ago and downloaded via Synaptic version 2.2 the Intel TBB libraries. However, in the Intel TBB web, it says that the current version is 4.0. Why the latest version don't appear in Synaptics to be downloaded? Maybe I'm missing something :(.

Thanks in advance.

PS: My sources.list file is attached!

---

### Post by drs305 on 2011-09-20
morle,

Welcome to the Ubuntu Forums.

In general, the Ubuntu repositories contain the packages for use by the specific version of Ubuntu you are running. Once a version of Ubuntu is released (Maverick, Natty, etc), the packages in the repositories are no longer updated to later versions. This gives the release stability. 

The packages in the primary Ubuntu repositories have been tested to ensure they work with that version of Ubuntu. Newer versions of packages aren't tested so they are not included in the repositories even though they may be available by 3rd party vendors.

There are some exceptions: security patches and sometimes newer kernels and very rarely a later version of a popular piece of software. Usually the advice given to someone wanting to install a newer version of a piece of software is to update to a later version of Ubuntu which may contain the newer application, enabling the 'backports' or 'proposed' repositories, or or going outside the normal repositories and accepting the risk of breaking your system.

Here is more on the Ubuntu method of using repositories:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by shashi20008 on 2011-09-20
Reload your repositories information in synaptic (by clicking reload button, obviously :P) then update your tbb library you will get most stable version (according to Ubuntu) i.e. 3.0. I personally believe that should be enough for your needs, however, if you require anything newer than that for latest tech stuff or testing you should download the tarballs form their website ([http://threadingbuildingblocks.org/ver.php?fid=175](http://threadingbuildingblocks.org/ver.php?fid=175) for v4.0) and install the library through that tarball. Installation through tarballs is not as easy as with synaptic, however you can get proper guidance from other posts on this website :-)

regards
shashi

---

### Post by morle on 2011-09-20
Thanks drs305 and shashi20008. I enabled the backports however the only version of Intel TBB that appears is still the 2.2. I suppose that the only way to obtain the latest version via Synaptics is to upgrade to a newer version of Ubuntu, isn't it?

Again, thanks.

---

### Post by drs305 on 2011-09-20
I am using Oneiric, the development version of Ubuntu that is still in Beta testing. Even in this version, the latest TBB library is 3.0+r147 (even in backports/proposed).

---

### Post by morle on 2011-09-20
I see. Ok! Thanks!

---

