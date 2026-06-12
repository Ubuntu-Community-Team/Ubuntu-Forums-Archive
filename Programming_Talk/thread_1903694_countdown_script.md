---
title: "countdown script"
date: 2012-01-03
forum: Programming Talk
---

### Post by Drenriza on 2012-01-03
Hi all.

Is it possible to create a countdown script that can countdown to
13.09.2013 13:00,
that for example open a terminal window and show the live countdown at system start.

The time symbolics the end of my six year long study :p

Thanks on advance.
Kind regards.

---

### Post by 11jmb on 2012-01-03
Certainly.

I wouldn't know off the top of my head how to do it in bash, but here is a simple python version.

```

from datetime import datetime

now = datetime.now()
date = datetime(2013, 9, 13, 13) #(year, month, day, hour)
delta = date-now;

days = delta.days
seconds = delta.seconds

print "T Minus {0} Days, {1} Seconds".format(days, seconds)

```

You can do some simple processing beyond that to get years, hours, and mins (months will be tough)

---

### Post by gnometorule on 2012-01-04
I"m not exactly sure what you would like, but here is a version that does the job as I understand it. It opens a new gnome terminal in which it displays a countdown. If you'd like better graphic support, you'd have to rely on one of the packages that you can get from the repositories. I tested it, and it runs fine on my netbook (10.04). 

countdown_exec: (put this into any of your directories and make it executable using chmod u+x; let's call the directory 'DIREC' (absolute address))

```

#!/bin/bash
# countdown script at login

callback(){

clear
now=`date +%d.%m.%Y-%H:%M:%S`
graduation=`date --date="13 Sep 2013 13:00" +%d.%m.%Y-%H:%M`
sec_today=`date +%s`
sec_grad=`date --date="13 Sep 2013 13:00" +%s`
sec_delta=$[$sec_grad - $sec_today]
min_delta=$[$sec_delta / 60]
hours_delta=$[$min_delta / 60]

echo -e "Today is: \t$now"
echo -e "Graduation on: \t$graduation"
echo "---------------------------------------"
echo "Time to graduation:"

echo -e "\tSeconds: $sec_delta" | sed '{
:start
s/\(.*[0-9]\)\([0-9]\{3\}\)/\1,\2/
t start
}'

echo -e "\tMinutes: $min_delta" | sed '{
:start
s/\(.*[0-9]\)\([0-9]\{3\}\)/\1,\2/
t start
}'

echo -e "\tHours:\t$hours_delta" | sed '{
:start
s/\(.*[0-9]\)\([0-9]\{3\}\)/\1,\2/
t start
}'

sleep 2
}

count=0
while [ $count -eq 0 ]
do
    callback
done



```countdown: (put this into the same directory DIREC, and make it executable too)

```


#!/bin/bash
# start countdown_exec in new shell

gnome-terminal -x "DIREC/countdown_exec" &


```Finally,, go to your home directory and add this line to the .bashrc:

DIREC/countdown

---

### Post by gnometorule on 2012-01-04
You need to kill the new shell, or add your own steering logic to terminate upon whichever action you would like. For now, just use ctrl-c.

---

### Post by Drenriza on 2012-01-04
Thanks gnometorule

---

