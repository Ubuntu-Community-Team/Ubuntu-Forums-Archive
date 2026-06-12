---
title: "sorting by # of 'hits'"
date: 2008-05-15
forum: Programming Talk
---

### Post by sdobbers on 2008-05-15
Hey guys,

I'm pretty new to programming in Python (and well programming in general...did it a few years back, but just getting back into it).  I have a question about this program I'm working on, and was hoping you guys might be able to give me a nudge in the right direction.

A little background on the program.  I'm creating a code library, so that when I find bits of code online I can put them into a file of mine.  I add a title, some title keywords (...redundant, but at the time for some reason it didn't cross my mind to just search the title directly...), and some keywords that tell us what the program does.  Then I have a little menu that asks whether you want to search by title, or keyword.  Once you preform the search, it spits out a list of Titles that matched...then you type in the number and out pops the code snippet.

Ideally, what I'd like to do is sort it by the one that got the most 'hits'.  Right now it's just in a random order...which isn't a problem at the moment considering I only have a total of 9 unrelated code snippets.  However, once my library grows it will become a problem.

Now what I've thought about doing is, counting the number of hits in the "found list" and assigning it to a dictionary of {title:# of hits}.  From here, is there any way to sort by value instead of key?  If not, is there a more efficient way to go about this?

Thanks in advance,
Sean

---

### Post by Wybiral on 2008-05-15
Yes, the sort method for lists allows you to pass a comparison function, so you can just pass a lambda or something to sort it however you want to.

```

x = [(4, "c"), (1, "b"), (3, "a"), (2, "d")]
x.sort(lambda a, b: cmp(a[0], b[0])
print x
x.sort(lambda a, b: cmp(a[1], b[1])
print x

```

---

### Post by pmasiar on 2008-05-16
Interesting idea for a program. It might be good for training task, but in real use I would approach it differently.

Wiki is convenient way to create page with links to other web resources (and comments about the links). You can get free wiki hosting at many places, I use pbwiki.com, see my sig.

There are already many resources like that, one of the most popular is [http://aspn.activestate.com/ASPN/Python/Cookbook/](http://aspn.activestate.com/ASPN/Python/Cookbook/)

BTW next time at least put [Python] in title of your post, you may get more responses. Read 'how to ask questions smart way' in my sig.

---

### Post by LaRoza on 2008-05-16
> **pmasiar said:**
> 
Wiki is convenient way to create page with links to other web resources (and comments about the links). You can get free wiki hosting at many places, I use pbwiki.com, see my sig.

pbwiki 2.0 is very bad IMO. I recommend using the original version if you can, or using wikidot.com.

---

### Post by ghostdog74 on 2008-05-16
for Python 2.4 and later, sort has the key parameter
```

import operator
x = [(4, "c"), (1, "b"), (3, "a"), (2, "d")]
print sorted(x, key=operator.itemgetter(0))

```

---

