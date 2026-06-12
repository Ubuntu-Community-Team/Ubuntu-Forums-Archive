---
title: "Search inside files - complex logic"
date: 2015-12-30
forum: Programming Talk
---

### Post by getut on 2015-12-30
I think I need to be using regex within grep for this, but I need to search some very large folder structures for all files with contents matching search terms similar to these:

pseudo code

(bunny OR rabbit) AND (jumps OR hops OR flies)

(Sammy) within 3 words of (Van OR Halen)

Preferably searching all variants at the same time:

((bunny OR rabbit) AND (jumps OR hops OR flies)) OR ((Sammy) within 3 words of (Van OR Halen)) OR ..... you get the idea

Even greatly simplified, I'm having trouble getting anything like an AND to work at all, especially combined with the OR's.

---

### Post by SeijiSensei on 2015-12-31
You can use egrep (or "grep -E") for ORs and pipes for ANDs like this:

```
egrep 'bunny|rabbit' < somefile | egrep 'jumps|hops|flies'
```

That will return lines in the file "somefile" containing "bunny" or "rabbit" and also "jumps" or "hops" or "flies".  

You could pass a directory listing like this:

```
ls -lR | egrep 'bunny|rabbit' | egrep 'jumps|hops|flies'
```

The vertical bar has two different meanings here.  Within an extended regex expression it means OR.  At the operating system level it acts as a "pipe" which takes the left clause as input to the second egrep expression thus creating an AND.

If you want to search within the files, you'll probably need some form of for loop:
```

for f in *
do
    echo "File: $f"
    egrep 'bunny|rabbit' < $f | egrep 'jumps|hops|flies'
done

```
I can't think of a way to do "within three words."  Some more powerful search engines like [Sphinx]("http://www.sphinxsearch.com/") can do that, I believe, but you'd need to build an SQL database containing all the files' contents and indexing that.

---

