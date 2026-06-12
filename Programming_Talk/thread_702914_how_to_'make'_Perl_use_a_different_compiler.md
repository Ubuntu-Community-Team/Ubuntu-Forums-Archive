---
title: "how to 'make' Perl use a different compiler"
date: 2008-02-20
forum: Programming Talk
---

### Post by DouglasAWh on 2008-02-20
Ok, I am very much new to Perl and compiling things, but it seems that the issues presented at [http://ubuntuforums.org/showthread.php?t=693865](http://ubuntuforums.org/showthread.php?t=693865) might be related to the perl scripts trying to use 'make,' while it needs to use nmake (or maybe dmake).  I have Visual C++ installed, which is supposed to be able to compile stuff, but maybe Perl doesn't know how to access that.  So, if I need to go in and modify something, what is it that I need to go in and modify?

Thanks!

---

### Post by ghostdog74 on 2008-02-20
I have never ever needed a Visual C++ compiler on my windows machines to install Activestate Perl. Its just double click and install that's it. Sorry there, can't help much.

---

### Post by DouglasAWh on 2008-02-20
> **ghostdog74 said:**
> I have never ever needed a Visual C++ compiler on my windows machines to install Activestate Perl. Its just double click and install that's it. Sorry there, can't help much.

I've confused you.  When I try to install modules using CPAN is when the 'make' command is used.  The ActiveState MSI installs fine and I can get to the CPAN shell, but all sorts of issues happen when I try to install the MSDE module, as documented in the other thread.  Hope that makes more sense now.  The installation through CPAN calls some files and I'm thinking maybe I have to download one of those files and modify it and then run it, but I don't know what file or how to modify it.  I can copy the DOS logs into this thread by they are already at [http://ubuntuforums.org/showthread.php?t=693865](http://ubuntuforums.org/showthread.php?t=693865) so I don't see much point.

Thanks for trying!

---

### Post by ghostdog74 on 2008-02-20
> **DouglasAWh said:**
> I've confused you.  When I try to install modules using CPAN is when the 'make' command is used.  The ActiveState MSI installs fine and I can get to the CPAN shell, but all sorts of issues happen when I try to install the MSDE module, as documented in the other thread.  
When you use ActiveState, use the[ PPM packages.]("http://aspn.activestate.com/ASPN/Downloads/ActivePerl/PPM/Zips").

---

