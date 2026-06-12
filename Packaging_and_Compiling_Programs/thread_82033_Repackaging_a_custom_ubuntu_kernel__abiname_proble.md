---
title: "Repackaging a custom ubuntu kernel / abiname problem"
date: 2005-10-25
forum: Packaging and Compiling Programs
---

### Post by nooky59 on 2005-10-25
Hi,

I've followed this WIKI page :

[https://wiki.ubuntu.com/KernelBuildpackageDetailedHowto](https://wiki.ubuntu.com/KernelBuildpackageDetailedHowto)

in order to add a dpatch to the 2.6.12.23 current kernel and make a 686 deb package of it.

I've this error

```

Missing /home/florent/linux-source-2.6.12-2.6.12/debian/abi/2.6.12-9.23/abiname file.

```

when doing the

```

dpkg-buildpackage -rfakeroot -us -uc -b

```

When I do a ls -l debian/abi, there is a 2.6.12-9.22 folder but not a 2.6.12-9.23 folder...

I suppose I can make a mv or cp of it in order to have a 2.6.12-9.23 folder but as it is the true deb-source of the current stock Ubuntu kernel, the Ubuntu dev guys have successfully compiled the kernel package without 2.6.12-9.23 folder so I don't know if it's the perfect way to make a cp or mv of 2.6.12-9.22 to 2.6.12-9.23

Anyone can help ?

If someone give me a perfect answer, I will update the WIKI page, I promise ;)

---

### Post by nooky59 on 2005-10-29
Really anybody skilled enough for this ?

I have decided to keep the .23 release instead of a .23custom release but there is still problematic abi issues after...

The build process failed near the end telling that the abi has changed and displaying a diff. This diff show the modules that has been changed by the dpatch added.

The WIKI page is definitively not up to date, nor functionnal.

---

