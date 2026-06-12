---
title: "Ghost install of valac nightly build?"
date: 2011-02-19
forum: Packaging and Compiling Programs
---

### Post by FlyingIsFun1217 on 2011-02-19
Hey,

I have recently compiled the valac compiler from a daily git pull, and everything worked fine (building it anyway). When I went to do the 'sudo make install', everything went through it's normal paces as if it had no problems, but when I run the command 'valac' or 'vala', I receive the error that it's not installed, and that I should install from the ubuntu repositories (which I do not want to do, as it is an older version).

Has anyone had this problem before? I can't seem to find anyone else who has encountered this error. It's as if it just installed ghost files or something.

Thanks!
FlyingIsFun1217

---

### Post by MadCow108 on 2011-02-19
make install usually installs into /usr/local by default
if /usr/local/bin is not in your $PATH variable the executable will not be found if you just type in the name (without the full path)

either put the path into PATH (export PATH=$PATH:/path/to/exec) or change the installation directory to /usr (mostly over ./configure --prefix=/usr)

---

### Post by FlyingIsFun1217 on 2011-02-19
I guess using the configure prefix is what needed to be done, took care of the problem!

Thanks for the help, would have gone crazy thinking I'd already done that.

FlyingIsFun1217

---

