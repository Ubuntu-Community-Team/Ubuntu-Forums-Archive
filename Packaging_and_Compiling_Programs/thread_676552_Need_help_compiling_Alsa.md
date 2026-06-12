---
title: "Need help compiling Alsa"
date: 2008-01-23
forum: Packaging and Compiling Programs
---

### Post by Gannin on 2008-01-23
First let me give you a little background.  I'm running Ubuntu 7.04, and I'm currently using Alsa 1.0.15.  I've compiled 1.0.14 and 1.0.15 on this machine so I know I should, in theory, have all the libraries and what-not that I need.

I tried compiling the new 1.0.16rc1 and got a compilation error, so then I tried compiling the daily snapshot and got the same error.  The error is:

~/Desktop/alsa-driver-hg20080123/acore/../alsa-kernel/core/info_oss.c:96: error: ‘system_utsname’ undeclared (first use in this function)

Any help would be greatly appreciated.

---

### Post by geraldm on 2008-01-26
Your configure options did not include the kernel headers
OR the kernel source headers were not found in the expected location.
See INSTALL file in the top directory of the source.
pass to configure: {substitute your directory for kernel headers}
  --with-kernel=/usr/include

Gerald

---

### Post by Gannin on 2008-01-26
Thanks for trying to help :).  It looks like the problem was actually a bug in their sources, which they since have fixed in their daily source release.  But unfortunately not even this latest version fixes a problem I have where certain sounds from certain programs are crackly, which after digging around sounds like it's a problem caused by when certain sample rates are being converted to other sample rates for my sound card.  But that's another subject entirely.  Thanks again :).

---

