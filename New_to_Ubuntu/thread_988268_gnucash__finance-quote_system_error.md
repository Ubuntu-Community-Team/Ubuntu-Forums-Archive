---
title: "gnucash / finance-quote system error"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by doubleij on 2008-11-20
Hi,
I am configuring my new Dell XPS m1330 (pre-installed Ubuntu 8.04).

I found gnucash and the libfinance-quote in the repositories and installed without problems. gnucash runs fine, but I cannot fetch prices for securities or currencies. I get a system error when I click Get Quotes in the Price Editor dialog of Gnucash. I get the following error starting from the command line.

```
$ gnucash -v
gnc.bin-Message: main: binreloc relocation support was disabled at configure time.
```

This error was referenced in this [post]("http://ubuntuforums.org/showthread.php?t=795024&highlight=gnucash+error"), but no solution was found. I am running Finance Quote 1.13 and Gnucash 2.2.4 (from the repositories).

I can obtain security quotes using finance quote from the command line, but not through gnucash. 
```
~$ gnc-fq-dump yahoo GOOG
Finance::Quote fields Gnucash uses:
    symbol: GOOG                 <=== required
      date: 11/20/2008           <=== required
  currency: USD                  <=== required
      last: 280.79               <=\       
       nav:                      <=== one of these
     price: 280.79               <=/        
  timezone:                      <=== optional
```

Clicking get quotes for a google security in Gnucash results in a system error. 

Any help? I'm stumped. Finance quote and gnucash work great on my windows laptop. I really need to get both working in Ubuntu. On Windows, I am running GnuCash 2.2.7 with Finance Quote 1.15. I have not found a guide for installing gnucash / finance-quote with Ubuntu. I've done lots of google searches, but have not found much help, so I don't know how to troubleshoot further.

Any ideas?

---

### Post by MicahCarrick on 2009-01-02
Has this been resolved yet?

---

### Post by doubleij on 2009-01-04
No, it has not! I never heard back from anyone about this. I posted the bug with the gnucash support team and they have not triaged the bug report.

I installed 2.2.7 from source and that solved the problem, but AFAIK the version in the repos is still bad.

---

### Post by MicahCarrick on 2009-01-04
I was able to resolve it by manually editing the file: /usr/share/perl5/Finance/Quote/Yahoo/Base.pm

I changed the FIELD_ENCODING from this:
```
@FIELD_ENCODING = qw/s n l1 d1 t1 c1 p2 v b a p o m w e r r1 d y j1 q a2 c4/;
```

to this (the t1 and d1 are swapped):
```
@FIELD_ENCODING = qw/s n l1 t1 d1 c1 p2 v b a p o m w e r r1 d y j1 q a2 c4/;
```

---

### Post by Charismatic1 on 2009-04-07
personal and small-business financial-accounting software freely licensed under the GNU GPL. Designed to be easy to use, yet powerful and flexible, GnuCash allows you to track bank accounts, stocks, income and expenses

---

