---
title: "Newbie question: schroot vs. pbuilder? Which is the preferred chroot environment?"
date: 2011-05-19
forum: Packaging and Compiling Programs
---

### Post by kaustavdm on 2011-05-19
Hi all,

I am totally new to Ubuntu/Debian packaging (in fact, new to the world of packaging). I've been reading the docs at [https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide).

On my Lucid 64bit server, I've set up Lucid chroots following both [https://wiki.ubuntu.com/DebootstrapChroot]("https://wiki.ubuntu.com/DebootstrapChroot") and [https://wiki.ubuntu.com/PbuilderHowto]("https://wiki.ubuntu.com/PbuilderHowto"). At the present, I can successfully schroot into Debootstrap's Lucid chroot installation, as well as use the pbuilder for building debs. (I've tried out the tutorial at [PbuilderHowto - Rebuilding a package]("https://wiki.ubuntu.com/PbuilderHowto#Rebuilding a package")).

My question is, as the title suggests, which of the two methods are more preferred or reliable as chroot during package building? schroot or pbuilder? Also, I'd be glad to know why they are preferred and whether it is just a matter of personal preference?

One answer is, as I think, pbuilder satisfies all dependencies on its own while building a package while in schroot, one has to install the dependencies manually. Any further suggestions?

---

### Post by SevenMachines on 2011-05-19
PBuilder, its designed for the job. It unpacks a clean, minimal base system creating the chroot, and then satisfies build dependencies using your packaging. This checks that your packaging is (likely) correct, and will build properly on a other systems. Obviously schroot alone would not preserve a clean minimal build environment, nor check build dependencies properly

---

### Post by kaustavdm on 2011-05-19
> **SevenMachines said:**
> PBuilder, its designed for the job. It unpacks a clean, minimal base system creating the chroot, and then satisfies build dependencies using your packaging. This checks that your packaging is (likely) correct, and will build properly on a other systems. Obviously schroot alone would not preserve a clean minimal build environment, nor check build dependencies properly

So, pbuilder seems to be a better choice in packaging. Thanks :)

---

