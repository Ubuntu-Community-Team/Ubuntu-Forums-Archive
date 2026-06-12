---
title: "Sed ar gawk???"
date: 2009-11-17
forum: Programming Talk
---

### Post by Barriehie on 2009-11-17
My apologies if this is the wrong subforum; please move if so!  So I've decided to print out some manpages and when I *man SomeCommand > SomeFile*and then open SomeFile in an editor I've got the escape sequences for the underlining messing up the formatting, and appearing as \xxx\xxx\xxx.  I've determined from wikipedia that both are pretty much text file editors and gawk seems to be more enabled as it were.  Can either of these do this or will the non-ASCII escape sequences mess things up???

I would like to learn whichever of these is most useful or at least the one that is most used!  This also doubles back on my desire to learn regexp's.  Any input on which to learn over the other will be much appreciated also!

TIA,
Barrie

Edit:  Just found a link on google in regards to using groff to print them and my initial attempts at pulling out the escape seq. via sed and emacs aren't working!  

Okay, just found out that I can:
```

man ls | col -b > ./ls.txt

```
to achieve what I was looking for but my second ? still stands, which of the two, sed or gawk, would be the better one to learn.

Thanks again! :)

---

### Post by ghostdog74 on 2009-11-17
1) you can use groff to format your man pages. Also check the man page of "man" for -t option
2) Use gawk, and never bother about sed. See my sig for gawk manual.

---

### Post by Barriehie on 2009-11-17
> **ghostdog74 said:**
> 1) you can use groff to format your man pages. Also check the man page of "man" for -t option
2) Use gawk, and never bother about sed. See my sig for gawk manual.

Thank you ghostdog74, I compliment your inputs to the *nix community, they've kept me busy for only knows how long!

Barrie

---

