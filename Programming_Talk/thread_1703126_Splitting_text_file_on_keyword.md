---
title: "Splitting text file on keyword"
date: 2011-03-08
forum: Programming Talk
---

### Post by igfud on 2011-03-08
I am have a bunch of text file assignments all in the same format of:

```
Problem 1:
(varying number of lines of text)
Problem 2:
(varying number of lines of text)
.....
Problem 20:
(varying number of lines of text)
```

I want to iteratively look at/edit all the "Problem 1"s, then all the "Problem 2"s, etc (so I can grade one problem at a time). I thought the easiest way to do this might be to parse each file into 20 smaller files, each containing one problem, and iterate through them with a loop in a bash script such as:

```
for i in `ls *.txt`; do
vim $i
done
```

Once I was done with all the edits, I could rebuild all the files with two nested loops such as:

```

for j in `seq 1 40`; do
for i in `seq 1 20`; do
cat problem$i_test$j.txt >> $j_final.txt
done
done

```

I'm not sure this is the best way to go about this (if you have a better idea, please let me know!), but how might one go about splicing a file containing blocks of text into 20 smaller files, each with one of the problems? I've been messing around with some regular expressions and sed, but no luck.

Thanks,
igfud

---

### Post by ve4cib on 2011-03-09
In rough pseudo-code:
```

# open 20 files, storing the handles in an array
outputFiles = [q1.txt, q2.txt, q3.txt, ..., q20.txt]

foreach file f in inputFiles {
    open f for reading
    for i = 1 to 20 {
        outputFiles[i].write(getQuestion(i,f))
    }
}

close(outputFiles)

```

getQuestion(i,f) simply reads file f and returns the string corresponding to the answer to question i.

Something like that would probably be the easiest way of going about it.  Obviously you could optimize things a bit, but I think having 20 file pointers (or a single pointer that you re-use, opening each output file in append mode), and looping through each input file is probably the most realistic way of doing what you want.

You could probably do this pretty easily in Python or Perl.

---

### Post by kaibob on 2011-03-09
> **igfud said:**
> I'm not sure this is the best way to go about this (if you have a better idea, please let me know!), but how might one go about splicing a file containing blocks of text into 20 smaller files, each with one of the problems? I've been messing around with some regular expressions and sed, but no luck.

Thanks,
igfud
You may want to have a look at the csplit utility, which  divides a text file into sections based on a specified pattern. By default, the newly created files are named xx00, xx01, xx02, and so on. There are many useful options as explained in the man page. 

A very simple example of the command itself is:

```
csplit file '/^Problem/' '{*}'
```

To process multiple files, the above command could easily be included in a loop.

---

