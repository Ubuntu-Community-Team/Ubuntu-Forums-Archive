---
title: "what does sudo apt-get -f install do?"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by mferarri on 2012-04-21
what does sudo apt-get -f install do?

---

### Post by d3v1150m471c on 2012-04-21
```

man apt-get

```

---

### Post by iponeverything on 2012-04-21
in theory it's supposed to fix borked dependencies.

---

### Post by williejones on 2012-04-21
From the man page:

> **-f**, **--fix-broken**Fix. Attempt to correct a system with broken dependencies in  place. This option, when used with install/remove, can omit any packages  to permit APT to deduce a likely solution. Any **package**(s) that are specified must completely correct the problem. This option is sometimes necessary when running APT for the first time; APT itself does not allow  broken package dependencies to exist on a system. It is possible that a  system's dependency structure can be so corrupt as to require manual intervention. Use of this option together with **-m** may produce an error in some situations.

---

### Post by mferarri on 2012-04-22
thanks to everyone who replied. i'm not being lazy. i just didn't realize that i was supposed to search the manual for "apt-get". very useful command btw. have a great day everyone!:popcorn:

---

