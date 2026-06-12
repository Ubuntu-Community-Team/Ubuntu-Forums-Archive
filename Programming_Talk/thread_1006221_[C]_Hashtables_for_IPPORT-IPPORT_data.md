---
title: "[C] Hashtables for IP/PORT-IP/PORT data"
date: 2008-12-09
forum: Programming Talk
---

### Post by daniele_dll on 2008-12-09
Hello,

i'm writing an usermode netfilter integration (using netfilter_queue) and i need to store and track connections (if there is), in general i need to track packets IN/OUT.

Actually, to test it, i used a linked list, with some little optimizations, but, before i start to write plugins for my app i need to let the core work in a reasonable way!

I've four lists, one for ip protocol supported type, this mean ICMP, IGMP, TCP and UDP, but i mainly interested to TCP and UDP only, because i'm working on an high level filter.

I really know few about hashtables, i ever used them in higher level languages, but what i know is that i need a GOOD hashing routine to reduce collisions (that make bigger the overflow table) and make search, insert, delete and modification faster.

Can someone point me out to some tutorial or doc that give some suggestion? And, if there is a good one, a link to an hashtable library under BSD/MIT license?

thank you!

PS: i've looked for RB Trees, but i really don't know nothing about them so i discarded these, but probably them are better than hashtable.

---

### Post by daniele_dll on 2008-12-09
I googled a lot, and i found some really interesting stuff:
[http://www.gnu.org/software/gperf/](http://www.gnu.org/software/gperf/)
and
[http://cmph.sourceforge.net/index.html](http://cmph.sourceforge.net/index.html)

to generate perfect hash functions, but i think that isin't my case because i can have too much possibilities (if i'm not wrong i should have something like 4294967295^4294967295^65535^65535 possibilities)

I founded another library too:
[http://cprops.sourceforge.net/](http://cprops.sourceforge.net/)

That appears much be interesting

Someone used it?

---

### Post by uljanow on 2008-12-09
I'd recommend the [c++ hashtables]("http://en.wikipedia.org/wiki/Technical_Report_1#Hash_Tables"). But saving IP ranges (IP/PORT-IP/PORT) in a hashtable is difficult. Another way is using binary trees which require O(log n) time. [Here's an example]("http://iplist.svn.sourceforge.net/viewvc/iplist/trunk/iplist/include/range.h?view=markup") that works with ranges.

---

### Post by daniele_dll on 2008-12-10
Hi, it's interesting stuff, but for C++ i've founded that intel released an hashtable lock free (atomic operations using cas). The problem is that i'm writing it using c :\

Do you have some stuff for C?

> **uljanow said:**
> I'd recommend the [c++ hashtables]("http://en.wikipedia.org/wiki/Technical_Report_1#Hash_Tables"). But saving IP ranges (IP/PORT-IP/PORT) in a hashtable is difficult. Another way is using binary trees which require O(log n) time. [Here's an example]("http://iplist.svn.sourceforge.net/viewvc/iplist/trunk/iplist/include/range.h?view=markup") that works with ranges.

---

