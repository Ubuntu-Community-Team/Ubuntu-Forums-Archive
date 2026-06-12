---
title: "how to make a custom entry in Synaptic for my application?"
date: 2011-10-20
forum: Packaging and Compiling Programs
---

### Post by limescout on 2011-10-20
Hello,
I'm wondering how to get my built-from-source app (mame64) into synaptic so I can manage it's uninstall from there when the need arises.  I've done a little googling but didn't come up with anything.

---

### Post by Slim Odds on 2011-10-20
> **limescout said:**
> Hello,
I'm wondering how to get my built-from-source app (mame64) into synaptic so I can manage it's uninstall from there when the need arises.  I've done a little googling but didn't come up with anything.

Synaptic works from a list of repositories. If you create your own, you can include it. It does not have to be Internet accessible, it can be local.

You can also just create .deb packages and install them with dpkg (which is what underlies Synaptic, apt-get, aptitude).

---

### Post by lovinglinux on 2011-10-20
Use *checkinstall* instead of *make install*. It will generate a deb before installing, that will be browsable through Synaptic.

---

### Post by Slim Odds on 2011-10-21
> **lovinglinux said:**
> Use *checkinstall* instead of *make install*. It will generate a deb before installing, that will be browsable through Synaptic.

Excellent point, checkinstall is awesome!

---

### Post by limescout on 2011-10-23
checkinstall isn't working because there's no install configuration that comes with the makefile.  Here's what checkinstall is returning:

```
========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

I was looking at [http://man.he.net/man1/dpkg-buildpackage](http://man.he.net/man1/dpkg-buildpackage) for this purpose.  I can't manage to find out how to make a .deb without remaking the binary.  would the -S option acomplish this?  I'm a little lost in this process.

---

