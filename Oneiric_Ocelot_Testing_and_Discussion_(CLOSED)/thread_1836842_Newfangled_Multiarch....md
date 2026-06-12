---
title: "Newfangled Multiarch..."
date: 2011-08-31
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Kazade on 2011-08-31
Hi guys,

I've just upgraded to 11.10 and one of the first apps I install is Gens/GS which is a 32bit-only app. In previous versions of Ubuntu I could install ia32-libs and --force-architecture the package, but in Oneiric I get the following:

 gens:i386 : Depends: xdg-utils:i386 but it is not installable

Any ideas how I can get this package installed? I already have the amd64 version... is this a bug?

---

### Post by pressureman on 2011-08-31
```

echo foreign-architecture i386 | sudo tee /etc/dpkg/dpkg.cfg.d/multiarch
sudo apt-get update
sudo apt-get install xdg-utils:i386

```

---

### Post by Kazade on 2011-09-04
I already had i386 enabled as a foreign architecture, still get this:
```

Package xdg-utils:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'xdg-utils:i386' has no installation candidate
```

Any other ideas?

---

### Post by pressureman on 2011-09-04
xdg-utils is not an arch-specific package. Get rid of the ":i386" after the package name. Beyond that, I'm out of ideas...

---

