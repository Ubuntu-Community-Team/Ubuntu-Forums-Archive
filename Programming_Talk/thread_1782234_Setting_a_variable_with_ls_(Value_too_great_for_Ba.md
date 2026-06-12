---
title: "Setting a variable with ls (Value too great for Base/BASH)"
date: 2011-06-14
forum: Programming Talk
---

### Post by Omegaclawe on 2011-06-14
I've been writing up a simple script for pruning the backups on my minecraft server, which, due to a mod I'm using, requires that I use a naming scheme using the date and time with leading zeroes. Changing the file name format is out of the question.

However, with the current method, when I try to read the file names to a variable array, it treats parts of the date (with leading zeros) as octal numbers, meaning anything with an 08 or 09 causes an error and aborts the script. My file names are going to have these numbers in them pretty much no matter what... so... how do I work around this?

Script:
```

declare -a backs
declare -a times
declare trans
declare k
declare trans2
declare trans3

backs=`ls backups`
for i in ${backs[@]}; do
    trans=${backs[i]:0:19}
    times[i]=(`date --date $trans`)
done
for j in ${times[@]}; do
    trans=$(expr `date` - 605000)
    if [j -ne 0 ] ; then
        k=$(expr $j - 1)
    else
        k=0
    fi
    trans2=$(expr $times[k] + 86000)
    trans3=$(expr `date` - 87000)
    if [ $times[j] -gt $trans ] ; then
        rm -f backup\`$backs[j]`
    elif [ $times[j] -lt $trans3 -a $times[j] -gt $trans2 -a $j -ne 0 ] ; then
        rm -f backup\`$backs[j]`
    fi
done

```I realize that my implementation might be a bit stupid... this is about the only major thing I've ever done with bash, or really, any other major unix scripting method. I got where I am through trial and error and google searches, but those have not helped me here.

---

### Post by Arndt on 2011-06-14
> **Omegaclawe said:**
> I've been writing up a simple script for pruning the backups on my minecraft server, which, due to a mod I'm using, requires that I use a naming scheme using the date and time with leading zeroes. Changing the file name format is out of the question.

However, with the current method, when I try to read the file names to a variable array, it treats parts of the date (with leading zeros) as octal numbers, meaning anything with an 08 or 09 causes an error and aborts the script. My file names are going to have these numbers in them pretty much no matter what... so... how do I work around this?

Script:
```

declare -a backs
declare -a times
declare trans
declare k
declare trans2
declare trans3

backs=`ls backups`
for i in ${backs[@]}; do
    trans=${backs[i]:0:19}
    times[i]=(`date --date $trans`)
done
for j in ${times[@]}; do
    trans=$(expr `date` - 605000)
    if [j -ne 0 ] ; then
        k=$(expr $j - 1)
    else
        k=0
    fi
    trans2=$(expr $times[k] + 86000)
    trans3=$(expr `date` - 87000)
    if [ $times[j] -gt $trans ] ; then
        rm -f backup\`$backs[j]`
    elif [ $times[j] -lt $trans3 -a $times[j] -gt $trans2 -a $j -ne 0 ] ; then
        rm -f backup\`$backs[j]`
    fi
done

```
I realize that my implementation might be a bit stupid... this is about the only major thing I've ever done with bash, or really, any other major unix scripting method. I got where I am through trial and error and google searches, but those have not helped me here.

Maybe you can use this:

```
$ expr 010 + 0
10
```

---

### Post by sisco311 on 2011-06-14
You don't need an array:
```

#!/bin/bash

shopt -s nullglob

date1=$(date -d 'yyyy-mm-dd hh:mm' +%s)
date2=$(date -d 'yyyy-mm-dd hh:mm' +%s)

cd /path/to/backups
for file in *
do
    # This part depends on the date format you use in the file names
    # You can use Pattern Expansion to get the year, month, day...
    # See [http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion]("http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion")

    date=$(date -d "${year}-${month}-${day} ${hour}:${minute}" +%s)

    if (( $date < $date1 )) && (( $date > $date2 ))
    then
        rm -i -- "${file}"
    fi
done

```

[http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion](http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion)
[http://mywiki.wooledge.org/BashFAQ/102](http://mywiki.wooledge.org/BashFAQ/102)

---

### Post by Omegaclawe on 2011-06-14
Thanks, Sisco! took a little experimentation, but I got it working as intended based on your script. The idea was to prune backups older than 24 hours, but leave one for each day throughout the week, which required me to change some things. In any case, here's the (hacky) script I ended up with:
```

shopt -s nullglob

date1=$(date -d yesterday +%s)
date2=$(date -d last-week +%s)
date3=$(date -d last-month +%s)

cd backups
for file in *
do
    # This part depends on the date format you use in the file names
    # You can use Pattern Expansion to get the year, month, day...
    # See http://mywiki.wooledge.org/BashGuide...eter_Expansion
    date=$(date -d "${file:0:4}-${file:5:2}-${file:8:2} ${file:11:2}:${file:14:2}:${file:17:2}" +%s)

    if (( $date < $date1 )) && (( $date < $date3 ))
    then
        rm -if -- "${file}"
    fi
    if (( $date < $date2 ))
    then
        rm -if -- "${file}"
    fi

    date3=$(($date + 86000))
done

```

Edit: Gah! Can't figure out how to get the [Solved] tag to appear! It was an option when I created the topic, but... I don't see the place to edit it in... :/

---

### Post by BrandonC19 on 2011-06-14
> Edit: Gah! Can't figure out how to get the [Solved] tag to appear! It  was an option when I created the topic, but... I don't see the place to  edit it in... :/ 	

At the top of this thread click "Thread Tools" and select "Mark as SOLVED".

---

### Post by Omegaclawe on 2011-06-14
Thanks... now I can let this thread die in peace :P

---

### Post by BrandonC19 on 2011-06-14
No problem. Have a good night.

---

