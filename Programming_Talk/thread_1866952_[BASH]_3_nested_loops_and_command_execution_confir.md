---
title: "[BASH] 3 nested loops and command execution confirmation"
date: 2011-10-22
forum: Programming Talk
---

### Post by gianx80 on 2011-10-22
Hi to all! I'm a novice to bash programming and I'm studying for an university exam about it. I solved an exercise, but I have a problem.

In my script I have 3 nested loops like these:

```
cat $FILENAME | while read LINE
do
	cd $LINE
	ls -p -1 > $TEMPFILE
	cat $TEMPFILE | while read FILE
	do		
		cat $TEMPFILE | while read OTHERFILE
		do

			rm -i $FILE
		done
	done

done
```

in the inner loop I have a rm -i command. What is the problem? If I remove the -i option the script works well and files are removed. If I use the -i option (as asked inn the exercise) the script prints to terminal the confirmation messages but it doesn't let me answer yes or no and ends its execution without deleting files.

I've already asked on Italian Ubuntu forums but nobody could help me.

Please help me :(

---

### Post by ofnuts on 2011-10-22
> **gianx80 said:**
> Hi to all! I'm a novice to bash programming and I'm studying for an university exam about it. I solved an exercise, but I have a problem.

In my script I have 3 nested loops like these:

```
cat $FILENAME | while read LINE
do
    cd $LINE
    ls -p -1 > $TEMPFILE
    cat $TEMPFILE | while read FILE
    do        
        cat $TEMPFILE | while read OTHERFILE
        do

            rm -i $FILE
        done
    done

done
```in the inner loop I have a rm -i command. What is the problem? If I remove the -i option the script works well and files are removed. If I use the -i option (as asked inn the exercise) the script prints to terminal the confirmation messages but it doesn't let me answer yes or no and ends its execution without deleting files.

I've already asked on Italian Ubuntu forums but nobody could help me.

Please help me :(I suspect an interaction between the while read and the input. Did you try something like
```

for $f in $(cat $otherfile)
do
 rm -i $f
done

```

---

### Post by sisco311 on 2011-10-22
@ofnuts

See: BashPitfalls #1 (link in my signature) and [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)


@gianx80

Check out: 
[http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)
[http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)
BashFAQ #1 , #20  and #89 (link in my sig)
BashPitfalls #2
and
[http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)

A pipe basically connects the stdout of one process to the stdin of another, effectively piping the data from one process into another.

In our case, | pipes the output of cat into the while loop. By default, both read and rm -i read from stdin. So, read reads the first line from the file, then rm -i reads the rest.

Did you learn about globs? What will */*/* match? 

Hmmm, I think I solved your homework...

---

