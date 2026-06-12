---
title: "Gcc3"
date: 2007-03-31
forum: Programming Talk
---

### Post by Warpnow on 2007-03-31
Okay, I want to downgrade to gcc3 because my code won't compile well in gcc4 and I don't have the time at present to debug all of the code.

I did

sudo apt-get install gcc-3.3 

It downlaod it. I edited gcc to gcc-3.3 in my makefile, but when it compiles it still spits out the errors that gcc4 does but gcc3 never did when it was the newest compiler. Is there something else I need to do to downgrade the gcc?

---

### Post by g8m on 2007-04-01
I think it works through /etc/alternatives.

try update-alternatives --list gcc to see if gcc is set up as an alternative. 

You can always do it yourself ofcourse,  /usr/bin/gcc is a soft link. ls -l /usr/bin/gcc will tell you to which version it points.

You can always remove this link en recreate it sudo ln -s /usr/bin/gcc-3* /usr/bin/gcc, so it points to the gcc you want to use.

Hope this helps.

---

