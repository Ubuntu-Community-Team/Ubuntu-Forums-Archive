---
title: "Git Version Numbers in Ubuntu Packages"
date: 2010-01-24
forum: Packaging and Compiling Programs
---

### Post by knipknap on 2010-01-24
Projects using Git have version numbers such as this:

  ```
0.1.0-9-gfcf38f7
```

When trying to use these in a Ubuntu package, the following error is produced:

  ```
native-package-with-dash-version
```

How are these supposed to be translated without losing the information contained in the version number? This is ambiguous:

  ```
0.1.0-9
```

---

### Post by Yellow Pasque on 2010-01-25
Example: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by knipknap on 2010-01-28
Thanks, replacing "-" by "+" works.

---

