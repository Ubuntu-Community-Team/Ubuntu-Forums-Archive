---
title: "First time indicator applet - help needed"
date: 2011-04-05
forum: Programming Talk
---

### Post by mikeym on 2011-04-05
Hi,

I'm just trying to get started on an indicator applet and I found an [article and example in the Gnome Journal](http://gnomejournal.org/article/67/an-introduction-to-the-message-indicator). I'm just trying to compile it but am getting a bit stuck (a new to C). 

Here's what I'm getting when I compile:

```

$ gcc indicator.c -o indicator $(pkg-config glib-2.0 indicate  --libs --cflags)
indicator.c:4:43: error: libindicate/indicator-message.h: No such file or directory
indicator.c: In function ‘main’:
indicator.c:38: error: ‘IndicateIndicatorMessage’ undeclared (first use in this function)
indicator.c:38: error: (Each undeclared identifier is reported only once
indicator.c:38: error: for each function it appears in.)
indicator.c:38: error: ‘indicator’ undeclared (first use in this function)

```

I've installed *libglib2.0-dev* and *libindicate-dev*. 

I'm assuming either the code has changed from the example or I'm missing some of the required header packages.

I've attached the code if anyone's interested.

---

### Post by johnl on 2011-04-05
Yup, it looks like the code you have is written using an older version of the library.  Check out the examples in the libindicator source tree either [here](http://bazaar.launchpad.net/~indicator-applet-developers/libindicate/trunk/files/head:/examples/) or via

```

apt-get source libindicator

```

hope this helps!

---

### Post by mikeym on 2011-04-06
Thanks Johnl. You're a genius. Still can't compile the new example but getting closer.

---

### Post by SledgeHammer_999 on 2011-04-06
Most probably pkg-config doesn't know a package named 'indicate'

What does this output(on the left column)?
```
pkg-config --list-all | grep indicate
```

If it outputs only one result then use it instead of 'indicate' in your compilation command. If it is more please post the results or try them one by one.

---

