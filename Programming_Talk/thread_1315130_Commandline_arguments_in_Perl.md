---
title: "Commandline arguments in Perl"
date: 2009-11-05
forum: Programming Talk
---

### Post by absolutezero1287 on 2009-11-05
So how do I do it?

I wrote a script that has many subroutines for doing various mathematical operations (solve quadratics, find the sum of all numbers in a finite series, midpoint between two lines, and others). I named the script math.pl but what I'd like it to do is print a usage message if no argument is passed, e.g. USAGE -g run the gauss subroutine, etc. etc. I figured that I could do something like:

if (@ARGV = "") {
print "USAGE:\n-g run the gauss subroutine\n";
}

However this doesn't look right.

---

### Post by diesch on 2009-11-05
```

if (not @ARGV) {
print "USAGE:\n-g run the gauss subroutine\n";
}
```

---

### Post by absolutezero1287 on 2009-11-05
> **diesch said:**
> ```

if (not @ARGV) {
print "USAGE:\n-g run the gauss subroutine\n";
}
```

Ok, I understand that bit but how would I get it to recognize an argument such as -g, --help, --version, and others.

---

### Post by diesch on 2009-11-05
Have a look at at the Getopt::Long module

---

