---
title: "How to run two versions of Firefox together?"
date: 2011-11-20
forum: Packaging and Compiling Programs
---

### Post by kvvv on 2011-11-20
Hi,

I wanted to compile the nightly branch of firefox in debug mode. But, after compiling and starting the executable with the absolute path, it still launched pre-installed version of firefox. The only way I could get around this was by uninstalling the previous version.

How do I run both the nightly and the stable branches of firefox?

---

### Post by San_SS! on 2011-11-20
Have you tried running it with the --no-remote option?

```
/path/to/firefox/firefox --no-remote
```

---

### Post by kvvv on 2011-11-20
Sweet that did it! Thanks.

---

