---
title: "Compiled Awesome WM won't start"
date: 2013-06-12
forum: Packaging and Compiling Programs
---

### Post by Ranko Kohime on 2013-06-12
After compiling Awesome 3.5.1, which completed successfully, I ran startx, and it ran for a few seconds, and then quit, with the following error:

```
/home/ranko/.config/awesome/rc.lua:50: attempt to index global 'beautiful' (a nil value)
E: awesome: main:524: couldn't find any rc file
```

After which, the Xserver shuts down normally.  If I comment out the reference to beautiful, it just stops on the next plugin, such as awful, with a similar message (a nil value)

I was under the impression that beautiful and awful were a part of the main tarball, is that not the case, or am I seeing some other issue here?

(Compiling really isn't my thing, but unfortunately Raring's version of Awesome is <3.5, and I want to use a few features only available after that release)

---

### Post by Toz on 2013-06-12
Are using the same config file from a 3.4x install? If so, you need to make some changes to it. See [http://awesome.naquadah.org/wiki/Awesome_3.4_to_git_master]("http://awesome.naquadah.org/wiki/Awesome_3.4_to_git_master").

Specifically, look for something like:
```
require("beautiful")
```
...and change it to:
```
beautiful = require("beautiful")
```

There are other changes to consider as well that are listed in that link above.

---

