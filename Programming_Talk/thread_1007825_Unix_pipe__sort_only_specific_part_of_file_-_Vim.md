---
title: "Unix pipe / sort only specific part of file - Vim?"
date: 2008-12-10
forum: Programming Talk
---

### Post by pieoncar on 2008-12-10
I'm having some trouble figuring out exactly how to sort only a specific range of text in a file.  Specifically, in a .eps file I have many repeated points in a graph, to the point where it takes an uncomfortable amount of time to render the graph (and it must remain in .eps or otherwise scalable format).  

I'd like to do something along the lines of

```
cat (first part of file) ( (ugly data part | sort -u) ) (rest of file) > new_file.eps
```

I can grep out only the ugly data, or only the clean parts, but it's necessary to have the first clean part before the ugly part, followed by the last clean part.  I'm not sure how to ensure that separation, it might be a simple grep option that I'm not aware of.

Alternatively, and this would probably be a little better/easier for me, is there a way in Vim to highlight all of the text I want to change, then use that as stdin to `sort -u` and replace the highlighted region with the stdout of `sort -u`?

Some of these files are up to 2.5MB, so it's important that I can automate as much as possible here.

Hopefully that was a little more clear than it looks now.  Any ideas?  I do plan on thanking the correct answer.

---

### Post by ghostdog74 on 2008-12-10
provide a sample of your eps file and describe the output needed clearly

---

### Post by cdtech on 2008-12-10
As ghostdog74 said it's almost impossible to know what to "grep" if you don't have a char to go by.

---

### Post by pieoncar on 2008-12-10
This is one of the smaller input files, and the corresponding output was done by cutting and pasting by hand.

The .eps file has many <coord coord Crs> lines, and many of these are duplicates - this particular input file has I think 369 lines' worth, and the output file has 255 after piping through `sort -u`.

Both files appear exactly the same, except output.txt didn't double (triple, quadruple, whatever) render the crosses.

Had to tarball to fit in the file extension size.

---

### Post by pieoncar on 2008-12-10
> **cdtech said:**
> As ghostdog74 said it's almost impossible to know what to "grep" if you don't have a char to go by.

Grepping isn't the problem - the data that needs to be uniq'ed is all in one chunk, but how do I *not* sort the parts before and after that chunk, and insert the sorted data in between those chunks in a new file?

---

### Post by pieoncar on 2008-12-10
Here's the ugly little script that gets the job done... Not the way I'd like to do things at all, but it produced the same output as I made by hand.

```

#!/bin/sh

TOTAL_LINES=`cat $1 | wc -l`

OUTFILE="$1.out"

head -n $((`grep -n "Crs$" $1 | head -n1 | cut -d: -f1`-1)) $1 > $OUTFILE

grep "Crs$" $1 | sort -u >> $OUTFILE

tail -n $(($TOTAL_LINES-`grep -n "Crs$" $1 | tail -n1 | cut -d: -f1`)) $1 >> $OUTFILE


```

---

### Post by cdtech on 2008-12-10
I was going to suggest the "uniq" command but that removes all duplicate entries:
```
uniq  ~/input.txt ~/output.txt
```

---

### Post by pieoncar on 2008-12-10
> **cdtech said:**
> I was going to suggest the "uniq" command but that removes all duplicate entries:
```
uniq  ~/input.txt ~/output.txt
```

Yeah, and it only removes duplicate, sequential entries, i.e.
```

foo
bar
bar
bar
foo

```
would become
```

foo
bar
foo

```
which is why you usually do `sort | uniq`; and finally someone just made a `sort -u` option which does the same thing.

The stripped files render MUCH more quickly now, if anyone was interested.

---

### Post by geirha on 2008-12-11
The way to do this in vim is to first mark all the lines to be sorted with visual mode (shift+v), then do ```
:!sort -u
```

In this case, go to the first entry by searching for the first line ending with Crs$, hit V then search for the first line not ending with an s

```
:0
/Crs$
V/[^s]$
k:!sort -u

```

---

