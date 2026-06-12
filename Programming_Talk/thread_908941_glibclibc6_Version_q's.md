---
title: "glibc/libc6 Version q's"
date: 2008-09-03
forum: Programming Talk
---

### Post by mr_skater99 on 2008-09-03
Hi guys,

I am trying to get set up to cross compile for different arch's (trying to get set up to work on jlime - wwww.jlime.com).

I have managed to install an older version of gcc via apt-get and change the symlink for gcc to point to this older version which works well.

Is there a way I can do something similar for libc6?

i.e. install an older version via apt-get and then change a symlink somewhere so that it is the version used?

Are there any ramifications for day to day use?  i realise when i compile/build things it will matter - but what about just using the system normally?

Thanks,

Scotty

---

### Post by joe_bruin on 2008-09-03
If you'll look in your /lib directory, you'll probably see that there's a libc.so.6 which is a symlink to a particular version (libc-2.7.so in my case).  Most applications will access libc through the symlink since they don't care about the version.  It is safe to have others installed in there as long as you don't screw around with the symlink that your system relies on.

However, that's probably not the approach you want to take.  If you're cross compiling, you probably want to avoid mixing non-current and different architecture stuff into your system directories*.  You should really be doing this in a separate user area.  Create $HOME/local/$SOMEARCH/ and make bin, lib, usr/include and other system directories in it.  They build your cross compiling tools to prefix that directory so that they will look for headers, libraries, and such in there.  You may need to set some environment variables too so that the tools look for things they need in those directories by default.

*unless you're mixing AMD64 and x86, which is a weird case.

---

### Post by mr_skater99 on 2008-09-03
Thanks for the advice Joe.  Seems very logical.  

I'm on a x86 compiling for ARM.  I

I'll have a try at setting up a separate user area for the arm stuff and pointing everything there.  

What is the apt command to see all the available versions of something (like libc6) in the repos?

Any other suggestions?

Thanks again.

---

