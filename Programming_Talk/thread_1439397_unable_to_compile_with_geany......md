---
title: "unable to compile with geany....."
date: 2010-03-26
forum: Programming Talk
---

### Post by rejuvenate on 2010-03-26
i am using geany to compile my perl code but it is unable to compile and giving error as```
perl -MO=Bytecode,-H,-o"tcpser.pl"c "tcpser.pl" (in directory: /home/harsha/Desktop/perl)
Can't locate B/Bytecode.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at (eval 1) line 18.
BEGIN failed--compilation aborted at (eval 1) line 18.
BEGIN failed--compilation aborted.
Compilation failed.
```
i want to know how to solve the problem and is there any better IDE available in ubuntu...

---

### Post by MindSz on 2010-03-26
I'm not really a perl programmer, but it seems to me that geany is having problems locating one of the files it requires (B/Bytecode.pm) in the folders listed in @INC: ```
/etc/perl
/usr/local/lib/perl/5.10.0
/usr/local/share/perl/5.10.0
/usr/lib/perl5 /usr/share/perl5
/usr/lib/perl/5.10 /usr/share/perl/5.10
/usr/local/lib/site_perl
```

So yeah, make sure the file is there.

---

### Post by FarNow on 2010-07-13
I'm having the same issue - problem is that neither Debian or Ubuntu seem to include B::Bytecode.pm? This was part of perl-core < 5.10 but now that Debian/Ubuntu Perl has moved past this version, it is no longer included? Strangely a google shows that it is somewhere in there as it shows up in repositories, but package search does not show it under any version?

Can any Ubuntu Wizard identify which package this could be obtained from? Should this be added to the geany dependencies?

Thanks a bunch,

FN

---

### Post by GregBrannon on 2010-07-13
You asked if there was a better IDE.  The problem you're having is not Geany's fault.  Geany is a very good, full-featured IDE with a minimal footprint, but if you're looking for something else, let us know what you mean by better.  The question of the best IDE comes up often in this topic area, so you could search for previous threads.

---

