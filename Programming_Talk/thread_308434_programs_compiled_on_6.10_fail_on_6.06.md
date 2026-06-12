---
title: "programs compiled on 6.10 fail on 6.06"
date: 2006-11-28
forum: Programming Talk
---

### Post by kornelix on 2006-11-28
I need some advice about how to avoid backward compatibility problems.

I have c++ / gtk2 software that does this:
  - compile on ubuntu 6.06: runs OK on 6.06 and 6.10
  - compile on ubuntu 6.10: crashes on 6.06, runs OK on 6.10

The crash message says that glibc 2.4 is required.
This is horrible news. Or am I not doing it right?

What should I do, in general, to maintain backward compatibility? 
Do I have to keep old versions of C libraries (and who knows what else)? 
Release multiple versions of the applications and explain to users how to deal with this?

---

### Post by Tomosaur on 2006-11-28
Upgrade to glibc2.4?

If getting people to upgrade may be a problem, you may aswell just compile it on 6.06 and release if it works. What's the reason for compiling on 6.10? If the working 6.10 version is no improvement over the 6.06 version, then it's a waste of time.

---

### Post by kornelix on 2006-11-28
> **Tomosaur said:**
> Upgrade to glibc2.4?

If getting people to upgrade may be a problem, you may as well just compile it on 6.06 and release if it works. What's the reason for compiling on 6.10? If the working 6.10 version is no improvement over the 6.06 version, then it's a waste of time.

This means I must stay on 6.06 for development, and either not keep up with Ubuntu or keep running old and new systems as long as they are incompatible. How long? How many OS generations will I need? For now, 6.06 programs run on 6.10, but not the reverse. Obviously if backward compatibility is not being maintained, this will only get worse and soon I will need a product version for every OS version. 

Is this the way forward?

Lack of backwards compatibility likely means that APIs were changed. API's should never change - only new ones should be added to support new capability, and small adaptors can normally be written to avoid having a large overlapping code base.

I hope it is not true that APIs were changed and that some other rational explanation will surface.

---

### Post by Tomosaur on 2006-11-28
No you won't because Edgy is not a stable release, so the vast majority of people will not upgrade to it anyway. Problems will likely be fixed in time for Feisty. If there's a problem with compilation on edgy, you should submit it to launchpad so somebody knows to fix it.

---

### Post by kornelix on 2006-11-29
According to Mark Shuttleworth, "binary compatibility is not a goal". I guess that settles the matter. It's not a bug, it's a feature.

Any sane software vendor who expects to provide support should not consider Ubuntu (or any Linux?). Or perhaps Mark's intent is that software vendors stick with Dapper for many years, and require their customers to do the same. Fat chance.

---

### Post by Tomosaur on 2006-11-29
I guess the multitude of developers who have no problem creating software are all just deluding themselves then.

---

### Post by pelle.k on 2006-11-29
It MIGHT be because of compiling against libc 2.4 when dapper has got libc 2.3. I have heard of backwards compability, but never upwards compability. :P You shouldn't expect software compiled against certain version of libraries to work on a slightly older system. That's what dependency checking is for. It _might_ work, but it's not guaranteed.

---

### Post by hod139 on 2006-11-29
You could release the source code and let the users build it for their specific system.

---

### Post by kornelix on 2006-11-29
> **Tomosaur said:**
> I guess the multitude of developers who have no problem creating software are all just deluding themselves then.

Sigh. I guess that's why so many commercial apps are so widely supported on Linux. 

Development is not the issue. It is making it work on many distros and many distro releases, without asking users to fix all the problems. The simplest example: directory naming and package naming is not consistent. A more complex example: take a look at what Mozilla.org does to make Firefox work on the three biggest Linux distros (fedora/RHEL, suse, ubuntu)
[http://developer.mozilla.org/en/docs/Linux_Compatibility_Reference](http://developer.mozilla.org/en/docs/Linux_Compatibility_Reference)

I am one of the few who bitch about Linux chaos, and my feeling is that 99% of Linux zealots either don't get it or like it that way.

---

### Post by kornelix on 2006-11-29
> **hod139 said:**
> You could release the source code and let the users build it for their specific system.

This works for maybe 3% of the users (more for Linux users, since only the technically adept can deal with Linux).

---

### Post by kornelix on 2006-11-29
> **pelle.k said:**
> It MIGHT be because of compiling against libc 2.4 when dapper has got libc 2.3. I have heard of backwards compability, but never upwards compability. :P You shouldn't expect software compiled against certain version of libraries to work on a slightly older system. That's what dependency checking is for. It _might_ work, but it's not guaranteed.

This is indeed the problem. I don't understand why it is compatible in one direction and not the reverse (compile on 2.3 works on 2.4).

My issue is that an application that uses only documented APIs (in my case: libc, gtk, gdk) should work across releases of these libraries as long as the APIs are stable.

---

### Post by cstudent on 2006-11-29
Set up a dapper chroot environment on your Edgy machine for compiling. 

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

---

### Post by pelle.k on 2006-11-29
I can't really say this is such a big issue. You wouldn't expect most windows XP applications to run under Windows 98. But you would expect most windows 98 appz to work in XP. This is true for most software, and generally OS independent.
The trick is to lower the bar to a point from which you instruct you users that - this software works with. People do it all the time. Take cdemu (sourceforge project) for example. They have decided kernel 2.6.17 should be the lowest kernel version for which it is made for. It'll still work on kernel 2.6.19 though....

---

### Post by po0f on 2006-11-29
kornelix,

glibc 2.3 is quite old, Red Hat/Fedora moved to 2.4 a while ago (I guess it helps the lead glibc dev works for Red Hat  :)).  I'm surprised it took Ubuntu so long.

Why don't you just release the source and let your users compile it for themselves?  Despite a majority of the users on these forums not knowing how to compile software, I think most could follow directions.  Just make sure your makefile or whatever build process you use is bullet- and idiot-proof.

Another option, since glibc and GTK are released under the LGPL, is statically linking your binaries.  Just make sure all the libraries you use are released under the LGPL and you should be fine.

---

### Post by RAOF on 2006-11-29
> **kornelix said:**
> ...

What should I do, in general, to maintain backward compatibility? 
Do I have to keep old versions of C libraries (and who knows what else)? 
Release multiple versions of the applications and explain to users how to deal with this?

You essentially have 4 options:
1) Release the source (with some kind of Makefile/configure/autotools setup), so it's easy for users on all systems to build and use.  This is the best solution, since you also grant people the ability to run your software under non-Ubuntu systems (and, potentially, non linux systems).  Also, this can be combined with one of the solutions below to make it easier for your users.

2) Build separate Edgy/Dapper/Whatever binaries.  The **pbuilder** package can help you doing this, by automatically setting up a clean Dapper (or Edgy, or Breezy, or Feisty, or Debian-Etch) system in a chroot.  The pbuilder system will work best if you're building debian packages (.debs), but can be used to just build binaries if you like.

3) Build a lowest-common-denominator binary.  Build on Dapper, and it **should** work on Edgy or anything later, since libraries tend to be backwards-compatible.  This should be done in a Dapper (or whatever) chroot, so **all** the libraries are Dapper versions.

4) Statically link your binary.  This is undoubtebly the worst solution, but will ensure your binary runs **everywhere**.  Problems include: if you actually want to support your binary, you'll need to rebuild and redistribute it each time one of your underlying libraries gets a security update.  Binary size: for example, statically linked Skype is 9MB larger (that's twice as big).  Memory usage: most of the libraries you want will be already loaded.

---

### Post by kornelix on 2006-11-30
Thanks for the suggestions. 

I already release source with a build script, and some users understand the problem and just rebuild from source. Others do not, and just expect it to work out of the box.

Looks like I need to complicate my life with pbuilder and chroot and making .deb packages. I started looking at this and the complexity is intimidating.

---

### Post by pelle.k on 2006-11-30
kornelix;
If you wan't to take the easy route, then install dapper and compile the package there. It'll work under edgy.
If you also would release the source (withna decent makefile), we would have the best of both worlds.
Good luck!

---

