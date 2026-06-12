---
title: "better way to avoid a count"
date: 2010-09-07
forum: Programming Talk
---

### Post by junapp on 2010-09-07
Digging around some python code in a google app engine app.

Can someone tell me a better way of writing:
```

if Seller.all().count():
    return [(sell.key(), sell.fullname) for sell in Seller.all().order('sortname')]

```such that the count() doesn't have to fire? Still a novice in python, and unsure of the proper constructs.

I don't quite know how to get the returned tuple/list if I did it in just the for loop

for sell in Seller.all().order('sortname'):

No biggie, just trying to optimize some pieces of code and learn a little more in the process.

---

### Post by endotherm on 2010-09-07
well, in python, len(array) will return the length of a tupple/array. is that the kinda thing you are looking for?

if len(Seller.all()):
...

---

### Post by geirha on 2010-09-07
That depends on what Seller.all() returns... and it's very hard to guess.

---

### Post by Bachstelze on 2010-09-07
> **junapp said:**
> 
No biggie, just trying to optimize some pieces of code and learn a little more in the process.

Not sure what you're trying to "optimize" here...

---

### Post by junapp on 2010-09-07
sure. 

Looking at: [http://code.google.com/appengine/docs/python/datastore/creatinggettinganddeletingdata.html](http://code.google.com/appengine/docs/python/datastore/creatinggettinganddeletingdata.html)
under: Getting Entities using a query
The [all()]("http://code.google.com/appengine/docs/python/datastore/modelclass.html#Model_all") method on a [Model]("http://code.google.com/appengine/docs/python/datastore/modelclass.html") (or [Expando]("http://code.google.com/appengine/docs/python/datastore/expandoclass.html")) class returns a [Query]("http://code.google.com/appengine/docs/python/datastore/queryclass.html") object

My thinking that the count must require a loop over the query object one time to get a count,  then I am looping through it again to populate "sell". It 'feels' wrong to say, "Are there some records here", Oh, there are, let's loop over them, instead of just looping over them directly. 

I'm still new to python.

---

### Post by StephenF on 2010-09-07
> **junapp said:**
> My thinking that the count must require a loop over the query object one time to get a count,  then I am looping through it again to populate "sell". It 'feels' wrong to say, "Are there some records here", Oh, there are, let's loop over them, instead of just looping over them directly.
Whether the code is optimised or not will depend on a number of factors like the language the count is implemented in and the size of the data set.

Anyway, this should work as long as count() did what I thought.
```

s = [(sell.key(), sell.fullname) for sell in Seller.all().order('sortname')]
if s:
    return s

```

---

### Post by junapp on 2010-09-07
yes, optimized might have been the wrong word. I was trying to reduce cpu cycles on google's app engine. Not that it matters tremendously in this case with a small recordset. Your suggestion is exactly what I was after. Thanks StephenF!

---

### Post by endotherm on 2010-09-08
> **junapp said:**
> sure. 

Looking at: [http://code.google.com/appengine/docs/python/datastore/creatinggettinganddeletingdata.html](http://code.google.com/appengine/docs/python/datastore/creatinggettinganddeletingdata.html)
under: Getting Entities using a query
The [all()]("http://code.google.com/appengine/docs/python/datastore/modelclass.html#Model_all") method on a [Model]("http://code.google.com/appengine/docs/python/datastore/modelclass.html") (or [Expando]("http://code.google.com/appengine/docs/python/datastore/expandoclass.html")) class returns a [Query]("http://code.google.com/appengine/docs/python/datastore/queryclass.html") object

My thinking that the count must require a loop over the query object one time to get a count,  then I am looping through it again to populate "sell". It 'feels' wrong to say, "Are there some records here", Oh, there are, let's loop over them, instead of just looping over them directly. 

I'm still new to python.

my first thought, is that unless you are starting with some kind of specialized list (which I don;'t believe you are), there isn't a more efficient way to take the count than simply looping over it. O(n). if you dig into how the runtime is coded, you will find that the len function and things like it just iterate over the list, accumulating a count.

another thing to consider as you learn to code, is that you should always check that something exists before accessing it. Python is more forgiving than most languages in this regard, but as a general rule, when writing formal code, assert (that data is there and valid), then access.

---

### Post by Bachstelze on 2010-09-08
> **endotherm said:**
> my first thought, is that unless you are starting with some kind of specialized list (which I don;'t believe you are), there isn't a more efficient way to take the count than simply looping over it. O(n). if you dig into how the runtime is coded, you will find that the len function and things like it just iterate over the list, accumulating a count.


The point is that he is *not* trying to "take the count". Read the code : the count is not stored into any variable, it is just discarded after its truth value is tested.

---

### Post by escapee on 2010-09-08
The one thing I'd keep in mind is that if this is an ORM it could be lazy loading and not actually executing till that final .count() method (switching for 'SELECT COUNT()'.

---

### Post by Tony Flury on 2010-09-08
What happens in the code if there is nothing in the queue/list ? It is not clear from the example.

One way of doing it might be to check if the queue/list has one entry on it (which should be quicker than a full count)

---

### Post by Bachstelze on 2010-09-08
> **Tony Flury said:**
> What happens in the code if there is nothing in the queue/list ? It is not clear from the example.


count() returns zero, which evaluates to False.

---

### Post by Tony Flury on 2010-09-08
@Bachstelze - yes - I knew that bit - but i was just curious as to what happens in the rest of the code if the count is zero.

Not that it matters really - a count of zero is the same as saying it is empty, or that it does not have at least one member.

Whether or not this fragment is worth optimising depends on what the distribution of list lengths is.

If you get a lot of empty lists, and a few other small lists - then there may well be no point optimising the count, as in most cases it will be very quick.
If on the other hand you have a lot of large list, then it might be worth optimising - either by only traversing the list once (as suggested by StephenF) or by checking for existance of just one element (rather than doing a full count).

---

### Post by Bachstelze on 2010-09-08
> **Tony Flury said:**
> @Bachstelze - yes - I knew that bit - but i was just curious as to what happens in the rest of the code if the count is zero.

The function will return the empty list. The return value is a list constructed by iterating over the elements in Seller. If Seller is empty, there is nothing to iterate over, so the resulting list will turn out empty as well:

```
>>> l = []
>>> [x for x in l]
[]

```

---

### Post by junapp on 2010-09-12
wow, thanks for the discussion.

The reason I was aiming to get rid of the count was because as far as I can tell, this particular code block was sending back the list to populate a html select dropdown. The count was never used, and an empty list was handled gracefully.

---

