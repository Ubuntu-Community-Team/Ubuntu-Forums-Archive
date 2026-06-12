---
title: "Perl: sysopen() not working!"
date: 2009-03-30
forum: Programming Talk
---

### Post by computer_freak_8 on 2009-03-30
I think all I need is a quick syntax example and I'll be set.

Here's what I've got now:
```
sysopen(WL, $filepath1, O_RDRW) or die "$filepath cannot be opened.";
```
And it gives the error:
```
Argument "O_RDRW" isn't numeric in sysopen at ./perl-fix.pl line 7.
```

I've looked [here]("http://perldoc.perl.org/perlopentut.html"), as well as a few other places, but I can't seem to get it figured out. Any ideas?

---

### Post by ghostdog74 on 2009-03-30
see how they open files here:
```

perldoc perlopentut

```

---

### Post by computer_freak_8 on 2009-03-30
> **ghostdog74 said:**
> see how they open files here:
```

perldoc perlopentut

```
Yes, that's what I linked to. Any ideas on what's wrong with my code? If I understood that site correctly, my code should work...

---

### Post by unutbu on 2009-03-30
According to [http://perldoc.perl.org/functions/sysopen.html](http://perldoc.perl.org/functions/sysopen.html)
there is a mode called O_RDWR for opening the file in read-write mode. (Note that it is RDWR, not RDRW).

---

### Post by ghostdog74 on 2009-03-30
> **computer_freak_8 said:**
> Yes, that's what I linked to. Any ideas on what's wrong with my code? If I understood that site correctly, my code should work...

just use open(), its simpler.
```

open(FH, "+< $path");

```
also, as unutbu mentioned, spell them correctly.

---

### Post by computer_freak_8 on 2009-03-31
> **unutbu said:**
> (Note that it is RDWR, not RDRW).
Ah, whoops! I see now. Well, I changed it and:
```
Argument "O_RDWR" isn't numeric in sysopen at ./perl-fix.pl line 7.
```

@ghostdog74:

Thanks, that worked!

---

