---
title: "how to  that should be simple and obvious : install perl modules via apt"
date: 2007-10-26
forum: Programming Talk
---

### Post by cacycleworks on 2007-10-26
Hey All,

In case this can help someone googling their way around for help (like I do)... I'm a recent linux retread ; was lost in windoze for a decade but did lots of cli in solaris, etc, during college.

Today, I got some code from googling on CIDR information and ran into something new to me in linux: how to install perl modules. The error was 

Error:  Can't locate Net/CIDR.pm in @INC (@INC contains:  [path stuff] ) at /path/to/my/script.pl line 7. And it said something about cpan. 

OK, I'm a pretty good hacker of cli and making things work, but cpan kicked my butt. Hmph. I don't know how I thought of apt-get, but this was The Light that saved me:

```
$ apt-cache search perl | grep net | grep -i CIDR
libnet-cidr-lite-perl - Merge IPv4 or IPv6 CIDR address ranges
libnet-cidr-perl - Manipulate IPv4/IPv6 netblocks in CIDR notation
$
```

Just thought I'd post the reminder / share my research in hopes of saving someone an hour. :)

---

### Post by tkharris on 2007-10-27
What problems did you have with cpan?  Most of the Debian repos have a very limited set of the the most popular perl modules, I assume Ubuntu's repos are the same way.  If you're a perl coder and need access to the most current and most complete perl modules you can't beat cpan.

---

### Post by cacycleworks on 2007-10-27
* shrugs * got me. Prolly something typical... was the usual small error early on that led to another and another. When researching all that, I think is when I found the apt-get and got it working in about 40 seconds.

I'm not exclusively perl or any language. I use whatever axe is in front of me. :) 

Soooo, 40 seconds or spend who knows how long trying to understand the cpan command line? 

... just finished up an awesome php script for dumping perfectly formatted 76 character wide plain text e-mail replies... :P  :D

---

