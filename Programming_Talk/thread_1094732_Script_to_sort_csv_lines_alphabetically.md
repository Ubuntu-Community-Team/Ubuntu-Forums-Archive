---
title: "Script to sort csv lines alphabetically"
date: 2009-03-12
forum: Programming Talk
---

### Post by Vadi on 2009-03-12
Hi,

I don't suppose anyone has a script that would sort cvs rows alphabetically, based on the first item of a row?

Just I'd ask before I dig into this tomorrow ;)

---

### Post by ghostdog74 on 2009-03-12
```

# sort csvfile

```
check the man page for sort for more details.

---

### Post by monkeyking on 2009-03-12
You can use unix sort directly, no need for scripts.
Something like
[PHP]
sort -t ',' -k1 yourfile.txt
[/PHP]

good luck

---

### Post by ghostdog74 on 2009-03-12
since its based on first item, sort will do
```

# more file
c,y,i,e
a,b,c,d
d,e,f,x
b,p,o,q

# sort -t ',' -k1  file
a,b,c,d
b,p,o,q
c,y,i,e
d,e,f,x

# sort file
a,b,c,d
b,p,o,q
c,y,i,e
d,e,f,x


```

---

### Post by Vadi on 2009-03-12
Haha, thanks, looks like this will work. I'll give it a try. Does it exclude quotes? (first character is a quote in all of them) - or maybe I can just give it the 2nd char. Anyway will read the manual and thanks for the great tip.

---

### Post by monkeyking on 2009-03-12
> **ghostdog74 said:**
> since its based on first item, sort will do
Where do you have this information?

```

OS is F[.C][OPTS], where F is the field number  and  C  the  character
       position  in  the field; both are origin 1.  If neither -t nor -b is in
       effect, characters in a field are counted from  the  beginning  of  the
       preceding  whitespace.   OPTS  is  one  or  more single-letter ordering
       options, which override global ordering options for that  key.   If  no
       key is given, use the entire line as the key.


```

Futher more 

```

*** WARNING *** The locale specified by the  environment  affects  sort
       order.  Set LC_ALL=C to get the traditional sort order that uses native
       byte values.

```

edit:
I think som linux dists, defaults to the first column as key, while others use hole line.
The only way to be certain I guess is to use a specifik col key.

---

### Post by ghostdog74 on 2009-03-12
my settings
```

# locale
LANG=POSIX
LC_CTYPE=en_US.UTF-8
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=


```

---

