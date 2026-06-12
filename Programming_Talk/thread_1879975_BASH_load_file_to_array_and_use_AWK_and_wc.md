---
title: "BASH: load file to array and use AWK and wc"
date: 2011-11-12
forum: Programming Talk
---

### Post by hailholyghost on 2011-11-12
Hello,:popcorn:

I am attempting to load output of a command to an array to minimize hard drive use.

This is the original script (which works)
```
#!/bin/bash

qstat -u $USER > tmp
awk '/R/{sum+=$7} END {print "There are", sum, "processors in use"}' tmp
awk '/R/{print $7}' tmp | wc -l | ~/pca '$1-1' | awk '{print "There are", $0, "jobs running"}'
awk '/Q/{print $7}' tmp | wc -l | ~/pca '$1-1' | awk '{print "There are", $0, "jobs in queue"}'
awk '/C/{print $7}' tmp | wc -l | awk '{print "There are", $0, "jobs stopped"}'
rm tmp
```

The problem with this script is that it writes to a file called "tmp" on the HD, which requires a lot of I/O.

I am trying to alter the code so the output of qstat -u $USER, which looks like:```
[dave@bluehive ~]$ qstat -u $USER

bhsn:
                                                                         Req'd  Req'd   Elap
Job ID               Username Queue    Jobname          SessID NDS   TSK Memory Time  S Time
-------------------- -------- -------- ---------------- ------ ----- --- ------ ----- - -----
1101607.bhsn-int     dave  standard gacc.s.syn.99     15026     1   8    --  119:5 R 101:2
1101611.bhsn-int     dave  standard gacc.s.anti.tor   17515     1   8    --  119:5 R 100:1
1101612.bhsn-int     dave  standard s.syn.ol          25678     1   8    --  119:5 R 100:0
1105954.bhsn-int     dave  standard s.anti.ol         25377     1   8    --  119:5 R 87:22
1108616.bhsn-int     dave  standard lna.caau.99       32329     1   8    --  119:5 R 39:37
1116620.bhsn-int     dave  long     n.syn.ol          21717     1   8    --  336:0 R 13:55
1128672.bhsn-int     dave  standard rna.caau.ol       31860     1   8    --  119:5 R 01:47

``` is written to an array instead.

My first attempts have failed (I've commented out the last 4 commands, just trying the first right now).

```

#!/bin/bash

jobs=($(qstat -u $USER))
awk '/R/{sum+=$7} END {print "There are", sum, "processors in use"}' "${jobs[@]}"
#awk '/R/{print $7}'  | wc -l | ~/pca '$1-1' | awk '{print "There are", $0, "jobs running"}'
#awk '/Q/{print $7}' tmp | wc -l | ~/pca '$1-1' | awk '{print "There are", $0, "jobs in queue"}'
#awk '/C/{print $7}' tmp | wc -l | awk '{print "There are", $0, "jobs stopped"}'
#rm tmp
```

The reason I'm trying this is because I've had issues in the past about hard drive I/O massively slowing down the calculations.  I've got two questions:

1.  Does writing to an array, as opposed to writing to a temporary file and calling from that file, speed up calculations?  I think this is because the array uses RAM, as opposed to the file "tmp" which is on the hard drive.

2.  How can I use these awk and 'wc -l' commands to work on the array "jobs" the same way they worked with the file tmp?

Thanks so much!:P
-Dave

---

### Post by ofnuts on 2011-11-12
> **hailholyghost said:**
> Hello,:popcorn:

I am attempting to load output of a command to an array to minimize hard drive use.

This is the original script (which works)
The reason I'm trying this is because I've had issues in the past about hard drive I/O massively slowing down the calculations.  I've got two questions:

1.  Does writing to an array, as opposed to writing to a temporary file and calling from that file, speed up calculations?  I think this is because the array uses RAM, as opposed to the file "tmp" which is on the hard drive.

2.  How can I use these awk and 'wc -l' commands to work on the array "jobs" the same way they worked with the file tmp?

Thanks so much!:P
-Dave

[LIST]
[*]In Unix there is  a lot of disk I/O caching going on, so moving the data to RAM may not speed things as much as you think
[*]If the file is not small compared to available RAM you may end up trading your I/O problem against a swapping problem.
[*]You won't have as much functionality at you disposal to process array contents in Bash than you would have to process the same data in files. But if you insists the output can be easily ingested in an array using mapfile/readarray. ```
mapfile -t jobs < <(qstat -u $USER)
```
[*]maybe a middle-of-the-road solution is to use a RAM-mapped filesystem such as tmpfs. Your original script would still work.
[*]I don'tknowmuch awk, but the fact tha you run 4 different awk commands on the same file is a lot of I/O, and I'm pretty sure that all this could be done in one awk run (4x performance gain, if you are I/O bound)
[/LIST]

---

### Post by hailholyghost on 2011-11-12
Thank you very much ofnuts, I'll look into tmpfs.

I'll be toying around with the mapfile and readarray commands.

Thank you so much!!

---

