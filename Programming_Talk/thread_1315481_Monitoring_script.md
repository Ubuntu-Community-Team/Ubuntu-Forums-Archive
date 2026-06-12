---
title: "Monitoring script"
date: 2009-11-05
forum: Programming Talk
---

### Post by madsmeg on 2009-11-05
Hi guys

I am trying to write a script to monitoring script that reports the rss, pcpu and comm.

That isn't the hard part, the bit i am struggling with is;

find duplicate comm's, merge them into one adding up the cpu% use and rss use.

so far i have this:

```
#!/bin/bash

DATE=$(date +%F)
NAME="Test_$DATE.csv"
PROCS=""

ps -eo "rss,pcpu,comm" >> temp.txt

PROCS='cat temp.txt | grep ^PROCS= | sed 's/PROCS=//''

        for i in $PROCS ; do
                        HEAD='echo -n $HEAD$i rss,$i pcpu,'
                done

                HEAD='echo -n $HEAD | sed "s/.$//"'

                echo "rss,pcpu,comm" >> $NAME

        for j in $PROCS ; do
                TMPPROCSTAT=`grep $j temp.txt | awk '{rss+=$1} ; {pcpu+=$2} ; END { print rss","pcpu }'`
                # if [ "$TMPPROCSTAT" = "," ] ; then
                #       TMPPROCSTAT="NA,NA"
                # fi
                PROCSTAT=`echo "$PROCSTAT$TMPPROCSTAT,"`
                done
                PROCSTAT=`echo -n $PROCSTAT | sed "s/.$//"`
                echo $PROCSTAT >> $NAME
        rm temp.txt

```

I am putting the values into a csv file, adding the rss, pcpu and comm as headings, then want the info displayed below.

all i am getting as output at the moment is:

```
rss,pcpu,comm
,,,,,,,,,,,1234,0,,,,,
```

that not exact values, just an example :p

Any help, or a point in the right direction will be appreciated, or if anyone knows of a better way that what i am trying...

---

### Post by diesch on 2009-11-05
Maybe something like this:
```
ps -eo "rss,pcpu,comm" --no-header | awk '{rss[$3]+=$1; pcpu[$3]+=$2} END {OFS=","; for (r in rss) print rss[r], pcpu[r], r}'

```

---

### Post by madsmeg on 2009-11-06
Got it all sorted, thanks a lot
ended up using :

```
ps -eo "rss,pcpu,comm" | awk '{ rss[$3] += $1; pcpu[$3]+=$2 } END { for (a in rss) printf "%.f, %.1f, %s\n", rss[a], pcpu[a], a }' >> $PRFNAME
```

before reading your reply

Thanks a lot though :)

---

