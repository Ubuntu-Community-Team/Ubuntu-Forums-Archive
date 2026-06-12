---
title: "ln: target `kernel+/source' is not a directory kernel compiling with make=0 error"
date: 2010-09-10
forum: Programming Talk
---

### Post by jamesbon on 2010-09-10
I cloned the 2.6 latest  kernel tree on my system and in my home
directory made a folder named btc
git clone git://[URL="http://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux-2.6.gitlinux-2.6"]git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux-2.6.git
linux-2.6[/URL]
then compiled as
yes '  ' | make 0=$HOME/abcd/ oldconfig

worked well.
Then
make 0=$HOME/abcd

this also worked but when I did

sudo make 0=$HOME/abcd modules_install
```

ln: target `kernel+/source' is not a directory
make: *** [_modinst_] Error 1

```As far as I understand when I used make =/path/to/some/directory this I used correctly on above.

Also there was not a single file in $HOME/abcd 
when make was invoked as make 0=$HOME/abcd

---

