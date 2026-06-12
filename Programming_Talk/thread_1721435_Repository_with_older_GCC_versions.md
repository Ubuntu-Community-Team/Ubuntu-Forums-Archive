---
title: "Repository with older GCC versions"
date: 2011-04-04
forum: Programming Talk
---

### Post by Asmodai on 2011-04-04
Hey,

Is there a repository that has various different versions of GCC (g++ in particular)?
Newer versions often introduce regressions that can slow down some programs, so it's generally a good idea to try a few different versions to see which of them yields the best results in terms of execution speed and/or binary size.
I'd like to create an automated build system that compiles the project with various versions of GCC (and possibly ICC) and selects the best one.

At the moment, I have GCC 4.4/4.5/4.6 installed, however I'd like some older versions too (particularly from the 3.x series).

---

### Post by johnl on 2011-04-04
I'm not sure I buy in to your argument 100%, but [ftp://ftp.gnu.org/gnu/gcc/](ftp://ftp.gnu.org/gnu/gcc/) and  [ftp://ftp.gnu.org/old-gnu/gcc/]("ftp://ftp.gnu.org/old-gnu/gcc/") should have the source of every conceivable version of gcc.

---

### Post by Telengard C64 on 2011-04-04
Instead of adding multiple **gcc** versions to your current system, why not run multiple systems? You can setup older versions of Ubuntu in a virtual machine such as VirtualBox. That way you have access to older **gcc**, and you can test your program for compatibility with older systems at the same time.

Just a suggestion.

---

### Post by Asmodai on 2011-04-04
> **johnl said:**
> I'm not sure I buy in to your argument 100%, but [ftp://ftp.gnu.org/gnu/gcc/](ftp://ftp.gnu.org/gnu/gcc/) and  [ftp://ftp.gnu.org/old-gnu/gcc/](ftp://ftp.gnu.org/old-gnu/gcc/) should have the source of every conceivable version of gcc.
Well, for one smaller project I was working on, compiling with 4.6 slowed down the program by 20% in comparison to 4.4/4.5.
And while 4.4 and 4.5 are the same in terms of speed, the binary 4.5 produces is 10% larger than 4.4.
In some less common cases, the difference can be significantly greater than 20%, so I would say it's worth it. Even a speedup of 20% is not bad, considering it's essentially free (after the initial setup of the system, anyway).
I hoped to avoid compiling the old releases myself, but perhaps I'm overestimating the effort involved. I'll give it a try, thanks.

> **Telengard C64 said:**
> Instead of adding multiple **gcc**  versions to your current system, why not run multiple systems? You can  setup older versions of Ubuntu in a virtual machine such as VirtualBox.  That way you have access to older **gcc**, and you can test your program for compatibility with older systems at the same time.

Just a suggestion.
Hm true, that would be a possibility. One disadvantage would be that building could take quite a while since all VMs must be started and stopped one after another.
But the fact that it allows testing on various distributions is definitely a plus. I already have a VM with 9.10, so it might be a good idea to expand the collection a bit.

---

### Post by MadCow108 on 2011-04-04
if your only compiling just use a small chroot, built with debootstrap, instead of full blown virtual machine.
you can fit a dozen ubuntu/debian build chroots on a medium sized usb stick.
some tools which make setup very simple for debian/ubuntu are e.g. pbuilder/cowbuilder and sbuild.
e.g. pbuilder:
```

sudo pbuilder --create --basetgz mymaverickchroot.tgz --architecture i386 --distribution maverick --debootstrapopts --variant=buildd
... wait
sudo pbuilder --login --basetgz mymaverickchroot.tgz --save-after-login

```

---

### Post by NathanB on 2011-04-04
> **Telengard C64 said:**
> Instead of adding multiple **gcc** versions to your current system, why not run multiple systems? You can setup older versions of Ubuntu in a virtual machine such as VirtualBox. That way you have access to older **gcc**, and you can test your program for compatibility with older systems at the same time.

Just a suggestion.

That is a really good point.  I bet that's how they got UPS ( [http://ups.sourceforge.net/](http://ups.sourceforge.net/) ) to compile almost *everywhere* no matter the distro/flavor of the month.

---

### Post by Telengard C64 on 2011-04-04
> **Asmodai said:**
> One disadvantage would be that building could take quite a while since all VMs must be started and stopped one after another.

True it will take some time to compile on each system, but as long as your host has sufficient resources I don't see any reason not to run multiple VMs simultaneously. I've done it myself on a relatively underpowered system with VirtualBox. OTOH, if disk contention becomes an issue then perhaps you might try setting up your VMs on a flash drive or SDD instead of a spinning disk.

---

