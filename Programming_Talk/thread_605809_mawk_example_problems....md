---
title: "mawk example problems..."
date: 2007-11-07
forum: Programming Talk
---

### Post by pylon42 on 2007-11-07
I'm just messing around with this whole bash scripting thing... having some problems with mawk.

This is copied and pasted directly from "man awk"

```
echo  abc | mawk { gsub(//, "X") ; print }
```

The example says it should return:
XaXbXcX

However, all I get is:

```
 line 5: syntax error near unexpected token `('
line 5: `echo  abc | mawk { gsub(//, "X") ; print }'
```

I assume this problem is the result of something very basic, but I've only been messing around with this shell scripting stuff for a couple hours.

Any help would be appriciated

---

### Post by Micah Elliott on 2007-11-07
If you wrap mawk's argument (the whole source) into single-quotes your example will work.

```

$ echo  abc | mawk '{ gsub(//, "X") ; print }'
XaXbXcX

```

BTW, do you have some reason for using mawk instead of say gawk?  Just curious if mawk has some advantages.  It doesn't appear to even have a --help option, and the manpage doesn't compare it to gawk.

---

### Post by pylon42 on 2007-11-07
Thank you kindly.

No reason in particular. I typed "man awk" and the man for mawk popped up...

I'm just playing around with stuff, I didn't even know what awk was 3 hours ago.

Thanks again

---

### Post by desanti on 2007-11-07
> **pylon42 said:**
> Thank you kindly.

No reason in particular. I typed "man awk" and the man for mawk popped up...

I'm just playing around with stuff, I didn't even know what awk was 3 hours ago.

Thanks again

did you find an answer to your problem?? i can't mawk to work either.thanx.

---

### Post by desanti on 2007-11-07
> **Micah Elliott said:**
> If you wrap mawk's argument (the whole source) into single-quotes your example will work.

```

$ echo  abc | mawk '{ gsub(//, "X") ; print }'
XaXbXcX

```

BTW, do you have some reason for using mawk instead of say gawk?  Just curious if mawk has some advantages.  It doesn't appear to even have a --help option, and the manpage doesn't compare it to gawk.

i tried the same thing(man page example) and did as you suggested.did not work.using awk for windows
i had no problem.with linux??

---

