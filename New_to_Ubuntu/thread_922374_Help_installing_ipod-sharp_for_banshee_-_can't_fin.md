---
title: "Help installing ipod-sharp for banshee - can't find libraries"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by Offramp on 2008-09-17
Hi all,

I am trying to build a library from the banshee project page (ipod-sharp).  I cannot get my ipod to be recognised by banshee (although is by gtkpod and rythmbox) One of the posts on their site suggests making sure ipod-sharp and podsleuth are installed. I downloaded the tarball for ipod-sharp from banshee and when I type ./configure I am presented with this error:

```
checking for MONO_MODULE... configure: error: Package requirements (mono >= 1.1.10) were not met:

No package 'mono' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MONO_MODULE_CFLAGS
and MONO_MODULE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details
```

I did some reading and MONO is a JIT compiler and Banshee utilises it.  I checked Synaptic and I have MONO libraries installed which are greater than the error, so is there something I am missing? I am using an up to date ubuntu 8.04

Cheers

---

### Post by tgalati4 on 2008-09-17
banshee-1 seems to work fine with my iPod 2nd gen nano.  Try installing banshee-1.  Since it's a code rewrite, it doesn't interfere with your original banshee installation.  I couldn't get DAAP music shares to work though with banshee-1.  They work fine under banshee.

---

### Post by Offramp on 2008-09-17
Thanks for your response. I am using banshee-1 (1.2.1.), and whilst I have ipod-sharp installed, I am not sure it is is the most recent release, and this is why I was trying to build the latest version.

---

