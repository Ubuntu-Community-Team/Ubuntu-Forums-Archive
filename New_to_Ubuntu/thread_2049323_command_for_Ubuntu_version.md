---
title: "command for Ubuntu version"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by chemjeff on 2012-08-28
Is there a command that will tell me what version of Ubuntu I am running (10.04, 11.10, etc.)?

---

### Post by CharlesA on 2012-08-28
```
lsb_release -r
```

---

### Post by chemjeff on 2012-08-28
Thanks!  Say, is there a "master FAQ" that has these types of commands listed in them?  There seem to be an awful lot of commands.

---

### Post by taras.kuzyo on 2012-08-28
> **chemjeff said:**
> Thanks!  Say, is there a "master FAQ" that has these types of commands listed in them?  There seem to be an awful lot of commands.

[http://cb.vu/unixtoolbox.pdf](http://cb.vu/unixtoolbox.pdf)

---

### Post by SlugSlug on 2012-08-28
also

```
cat /etc/issue
```

```
uname -a
```

---

### Post by MG&amp;TL on 2012-08-28
> **chemjeff said:**
> Thanks!  Say, is there a "master FAQ" that has these types of commands listed in them?  There seem to be an awful lot of commands.

Yeah, you're running a GUI on something that's meant to be run from a command line. :)

There's a lot of commands, but only a few are everyday or useful for most people. [https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

