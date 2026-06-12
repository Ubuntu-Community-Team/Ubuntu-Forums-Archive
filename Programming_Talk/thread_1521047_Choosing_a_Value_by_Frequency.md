---
title: "Choosing a Value by Frequency"
date: 2010-06-30
forum: Programming Talk
---

### Post by DaGarver on 2010-06-30
First, some background. I'm doing research in bioinformatics, specifically in genetic sequencing and research. Right now, we're doing some random sequence generation to test out some scoring algorithms to help us find [promoters]("http://en.wikipedia.org/wiki/Promoter_%28biology%29"). I'm doing this in Python, and I have the frequencies for everything that I need. Right now, my code for choosing values is just a set of if ... elif ... else statements. Is there an easier way to choose values based on frequency or is my approach really the only sensible one?

Thanks for your time.

---

### Post by rrashkin on 2010-06-30
My guess is that it depends on how you have your data organized.  Without seeing your code it's hard to say but if you have lists of data organized by frequency, or a dictionary of lists of data keyed by frequency or some other organization, it should be possible to pull out what you want "unconditionally".

---

### Post by geoffjay on 2010-06-30
One way would be to put all of your data into some type of collection that supports sorting, eg. GLib's linked list has g_list_sort(...) which I guess in python would be list.sort(...)

EDIT: I may have misunderstood the question, if so disregard.

---

### Post by DaGarver on 2010-06-30
I got it figured out. Just threw my frequencies into a dictionary and iterated through the dictionary as necessary. Thanks for your time, though, guys. :)

---

### Post by PaulM1985 on 2010-06-30
If you are doing a random sequence and you want to find the most frequent number, have an array where each element is a number in the sequence.

Then do something like:

```

int[] sequenceStore = new int[10];

for (int i = 0; i < mySequence.length; i++)
{
    sequenceStore[mySequence[i]] = sequenceStore[mySequence[i]] + 1;
}

```

In sequenceStore you now have a count of each of the values.  (I know this is not python code, just an idea).  You then loop through sequenceStore and see which index has the highest value.

Paul

---

### Post by Some Penguin on 2010-06-30
Depending on the scale of the problem this can actually be fairly interesting.

If, for instance, you simply want a single extrema, and there are few enough events that you can easily fit counters for each of them in memory, it's hard to beat a straightforward count + linear scan of counters.

If you want the top-100 events out 10,000, well, counters will still trivially fit in memory, and after akk counting is done you iterate over the counters with a heap.  You then pull out 10 items from that heap.  This scales linearly (# of events observed) * log (# of distinct events observed).

If you want to be able to get top-K analysis *at any time* and then get more observations, you may want to instead have a data structure which maintains (1) a tree structure ordered by frequency, and (2) a map of event type to tree node.  This gets fairly complicated, but has probably already been done for you by many, many people because this isn't that wacky of an idea.

If you want the top-100 distinct events out of a billion possible events, and you have a hundred billion observations,  you're quite possibly in the land of Probably Approximately Correct algorithms unless you resort to long scans heavily bound by disk I/O.   "The space complexity of approximating the frequency moments" by Alon, Matias and Szegedy (STOC '96) would be a relevant read.

---

