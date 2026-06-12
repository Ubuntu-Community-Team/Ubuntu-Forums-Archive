---
title: "Simple(?) command line / shell script problem"
date: 2007-08-23
forum: Programming Talk
---

### Post by fedira on 2007-08-23
This seems like a simple thing, and for some reason I'm stuck.

I have two lists of files, list1.txt and list2.txt.
Each list has one filename per line.

I want to do: 
For each file in list2.txt, check if it's in list1.txt.
If there's a match, return the file name.

Is there some way I could do something like:
cat list1.txt | grep `one line at a time from list2.txt`

I have no idea if grep is flexible enough to do something like this, but I do know that it's possible to use it in ways more complicated than I know.

Or is using find a better option? The files listed in list2.txt also exist in a directory (with many subdirectories & other files, but can probably be filtered based on their unique extension).

Hopefully someone can help me figure this out! It seems simple, and I feel quite dumb for not being able to come up with a solution.

Thanks for your help!

---

### Post by s1ightcrazed on 2007-08-23
Without giving it too much thought:

You will want to do 2 loops, one nested inside the other. 

the first for loop with read the first file, line by line, the second for loop will then read each line in the second file, and see if it matches the line read from the first file. If it does match, then you could write that out to a third file. 

I can show you actual code to do this, but I'm hoping the theory will be enough to get you started (doing it yourself is, of course, the best way to learn).

---

### Post by lloyd_b on 2007-08-23
Here's a simple shell script that I think does what you want.  I call it "lookup":
```
#!/bin/bash
#
# Usage: lookup [file1] [file2]
#
FILE1=`cat $1`

for CURLINE in $FILE1; do
        grep "$CURLINE" $2
done
```

Explanation:  Get the contents of the first command line parameter ([file1]) into a shell variable called FILE1.  Then loop through this list one item at a time, and execute a grep to see if that item appears in the file specified by the second command line parameter ([file2]).

A couple of "gotchas":  
First, this script does not input validation, so if you give it a garbage file name, you'll get garbage results.  

Second, because of the way the "do" loop operates, there will be problems if any of the items in FILE1 have spaces in them (spaces in filenames, in your situation). 

Lloyd B.

---

### Post by kebes on 2007-08-23
If the two files with lists don't have duplicate lines, then this should work:

```

cat file1.txt file2.txt | sort | uniq -d

```

(Takes the contents of both files, sorts it, and looks for duplicate lines.)

If the file listings contain internal duplicates, then you just use "sort" and "uniq" on each file separately first, to get rid of duplicates. Something like:

```

cat file1.txt | sort | uniq > tmp1.txt
cat file2.txt | sort | uniq > tmp2.txt
cat tmp1.txt tmp2.txt | sort | uniq -d

```

---

### Post by fedira on 2007-08-23
Thanks for all of the helpful replies!

I think Kebes's solution is exactly what I was looking for (perfect, really), but I learned from the other suggestions as well, so thank you. 

I'm just starting out, so thanks for the patience and the help!

Also, just a follow-up question, since "uniq" is new to me (see, I told you I was a novice). Is uniq *without any flags* the same as sort -u?

---

### Post by kebes on 2007-08-23
> **fedira said:**
> Is uniq *without any flags* the same as sort -u?

Yes, you're right: "sort -u" and "uniq" do the same thing. (But "uniq -d" shows only the duplicates... I don't know of a way to do that with "sort".)

---

