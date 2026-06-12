---
title: "Benchmark: kernel 2.6.8-386 vs kernel 2.6.8-686"
date: 2005-04-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Bogart on 2005-04-09
Some time ago I found a wiki topic about optimized pakages for Ubuntu promising some tests about it (I can't find it now), and also some threads in the forum ([like this one](http://www.ubuntuforums.org/showthread.php?t=13753) ) about why not using i686 optimizations instead of i383. So I decided to make a test and see what could i find out.

I recently read an interesting article ([part 1](http://software.newsforge.com/article.pl?sid=04/12/27/1238216&tid=72)  [part 2](http://www.newsforge.com/article.pl?sid=04/12/27/1243207) using mysql to compare different operating systems, so i decided to follow it to compare kernel 2.6.8.1-5-383 to kernel 2.6.8.1-5-686 on my Ubuntu install. Unfortunatly on that article they use 2 benchmark programs, but I only managed to compile one of them, super-smack, as sysbench wouldn't compile on my box.

So my tests are just the two available with this program. The first one simulates 10 users connecting 10000 times each to a database and selecting some data, and the second one is the same but updating the data. I run each test 6 times and made the avarage to get the result.

The machine I tested it is a Pentium IV 2.6Ghz 256Mb/RAM.

The results:

The first test had very sonsitent results -that is, each time I repeated the test the numbers were almost the same.

With kernel 2.6.8.1-5-386 it run 13375 queries per second.
With kernel 2.6.8.1-5-686 it run 14036 queries per second.

So kernel 686 optimized was 4% faster.

The second test was not so consistent. Results would vary a little each time I run the test, and since the results were so close between both kernels it would be difficult to say with one was faster. In the end, making the average i got:

kernel 383: 3875 reqs per sec.
kernel 686: 3927 reqs per sec.

So again i686 was faster, but just 1.3%.

I decided to run a different test using the Gimp this time. I opened a big picture (almost 1mb size) and applied the slowest filter I found (cubist for this pic).

With kernel 386 it took 38.5 seconds to apply it, while with kernel 686 it took 39 seconds.

These results confirmed my impression by using both kernels for some time that there is no real difference between one and the other. Maybe in different test (and different machines, maybe AMD's) the difference between the default pakages and optimized ones may be bigger, but on a pentium iv (at least in mine) they seem to work almost the same (very fast, by the way). I know they are just small tests to draw big conclusions, so I hope others can make some further research to see when and for who it might be worth to compile their own pakages, and in which cases it's just not necessary at all.

Regards :)

---

### Post by humanity_to_others on 2005-04-09
There was also a benchmark with Doom3 and Ubuntu: [http://home.comcast.net/~morphodone/](http://home.comcast.net/~morphodone/)

---

