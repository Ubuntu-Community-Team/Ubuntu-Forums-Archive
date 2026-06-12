---
title: "EVEMon in Ubuntu 8.04"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Skeet on 2008-05-22
I can see here that there is a guide about how to install EVEMon in Ubuntu 7.10.

[http://evemon.battleclinic.com:8000/trac/wiki/MonoBuildOnUbuntu7.10](http://evemon.battleclinic.com:8000/trac/wiki/MonoBuildOnUbuntu7.10)

I have tried running through the instructions provided in 8.04. However when I get up to configuring and compiling mono, I get the following error:

```

checking for pkg-config... /usr/bin/pkg-config
Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found
Package gthread-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gthread-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gthread-2.0' found
Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found
Package gthread-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gthread-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gthread-2.0' found
checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 1.3.11) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I think it has something to do with my Gnome version, maybe it isn't supported by Gnome 2.22?

Does anyone have an alternative way of installing it in Ubuntu 8.04? Or can it not be done?

Cheers in advance.

---

### Post by Skeet on 2008-05-22
Solved. I needed to update my GTK version. Its making as I type now.

---

### Post by Phoenixzeus on 2008-05-22
Just what I needed,
Thanks

---

### Post by Skeet on 2008-05-22
All compiled and running. However I tried to make it minimize to tasktray and it's begun crashing on startup, every time. Pretty bad support tbh.

---

### Post by erikschneider21 on 2008-06-21
I hope I don't get in trouble for digging this up...

I'm running Hardy 64-bit and I'm trying to get EVEMon working on it, but when I try to follow the directions (actually, the very first direction) in the original post, I get this error:

```

Package mono is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mono has no installation candidate
```

I have Mono and MonoDevelop installed, too... I'm pretty sure this error means I need to get it from a different source, but I'm unable to find it.

Also, I don't have the folder opt/mono, and I'm fairly new to Linux, so I'm not sure whether the directions themselves would create this directory.

Thanks for any help,

Erik

---

### Post by AtomicSpark on 2008-06-21
> **erikschneider21 said:**
> I hope I don't get in trouble for digging this up...

I'm running Hardy 64-bit and I'm trying to get EVEMon working on it, but when I try to follow the directions (actually, the very first direction) in the original post, I get this error:

```

Package mono is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mono has no installation candidate
```

I have Mono and MonoDevelop installed, too... I'm pretty sure this error means I need to get it from a different source, but I'm unable to find it.

Also, I don't have the folder opt/mono, and I'm fairly new to Linux, so I'm not sure whether the directions themselves would create this directory.

Thanks for any help,

Erik

I actually just submitted an error for this. The package is now called "mono-runtime", there should be a transitional package from mono to mono-runtime.

[https://bugs.launchpad.net/ubuntu/+source/mono/+bug/241965](https://bugs.launchpad.net/ubuntu/+source/mono/+bug/241965)

---

### Post by erikschneider21 on 2008-06-21
Thanks!

Only after changing "mono" in the initial command to "mono-runtime", I encountered a dependency problem, which I fixed with Synaptic and altering my software sources, and now I have three more that I can't seem to fix:
```

The following packages have unmet dependencies:
  libmono-corlib2.1-cil: Depends: mono-jit (< 1.2.7) but 1.9.1+dfsg-1ubuntu1~dhx2 is to be installed
  libmono-dev: Depends: libmono0 (= 1.2.6+dfsg-6ubuntu3) but 1.9.1+dfsg-1ubuntu1~dhx2 is to be installed
  libmono-system2.1-cil: Depends: mono-jit (< 1.2.7) but 1.9.1+dfsg-1ubuntu1~dhx2 is to be installed
  libmono0-dbg: Depends: libmono0 (= 1.2.6+dfsg-6ubuntu3) but 1.9.1+dfsg-1ubuntu1~dhx2 is to be installed
E: Broken packages
```

It looks like the versions I have are above those required... I think.

I would have thought that wouldn't be a problem.

---

### Post by Krissam on 2008-07-08
> **Skeet said:**
> Solved. I needed to update my GTK version. Its making as I type now.

and how do you do that? im getting the same error, i tried apt-get update, but it doesn't do anything :/

---

