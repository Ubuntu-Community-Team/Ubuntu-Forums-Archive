---
title: "perl locale problems"
date: 2005-01-17
forum: Programming Talk
---

### Post by ow50 on 2005-01-17
I have problems with using my locale in perl. I have all my locale environment variables set to "fi_FI.UTF-8" (finnish).

I use the following script to test perl locale handling:
```
#!/usr/bin/perl

print "\nno locale:\n";
print +(sort grep /\w/, map { chr } 0..255), "\n";

use locale;
print "\nusing locale:\n";
print +(sort grep /\w/, map { chr } 0..255), "\n";
```

And the output looks like:
```
no locale:
0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ_abcdefghijklmnopqrstuvwxyz

using locale:
_aAbBcCdDeEfFgGhHiIjJkKlLmMnNoOpPqQrRsStTuUvVwWxXyYzZ0123456789
```

The order of the characters is a bit different, so "use locale" obviously does something, but it does not include letters åÅäÄöÖ, which are in the finnish alphabets. Out of curiousity I tried the same thing with locales "de_DE.UTF-8" (german) and "sv_SV.UTF-8" (swedish) and got the exact same output.

Any help would be much apprechiated.

---

