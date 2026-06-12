---
title: "I need a c++ threading tutorial"
date: 2006-11-17
forum: Programming Talk
---

### Post by Luggy on 2006-11-17
I'm looking for a really good threading tutorial for c++. I have tried to search online and have found tutorials but they are usually too brief and not simple enough for me to properly understand. Most of the tutorials that I have seen are a page long and don't include much more than the class and description of what it's methods do; I don't understand what they are getting at.

If anyone can point me in the direction of a good resource it would be much appreciated.

---

### Post by jr.gotti on 2006-11-17
I know this isn't the answer you're looking for...but if you're really interested in programming grab a book...

Tutorials online are like you said too brief and don't really give you what you need. 

You can find a good one on Ebay or Amazon for relatively cheap.

[http://www.amazon.com/C%2B%2B-Programming-Language-Special-3rd/dp/0201700735/sr=8-1/qid=1163787627/ref=pd_bbs_sr_1/102-6540719-9945737?ie=UTF8&s=books](http://www.amazon.com/C%2B%2B-Programming-Language-Special-3rd/dp/0201700735/sr=8-1/qid=1163787627/ref=pd_bbs_sr_1/102-6540719-9945737?ie=UTF8&s=books)
[http://www.amazon.com/C%2B%2B-Primer-Plus-5th-Sams/dp/0672326973/sr=8-2/qid=1163787627/ref=pd_bbs_sr_2/102-6540719-9945737?ie=UTF8&s=books](http://www.amazon.com/C%2B%2B-Primer-Plus-5th-Sams/dp/0672326973/sr=8-2/qid=1163787627/ref=pd_bbs_sr_2/102-6540719-9945737?ie=UTF8&s=books)

Are two very good ones. Good luck!

---

### Post by THaugland on 2006-11-17
I recommend using pthreads for portability.
[http://www.llnl.gov/computing/tutorials/pthreads/](http://www.llnl.gov/computing/tutorials/pthreads/)

A good book on pthreads:
[http://www.amazon.com/Programming-POSIX-Threads-David-Butenhof/dp/0201633922/sr=8-2/qid=1163811130/ref=pd_bbs_2/002-1382350-3880841?ie=UTF8&s=books](http://www.amazon.com/Programming-POSIX-Threads-David-Butenhof/dp/0201633922/sr=8-2/qid=1163811130/ref=pd_bbs_2/002-1382350-3880841?ie=UTF8&s=books)

---

### Post by amo-ej1 on 2006-11-20
Well my suggestion would be that before doing _anything_ with threads, you should first learn what threads are all about, read some things about multithreading, mutual exclusion, mutex, critical sections, dining philosophers etc so you know what issues can and SHALL occur. After that (or while figuring that out) you should indeed take a look at pthreads and look how those concepts apply in pthread (manpages can be rather nice here). Personally i'm working rather a lot with pthreads and never read any book about them (but it read a lot of things on concurrency etc). and in case of any questions, don't hesitate to ask them here ;)

my 2 cents

---

### Post by pharcyde on 2006-11-22
Once you've become familiar with threading techniques as mentioned above you could check out pthreads or boost threads.

pthreads -> [http://www.llnl.gov/computing/tutorials/pthreads/](http://www.llnl.gov/computing/tutorials/pthreads/)
boost    -> [http://www.boost.org/doc/html/threads.html](http://www.boost.org/doc/html/threads.html)

---

