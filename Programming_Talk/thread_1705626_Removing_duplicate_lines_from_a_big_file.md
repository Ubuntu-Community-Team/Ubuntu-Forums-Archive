---
title: "Removing duplicate lines from a big file?"
date: 2011-03-12
forum: Programming Talk
---

### Post by Ranko Kohime on 2011-03-12
I posted here in Programming Talk, because I don't think this is quite General discussion material.

Anyway, I have a VERY large text file I need to remove duplicate lines from.  By large, I mean 3.5 GIGAbytes.  That is not a misprint.

I tried to use TextWrangler on my Mac, but it choked on the file.  Splitting the file into 256mb chunks allowed TextWrangler to open it, but it still was unable to successfully process the duplicate lines.

So are there any Linux utilities which will remove the duplicate lines from a file larger than the installed system memory?  (My Ubuntu laptop has 1GB of RAM)

---

### Post by MadCow108 on 2011-03-12
sort -u should be able to handle it

---

### Post by n~kf)}BW% on 2011-03-12
If you don't want to sort the file, just use uniq...

```
cat oldfile.txt | uniq > newfile.txt
```

Don't be surprised if it takes relatively long though.

---

### Post by jon zendatta on 2011-03-12
try
```
sort file | uniq
```

---

### Post by wmcbrine on 2011-03-12
Of course the trouble is that uniq only gets duplicate lines that are adjacent. So, it's easy to remove adjacent duplicate lines, and it's also easy to remove non-adjacent duplicate lines, but it's harder to remove non-adjacent duplicate lines while preserving the original order of the text file.

Solutions for the latter in Python:

```
# If you have insane amounts of memory
lines = []
outfile = open('newfile.txt', 'w')
for line in file('oldfile.txt'):
    if line not in lines:
        lines.append(line)
        outfile.write(line)
outfile.close()
```

```
# If you don't
outfile = open('newfile.txt', 'w')
for line in file('oldfile.txt'):
    if line not in file('newfile.txt'):
        outfile.write(line)
        outfile.flush()
outfile.close()
```

I don't even want to think about how slow version 2 will be, and version 1 is bad enough. But if you're desperate enough, it should work.

---

### Post by Some Penguin on 2011-03-12
perl + DBM hashing (via Berkeley DB, say) + tied hashes would serve well enough.   Single pass, keep line and insert into hash if not already in tied hash, and it'd preserve order.

---

### Post by jon zendatta on 2011-03-12
> **wmcbrine said:**
> Of course the trouble is that uniq only gets duplicate lines that are adjacent. So, it's easy to remove adjacent duplicate lines, and it's also easy to remove non-adjacent duplicate lines, but it's harder to remove non-adjacent duplicate lines while preserving the original order of the text file.
Yes thats why you sort then pipe through uniq?Nice Python idea:KS

---

### Post by n~kf)}BW% on 2011-03-12
ZOMG, why are you reinventing the wheel in python? This feature well implemented in uniq program which is non-interpreted thus faster for this task. And the OP didin't ask for sort, so why loose time doing that?

---

### Post by shawnhcorey on 2011-03-12
> **Ranko Kohime said:**
> So are there any Linux utilities which will remove the duplicate lines from a file larger than the installed system memory?  (My Ubuntu laptop has 1GB of RAM)

Questions:

Is it important to preserve the ordering of the lines in the file?

If so, do you want to keep the first line of a set of duplicates or the last line?

---

### Post by MadCow108 on 2011-03-12
> **slovenia said:**
> If you don't want to sort the file, just use uniq...

```
cat oldfile.txt | uniq > newfile.txt
```

Don't be surprised if it takes relatively long though.
 ...
ZOMG, why are you reinventing the wheel in python? This feature well implemented in uniq program which is non-interpreted thus faster for this task. And the OP didin't ask for sort, so why loose time doing that?


uniq only operates on sorted files..

man uniq
> Filter **adjacent** matching lines from INPUT
Note:  'uniq'  does  not detect repeated lines unless they are adjacent.  You may want to sort the input first, or use `sort -u' without
       `uniq'.  Also, comparisons honor the rules specified by `LC_COLLATE'.

so either sort -u or sort file | uniq
the former is obviously more efficient

the python solution 1 will not work due to op's requirements and solution 2 will bin insanely slow.
if you want to reinvent sort, use a split and merge algorithm like sort does.

---

### Post by Ranko Kohime on 2011-03-12
> **shawnhcorey said:**
> Questions:

Is it important to preserve the ordering of the lines in the file?
No, I wouldn't mind if the file got sorted.

---

### Post by Ranko Kohime on 2011-03-12
> **MadCow108 said:**
> sort -u should be able to handle it
I tried this first on my Mac, since it has more hardware resources, and got the following error:

```
sort: string comparison failed: Illegal byte sequence
sort: Set LC_ALL='C' to work around the problem.
sort: The strings compared were `Omniprudent?' and `Omnip\346dia'.

```

It also failed on my Ubuntu machine, with an error that _/tmp_ ran out of space, which is correct, as _/tmp_ is a ramdisk.  (Out of necessity, SSD without ~4GB of free space)

---

### Post by MadCow108 on 2011-03-12
gnu sort does not understand unicode but you can use byte order sorting to archive the same effect:
LC_ALL='C' sort -u file


without enough harddisk space your problem cannot be solved so easily. you then need a in-place sort algorithm and I am not aware of a shell util which does that, you would have to write/copy-paste it yourself
if you have space somewhere try changing the tmp directory:
sort -T /some/dir -u file

btw here's Some Penguin nice solution with redis and python, but its also very slow (but can be optimized):
```
import redis
server = redis.Redis("localhost", port=6380)
f = open("tmp.txt", "r")
o = open("out.txt", "w")
for l in f:
  if not server.get(l):
    o.write(l)
    server.set(l, 1)
```

---

### Post by Shpongle on 2011-03-12
you could split the file , and compare the text in each file segment  against itself and then against the other segments . It would be a pain though but if would save memory. 

you could also try make a quick prog to loop the file , and string compare sequentially and remove duplicates.

---

### Post by Ranko Kohime on 2011-03-12
> **MadCow108 said:**
> without enough harddisk space your problem cannot be solved so easily. you then need a in-place sort algorithm and I am not aware of a shell util which does that, you would have to write/copy-paste it yourself
if you have space somewhere try changing the tmp directory:
sort -T /some/dir -u file
I should have mentioned, the Mac has more than 200GB of free space, it is the Ubuntu laptop which does not.  I can't believe that in the 4 times I read the --help for sort, that I somehow missed that parameter.  :oops:

Edit: The Ubuntu laptop is reading the file via SMB, so I'll try with the temp file on the network drives.

---

### Post by Some Penguin on 2011-03-12
> **Shpongle said:**
> you could split the file , and compare the text in each file segment  against itself and then against the other segments . It would be a pain though but if would save memory.

If the splitting always sends instance of the same line to the same segment (for instance, splitting by the first couple of characters from an MD5 hash of the line, which might be reasonably 'fair'; there may be simpler splitting methods but without knowing the nature of the content it's hard to say) then there'd be no need to compare between segments -- each could be processed individually and the results concatenated.

---

### Post by wmcbrine on 2011-03-13
slovenia and jon zendatta appear not to have understood what I wrote, while MadCow108 made a comment about "reinventing sort" that makes no sense, since the whole point of my code was to *avoid* sorting. But it's moot now, since the OP has said that sorted output is OK.

---

### Post by n~kf)}BW% on 2011-03-13
I apologise, i failed :D I'm glad you "sorted it out" though ;)

---

