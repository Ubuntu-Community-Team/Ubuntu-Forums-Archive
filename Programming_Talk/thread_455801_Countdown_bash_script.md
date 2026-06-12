---
title: "Countdown bash script??"
date: 2007-05-27
forum: Programming Talk
---

### Post by odiseo77 on 2007-05-27
HI all, first I'm a bash newb (is the only programming language I can understand a bit). Also, excuse me if this is not allowed here; but basically what I'm trying to do is a countdown script that outputs the days, hours and minutes remaining until a certain date/time, so far, the only thing I've managed to write is this:

```
#!/bin/bash

VAL="`date +%d-%m-%y-%H-%M`"
until [ $VAL -eq 28-05-07-00-00 ]
do
#certains commands that I don't know 
  echo "XX days, XX hours, XX minutes remaining"
done
```

As you can see, my bash knowledge is very poor :D But can someone point me in the right direction? (is not necessary that someone else writes the script for me but just give me some hints and clues to help me figure this out)

Regards and thanks in advance.

---

### Post by spin2cool on 2007-05-27
My advice is to use the "date +%s" to get your date.  This is the number of seconds since 1/1/1970 and makes it easy to do date arithmetic.   Convert your target date to this format, then just subtract the current date from your target date.  This makes it so that you won't have to worry about how your script will wrap around new months or years, etc.

---

### Post by spin2cool on 2007-05-27
upon further review, this looks like a great resource that may help:
[http://www.unix.com/showthread.php?t=13785](http://www.unix.com/showthread.php?t=13785)

---

### Post by odiseo77 on 2007-05-27
Thank you spin2cool!! I overview the article and it seems very interesting (and it's a good chance to learn). Well, I'll try it tomorrow, or rather today after I wake up, since it's 2:11 am here and I'm going to bed now :D

I'll let you know how it goes.

Regards and thanks again for your help.

---

### Post by ghostdog74 on 2007-05-27
```

awk 'BEGIN {    
            newdate=mktime("2007 05 28 12 00 00")
	    ("date +%s") | getline datenow;close("date +%s")
	    diff=newdate-datenow
	    while ( diff > 1 ) {	        
	        print diff " seconds to 2007 05 28"
		"sleep 2" | getline		
		close("sleep 2")
		("date +%s") | getline datenow
		close("date +%s")
		diff=newdate-datenow
	    }
	    
}' 

```

---

### Post by odiseo77 on 2007-05-27
Well, I was the whole morning messing around several test scripts I made to no avail, but since my bash knowledge is very poor as I said before and I need the script to be running today until midnight and didn't have the time to do it, I made a little cheat: search on google and found [this]("http://linide.sourceforge.net/0086.html") :p :D I copied the script and edited to my like and it looks like this:

```
#!/bin/bash

destin="$2"
target=`date +%s --date="28 May 2007 00:00:00"`
source=`date +%s`

diff=`expr $target - $source`

seconds=$diff
min_sec=`expr $diff / 60`:`expr $diff % 60`
ho_mi_s=`expr $diff / 3600`:`expr \( $diff % 3600 \) / 60`:`expr $diff % 60`
hou_sec=`expr $diff / 3600`:`expr $diff % 3600`
day_sec=`expr $diff / 86400`:`expr $diff % 86400`
da_mi_s=`expr $diff / 86400`:`expr \( $diff % 86400 \) / 60`:`expr $diff % 60`
d_h_m_s=`expr $diff / 86400`:`expr \( $diff % 86400 \) / 3600`:`expr \( \( $diff
 % 86400 \) % 3600 \) / 60`:`expr $diff % 60`
wdh_m_s=`expr $diff / 86400 / 7`:`expr \( $diff / 86400 \) % 7`:`expr \( $diff %
 86400 \) / 3600`:`expr \( $diff % 3600 \) / 60`:`expr $diff % 60`

echo $ho_mi_s Hours:Minutes:Seconds remaining\!
```

I know it's not a real solution (I mean, would have been better to do it by myself), but as a temporary workaround, it's ok... hope I can learn more about bash programing -and maybe even other programming languages- in the future but I need to read a lot to accomplish complex tasks like this.

Regards and thanks for your help :)

---

### Post by JT673 on 2007-05-27
My solution has a little bit more features, but not as elgant as the other designs:

```
#!/bin/bash

file=`ls ~/bin/countdown.txt`
usage="Usage: $0                  #get time until destination\n \
              $0 --add time name  #assign time to the name\n \
              $0 --reset [time]   #reset clock, to time, if given\n \
       See man date(1) for time add/reset format."

now=`date +%s`

if [ "$1" = "--add"  ] ; then
	if [ "$#" -lt "3" ] ; then
		echo "Need more arguments!"
		echo $usage
		exit 1
	fi
	echo -n "$3:"`date -d "$2" +%s`"::" >> $file
	exit
elif [ "$1" = "--reset" ] ; then
	echo "" > $file
	exit
fi

records=`cat $file`
numrecords=`cat $file | grep "::" | wc -l`
while [ $numrecords -gt 0 ]
do

	destfull=`echo $records | nawk -F:: '{print $1}'`
	destname=`echo $destfull | nawk -F: '{print $1}'`
	dest=`echo $destfull | nawk -F: '{print $2}'`
	
	interval=`expr $dest - $now`
	seconds=`expr $interval % 60`
	interval=`expr $interval - $seconds`
	minutes=`expr $interval % 3600 / 60`
	interval=`expr $interval - $minutes`
	hours=`expr $interval % 86400 / 3600`
	interval=`expr $interval - $hours`
	days=`expr $interval % 604800 / 86400`
	interval=`expr $interval - $hours`
	weeks=`expr $interval / 604800`
	echo "$destname: "$weeks" weeks, "$days" days, "$hours" hours, "$minutes" minutes, "$seconds" seconds"
	records="${records#$destfull"::"}"
	numrecords=`expr $numrecords - 1`
done
```

Put a "countdown.txt" in your bin folder (or edit "file=`ls ~bin/countdown.txt`" to something else), and do something like

```
$ countdown --add "Nov 1 2008" "Presidential Elections"
$ countdown
*Presidential Elections: 74 weeks, 5 days, 7 hours, 10 minutes, 36 seconds*
```

---

### Post by juicymixx on 2007-06-01
This is really nice!   I've been using it on multiple machines for various countdowns.   I've run into one in which the date command doesn't have the -d option.   Is there a way to get this to work in that instance?

Thanks!


oh, hey.   I got it.   Here's one way:

replace:
echo -n "$3:"`date -d "$2" +%s`"::" >> $file

with this:
conv_sec=`echo "puts [clock scan { $2 }]" | tclsh`
echo "$3:${conv_sec}::" >> $file


also if you don't have nawk, link to gawk!   everything works great (of course)!

---

