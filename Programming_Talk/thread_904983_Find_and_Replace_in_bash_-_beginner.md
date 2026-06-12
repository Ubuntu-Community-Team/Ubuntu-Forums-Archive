---
title: "Find and Replace in bash - beginner"
date: 2008-08-29
forum: Programming Talk
---

### Post by BLo on 2008-08-29
Hi,

I have a bash script and I want it to find and replace text in a file. I know I can use sed to go something like 

```
 sed 's/foo/bar/'   
```



But what I want to actually do is find the search string from the beginning of the line and replace the whole line, not just the search string.

Basically I want to update lines in a file if it already exists otherwise I'm just going to append to the end of the file.

Any help is much appreciated

---

### Post by monkeyking on 2008-08-29
Can you elaborate a little on what you would to do.

If I understand correctly, you have an ID, on each line followed by something else.

So when you run your script, you have you ID and the data you want to add.

if the ID exists, you want to replace the line, otherwise append it to the end of the file?

If this is correct I would do it in the following dirty way.

grep the ID, if it doesn't show up, append it with the >> operator
if it exist, find out which line it is in with grep -n.
then take the first part of the file with 
head -nLINENUM-1 > outfile
cat YOURDATA >>outfile
tail -nLINENUM+1 >> outfile
delete the original.

---

### Post by ghostdog74 on 2008-08-29
the best is to provide sample input files that you want to change, and show your expected output results.

---

### Post by BLo on 2008-08-30
monkeyking thanks, that should work for what im after. I didnt think of cutting out the top half of the file then cutting out the bottom

Basically yes each line starts with an identifier, followed by other data related to that user seperated by spaces. 

identifier data data data 
101 exampledata moresampledata 102sampledata
102 exampledata moresampledata data

The problem is though the identifier might show up in the data so my understanding is if I grep 102 both lines will show. But each Identifier should be unique.

---

### Post by ghostdog74 on 2008-08-30
if that's the case, this might do
```

awk '$1==102{print "This is replaced line";next }1' file > temp
mv temp file

```

---

