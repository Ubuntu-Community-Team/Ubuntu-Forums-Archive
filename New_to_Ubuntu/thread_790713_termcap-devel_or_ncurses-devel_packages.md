---
title: "termcap-devel or ncurses-devel packages"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Third Note on 2008-05-11
Hello!

I have installed ssh client. Everything is fine, but the only one busily message fires up every time I login: "Need basic cursor movement capability, using vt100". I have found the solution (at the [http://gd.tuwien.ac.at/utils/shells/ssh/README.SSH2](http://gd.tuwien.ac.at/utils/shells/ssh/README.SSH2) page). There is phrase: "If you have a Linux system, then that is probably because you don't have either termcap-devel or ncurses-devel packages installed." But I can't find this packages. And I have no idea where are they could be. apt-cache search command does not help me, maybe you can help? :)

Thank you.

---

### Post by jrib on 2008-05-12
libncurses5-dev but installing this will do nothing as you would need to recompile.  I don't receive that error though, so not sure where it is coming from

---

### Post by Third Note on 2008-05-12
Thank you, _jason. It works great.

First I've installed libncurses5-dev package without ssh recompile, it's not helped. But then I've recompiled shh with libncurses5-dev already installed, as you said, and now it works. (Recompile is the key in this case.)

Thaks again.

---

