---
title: "Escape characters and arrow keys in perl"
date: 2011-11-11
forum: Programming Talk
---

### Post by 7cardcha on 2011-11-11
How do I stop nasty escape characters from being printed? And how do I detect when arrow keys have been hit?

---

### Post by hailholyghost on 2011-11-12
Hey,

> How do I stop nasty escape characters from being printed?

What kind of script are you using?  This doesn't print escape characters:

```
#!/usr/bin/perl -w

print "Hello world\n";
```

Pretty easy.

I'm not sure what you mean by detecting arrow keys being hit.

---

