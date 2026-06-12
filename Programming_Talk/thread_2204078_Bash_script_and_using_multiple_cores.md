---
title: "Bash script and using multiple cores"
date: 2014-02-06
forum: Programming Talk
---

### Post by Derek Karpinski on 2014-02-06
What I have is hundreds of folders worth of files.  Some files are plain text, some are rtf, some xls, doc, docx, etc.  One file may be duplicated in multiple sub-folders. I need to generate a list of files that contain a certain string.  For example's sake, I'm searching for the word 'epoxy'.  To eliminate searching multiple files, I've created a list of the filenames I've already scanned, and will skip that file.  It seems to work pretty well, but I have about 75GB of files to search through, and even with a SSD drive, it's taking hours.  Note, I'm using cygwin 32 bit, but do have access to linux if I need it, although it won't be native (in a vm).  What I'm after is a way to use all 4 cores of my computer to search faster.

See attached script.

```
#!/bin/bash

rm ./files.txt
touch ./files.txt




find ~/documents/setup_sheets/ -type f | while read f


base="`basename "$f"`"


do
    grep "$base" files.txt
    rc=$?
    if [[ $rc -eq 0 ]] ; then
        echo "*** Skipping duplicate file "$base" ***"
        continue
    fi
    echo "$base" >> files.txt


    strings "$f" | grep -q 'epoxy'
    rc=$?
    echo "Scanning file "$base""
    
    if [[ $rc -eq 0 ]] ; then
        echo "$f" >> ./matches.txt
    fi
done


#sed -i 's/.*\///' ./matches.txt
```

Can someone help me optimize this code for speed?

---

### Post by tgalati4 on 2014-02-06
Put your script on a USB flash drive and boot a Live DVD of linux.  Manually mount the drive in terminal then run your script.  It should be much faster.

grep has a recursive switch which would be much faster than using *find* with a while loop.  I wouldn't worry about duplicate files.  Dump everything in your output text file, then process that separately.  That would be much quicker than trying to elimate duplicate searching before applying grep.

---

### Post by ssam on 2014-02-07
not sure that running from a live cd will make much difference. Though using grep recursively may help, and will simplify the script.

If the search is limited by disk speed, then using multiple threads will not help much. It can never be faster than the time it takes to read 75GB from disk.

If you are looking for duplicates then the best thing is probably to make a checksum of every file (md5sum), and just look through the list for files with the same check sum.

---

### Post by ofnuts on 2014-02-07
Not sure that using the 4 cores is going to be faster, this kind of action is typically I/O bound, even with a SSD. To use several cores you could start several instances of find/grep in parallel on subdirectories, and then concatenate the result files: something like:

```

set -a pids
for subdir in *. 
do
  cd $subdir
  # start grep in background over the subdirectory, and keep its pid
  grep -R {pattern} > ../$subdir.partresult &
  pids[${#pids
[*]}]=$!
done

# Now wait until all processes are finished. We don't need to for wait them in the order 
# in which they terminate, we just to make sure that the rest of the code isn't run until
# all have finished.
for pid in ${pids
[*]}
do
  wait $pid
  # print "Sensed end of $pid"
done

# All processes finished, get he final result from the parts
cat *.partresult >final.result

```

On a hard disk this would be utterly pointless, because the hard disk contention (HDD head moves) is going to cost you a lot more than what you gain when searching with more cores. On a SSD the I/O contention is only on the data rate through the interface, so it will never be worse than with a single process, even if I doubt that it can get significantly better.

---

