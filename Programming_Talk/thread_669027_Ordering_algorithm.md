---
title: "Ordering algorithm"
date: 2008-01-16
forum: Programming Talk
---

### Post by Erdaron on 2008-01-16
I'm working on a script to help me organize and analyze some data. Well, there's a lot of it. 185,000 lines in 5 columns. It's time-dependent, but the time scale is out of order, so I need to put it back into order.

I've actually already written a script to do this, but it's quite slow, and was wondering if there are faster algorithms out there. I'm kind of new to programming, don't know many tricks.

The problem is basically this. I have a long list of unordered numbers, and I need to put them in, say, ascending order.

Here's the algorithm I've come up with:

```
Name given list A.
Find smallest number in A, call it y.
Put y in a new list, called B.
Delete y from A.
Repeat.

To find the smallest number in A:
Let y = A(0)
If y > A(1), let y = A(1)
If y > A(2), let y = A(2)
Like that until A runs out.
```

I also came up with another, more convoluted algorithm (though it is as efficient):

```
Compare A(0) to A(1)
If A(0) > A(1), exchange them
Compare A(1) to A(2)
If A(1) > A(2), exchange them
...
Repeat, but this time only consider the first N - #iterations numbers (since the biggest number will be pushed to the end by the first iteration, and so forth).
```

Both cases require N*(N-1) / 2 compares.

Oh, and so far I've been working in Python. Would doing this in C++ speed this up any?

---

### Post by Erdaron on 2008-01-16
I just calculated the number of comparisons required for my data - approximately 1.7E10.

I'm doomed.

---

### Post by RIchard James13 on 2008-01-16
What you seem to need is a good sorting algorithm. There are quite a few out there. You can see the common ones on the following page.
[http://en.wikipedia.org/wiki/Sorting_algorithm]("http://en.wikipedia.org/wiki/Sorting_algorithm")

I personally would try quicksort and move from python to c++.

I think your second example is bubble sort. Don't know what your first is maybe bucket?

---

### Post by Erdaron on 2008-01-16
I think my first choice is a selection sort.

Actually, from those listed on the page, merge sort sounds like the best idea for my case. My data is actually several ordered sets stacked on top of each other - so that's perfect!

I haven't touched C++ in years, and am kind of wary of it right now. I definitely want to learn it again, though.

---

### Post by CptPicard on 2008-01-16
Just thought to quickly congratulate you for coming up with bubble sort on your own... it's the less obvious of the sorting algorithms that people usually "invent". And yes, mergesort sounds like what you need. If your data isn't composed of segments that are exactly in order (say, they are "almost in order"), look at insertion sort.

---

### Post by ghostdog74 on 2008-01-16
> **Erdaron said:**
> I'm working on a script to help me organize and analyze some data. Well, there's a lot of it. 185,000 lines in 5 columns.
...
Oh, and so far I've been working in Python. Would doing this in C++ speed this up any?

A lot depends on how you code your program and whether you are using the "best" method. and 185000 lines should not be a problem. How does your data look like. post a few lines if you want.

---

### Post by Arndt on 2008-01-16
> **Erdaron said:**
> I'm working on a script to help me organize and analyze some data. Well, there's a lot of it. 185,000 lines in 5 columns. It's time-dependent, but the time scale is out of order, so I need to put it back into order.

I've actually already written a script to do this, but it's quite slow, and was wondering if there are faster algorithms out there. I'm kind of new to programming, don't know many tricks.


Do you need to program it yourself? Can you put the program 'sort' to use?

---

### Post by Erdaron on 2008-01-16
> **CptPicard said:**
> Just thought to quickly congratulate you for coming up with bubble sort on your own... it's the less obvious of the sorting algorithms that people usually "invent". And yes, mergesort sounds like what you need. If your data isn't composed of segments that are exactly in order (say, they are "almost in order"), look at insertion sort.
Thank you!

Also, it's very comforting when you think you've designed something clever, and then find out someone already did it fifty years ago :).

[QUOTE=ghostdog74]A lot depends on how you code your program and whether you are using the "best" method. and 185000 lines should not be a problem. How does your data look like. post a few lines if you want.[/QUOTE]

Apparently 185000 lines *is* a problem if you're using the wrong method :D. Or Excel, which can't handle more than 2^16 lines.

One set of data might look like this:

-0.1 / 0.123 / 0.145 / 0.566 / 0.222
-0.05 / 0.122 / 0.150 / 0.561 / 0.222
0 / 0.100 / 0.050 / 0.600 / 0.222
+0.05 / 0.100 / 0.060 / 0.598 / 0.225
+0.1 / 0.102 / 0.070 / 0.597 / 0.221

(Just imagine forward slashes are tabs.)

The first column is time, other columns are readings from four different sensors. There are six sets, each taken on a different time scale - they all have zero, but sampling frequency is different. I need to make them together into one massive set. 

[QUOTE=Arndt]Do you need to program it yourself? Can you put the program 'sort' to use?[/QUOTE]

I would prefer to program it myself. I'm using this as an opportunity to learn programming. In the future, I may need to write much more complicated analysis code, so this is good practice.

---

### Post by pjkoczan on 2008-01-16
If you understand recursion well enough, you should use mergesort or quicksort. Those have average complexity on the order of n*log(n) (base 2 logarithm, which works itself out to a few million comparisons in your data set, something that could easily be done in a few seconds on a modern processor.

If you really want to go nuts, go with shellsort or hashsort, but I wouldn't recommend those unless you're really bored.

---

### Post by aks44 on 2008-01-16
AFAIK [introsort]("http://en.wikipedia.org/wiki/Introsort") (a mix of quicksort and heapsort) is the most efficient sorting algorithm ATM (for the general case). On average the complexity is the same as quicksort, but its worst case is less expensive than quicksort's worst case. Most C++ STL implementations use it now (std::sort).

Of course if your data is arranged into identifiable patterns you'll be better off taking advantage of them, and choose the algorithm accordingly.

---

### Post by popch on 2008-01-16
Having seen your sample data, some thoughts:

There are some 200'000 tuples. How many different timestamps are there? If the ratio of tuples to timestamps is significantly greater than one, sorting unique timestamps and then collating with tuples might be faster.

The ordering of the sample data suggests that there might be an underlying order to the tuples. If there are longish sequences of chronologically sorted tuples, then sorting might not be the best strategy. Instead, merging the partial sequences into one master sequence could be much more efficient.

---

### Post by popch on 2008-01-16
On second thought, why not import the whole set into a database? Using plain SQL, you can build subsets, project fields and much more, and all sorted any which way. That's what databases are good at, much better than you or I willl ever get.

Yes, you have said that you preferred programming it. Perhaps you might consider inventing another wheel.

---

### Post by evymetal on 2008-01-16
> **popch said:**
> 
Yes, you have said that you preferred programming it. Perhaps you might consider inventing another wheel.

But sometimes you have to... once you get enough data and you want to parallelise it across machines. (I love those problems... :-) )

---

### Post by pmasiar on 2008-01-16
Looks like too much data to store all in RAM, right?
I suggest storing all data in SQLite table, and use SQL to get any of them in any order. 

Do you have some time limits for processing it? I mean, the more time you have to process it, the more lazy you can get, and the more you can let computer do for you.

---

### Post by popch on 2008-01-16
> **pmasiar said:**
> Looks like too much data to store all in RAM, right?

At the moment, we are talking about something in the order of  200*32*10**3 Bytes = 6.4MB or less. That would fit nicely into RAM.

---

### Post by dwblas on 2008-01-16
> My data is actually several ordered sets stacked on top of each otherIn which case you would use a merge sort, but the question is what container to you use to store and sort.  The container would be a list of lists or a dictionary of lists.  If you use a dictionary of lists then there is no need to sort, but approximately 200,000 recs might be time consuming.  I would suggest starting with all 200,000 in a list of lists and time it using the_list.sort().  Python's sort algorithm is pretty efficient.  Then use a loop to sort a list of say every 1000 recs and merge with the list of previously sorted recs into a 3rd list. Next, time it using a dictionary.  If none of the times is acceptable, then SQLite would be the next option.

---

### Post by CptPicard on 2008-01-16
> **dwblas said:**
> In which case you would use a merge sort, but the question is what container to you use to store and sort.

An array, with the sorted subsets one after the other all in the same list. You can do a mergesort in place like that without complex time-consuming containers. EDIT: whoops, no you can't. Forgot about mergesort's requirement of auxiliary space. But still it's important to make sure you keep implementation memory-efficient...

---

### Post by Erdaron on 2008-01-16
I'm currently thinking like this.

Data is stored in six different files, each one an ordered list.
[LIST=1]
[*]Start with two empty lists, list1 and list2.
[*]Load a file, read into list2.
[*]Send both lists to merge-sorting function.
[*]Take its output, make it list1.
[*]Go to step 2.
[/LIST]

This should work, right?

EDIT: I don't know anything about SQL. It may, in fact, be faster, but I'd have to learn a whole new system. But I'll put it on the list for future exploration.

---

### Post by dwblas on 2008-01-16
Your idea with a slight revision.  You are probably already assuming that you would do this.

Data is stored in six different files, each one an ordered list.
   1. Start with two empty lists, list1 and list2.
   2. Load a file, read into list2 -->  and sort list2 - I wouldn't assume ordered
   3. Send both lists to merge-sorting function.
   4. Take its output, make it list1.  That is
        list1=sort_merge(list1, list2)
        i.e function returns list3 = list1 & list2 combined
        copying the returned list to list1 is a waste of time
   5. Go to step 2.

That should work.  Note that it is faster to divide 100,000 recs into 100 sorts of 1000 each, instead of sorting 100,000 recs.  The optimum number of sorts depends on processor and disk speed.  You can also group your data first if you know the range, so that one-tenth or whatever of the data is in each list
     list1 = -1-->0
     list2 = 0-->1 etc
But the idea you have should work ok.  The problem with the first idea is that you were swapping every time you found a lower record.  You should go through the whole list and find the record with the lowest key and then swap that record once.

BTW, if you want to try SQLite (you can use it in memory as well as on disk), post back for suggestions.

---

### Post by Erdaron on 2008-01-16
@dwblas - files come pre-sorted, so that's not a problem. Output of sort_merge is fed directly into list1. I had a bad habit of using lots of intermediate variables, but I'm getting better at it.

Also, not all data sets were equal. One with 120000 lines, four with 15000, and one with 5000 (I don't control data recording, so I don't know why that is). I started by merging smallest files first, which works a lot better. Just for kicks, I made a variable to keep track of how many comparisions were made. 230,853, and the whole thing took a little more than a minute to sort.

This brings up a question. My computer is 1.5GHz Celeron M with 1.25 gigs of RAM. What takes so long? It seems like the machine should breeze through this in a few seconds.

---

### Post by mathisdermaler on 2008-01-16
For a set of records that easily fits in ram, just load them all into a python list (concatenate multiple lists together if necessary).

Example:

```

list1 = [(-0.1, 0.123 , 0.145 , 0.566 , 0.222), 
    (-0.05 , 0.122 , 0.150 , 0.561 , 0.222)]

list2 = [(0 , 0.100 , 0.050 , 0.600 , 0.222),
(+0.05 , 0.100 , 0.060 , 0.598 , 0.225),
(+0.1 , 0.102 , 0.070 , 0.597 , 0.221)]

l = list1 + list2   # concatenate all lists together
l.sort(lambda x, y: cmp(x[0], y[0])) # sort by first column
for i in l:
    print i

```

Sorting 200,000 records by this method takes 6 seconds on my machine.  Probably the built-in python sort is written in C so it's faster than any sort that can be written in python itself.

---

### Post by slavik on 2008-01-17
what about python's dictionary? (if I understand python, its dictionaries are perl's hashes).

also, look into heapsort :) (always nlogn :))

---

### Post by popch on 2008-01-17
> **Erdaron said:**
> I'm currently thinking like this.

Data is stored in six different files, each one an ordered list.[LIST=1]
[*]Start with two empty lists, list1 and list2.
[*]Load a file, read into list2.
[*]Send both lists to merge-sorting function.
[*]Take its output, make it list1.
[*]Go to step 2.[/LIST]This should work, right? (...) 

If all of the data is in just six files, each of them already ordered in the required sequence (ascending by time stamp), then you need not a sorting algorithm but a merging algorithm, and that's orders of magnitude simpler to do.
[LIST]
[*]Open all six input streams
[*]fetch and buffer one row from each input stream
[*]repeat until all data is written[LIST]
[*]find the input stream with the smallest time stamp; if there is more than one with the same time stamp, take the first one encountered
[*]copy the row of the selected input stream to the output stream[/LIST][LIST]
[*]fetch and buffer the next row of the selected input stream[/LIST] [/LIST]For R rows (tuples) in S input streams, the number of comparisons to be done is =< R*(S-1). That's the maximal number, and it applies to the case when the maximum time stamp occurs in each and every stream, i.e. if all streams are open and being read from until the very end of the merging procedure.

Take care to convert the time stamp to a reasonable number format immediately upon fetching each row; otherwise you could keep on converting strings to numbers for each individual comparison.


'Streams' could be files on disk or some arbitrary structures in RAM.

---

### Post by Arndt on 2008-01-18
> **pjkoczan said:**
> If you understand recursion well enough, you should use mergesort or quicksort. Those have average complexity on the order of n*log(n) (base 2 logarithm, which works itself out to a few million comparisons in your data set, something that could easily be done in a few seconds on a modern processor.



If the choice is between quicksort and mergesort, always use mergesort. Quicksort isn't stable; mergesort is.
There are too many table displays out there that use unstable sorting algorithms.

---

### Post by jblebrun on 2008-01-18
Here's a silly alternate solution, showing how you can use the filesystem as a bare-bones DB. :-)

Go through the list, and save each line as a file, where the filename is the timestamp. If the file exists already, append the line to the existing file.

Then just do:

for i in `ls -C1`; do cat $i >> sorted_data; done

---

### Post by Erdaron on 2008-01-18
Thank you all for so much help! It's also interesting how many different solutions have been offered. I never understood why in python community there's supposedly the idea that there is only one right way to do a thing.

Can someone explain to me how the sort() method works? Specifically the optional arguments. How does that sequence of arguments make it sort by first column? I'm a newbie.

I think I understand what cmp does. What does lambda do?

I tried it out with simple lists, and it is wicked fast, at least compared to other, python-scripted methods I've tried.

---

### Post by mathisdermaler on 2008-01-20
> **Erdaron said:**
> 

Can someone explain to me how the sort() method works? Specifically the optional arguments. How does that sequence of arguments make it sort by first column? I'm a newbie.

I think I understand what cmp does. What does lambda do?



The optional argument to .sort() is a function that tells .sort() how to determine which of two items in the list is greater.  The .sort() method will call the function multiple times with different pairs of items to determine how to sort each pair of items.  The comparison function takes two arguments and returns < 0 if the first is less, 0 if the elements are equal, and > 0 if the first is greater.

l.sort() is the same as l.sort(cmp) 

cmp is defined like this (or equivalent code):
```
def cmp(a, b):
  if a < b:
    return -1
  if a > b:
    return 1
  return 0
```

What's a lambda?  A lambda is basically an inline function.  I could write it like this without using lambda:

```
def compare_by_first_column(a, b):
  return cmp(a[0], b[0])

l.sort(compare_by_first_column)
```

By using "cmp(a[0], b[0])" in place of "cmp(a, b)", it causes the .sort() method to sort by the first member of the tuple.  (first column)

Just a quick example: if you wanted to sort case-insensitively on the third column, you would say:

```
l.sort( lambda x, y: cmp(x[2].upper(), y[2].upper()) )
```

---

