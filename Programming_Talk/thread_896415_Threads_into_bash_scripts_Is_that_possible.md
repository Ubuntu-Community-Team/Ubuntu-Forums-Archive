---
title: "Threads into bash scripts? Is that possible?"
date: 2008-08-21
forum: Programming Talk
---

### Post by CyberAngel on 2008-08-21
Hello,

I have a situation that I need to be monitoring a file using "tail -f" for changes.
The filename will always be something like this:

YYYYMMDD.dat

for example 20080821.dat

When the day is changing, a new file is created with the new date for it`s filename. So if today the file is 20080821.dat the next one will be 20080822.dat

My problem now, is that when that occurs (new file just created) I want to stop monitoring the old one and instantly start monitoring the new one.

How do you think it`s the best way to achieve that?

I have a bash script that it is checking the file like this:

```
#!/bin/bash

tail -f $1 | while read line; do
   #DO SOMETHING
done
```

and I can also know which is the last filename using a polling technique like this:

```
#!/bin/bash

while [ 1 ]; do

	LATEST_FILE=`ls | grep '20[0-9][0-9]\(0[1-9]\|1[0-2]\)\(0[1-9]\|[1-2][0-9]\|3[0-1]\).dat' | tail -1`
	sleep 1

done
```

Both of these code blocks has an endless loop so I can`t combine them in a single script without the use of threads.
Is it possible to use threads for bash scripts and call from the second Code block the first one like a function, when I determine that the $LATEST_FILE just changed?

Thanks

---

### Post by ghostdog74 on 2008-08-21
try this. Untested.
```

#!/bin/bash
monitorfile="20080821.dat"
while true
do
    newfile=$(date +%Y%m%d -d "1 day ")".dat"
    if [ -e ${newfile} ]; then
        monitorfile=${newfile}
        ps -ef| awk '/tail/&&!/awk/{c="kill -9 "$2;system(c)}'
    fi
    if [[ -z $(pidof tail) ]];then
        echo "Starting tail -f ... $monitorfile"
        tail -f $monitorfile &        
        TAIL_PID=$!
        echo "pid of tail is $TAIL_PID"
    fi
    sleep 30
done


```

---

### Post by dtmilano on 2008-08-21
I think this is what you should need, of course adapt it to your needs

```
#!/bin/bash

trap 'myfilename' USR1

myfilename()
{
   echo "midnight, searching new file..."
   filename="f$j"
   : $(( j++ ))
}


j=0
i=0
myfilename

while :
do
   echo "reading file $filename..."
   sleep 1
   : $(( i++ ))
   # check for midnight
   if [ $(( i%5 )) -eq 0 ]
   then
      echo "suicide ;-)"
      kill -USR1 0
   fi
done

```

---

### Post by CyberAngel on 2008-08-22
Thanks for the replies guys!

Finally I created two different scripts.
One script is doing the job and the other one is checking if a newer file in the directory exists (using ls and checking the filenames every second).
If a newer file created, then it is killing the first running script and starting it again by setting it to check the new file of course.

---

