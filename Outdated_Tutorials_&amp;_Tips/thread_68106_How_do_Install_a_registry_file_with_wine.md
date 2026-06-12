---
title: "How do Install a registry file with wine?"
date: 2005-09-22
forum: Outdated Tutorials &amp; Tips
---

### Post by xmastree on 2005-09-22
I'm running a windows program with wine. It's shareware, I've registered it, and I have the .key file.
How do I get the details into the registry?

I've tried wine regedit filename.key but...
```
wine regedit <filename>.key
Invoking /usr/lib/wine/wine.bin regedit <filename>.key ...
wine: cannot find 'regedit'
Wine failed with return code 1

``` :confused:

---

### Post by Bruce Westfall on 2006-01-30
I can't get it to import .reg files yet, but just typing "wine regedit.exe" worked for me.

If it doesn't, perhaps you should have it use the Windows regedit program.

In your home directory under .wine is a config file.

Open that, then remove the semicolon in front of the line that reads-
;"C:\\windows\\regedit.exe" = "native, builtin"
 - line 120 in my file.

That should force wine to use the native windows exe.

-not much help, but I'm learning...

---

