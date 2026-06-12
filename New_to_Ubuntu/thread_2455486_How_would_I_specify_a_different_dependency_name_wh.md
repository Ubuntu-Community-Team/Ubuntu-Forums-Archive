---
title: "How would I specify a different dependency name when compiling?"
date: 2020-12-20
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-12-20
Hello all,

I'm trying to compile VBA-M, a game boy advanced emulator, but one of the dependencies in the install script has had it's name changed in the Ubuntu 20.04 repositories. libwxgtk3.0-dev is now libwxgtk3.0-gtk3-dev. How should I solve this? should I just create a symlink of the name that the program expects to find and link it to the actual library? or is there a more elegant solution?

Sorry if that's a bit vague, if there is any more specific information needed I can find out but right now all I can say is that it is built with cmake

Thanks!

---

### Post by CatKiller on 2020-12-20
There's a PPA and a snap.

The devs appear to have already considered the part you're worried about. The script that installs dependencies has this:

```
        # in newer distros
        wx_lib=$(apt-cache search 'libwxgtk3.0-gtk3(-[^[:space:]]+)?$' | grep -v -- -dev | sed 's/ - .*//')
        wx_lib_dev=$(apt-cache search 'libwxgtk3.0-gtk3-dev(-[^[:space:]]+)?$' | sed 's/ - .*//')
```

If I were to hazard a guess, I think the problem is that the dev hasn't updated their stuff for focal.

---

### Post by jcdenton1995 on 2020-12-21
> **CatKiller said:**
> There's a PPA and a snap.

The devs appear to have already considered the part you're worried about. The script that installs dependencies has this:

```
        # in newer distros
        wx_lib=$(apt-cache search 'libwxgtk3.0-gtk3(-[^[:space:]]+)?$' | grep -v -- -dev | sed 's/ - .*//')
        wx_lib_dev=$(apt-cache search 'libwxgtk3.0-gtk3-dev(-[^[:space:]]+)?$' | sed 's/ - .*//')
```

If I were to hazard a guess, I think the problem is that the dev hasn't updated their stuff for focal.

wow, that was a good spot! In the end I tried downloading and compiling it again and the second time it worked! A bit annoying as I didn't do anything different apart from downloading the .zip as opposed to the .tar.gz file, maybe the latter is broken in some way? Thanks for taking a look at it for me.

---

