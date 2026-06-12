---
title: "Is this possible?"
date: 2015-06-08
forum: Programming Talk
---

### Post by slooksterpsv on 2015-06-08
Lets say I have two files - text files with names of fruits and vegetables - like so:

Apple
Banana
Carrot
Orange
...

so lets say the first file has 100 items, the second file has 50. Following so far?

How the heck could you merge those two files (lets say they're already sorted), but you can only read one file and 1 line from said at a time - can't open both of them. I've been racking my brain trying to think through this, but I don't know. There isn't a distinct pattern, and the only way I can think of doing it is either by:

1) Adding the sum of the first three letters as integers
2) Comparing one to the other
3) Merge.

But that doesn't work if I have like:

AAB
ABA

as those could be seen as equal. I can only read 1 line from 1 file only. I can't read 1 line from each file. I'm lost on how to think through this. Any tips? I don't want the code or answer, I want help thinking through it.

Hmm....

---

### Post by TheFu on 2015-06-08
```
cat A B | sort > /tmp/output
```

or
```

cat A B | sort | uniq > /tmp/output
```
if you can't have duplicates.

I suppose if you must use a programming language, I'd use perl and read each file into an array, then concat those arrays together, then sort them.  About 5 lines of perl, if I'm not too stingy with the CR. Most languages have a sort method for any array/string classes. No need to over think this - especially for any files with fewer than 100K lines.  Of course, if you have 100K lines per second coming in (and many places do), then the problem becomes harder.

---

### Post by pfeiffep on 2015-06-08
I believe that a -u option on the sort will eliminate duplicates.

---

### Post by TheFu on 2015-06-08
> **pfeiffep said:**
> I believe that a -u option on the sort will eliminate duplicates.

According to my Linux manpage, you are correct sir.
Linux sort isn't the same as Solaris, HP-UX, AIX, BSD sort versions which may not have that option. 

With all that said, I'd use the -u option, if I didn't need the script to be portable to UNIX systems. Reducing an extra pipe and process makes complete sense.

BTW, I learned that Linux sort has a -h option .... which is good to sort G, M, K, sizes. It is one of my favorite new options in sort.

```
du -hs /*  |sort -rh |more
``` Very handy to see which directory is sucking all the storage.

---

### Post by slooksterpsv on 2015-06-09
Here's the stickler, you can't use arrays, you can only read 1 line from 1 file at a time. Maybe the person is wanting me to utilize an external command. I'm not sure.

---

### Post by TheFu on 2015-06-09
Why no arrays? That wasn't in the initial problem statement. Arrays are a basic data structure in every language.

---

### Post by ofnuts on 2015-06-09
Define "read one line at a time". Does this mean that you can have only one line from all files in memory at a given time?

---

### Post by trent.josephsen on 2015-06-09
Agreed, the problem statement is too vague. What are you asking about exactly? Your question appears to be about merging two files but the partial solution you propose is just an algorithm (albeit incorrect) for comparing two strings. (Almost every language has built-in capability to compare two strings, so I guess I'm missing something here.)

Does the language matter? Also, does "no arrays" mean no lists, no hashtables, no sets, no trees, no records... or just no arrays?

---

### Post by TheFu on 2015-06-09
> **trent.josephsen said:**
> Does the language matter? Also, does "no arrays" mean no lists, no hashtables, no sets, no trees, no records... or just no arrays?

Could we just shove all the data into a DB table and have the DB sort it?

Last time I had to write a set of sort routines was 1983. What we learned was that out of the 5 different routines that we wrote, the built-in sorting for the language was smarter, faster, and used less memory. It was a good lesson and has served me well all these years.

---

