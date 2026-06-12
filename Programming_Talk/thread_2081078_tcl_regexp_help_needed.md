---
title: "tcl regexp help needed"
date: 2012-11-05
forum: Programming Talk
---

### Post by Derek Karpinski on 2012-11-05
I've been using tcl for awhile now.  Nothing super fancy, mostly low-grade stuff.  I'm always wanting to learn something new, and try things different ways.

So, my question:

suppose a variable 'test' that can be any value from 1-29.

I want to check for it's value and steer my logic depending on it's value.  I want to check if the value is one of the following:
0, 1, 3, or 24.

I accomplished this with:
```

switch $test {
     0 {do stuff}
     1 {do stuff}
     3 {do stuff}
     24 {do stuff}
     default {do other stuffs}
}

```Problem solved...........

But I want to learn regular expressions a bit more.  So I tried:

```

if { [regexp {[0]|[1]|[3]|[24]} $test] == 1} {
     do stuff
} else {
     do other stuffs
}

```But my regex is not working.  It matches a 2.  I need it to match any one of those numbers (0, 1, 3, or 24) and the whole number only.

What am I doing wrong?

---

### Post by stylishpants on 2012-11-06
```

if { [regexp {[0]|[1]|[3]|[24]} $test] == 1} {
     do stuff
} else {
     do other stuffs
}

```

You are using character classes unnecessarily.
The syntax [24] matches any one of the characters inside the [], ie. 2 or 4.
That is why your code matches "2".

Try eliminating square brackets from the regexp.

You may also need word boundaries or line delimiters on either end of your regex, depending on what your input string looks like.  For example, if your input string was "240" then the regex {1|3|24} would match it unless you added something to the end of the regex to tell it to stop matching after the 4.

---

### Post by Derek Karpinski on 2013-01-03
Yes, that worked.  Thank you!

---

