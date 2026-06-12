---
title: "/bin/bash: ./perl_script.pl: usr/bin/perl: bad interpreter: No such file or directory"
date: 2014-08-20
forum: Programming Talk
---

### Post by NerdcoreSteve on 2014-08-20
I wrote a perl script in ubuntu, in vim.

I put this at the top:
```
#!usr/bin/perl
```
(I also tried a -W but the result is the same)

The script works find if I run the script using perl.

When I run it with ./ I get this error:

```
/bin/bash: ./perl_script.pl: usr/bin/perl: bad interpreter: No such file or directory
```

Just to emphasize, I did not write this in windows. This script has never seen windows.

---

### Post by steeldriver on 2014-08-20
Try

```

#![COLOR=#0000ff]**/**[/COLOR]usr/bin/perl

```

---

### Post by NerdcoreSteve on 2014-08-26
That did it. Thanks. :)

---

