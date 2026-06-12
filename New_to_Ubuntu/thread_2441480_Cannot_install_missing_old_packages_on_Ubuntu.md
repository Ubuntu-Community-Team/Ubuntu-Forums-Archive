---
title: "Cannot install missing old packages on Ubuntu"
date: 2020-04-23
forum: New to Ubuntu
---

### Post by thiguchi on 2020-04-23
Hello,

I am trying to install a commercial software for RHEL on Ubuntu 19.10.
If I check the dependencies by ldd.
The only packages missing in the system are the three:
- libpng15.so.15
- libicui18n.so.50
- libicuuc.so.50
- libicudata.so.50
The last three seem to belong to a package libicu50.
I have newer versions, libpng16 and libicu55 libicu63, installed.
I searched for them on repositories but could only find versions other than 50 for libicu. I only found rpms for libicu50 on web search.
 As for libpng, I found it on Sourceforge and installed it by building manually, but still don't see it reflected on the output of ldd.

Could anyone give me instructions for installing them on Ubunutu?

Thanks very much in advance!

---

### Post by wildmanne39 on 2020-04-23
Hello and welcome to the forum.

*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

### Post by DuckHook on 2020-04-23
Welcome to the forums thiguchi,

If you are trying to install RHEL packages on Ubuntu, you ought to be aware of how fraught with danger such attempts are. We do not know how experienced you are with Linux, but distros cannot be mixed because they each make different decisions about what libraries&#8212;and which versions of libraries&#8212;they will include. In your case, the libraries are either missing or the versions are incompatible. Of the two, the last is the most problematic. Forcing the wrong library versions onto your system is more than likely to break it.

Your proposed course of action is not recommended.

I see the following choices:

[LIST=1]
[*]See if there is a more recent version of the commercial software available that runs on Ubuntu's newer libraries,
[*]Install and run an older version of Ubuntu that has the older libraries (like Bionic or Xenial),
[*]Install the proper version of RHEL or Fedora in a VM and run your commercial app from within the VM,
[*]Install a Docker instance that has the right libraries to run just this app,
[*]Make use of an LXD container to run RHEL or Fedora, within which your commercial app should be able to run almost natively. This last option is linked in my sig: *Sandboxing Apps with LXD*.  Note that this method requires some Linux-Fu to implement and is not appropriate for beginners.
[/LIST]

---

