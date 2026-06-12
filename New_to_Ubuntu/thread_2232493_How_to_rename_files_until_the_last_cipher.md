---
title: "How to rename files until the last cipher?"
date: 2014-07-02
forum: New to Ubuntu
---

### Post by goblinslayer3 on 2014-07-02
What's the command to rename a file, retaining only the name until the last cipher?
For example:

AR002_something -> **AR002**
AD221something -> **AD221**

---

### Post by steeldriver on 2014-07-02
If you mean remove **any trailing sequence of non-digits**, you could maybe use

```

rename -vn 's/\D+$//' *

```

The '-n' option indicates a dry-run so you can test it before committing - bear in mind that if you have any filenames in the directory that *don't* contain any digits, it will try to rename them to nothing.

---

### Post by goblinslayer3 on 2014-07-02
Thanks! 
Yes, this is what i wanted. 

Btw, do you know any way to locate the files that ended with a non-digit before the conversion? 
Because renaming there where few images that had a number at the very end (AR201something2). I could search for them manually but i would prefer something automatic.

---

### Post by Lars Noodén on 2014-07-02
[find](http://manpages.ubuntu.com/manpages/trusty/en/man1/find.1.html) has some limited regular expression capability.  It's not pcre so you'll have to fiddle a bit to get the right combination.  

```

find . -regex '^.*[^0-9][^0-9]*$' -print

```

---

