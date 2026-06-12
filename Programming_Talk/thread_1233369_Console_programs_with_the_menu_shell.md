---
title: "Console programs with the menu shell"
date: 2009-08-06
forum: Programming Talk
---

### Post by CryptiniteDemon on 2009-08-06
So how do you make console menus?  Like the type we get with Slackware's installation, or ubuntu server, or partimage?

---

### Post by qamelian on 2009-08-06
> **CryptiniteDemon said:**
> So how do you make console menus?  Like the type we get with Slackware's installation, or ubuntu server, or partimage?
I believe that is done by using the ncurses API. A quick search on Google finds plenty of info on this.
[http://www.google.ca/search?q=ncurses&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=ncurses&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by unutbu on 2009-08-06
Not that I know anything about ncurses or newt (LOL), but it appears partimage uses libnewt (rather than ncurses):
```

apt-cache show partimage
```
```
Depends: libbz2-1.0, libc6 (>= 2.7-1), libgcc1 (>= 1:4.1.1-21), **libnewt0.52**, libpam0g (>= 0.99.7.1), libslang2 (>= 2.0.7-1), libssl0.9.8 (>= 0.9.8f-1), libstdc++6 (>= 4.1.1-21), zlib1g (>= 1:1.2.3.3.dfsg-1)

```

CryptiniteDemon, if you are planning on writing shell scripts, you might be interested in checking out whiptail:
```

apt-cache show whiptail
```

```
Depends: libc6 (>= 2.4), **libnewt0.52** (>= 0.52.2), libpopt0 (>= 1.14), libslang2 (>= 2.0.7-1)
...
Description: Displays user-friendly dialog boxes from shell scripts
 Whiptail is a "dialog" replacement using newt instead of ncurses. It
 provides a method of displaying several different types of dialog boxes
 from shell scripts. This allows a developer of a script to interact with
 the user in a much friendlier manner.

```

---

### Post by nvteighen on 2009-08-07
I've read a bit of the newt API and it seems really good for cases in which you need a widget-based library for terminal manipulation. ncurses does this in a lower-level fashion (but still higher-level that brute termios hacking).

ncurses is really a nightmere. It has to follow with a very old standard (XSI Curses standard) and that makes it adopt some API techniques that nowadays are really weird. For example, the whole "hidden machinery" based on global variables which makes it very confusing at times. Heck, even in Python it's a nightmere to use.

But I fear ncurses is still the most used library for this stuff, mainly because of being older and therefore, more tested.

---

