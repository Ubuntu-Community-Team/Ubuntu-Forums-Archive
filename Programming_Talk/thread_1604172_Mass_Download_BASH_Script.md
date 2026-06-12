---
title: "Mass Download BASH Script"
date: 2010-10-23
forum: Programming Talk
---

### Post by xIHammerIx on 2010-10-23
Hey all,

I tend to need to download a lot of weather maps via wget.  Today I started to write a BASH script to allow for mass downloads, but am having a little trouble.  What I'd like it to do is ask for a start and stop times. For example downloading January 1st 2009 through March 15th 2010

Start Year 
09
Start Month 
01
Start Date 
01
End Year
10
End Month
03
End Date
15

I can't wrap my head around getting it to account for the changing of months (going form the 31st or whatever to the 01st) and going from December (12) to January (01).

Could someone throw me a bone? Thanks!

---

### Post by DaithiF on 2010-10-23
Hi,
date manipulation in bash is not very convenient.  however it is possible, something like this may give you some ideas:

```
start="01 Jan 2009"
end="28 Feb 2009"

day="$start"

while true 
do
        echo $day
        [[ "$day" == "$end" ]] && break
        day=$(date -d "$day +1 day" +"%d %b %Y")
done

```

---

### Post by gmargo on 2010-10-24
I prefer to specify the dates on the command line, using the YYYYMMDD format.  Never prompt the user for anything if you can help it.  Here's a script that cycles from a start date to an end date.  Much of the script is error and format checking.  It uses DaithiF's method for +1 day increments.

```

#!/bin/sh
# vim: ts=8 sts=4 sw=4 et :

if [ $# -ne 2 ] ; then
    echo "Usage: $0 YYYYMMDD YYYYMMDD"
    exit 1
fi
start="$1"
end="$2"

echo "$start" | grep -q -E '^[[:digit:]]{8}$'
if [ $? -ne 0 ] ; then
    echo "Bad start date"
    exit 2
fi
echo "$end" | grep -q -E '^[[:digit:]]{8}$'
if [ $? -ne 0 ] ; then
    echo "Bad end date"
    exit 2
fi

date -d "$start" > /dev/null 2>&1
if [ $? -ne 0 ] ; then
    echo "Bad start date"
    exit 2
fi
date -d "$end" > /dev/null 2>&1
if [ $? -ne 0 ] ; then
    echo "Bad end date"
    exit 2
fi

date="$start"

while [ "$date" -le "$end" ] ; do
    year=$(echo "$date" | sed 's/^\(....\).*/\1/')
    month=$(echo "$date" | sed 's/^....\(..\).*/\1/')
    day=$(echo "$date" | sed 's/^......\(..\).*/\1/')

    echo "date=$date (year=$year month=$month day=$day)"

    date=$(date -d "$date +1 day" +"%Y%m%d")
done

```Here some simple output:
```

$ sh bone.sh 20001228 20010102
date=20001228 (year=2000 month=12 day=28)
date=20001229 (year=2000 month=12 day=29)
date=20001230 (year=2000 month=12 day=30)
date=20001231 (year=2000 month=12 day=31)
date=20010101 (year=2001 month=01 day=01)
date=20010102 (year=2001 month=01 day=02)

```

---

### Post by xIHammerIx on 2010-10-25
Thanks guys.  This should really get me going. Much appreciated.

---

