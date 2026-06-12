---
title: "Nvidia driver update and old kernels"
date: 2013-08-09
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2013-08-09
Hi,

I usually keep 2 or 3 kernels around and use the most updated one for a few weeks before I remove the old ones. I  notice that if I upgrade the Nvidia driver (with xorg-edgers) I got dropped back to nouveau if I log into  a previous kernel even though everything works fine with the current kernel (from which I update the Nvidia driver) My way to work around thid is to boot into the current kernel (or whichever one from which I upgraded the graphic driver) and then reinstall the older kernels (or other kernels) then I can boot into any of them with the Nvidia driver working.

Somehow I think this may not be the correct way of doing it as it sounds rather clumsy, is there a better way? Does this only happen if the current kernel and the older one have a major version difference (say 3.10.x vs 3.8.y ) and  that there is no need to reinstall if the kernels only differ by a minor version (say 3.8.x vs 3.8.y)?

Thanks

---

