---
title: "pkg-config - adding new package?"
date: 2007-01-02
forum: Programming Talk
---

### Post by Ben Sprinkle on 2007-01-02
```

/home/user/Desktop# g++-4.1 a.cc `pkg-config gtkmm-2.4 --cflags --libs` Package gtkmm-2.4 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkmm-2.4.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkmm-2.4' found

```
I installed gtkmm, how do I add it to the pkg-config list?

---

### Post by llonesmiz on 2007-01-03
You need to install the -dev package. gtkmm*-dev.

---

### Post by Ben Sprinkle on 2007-01-03
Thanks, I just figured that out last night lol.

---

