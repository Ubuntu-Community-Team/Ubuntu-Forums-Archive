---
title: "urgent help with tcl regexp and regsub"
date: 2012-08-11
forum: Programming Talk
---

### Post by ggankhuy on 2012-08-11
I tried removing the garbage from following string: pattern to be removed is ^[[xm where x is any number.

^[[1mPCIE^[[0m  0x0000000000000000 : 0x3C008086

Result wanted to be this: 
PCIE 0x0000000000000000 : 0x3C008086

I tried using following: 
regsub -all "\^\[\[[0-9]m" $op  " " $op2

But it is not working. Can someone help me please? 
Thanks,

---

### Post by trent.josephsen on 2012-08-11
Are you sure that's a literal caret ^ and a literal bracket [, and not the ASCII escape character \033, which often displays as ^[?

---

### Post by ggankhuy on 2012-08-11
Not sure, may be, in the case if it turned out to be ascii character, what do  I do? Thanks,

---

### Post by ggankhuy on 2012-08-11
Problem is I dont only see ^[[1m
I also see ^[[0m too. Thanks,

---

### Post by trent.josephsen on 2012-08-11
Not familiar with Tcl, but in Perl I'd probably do something like

```
$line =~ s/\x1b\[\d+m//g;
```

'\x1b' is a literal ASCII ESC (oct 33 = dec 27 = hex 0x1b). '\d' is a shortcut for [0-9]. (In case it's not clear, the pattern in the above code is "\x1b\[\d+m"; the other stuff is the Perl substitution operator being applied to the variable $line. Just trying to make this look a little less like line noise to the uninitiated).

Hopefully you can apply this to Tcl.

---

