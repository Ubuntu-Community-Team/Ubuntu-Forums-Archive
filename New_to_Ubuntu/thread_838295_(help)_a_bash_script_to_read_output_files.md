---
title: "(help) a bash script to read output files"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by leptons on 2008-06-23
Hi guys... I'm not sure where to post this, please move this post if it is in the wrong place.

Alright, here goes:

I have approximately 1000 output files generated from some scientific simulations of something. Apparently, about 2-3% of them are bad. When a file is bad, it says something like "job killed" and/or "exist status 65".

These error messages happen at the end of each output file.

To analyze these data, I need to filter out the bad ones. So I would need to create a script that reads the tail of each output and search for strings such as "job killed" or "status 65", and then output the filenames such that this happens.

I know very little bash scripting... except some very basic stuffs like echo, simple for loop...etc. I searched lots of tutorial but lots of them seem very complicated. I would appreciate it if anyone can point me to the right direction (what command to use, ideas for implementation...etc).

---

### Post by lloyd_b on 2008-06-23
> **leptons said:**
> Hi guys... I'm not sure where to post this, please move this post if it is in the wrong place.

Alright, here goes:

I have approximately 1000 output files generated from some scientific simulations of something. Apparently, about 2-3% of them are bad. When a file is bad, it says something like "job killed" and/or "exist status 65".

These error messages happen at the end of each output file.

To analyze these data, I need to filter out the bad ones. So I would need to create a script that reads the tail of each output and search for strings such as "job killed" or "status 65", and then output the filenames such that this happens.

I know very little bash scripting... except some very basic stuffs like echo, simple for loop...etc. I searched lots of tutorial but lots of them seem very complicated. I would appreciate it if anyone can point me to the right direction (what command to use, ideas for implementation...etc).

You should be looking at the "grep" command.  Here's a simple example:
```
grep "job killed" *
```
Will look in all files in the current directory, and display any line from any of them that contains the string "job killed" (along with the filename).

So a simple script, once for "job killed" and again for "status 65" will give you the basic information.

Note that the output from these commands looks like
```
test2:job killed
test3:job killed
```where "test2" and "test3" are the filenames, and the part after the colon is the line containing the matching text.  If you just want the file names, use ```
grep -l "job killed" *
```

You can use these list of files to feed a loop, automatically deleting them or moving them to another directory.  How sophisticated you want to get depends on your requirements (if it's a one-time job, I wouldn't waste the effort, but if it's something you'll be doing on a daily basis, then more effort now would save time in the future).

Hope this helps.

Lloyd B.

---

### Post by hyper_ch on 2008-06-23
something like this:

```

#!/bin/bash
DIR=/path/to/dir
COND1="job killed"
COND2="exist status 65"
cd $DIR
for i in $( ls ); do

    for j in $( cat $i ); do
        if [ $j = $cond1 ]
            rm $i;
        elsif [ $j = $cond2 ]
            rm $i;
        fi
    done

done

```

---

### Post by leptons on 2008-06-23
Thank you! lloyd_b, I cannot believe I didn't know about the grep command before. works like a charm.

I've copied down hyper_ch's script just in case when I need to do something more complicated. 

Thanks for the help and the celerity of the responses!

---

### Post by aheckler on 2008-06-23
A simpler method might be to use grep in the directory, and then pipe the output of that to xargs and delete the files in one line. Something like this, IIRC:

```
grep -l "job killed" * | xargs rm
```

Although their might be some complications with filenames or something, so I wouldn't try this without some testing.

---

