---
title: "Using Squid or Apache as an apt repo cache?"
date: 2006-04-04
forum: Repositories &amp; Backports
---

### Post by daledude on 2006-04-04
Sorry if wrong forum...

Does anyone know of a How-to (or other) that shows a configuration for squid or apache to be an apt respository cache? I currently use apt-proxy and it works well, but I want to combine caching of other distro repositories into one setup. Squid seems ideal but a bit overwhelming.

Thanks for any hints.

---

### Post by fdoving on 2006-04-17
Squid is nice.

I use this in my squid.conf to keep .deb's in the cache.
```

refresh_pattern -i *.deb$ 129600 100% 129600

```


- Frode

---

### Post by LordMerlin on 2006-04-18
[quote=fdoving]Squid is nice.

I use this in my squid.conf to keep .deb's in the cache.
```

refresh_pattern -i *.deb$ 129600 100% 129600

``` 


Can this be used with other file types as well? Let's say .rpm / tar.gz / .tar / .tar.bz2 / etc?

---

### Post by fdoving on 2006-04-18
Sure.
```

refresh_pattern -i *.deb$ 129600 100% 129600
refresh_pattern -i *.rpm$ 129600 100% 129600
refresh_pattern -i *.tgz$ 129600 100% 129600
refresh_pattern -i *.exe$ 129600 100% 129600
refresh_pattern -i *.cab$ 129600 100% 129600

```
and so on.. 


- Frode

---

