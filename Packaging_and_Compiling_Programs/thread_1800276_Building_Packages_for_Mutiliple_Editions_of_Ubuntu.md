---
title: "Building Packages for Mutiliple Editions of Ubuntu"
date: 2011-07-08
forum: Packaging and Compiling Programs
---

### Post by shire_p on 2011-07-08
Hi,  I am Ubuntu/Linux novice, this is my first post. I'm trying to understand how to build a package. I've read quite a few documents and understand the basics although I have not built one yet. Do I need to build a separate package for every edition (e.g. Hardy, Lucid etc.) of Ubuntu that I want my GUI application to run on? If so, should I build the package for a specific edition on that edition of Ubuntu? If not, are there any guidlines or recommendations for building packages that would run on multiple editions of Ubuntu? For example, on another popular OS its common to dynamically load a library, if the functionality is not there, then try to degrade gracefully.  Do you know if the answers to these questions also apply to other Linux distributions?    Thanks in advance for any help.

---

### Post by Bachstelze on 2011-07-11
> **shire_p said:**
> I've read quite a few documents and understand the basics although I have not built one yet.

Then do it!  Do not wait until you know everything before building your first package, because you will *never* know everything. ;)

> Do I need to build a separate package for every edition (e.g. Hardy, Lucid etc.) of Ubuntu that I want my GUI application to run on?

You might not *need* to.  Often, a package built for one release of Ubuntu will work fine on another.  However, this is not guaranteed, so it's better do build it for every targeted release anyway (packages on the official repositories and on PPAs are always built on the target release).

> If so, should I build the package for a specific edition on that edition of Ubuntu?

Yes.  Note that this does not mean that you need to have every edition installed, however.  There are tools that let you have a "build system" for every release that you can use from your main system without rebooting (look at pbuilder).

---

### Post by shire_p on 2011-07-11
Hi Bachstelze,  Thanks for the clear and detailed explaination. I have now built my first simple package. When I looked through the repository I wasn't sure if packages had been rebuilt because they application changed version number or because they targeted a different version of Ubuntu. While looking for an IDE I noticed that CodeLite provides multiple packages for diffenent Linux distros and versions. I see, pbuilder looks really useful.    > **Bachstelze said:**
> Then do it!  Do not wait until you know everything before building your first package, because you will *never* know everything. ;)



You might not *need* to.  Often, a package built for one release of Ubuntu will work fine on another.  However, this is not guaranteed, so it's better do build it for every targeted release anyway (packages on the official repositories and on PPAs are always built on the target release).



Yes.  Note that this does not mean that you need to have every edition installed, however.  There are tools that let you have a &quot;build system&quot; for every release that you can use from your main system without rebooting (look at pbuilder).

---

