---
title: "previously installed software package archives location in xubuntu?"
date: 2012-06-29
forum: New to Ubuntu
---

### Post by goodbye-windows(tm) on 2012-06-29
I need to make some space on my harddrive, after trying to figure out why it won't run, I finally realized the harddrive was full.

I remember there was a directory where previously installed software packages were archived, but I can't remember where it was. The old installation packages can safely be deleted I think.

What is the path to the previously installed software installation files? 

All I can remember is that it had a directory called 'var' in the path.

I'm running xubuntu.

TY.

Art

---

### Post by MG&amp;TL on 2012-06-29
[I]/var/cache/apt/archives/

[/I]...is what you're after.

```
sudo apt-get clean
sudo apt-get autoremove
```

should also help.

---

