---
title: "Perl Modules Error"
date: 2009-07-14
forum: Programming Talk
---

### Post by dellwood on 2009-07-14
Hi,

When I run **file.pl** which includes the **configRead.pm** perl module, I recieve the following error:

```

perl file.pl                              ~/programs/perl/my_examples
configRead.pm did not return a true value at file.pl line 3.
BEGIN failed--compilation aborted at file.pl line 3.

```

file.pl: [http://www.pastie.org/545779](http://www.pastie.org/545779)

configRead.pm: [http://www.pastie.org/545781](http://www.pastie.org/545781)

I can't figure out why...I have the exact same situation with another pair of files ( that works fine ) and I've crossed check the pairs a good many times.

All help is greatly appreicated :).

-Josh

---

### Post by unutbu on 2009-07-14
Put a 
```

1;
```
at the end of configRead.pm.

---

### Post by dellwood on 2009-07-14
Thanks, it worked :D.

Could you point me to some documentation explaining this, as I'd like to know when I do/don't have to put this (like I said, the other two files with the same relationship didn't require it).

Thanks :).

-Josh

---

### Post by unutbu on 2009-07-14
[http://en.wikipedia.org/wiki/Perl_module:](http://en.wikipedia.org/wiki/Perl_module:)

```
  # A Perl module must end with a true value or else it is considered not to
  # have loaded.  By convention this value is usually 1 though it can be
  # any true value.  A module can end with false to indicate failure but
  # this is rarely used and it would instead die() (exit with an error).
  1;
```

When I was actively coding in Perl, I learned this and did not question it.
Larry Wall said my modules should end with a "1;" so that is what I did.

Now that I've switched to Python, I believe a good programming language should
not force this kind of arbitrary, un-useful rule upon its users. ;)

---

### Post by dellwood on 2009-07-14
Thanks for the reply.  I'm using an eight year old book currently, and I'm not sure when the feature was implemented, but this book sure doesn't mention it.  

> 
Now that I've switched to Python, I believe a good programming language should
not force this kind of arbitrary, un-useful rule upon its users. 

I could switch to, I'd just loose my job :D (j/k...I'm learning python in my free time).

Thanks again :)

-Josh

---

