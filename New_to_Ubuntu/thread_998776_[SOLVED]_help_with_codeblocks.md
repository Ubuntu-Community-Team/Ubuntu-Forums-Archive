---
title: "[SOLVED] help with codeblocks"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by itsols on 2008-12-01
I'm as good as new-born on ubuntu and everything like it. I got some help and installed code blocks. when I tried to build, I got this error:

error: wx/app.h: No such file or directory

I have no idea how to fix this (on ubuntu) as I've made a switch from Windows. ANY HELP IS HIGHLY VALUED.

Many thanks.

---

### Post by ByteJuggler on 2008-12-01
OK I'm not near my ubuntu machine and haven't tried CodeBlocks, but the error suggests you're missing some WX libraries and include files.  Perhaps you should install the (guessing) libwxgtk package and libwxgtk-dev package?

---

### Post by ByteJuggler on 2008-12-01
Might also look at this: [https://help.ubuntu.com/community/AutoApt](https://help.ubuntu.com/community/AutoApt)

---

### Post by itsols on 2008-12-05
Many thanks to all those who tried helping out, and to ByteJuggler, in particular who said:

> **ByteJuggler said:**
> ...the error suggests you're missing some WX libraries and include files.  Perhaps you should install the (guessing) libwxgtk package and libwxgtk-dev package?

I was able to trace the issue. This was the cause:

The new Code::Blocks that I installed was looking for wsgtk libraries with version 2.8.9 and my OS (version 7.10 or Gutsy) had its sources pointing to older versions. So I had installed the new  wxgtk and I had omitted the -dev package. The moment I updated (or should I say upgraded) my sources and packages, everything just fell in line.

Hope other new-comers to Ubuntu will figure this out as well.

Many thanks again.

---

### Post by itsols on 2008-12-05
For the benefit of the other newbies (like me), here's where you have full, stet-by-step instructions on how to install the new wx libraries on Gutsy. And at this moment, The libraries for wx are available as on version 2.8.9.

The link:

[http://wiki.wxpython.org/InstallingOnUbuntuOrDebian](http://wiki.wxpython.org/InstallingOnUbuntuOrDebian)

Just follow the steps outlined and check it out with Synaptic. It should work just fine. Soon after the installation (I mean update), I did a check on Code::Blocks and it was fantastic. No mo "wx/app" missing errors :)

Happy coding!

---

