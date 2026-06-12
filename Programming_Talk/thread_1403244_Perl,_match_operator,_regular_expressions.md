---
title: "Perl, match operator, regular expressions"
date: 2010-02-10
forum: Programming Talk
---

### Post by Tanchistu on 2010-02-10
I've google it half an hour, maybe I'm passing it without realizing.

```
if ($a[$i] =~ /$d/){}
```

It works as intended, but if I have "(" or ")" it stops working.

Ex: $a[$i]=Portishead - 1995-06-07 - Glory Times (disc 2_ Glory)::00 - Glory Times (Disc 2).log

$d = Portishead - 1995-06-07 - Glory Times (disc 2_ Glory)

Thanks in advance.

---

### Post by Some Penguin on 2010-02-10
Quote it.

/\Q$d\E/

---

### Post by Tanchistu on 2010-02-10
It works, 

Thanks

---

### Post by Hellkeepa on 2010-02-10
HELLo!

Excuse my little foray into the world of off-topic postings, but...
Portishead! :-D *Thumbs up*

Happy listenin'!

---

