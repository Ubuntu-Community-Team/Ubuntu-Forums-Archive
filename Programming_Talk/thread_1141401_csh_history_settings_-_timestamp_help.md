---
title: "csh history settings - timestamp help"
date: 2009-04-28
forum: Programming Talk
---

### Post by akvino on 2009-04-28
Hello all!

I am not sure if anyone knows of the csh variable compatable to HISTTIMEFORMAT which will add date to time displayed in .history file.

This is currently in my .cshrc file:
set history=500             # previous commands to remember.
set savehist=500


Thanks for any help :popcorn:

---

### Post by Arndt on 2009-04-28
> **akvino said:**
> Hello all!

I am not sure if anyone knows of the csh variable compatable to HISTTIMEFORMAT which will add date to time displayed in .history file.

This is currently in my .cshrc file:
set history=500             # previous commands to remember.
set savehist=500


Thanks for any help :popcorn:

'csh' doesn't seem to have it, but 'tcsh' does.

```
      history The first word indicates the number of history events to  save.
               The optional second word (+) indicates the format in which his$-1òð
               tory is printed; if not given,  $-1òø%h\t%T\t%R\nòù  is  used.   The
               format  sequences  are  described  below under prompt; note the
               variable meaning of $-1òø%Ròù.  Set to òø100òù by default.
```

Gee, I don't know what strange characters "man tcsh" gave me, but you can almost read it, I trust.

---

### Post by akvino on 2009-04-29
I added two lines to configuration files when the user logs in I take the date stamp:
echo "Date is: `date`" >> ~/.history

This did the trick.

---

