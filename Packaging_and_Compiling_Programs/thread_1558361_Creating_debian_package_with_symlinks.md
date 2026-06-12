---
title: "Creating debian package with symlinks"
date: 2010-08-22
forum: Packaging and Compiling Programs
---

### Post by alecive on 2010-08-22
Hi!

I'm a noob with debian packaging, and I'm not english, so sorry for my english and sorry if I write fool things. :)

I've created an iconset ([http://alecive.deviantart.com/art/AwOken-Awesome-Token-1-0-163570862](http://alecive.deviantart.com/art/AwOken-Awesome-Token-1-0-163570862)) and, since it's becoming more and more appreciated, I thinked to create a ppa for it.

So, I contacted someone that helps me explaining what to do to mantain a ppa. With a lot of time spent explaining me those things, I created my own ppa.

The ppa is here -> [https://launchpad.net/~alecive/+archive/antigone]("https://launchpad.net/%7Ealecive/+archive/antigone")

The iconset is correctly uploaded and builded, and it works. The problem is that the .deb package eliminates all symbolic links in the set!
In my iconset I use a lot of symlinks (to be clear, those that came out from the command "ln -fs"), so, if I change an icon change also all icons related to it, and meanwhile the iconpack remains little in dimensions.

A part from the fact that the deb package, without symlinks, became bigger (30MB instead of 12MB), the problem is that my iconset has a customization script that allows you to change a lot of things (from folder types to distributor-logo icons), but this customization script rely on the fact that the iconset has symlinks!

So my question is: how must I do to create a .deb package with symlinks???

Thanks in advance for any response

PS: I've also checked the ppa for another iconset, Faenza iconset ([https://launchpad.net/~tiheum/+archive/equinox]("https://launchpad.net/%7Etiheum/+archive/equinox")), and in that deb package there are symlinks, so it's possible do that!

---

### Post by sq7bti on 2010-08-22
check out the pre- and postinst functionality in [FAQ]("http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html")

s.

---

### Post by RainCT on 2010-08-22
You don't need `postinst' at all for symlinks. They can be included in the package just like normal files.

The details depend on the way you're doing the packaging, but using something like the following in debian/rules's `install' target should work:

```
ln -s /usr/share/whatever/file/you/want $(CURDIR)/debian/<pkgname>/usr/whatever/place/you/want/the/link
```

Everything inside debian/<pkgname> will end up inside the .deb, including the symlinks you put there.

---

