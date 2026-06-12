---
title: "[SOLVED] 'patch' recursively???"
date: 2007-11-19
forum: Programming Talk
---

### Post by altonbr on 2007-11-19
If I run:
```
diff -ur ./system ./system_new > kohana.diff
```

and then:
```
patch ./system/* kohana.diff
```

It returns the error:
> patch: system/helpers: extra operand
patch: Try `patch --help' for more information.

I can run diff recursively, how come patch can't? How do I apply a recursive diff with patch!? `patch --help` and `man patch` doesn't tell me :S

---

### Post by engla on 2007-11-19
normally you don't specify any files on patch's command line:

```
patch < kohana.diff
```

Should be enough. If the filenames don't match with the "slash level", use the appropriate -p0, -p1 etc option. (Also check in the man page)

---

### Post by altonbr on 2007-11-19
Hey great!

This worked perfectly!
```
patch -p1 < kohana.diff
```

Thank you! I never thought of loading the diff file INTO patch. Again, I appreciate the help. :)

---

