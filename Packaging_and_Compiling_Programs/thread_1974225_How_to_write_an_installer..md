---
title: "How to write an installer."
date: 2012-05-05
forum: Packaging and Compiling Programs
---

### Post by JoshDempsey on 2012-05-05
First off, I don't know if this is in the right section (I take it that it's not) so sorry if a moderator has to move this.

I come from another forum, far far away. Overclock.net. Basically it's an overclocking community. We have a live linux distrobution built off of Ubuntu with lots of overclocking tools; stress testing etc. Now however members want to be able to install this and remove it after using it as some people stress test for periods like 12 hours.

I took it upon myself to try and complete this but do not know where to start. I have been using Linux for about 4 years and know a fair bit, but am stumped by this as I haven't really been involved in a lot of Linux kernel/os programming.

Can someone tell me the basic steps how to create one or maybe provide a handy link that will shoot me in the right direction?

Thanks.
Josh.

---

### Post by lisati on 2012-05-05
*Thread moved to **Packaging and Compiling Programs**.*

---

### Post by Bachstelze on 2012-05-06
YOur message is not very clear. You want to create an installer for what exactly?

---

### Post by Mr. Picklesworth on 2012-05-06
If we're talking about Ubuntu, you (very) likely don't want an installer, but a software package. (In our case, a Debian package).

Here's a place to start:
[http://developer.ubuntu.com/packaging/html/packaging-new-software.html](http://developer.ubuntu.com/packaging/html/packaging-new-software.html)

Primarily, a package says what files are included in your application and where they go. It also says what other packages need to be installed for your package to work, and it can include fancy install scripts (but those are not often necessary).

The package itself is not executable. Ultimately, the package manager is the thing that installs it.

---

### Post by JoshDempsey on 2012-05-06
> **Bachstelze said:**
> YOur message is not very clear. You want to create an installer for what exactly?

Basically to install Ubuntu...

---

