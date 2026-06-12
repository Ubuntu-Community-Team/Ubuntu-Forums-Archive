---
title: "Do ... Loop"
date: 2008-08-03
forum: Programming Talk
---

### Post by felix001 on 2008-08-03
ill be the first to admit i am a bit of a bash scripting noob... but ive come againest a small problem...

LOG=/var/log/local2.log

for i in SEC-0 SEC-1 SEC-2 SEC-3 SEC-4 SEC-5 SEC-6 SEC-7
do
        grep $i $LOG | wc -l
done

The above works and gives me 8 different values. Later on in the script I wish to echo these strings, so i would like them as varibles.
Is there anyway to assign each total against a varible so when this is finished I have... something like..
$SEC-0=some number
$SEC-1=some number ..... etc etc

I hope I have made this clear, thanks in advanced....

Felix .. [http://fir3net.com](http://fir3net.com)

---

### Post by dexter.deepak on 2008-08-03
even i am a noob to this, but this should work :
```

LOG=/var/log/local2.log

for i in SEC-0 SEC-1 SEC-2 SEC-3 SEC-4 SEC-5 SEC-6 SEC-7
do
j=`grep $i $LOG | wc -l`
echo "$i=$j"
done

```

---

### Post by felix001 on 2008-08-03
Its kinda right but i think i didnt explain what im trying to do. 

Once outside of this loop I want to echo the variables (totals)..

This is the full code..

```
#!/bin/bash
#

# variables
LOG=/var/log/local2.log

for i in SEC-0 SEC-1 SEC-2 SEC-3 SEC-4 SEC-5 SEC-6 SEC-7
do
        grep $i $LOG | wc -l
done

#### Functions

overview(){
echo "Emergency     - Severity 0 - Logged $SEC-0"
echo "Alert         - Severity 1 - Logged $SEC-1"
echo "Critical      - Severity 2 - Logged $SEC-2"
echo "Error         - Severity 3 - Logged $SEC-3"
echo "Warning       - Severity 4 - Logged $SEC-4"
echo "Notification  - Severity 5 - Logged $SEC-5"
echo "Informational - Severity 6 - Logged $SEC-6"
echo "Debugging     - Severity 7 - Logged $SEC-7"
}

#### Main

echo "Cisco Log Viewer"
echo

if [ -f $LOG ] ; then
        echo overview
else
        echo "Unable to find logfile at $LOG" >&2
        exit 1
fi

exit 0

```

---

### Post by Diabolis on 2008-08-03
What you want is an array to store each value inside your loop and when its done. Go through the array with another loop that will print its values.

---

### Post by ghostdog74 on 2008-08-03
you can use arrays. See [here](http://tldp.org/LDP/abs/html/arrays.html)for examples. also read the whole bash manual in my sig. Also, for this
```

grep $i $LOG | wc -l

```
you can look at the grep man page for an option to just count the number of entries found. there's no need for wc -l

---

### Post by felix001 on 2008-08-04
ok ive been looking up arrays, and i have to say ... im completey confused...

i suppose the more ill learn so enough i should be able to find a fix to this issue soon enough...

---

### Post by dwhitney67 on 2008-08-04
Nothing to be confused about... it's quite easy.  Here's an example:
```
#!/bin/sh

LOG=/var/log/local2.log

for i in 0 1 2 3 4 5 6 7
do
        SEC_count[$i]=`grep SEC-$i $LOG | wc -l`
done

for i in 0 1 2 3 4 5 6 7
do
        echo SEC-$i count = ${SEC_count[$i]}
done
```

---

### Post by felix001 on 2008-08-05
Thanks exactly what i was looking for. 

Good stuff..

Thanks again...

Felix [http://fir3net.com](http://fir3net.com)

---

### Post by felix001 on 2008-08-05
```

```LOG="/var/log/local
level=(Emergency Alert Critical Error Warning Notification Informational Debugging)
for i in 0 1 2 3 4 5 6 7
do
        printf "${level[$i]} - " ;  grep -c SEC-$i $LOG
done
```

```

But the only thing im unsure of is how to allow for the wildcard in for the $LOG variable ????

---

### Post by ghostdog74 on 2008-08-05
what do you mean? explain more clearly.

---

### Post by felix001 on 2008-08-06
As in i have a variable LOG which i want to use for all my log files called local... so it would be 

LOG=/var/log/local??????

ive tried the * and ? but they dont seem to work...

---

### Post by ghostdog74 on 2008-08-06
if they don't work, show how they don't work and any error messages.
Put set -x  at the beginning of your script, run it and see what happens. Print out the value of LOG

---

### Post by dwhitney67 on 2008-08-06
The complaint appears to derive from LOG=/var/log/local2.log (as was listed in the original post).  Apparently this is not satisfactory; the OP wants us to solve yet another problem.

OP... please give **all** of the requirements!!!!

---

