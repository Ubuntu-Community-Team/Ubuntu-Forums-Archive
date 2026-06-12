---
title: "doing something wrong, sorting isn't working right."
date: 2010-03-30
forum: Programming Talk
---

### Post by bartre on 2010-03-30
hey, i'm working on a word counter, and i've got it working for the most part.
unfortunately, when we print out the finished count, it needs to be alphabetical.
my thought is that i can sort it before i do anything else, but it's not sorting it correctly

Here's my sort code, stsplit is an array of Strings:
```

for (i = 0; i < strsplit.length; i++) 
{
    for (j = i + 1; j < strsplit.length; j++) 
    {
        if( strsplit[i].compareToIgnoreCase(strsplit[j] ) > 0 )
        {
            tmp = strsplit[i];
            strsplit[i] = strsplit[j];
            strsplit[j] = tmp;
        }
    }
}

```

and here's the text i'm supposed to sort
```

Pioneer 10 Still Running After 30 years 
Posted by michael on Tuesday July 23
from the overdue-for-tuneup-and-brake-job dept.
evilempireinc writes "According to this article in Scientific American,
Pioneer 10 is still functioning 30 years after it was launched in 1972,
and is still sending back scientific data. The article mentions that two
other old space craft, Voyager, and IMP-8 are still functioning after
over 20 years as well due to overbuilt construction and redundant
systems. Can't help but wonder if the present generation of "faster,
better, cheaper" probes will ever live this long though." 

```

i'm also supposed to ignore the punctuation when sorting, but that's already taken care of
after sorting the String array, i get this:

```

Posted
10
10
1972
and
20
23
from
30
30
According
After
after
after
over
American
Pioneer
and
and
are
article
article
as
back
but
by
Can't
cheaper
construction
craft
data
dept
evilempireinc
due
ever
faster
better
functioning
functioning
generation
help
if
IMP-8
in
in
is
is
it
July
launched
live
long
mentions
michael
of
old
on
overbuilt
overdue-for-tuneup-and-brake-job
Pioneer
present
probes
redundant
systems
Running
Scientific
scientific
sending
space
still
still
Still
still
that
The
the
the
this
this
though
to
to
Tuesday
two
other
Voyager
was
well
will
wonder
writes
years
years
years

```

anyone know what's wrong?

---

### Post by MindSz on 2010-03-30
Are you sure the *compareToIgnoreCase()* function is correct or that you are using it the right way?

---

### Post by bartre on 2010-03-30
well, i initially tried equalsIgnoreCase(), but that didn't work at all.
Also, I've tried Arrays.sort() and set it to ignore case, but that still didn't sort correctly.
i'm honestly drawing a blank as to what's wrong.

---

### Post by geirha on 2010-03-30
I think some of the strings may contain \n, e.g. "after\nover". Make sure you also split on newlines.

EDIT: Yes, that is indeed it, all newlines are there, so it's sorting it right.

```

\nPosted
23\nfrom
dept\nevilempireinc
American\nPioneer
1972\nand
two\nother
after\nover
redundant\nsystems
faster\nbetter

```

---

### Post by bartre on 2010-03-30
yes, that fixed it.
now i've got it sorting right.
just one thing i other thing i need to fix, but that's just print formatting, so it's no big deal.
Thanks A lot!

---

