---
title: "can someone explain map reduce to me?"
date: 2010-08-18
forum: Programming Talk
---

### Post by badperson on 2010-08-18
I get the idea that it takes a large problem and breaks it into small chunks using key/value pairs and distributes it across a server cluster with multiple nodes, but for example, when I type in "the seattle mariners" into google, what are the key/value pairs in that case? 

Is "the seattle mariners" the key, and the document on a local machine being searched is the value? Then it returns a set of all pairs with a key of "the seattle mariners"?


Also, page rank...the system that counts how many other sites link to the page being returned as a result has to do with sorting the result set, not generating the result set, correct?

---

### Post by Queue29 on 2010-08-18
> , but for example, when I type in "the seattle mariners" into google, what are the key/value pairs in that case? 

This has nothing to do with MapReduce. 

Google uses MapReduce for their page rank algorithm while building their cache of the internet (so by the time you search for something, the whole mapping and reducing part is already done and over with). 

> Also, page rank...the system that counts how many other sites link to the page being returned as a result has to do with sorting the result set, not generating the result set, correct?

Sorting is a necessary (in a sane world at least) component of a Reducing algorithm, so your question doesn't really make sense. The results are sorted as the reducer does its job.

---

