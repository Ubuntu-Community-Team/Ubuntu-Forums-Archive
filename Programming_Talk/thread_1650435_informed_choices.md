---
title: "informed choices"
date: 2010-12-21
forum: Programming Talk
---

### Post by worksofcraft on 2010-12-21
I recently been working with internationalized text and there are a variety of ways to cope with full unicode character set. I decided to do some metrics on various "container" technologies.

The test uses pseudo random numbers so that it is repeatable and identical for each, but should not favor any. It consists of:
[LIST=1]
[*]creating an empty instance
[*]appending a random number of characters
[*]iterating thru the characters
[*]randomly indexing characters
[/LIST]

I used default settings for each type. No doubt tweaking specific parameters and shifting the emphasis of the tests would give different results.. but here they are anyway:

> 
C **array** time=0.130000 seconds, sum=-1209593684
std::**vector** time=0.410000 seconds, sum=-1209593684
agg:: pod_auto_vector time=0.210000 seconds, sum=-1209593684
agg:: pod_bvector time=0.300000 seconds, sum=-1209593684
Glib::**ustring** time=2.300000 :shock: seconds, sum=-1209593684
std::**string** time=0.300000 seconds, sum=2570412


The check sum is to ensure that they all have done exactly the same thing. Evidently it fails for std::string because that only does chars and not unicode, but the figure is interesting for comparison sake. However based on these figures I think it is worth considering alternatives to Glib::ustring any other suggestions ?

p.s. Test code attached for those interested.

---

### Post by worksofcraft on 2010-12-21
btw I recompiled with optimization. It makes a huge difference, so much so that I had to increase the number of iterations by a factor of 10 to avoid losing accuracy of timing.

Optimization also clearly helps with template classes making the agg:: pod_auto_vector just as good as a plain C array and the auto allocating agg:: pod_bvector even faster than std::string but with full unicode capability :shock:

> 
-O3 optimization
C array time=**0.820000** seconds, sum=-199939416
std::vector time=1.010000 seconds, sum=-199939416
agg:: pod_auto_vector time=0.800000 seconds, sum=-199939416
agg:: pod_bvector time=**0.990000** seconds, sum=-199939416
Glib::ustring time=19.190001 seconds, sum=-199939416
std::string time=**1.280000** seconds, sum=22425000


---

### Post by Vaphell on 2010-12-22
what about QString from Qt?

---

### Post by worksofcraft on 2010-12-22
> **Vaphell said:**
> what about QString from Qt?

After a bit more experimenting I discovered that Glib::ustring literally grinds to a halt on indexing (random access) as the string length increases.

Evidently packing codes into variable length byte sequences is  forcing ustring to decode the whole string every time you want to index.

I now just read the documentation on QString. It stores international characters in 16 bit quantities but it also uses multiple entries to encode bigger unicode values.

It might be interesting to compare it, but I suspect it has the worst of both worlds: Double the memory requirement of ustring for plain ascii yet also the high overhead of sequential processing for indexing... perhaps I'll check it when I have some spare time.

Now I did notice a post about bit map formats which are actually 24 bit entities and that would be sufficient for the full unicode character set too. Somehow image processing get round the word boundary issue when rasterizing images, so I suspect agg might have a template I can use to make vectors of 24 bit enities :popcorn:

---

### Post by MadCow108 on 2010-12-22
well obviously ustring performs worse than vectors on random access, ustring is a bidirectional list:
> Note this is not a random access iterator but a bidirectional one, since all index operations need to iterate over the UTF-8 data. Use std::advance() to move to a certain position.

[http://library.gnome.org/devel/glibmm/2.23/classGlib_1_1ustring__Iterator.html](http://library.gnome.org/devel/glibmm/2.23/classGlib_1_1ustring__Iterator.html)

the question is: do you need random access on strings?
often string operations are just a bunch of concatenations and regex-like parsing which are very efficient with lists

---

### Post by worksofcraft on 2010-12-22
> **MadCow108 said:**
> well obviously ustring performs worse than vectors on random access, ustring is a bidirectional list:

[http://library.gnome.org/devel/glibmm/2.23/classGlib_1_1ustring__Iterator.html](http://library.gnome.org/devel/glibmm/2.23/classGlib_1_1ustring__Iterator.html)

the question is: do you need random access on strings?
often string operations are just a bunch of concatenations and regex-like parsing which are very efficient with lists

That's a good question. As I said the metrics do depend on what emphasis I put on the different tests. I think there were only 50 random indexing operations against 1000 string iterations. Random indexing is performance wise similar to stepping backwards in a ustring which is needed some places. I also use strings as international chartacter lookup tables... e.g. to find the unicode characters for Chinese digit set.

I was hoping to view these strings as "black boxes" and remain oblivious to their internal implementation, however when you say it's a *bidirectional list*... what does that mean? Like a linked list where each character has a pointer to the next and a pointer to teh previous?  That's gunna suck in more ways than I can imagine :shock:

---

### Post by MadCow108 on 2010-12-22
I'm sorry I misinterpreted the iterator. No its not a list, just the iterator is bidirectional (= no good random access)

it actually uses a std::string as data container
which indicates that you benchmark is in some way flawed as the performance of ustring should not be so much worse than std::string when used correctly

---

