---
title: "How frequently are proprietary drivers updated in repositories?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by rfrench22 on 2008-07-11
I'm running 8.04 on an HP dv6000 series laptop that uses a Nvidia 6150 graphics processor.  Both the proprietary Nvidia driver - version 169.12 (available via Synaptics and Hardware Drivers program under the Administration menu), and the non-proprietary driver (NV) have annoying, but different problems associated with suspend and resume.  I noticed that Nvidia has released a more recent version of their proprietary driver in June (version 173.14.05) which is described in the release notes as addressing some display issues associated with the 8.04 release.  

I would like to try this driver, but it appears that there is some administrative downside to installing it via their installation procedure (such as having to reinstall it each time a new kernel is released) as opposed to obtaining it via the Ubuntu Update Manager mechanism.  Does anyone have experience about how long it takes to roll newer versions of proprietary drivers into the repositories?  It seems that there is a 173.14 'envy' version of the nvidia-glx-new driver, but there is no  'standard' nvidia-glx-new at version 173.14.

Thanks for your thoughts on this.

---

### Post by sdennie on 2008-07-11
Things may be different for an LTS release but, generally, the nvidia driver will not change for the lifetime of a release.  It's closed source so it can't be incrementally updated to fix problems.  I would try using envyng and, if that doesn't work, then using one of the many guides on this forum to install the drivers manually.

---

### Post by rfrench22 on 2008-07-12
Thanks for your guidance on this.  I'll try EnvyNG to install a newer version of the Nvidia driver.

---

