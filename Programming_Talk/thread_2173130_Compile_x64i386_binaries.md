---
title: "Compile x64/i386 binaries"
date: 2013-09-08
forum: Programming Talk
---

### Post by geohei on 2013-09-08
Hi.

I have a native x86_64 machine which runs Windows7.

I'd like to compile a binary for architectures x86_64 and i386 using a VM.

Can I install ubuntu-13.04-desktop-amd64 and compile the x86_64 and the i386 binaries?
Or do I have to install ubuntu-13.04-desktop-i386 for the i386 binary?
Or is it not possible to compile the i386 binary since the native hardware is x86_64?

In other words ...

Native x64 hardware -> VM with ubuntu-13.04-desktop-amd64 -> x86_64 binary -> works!
Native x64 hardware -> VM with ubuntu-13.04-desktop-amd64 -> i386 binary -> ???
Native x64 hardware -> VM with ubuntu-13.04-desktop-i386 -> i386 binary -> ???
Native x64 hardware -> VM with ubuntu-13.04-desktop-amd64 or ubuntu-13.04-desktop-i386 -> not possible to compile i386 binary ???

Thanks,

---

### Post by Bachstelze on 2013-09-08
gcc running on x86_64 can compile i386 code, just install [font=monospace]gcc-multilib[/font] and compile with the [font=monospace]-m32[/font] flag.

---

### Post by MadCow108 on 2013-09-08
cross compiling between i386 and amd64 is best done from a amd64 system with a i386 chroot.
you can cross compile directly via -m32 but its more error prone and can be difficult if the lbiraries you need are not available in i386 form (though that has improved greatly in newer versions of ubuntu).

easiest way to set it up a chroot is:
```
pbuilder-dist <distribution-of-choice> <architecture> create
pbuilder-dist <distribution-of-choice> <architecture> login --bindmount /working/folder/
#do your stuff
#logout
```

you can also build other architectures (armel, powerpc, ...) via emulation, but its slow.

---

### Post by geohei on 2013-09-08
Thanks for the replies.

Both of you don't pick up the VMs idea.

Doesn't it work using a VM? Something like this:
Native x64 hardware -> VM with ubuntu-13.04-desktop-i386 -> i386 binary -> ???

If that fails, I'll get back to your suggestions using gcc-multilib/ -m32 flag or i386 chroot.

---

### Post by MadCow108 on 2013-09-09
you can use a VM but you don't need to.
chroots have the same effect but without virtualization overhead.

---

