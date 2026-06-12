---
title: "Signing packages"
date: 2006-01-02
forum: Repositories &amp; Backports
---

### Post by nocturn on 2006-01-02
How does one sign packages (the way that the ones from Ubuntu are signed)?

I want to set up a custom repo with my own packages, but I would like to sign them (I have a seperate key for that).

---

### Post by nocturn on 2006-01-02
Is it correct that I should only sign Release (detach, armour) on my repo?

---

### Post by az on 2006-01-02
Well, AFAIK, all of the debian packaging scripts will sign the package you build if you have a key available.  This will happen even if you just download the source for a package and build it on your own machine.  Offhand, I do not know how to specify one particular key out of several.  I am sure it is well documented in the debian helper scripts packages.

So, no, you do not only have to sign the relase file.

---

### Post by nocturn on 2006-01-02
[QUOTE=azz]Well, AFAIK, all of the debian packaging scripts will sign the package you build if you have a key available.  This will happen even if you just download the source for a package and build it on your own machine.  Offhand, I do not know how to specify one particular key out of several.  I am sure it is well documented in the debian helper scripts packages.

So, no, you do not only have to sign the relase file.[/QUOTE]

The thing is that I'm creating custom packages, mainly for themes and meta packages.

I use dpkg-deb --build debian to build

---

### Post by nocturn on 2006-01-02
Hm, so far, it seems that signing Release to Release.gpg shows no 'NOT AUTHENTICATED' errors...

good

---

