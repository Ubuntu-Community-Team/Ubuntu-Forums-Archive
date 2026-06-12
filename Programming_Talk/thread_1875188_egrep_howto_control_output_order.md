---
title: "egrep: howto control output order?"
date: 2011-11-04
forum: Programming Talk
---

### Post by Lampi on 2011-11-04
if I have a textfile with content:

```
a some text
b some other text
c and another one
b this is some other text starting with b
```

How can I use egrep to match ^c ^b (both of them) and ^a in exactly this order?

I tried:

```
egrep textfile "^c|^b|^a"
```
but this will not sort the output to lines starting with c,b,a - I still get the original order (abcb)

Do I have to "pipe" the output through the sort command, or is there a better way?

---

### Post by Lars Noodén on 2011-11-04
> **Lampi said:**
> Do I have to "pipe" the output through the sort command, or is there a better way?

That would be the way to do it.  

```

egrep textfile "^c|^b|^a" | sort

```

The idea is that each program does one thing only but it does it very well.

---

### Post by Lampi on 2011-11-04
yep, thanks Lars!

*arrg* stupid me had to come up with a too simplistic example for illustration purposes](*,)

what would you do if I'm interested in the output order (cabb)? Because (cbba) was obvious sorting (alphabetic, descending) - my order problem is more like (cabb) so there is no obvious sorting order...

edit: maybe there is a more sophisticated way to grap patterns using perl or awk? I'm not really an expert on this, so I can't tell ...

---

### Post by Lars Noodén on 2011-11-04
> **Lampi said:**
> edit: maybe there is a more sophisticated way to grap patterns using perl or awk? I'm not really an expert on this, so I can't tell ...

You can specify custom sort orders in Perl, but it's been far too long since I've done that to be able to provide some demo code.

---

### Post by Arndt on 2011-11-04
> **Lampi said:**
> yep, thanks Lars!

*arrg* stupid me had to come up with a too simplistic example for illustration purposes](*,)

what would you do if I'm interested in the output order (cabb)? Because (cbba) was obvious sorting (alphabetic, descending) - my order problem is more like (cabb) so there is no obvious sorting order...

edit: maybe there is a more sophisticated way to grap patterns using perl or awk? I'm not really an expert on this, so I can't tell ...

I can't come up with anything better than this right now:

```
FILE=textfile; egrep '^c' $FILE; egrep '^a' $FILE; egrep '^b' $FILE
```

---

### Post by Vaphell on 2011-11-04
if you are interested only in custom order of 1st chars

```
$ echo $'abc\ncccc\naff\nbde' | sed 'y/acb/abc/' | sort | sed 'y/acb/abc/'
abc
aff
cccc
bde
```

switch characters to custom order, sort, switch back.

also you can do a trivial thing and grep in a loop

```
for pattern in "^a" "^c" "^b"
do
  echo $'abc\ncccc\naff\nbde' | egrep "$pattern"
done

abc
aff
cccc
bde


```

---

### Post by Lars Noodén on 2011-11-04
How about something like this:
```

for i in c b a;do egrep "^${i}" /path/to/some/file;done

```

---

### Post by Lampi on 2011-11-04
Thank you guys, the suggested "for" lines work fine 8-)

I'll mark this as solved.

---

