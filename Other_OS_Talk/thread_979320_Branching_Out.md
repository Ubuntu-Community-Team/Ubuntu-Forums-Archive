---
title: "Branching Out"
date: 2008-11-11
forum: Other OS Talk
---

### Post by WaeV on 2008-11-11
My first exposure to ubuntu was back when Dapper Drake was the new release.  I remember spending hours configuring the default screen size, adding ntfs read support (write?  Who're you kidding?!), not to mention Beryl.  Now, it's all too easy.  Even compiz and wine can be installed with a couple of clicks, maybe a restart.

My point is that I miss tinkering.  Ubuntu is stable, easy, and certainly faster than windows, but I'd like to branch out.  What are some other, more difficult linux distros with emphasis on speed?  I have already heard of Arch and Zenwalk, but more info would be great, maybe a small summary.  Also, I would like to avoid KDE.  I prefer Gnome, but am willing to try XFCE, especially in the name of speed.

---

### Post by cardinals_fan on 2008-11-11
Arch provides the ability to tinker but still keeps things pretty easy.  Slackware is very good for learning about your system.  Zenwalk provides an easy intro to Slack.  Gentoo (or Sourcemage/Lunar/etc.) provide total tweaking, but compiling from source can be a pain.  NetBSD is a great experience (it isn't Linux) and has a very clean design.  SliTaz is **tons** of fun but is still a bit new.  OpenSolaris is an entirely different experience.

---

### Post by WaeV on 2008-11-11
Are Opensolaris and NetBSD similar?  I know they're both Unix.

Arch says it is designed for i686 systems.  What's that mean?

Is Arch based on anything, as Ubuntu is based on Debian?

What do other OSes have in terms of package managers?

Do you mean compiling Gentoo can be a pain, or compiling programs whilst running Gentoo can be a pain?

Are Unix derivatives really any more different from Debian derivatives as Slackware Derivatives etc. are?

---

### Post by kk0sse54 on 2008-11-11
Sorcerer Linux anyone? Now that was an expierence and to think it used to be ranked within the top ten at distrowatch...

Edit:sorcerer linux = bad expierence, very very bad expierence...

---

### Post by WaeV on 2008-11-11
Hmm...

"Current versions of Sorcerer release some key components under the Sorcerer Public License and not the GPL, and the distribution has dropped the term GNU/Linux."

Sounds linux enough.  What's it like?

---

### Post by kk0sse54 on 2008-11-11
> **WaeV said:**
> Are Opensolaris and NetBSD similar?  I know they're both Unix.

Arch says it is designed for i686 systems.  What's that mean?

Is Arch based on anything, as Ubuntu is based on Debian?

What do other OSes have in terms of package managers?

Do you mean compiling Gentoo can be a pain, or compiling programs whilst running Gentoo can be a pain?

NetBSD is a BSD type operating system while OpenSolaris is based off of Sun's Solaris, both are  more closely related to Unix than Linux but are extremely different from each other. As for package management NetBSD uses pkgsrc while say for example Arch uses pacman and when it says Arch is designed for i686 systems it means it'ss designed for the i686 processor but there's also a X86_64 version. Gentoo on a whole is sometimes described as a pain as compiling anything can often be a pain.

---

### Post by cardinals_fan on 2008-11-11
> **WaeV said:**
> Are Opensolaris and NetBSD similar?  I know they're both Unix.
> **C!oud said:**
> NetBSD is a BSD type operating system while OpenSolaris is based off of Sun's Solaris, both are  more closely related to Unix than Linux but are extremely different from each other. As for package management NetBSD uses pkgsrc while say for example Arch uses pacman and when it says Arch is designed for i686 systems it means it'ss designed for the i686 processor but there's also a X86_64 version. Gentoo on a whole is sometimes described as a pain as compiling anything can often be a pain.
> **WaeV said:**
> 
Arch says it is designed for i686 systems.  What's that mean?
It's optimized for Pentium 4+ machines.
> **WaeV said:**
> 
Is Arch based on anything, as Ubuntu is based on Debian?
Inspired by CRUX and Slackware, but independently written.
> **WaeV said:**
> 
What do other OSes have in terms of package managers?
Arch's pacman is insanely good.  Source-based distros (and NetBSD) have automated systems that compile packages.  OpenSolaris has weak package management.  Slackware requires manual dependency handling by default, but it's easy to add a 3rd party app that does it for you (slackpkg or slapt-get).
> **WaeV said:**
> 
Do you mean compiling Gentoo can be a pain, or compiling programs whilst running Gentoo can be a pain?
All software installed on Gentoo (with some exceptions) must be compiled.
> **WaeV said:**
> 
Are Unix derivatives really any more different from Debian derivatives as Slackware Derivatives etc. are?
Definitely.  They aren't Linux, but OSs of their own.

---

### Post by namegame on 2008-11-11
> **WaeV said:**
> Are Opensolaris and NetBSD similar?  I know they're both Unix.


I've never actually used Opensolaris, but I did use Solaris for 1 year. My University's Computer Science department's OS recommended OS was Solaris. I found it to be quite stable and user-friendly.

They have now switched to CentOS. It's good too.

---

### Post by zmjjmz on 2008-11-11
If you want an experience I would recommend salvaging an old computer from a dump and then trying to get some form of Linux running on it. Depending on how old it is, it may be harder or easier than Ubuntu is. For the most part none of the Linux distributions meant for old hardware use GNOME, and only some use XFCE. 
They require a good bit of tweaking if you have something really old, but a lot of times you can get away with having it work perfectly out of the box (because the hardware is so old the drivers have been integrated into the kernel a long time ago).

---

### Post by basenvironment on 2008-11-12
debian of course....

---

### Post by WaeV on 2008-11-12
I think I'll go with Zenwalk.

---

### Post by Algus on 2008-11-13
Personally I wouldn't get near Gentoo.  I want my OS to just be able to work out of the box and that's why I love Ubuntu and Mint.  They may not be as "fast" as distros like Gentoo but they're sure a heck of a lot faster then Windows and they let me do everything that I need to do.

That said, it seems like there's no finer distro then Gentoo if you want to spend the time tinkering.  I know some of the more "hardcore" Linux guys I talk to swear by Gentoo.

---

### Post by tvtech on 2008-11-13
again can I say plan9   check out plan 9 by bell labs.

---

### Post by WaeV on 2008-11-14
I changed my mind.  I'm going with Arch.

Thanks for all your input!

---

### Post by mips on 2008-11-15
> **cardinals_fan said:**
> It's optimized for Pentium 4+ machines.


No, it's optimised for Pentium II+ machines. i686 is basically pentium 2 onwards.

[http://www.archlinux.org/about/](http://www.archlinux.org/about/)
> Arch Linux uses i686-optimized packages which gives us improved     performance over some of our i386-optimized cousins.  This means that Arch     Linux will only run on a Pentium II processor or higher.

[http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide#Installing_Arch_Linux](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide#Installing_Arch_Linux)
> **Pre-Installation**

 Arch Linux is optimized for the i686 processor and therefore will not run on any lower or incompatible generations of x86 CPUs (i386,i486,i586). A Pentium II or AMD Athlon processor or higher is required. Modern VIA C3 processors are also supported. x86-64 architectures are also officially supported. 


[http://en.wikipedia.org/wiki/Intel_P6](http://en.wikipedia.org/wiki/Intel_P6)

---

### Post by cardinals_fan on 2008-11-15
> **mips said:**
> No, it's optimised for Pentium II+ machines. i686 is basically pentium 2 onwards.

Yes, that's right.  See what I get for posting without thinking? :)

---

### Post by WaeV on 2008-11-16
I'm using the x86_64 version anyways.

---

### Post by lyjg1113 on 2008-11-18
[**?k?C**](http://www.shunfengbj.cn/) &#12289;&#36710;&#33337;&#35777;&#12289;&#23548;&#28216;[**?k?C**](http://www.shunfengbj.cn/) &#12289;&#33521;&#35821;&#22235;&#20845;&#32423;&#12289;&#23398;&#24037;&#23398;&#20301;[**?k?C**](http://www.shunfengbj.cn/) &#12289;&#20250;&#35745;&#24072;&#12289;&#20250;&#35745;[**?k?C**](http://www.shunfengbj.cn/) &#12289;&#25104;&#20154;&#33258;&#23398;&#33829;&#36816;&#35777;&#12289;&#23381;&#26816;&#35777;&#12289;&#36523;&#20221;&#35777;&#12289;&#20581;&#24247;[**?k?C**](http://www.shunfengbj.cn/)  &#12289;&#25151;&#22320;&#20135;&#26435;&#35777;&#30340;&#23553;&#38754;&#21360;&#21047;&#21672;&#35810;&#26381;&#21153;&#8230;&#8230;

---

