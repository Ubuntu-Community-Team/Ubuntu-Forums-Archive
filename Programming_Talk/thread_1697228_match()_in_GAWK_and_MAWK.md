---
title: "match() in GAWK and MAWK"
date: 2011-02-28
forum: Programming Talk
---

### Post by mouffon on 2011-02-28
Dear All,

Running Ubuntu 10.10 I observed an apparent incompatibility of the "match()" functions in mawk and gawk.  As "match" is one of the basic features of awk this looks strange to me.  Are there any ideas what I am doing wrong?  Many thanks for your help.

-----------

This is the AWK script "match.awk", which is meant to match acronyms (sequences of capital letters) and print them:

[I]for (i=1;i<=NF;i++){
    if (match($i,/[A-Z][A-Z]+/)) {print substr($i,RSTART)}
    }[/I]
-------------

This is the test data "matchtest.txt":

[I]ABC chains of meta 
chains of meta [/I]
-------------

"mawk -f match.awk matchtest.txt" produces (as desired):
*ABC*
-------------

"gawk -f match.awk matchtest.txt" produces:
[I]ABC
chains
of
meta 
chains
of
meta [/I]
-------------

---

### Post by gmargo on 2011-02-28
Confirmed.  That is really weird.

Another data point:  If you change the pattern to "[[:upper:]][[:upper:]]+", then gawk works but mawk does not.

Another data point: If you print out RLENGTH, which is the length of the match, it doesn't make sense either.  For instance, the word "chains" is matched, but with a length of 2, not 6 (or zero). "meta" gets a length of 3, not 4.

---

### Post by gmargo on 2011-02-28
It's **locale** related.  This gives me the correct result:
```

LC_ALL=C gawk -f match.awk matchtest.txt
-or-
LC_COLLATE=C gawk -f match.awk matchtest.txt

```From the gawk user manual:
[http://www.gnu.org/software/gawk/manual/gawk.html#Case_002dsensitivity](http://www.gnu.org/software/gawk/manual/gawk.html#Case_002dsensitivity)
> 
As of gawk 3.1.4, the case equivalences are fully locale-aware.  They are based on the C <ctype.h> facilities, such as isalpha() and toupper().     


Update: the gawk documentation actually mentions this problem: [http://www.gnu.org/software/gawk/manual/gawk.html#Locales](http://www.gnu.org/software/gawk/manual/gawk.html#Locales)

---

### Post by mouffon on 2011-03-01
Problem solved.  Many thanks.
(And sorry I did not find the solution myself.)

---

