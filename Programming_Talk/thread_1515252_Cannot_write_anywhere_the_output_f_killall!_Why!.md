---
title: "Cannot write anywhere the output f killall!? Why!?"
date: 2010-06-22
forum: Programming Talk
---

### Post by hakermania on 2010-06-22
I want to write the output of killall to a file, but this seems impossible.
I've tried```

killalll -v airodump-ng > ./unkilled
echo `killall -v airodump-ng` > ./unkilled
```
but in any occassion th efile ./unkilled is empty, although the command has output!
Any suggestions?

---

### Post by geirha on 2010-06-22
Why do you need that output? Anwyay, that output is probably written to stderr, see [http://mywiki.wooledge.org/BashFAQ/002](http://mywiki.wooledge.org/BashFAQ/002)

---

### Post by hakermania on 2010-06-22
In simple words?

---

### Post by Barrucadu on 2010-06-22
If the output is written to stderr, you can capture it like this:
```
killall -v airodump-ng 2> ./unkilled
```

---

### Post by hakermania on 2010-06-22
> **Barrucadu said:**
> If the output is written to stderr, you can capture it like this:
```
killall -v airodump-ng 2> ./unkilled
```
cool, you are right!

---

