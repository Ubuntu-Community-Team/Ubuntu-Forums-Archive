---
title: "bash elif issue"
date: 2011-11-18
forum: Programming Talk
---

### Post by Drenriza on 2011-11-18
Hi all.

I have written some bash "code" as follows
```
if [[ "$L1" == 0 && "$L2" == 0 ]]
  then
     echo "logfiles are within acceptable limits" >> $hvem
elif [ "$L1" == "0" ]
  then
     echo "error.log is within acceptable limits" >> $hvem
  else
     log1=$(du -h /home/nice/etc/error.log)
     echo ${log1} >> $hvem
elif [ "$L2" == "0" ]
  then
     echo "/home/nice/etc/logs/* is within acceptable limits" >> $hvem
  else
     log2=$(du -h /home/nice/etc/logs/* |grep -Ev ^0)
     echo "${log2}" >> $hvem
fi
```

But when i run the script i get
./2M-Locatel_system_overview_script: line 165: syntax error near unexpected token `else'
./2M-Locatel_system_overview_script: line 165: `else if [ "$L2" == "0" ]'

And i cant quite spot the problem. Hope their is someone who can point maybe the obvious out for me :p

---

### Post by ofnuts on 2011-11-18
> **Drenriza said:**
> Hi all.

I have written some bash "code" as follows
```
if [[ "$L1" == 0 && "$L2" == 0 ]]
  then
     echo "logfiles are within acceptable limits" >> $hvem
elif [ "$L1" == "0" ]
  then
     echo "error.log is within acceptable limits" >> $hvem
  else
     log1=$(du -h /home/nice/etc/error.log)
     echo ${log1} >> $hvem
elif [ "$L2" == "0" ]
  then
     echo "/home/nice/etc/logs/* is within acceptable limits" >> $hvem
  else
     log2=$(du -h /home/nice/etc/logs/* |grep -Ev ^0)
     echo "${log2}" >> $hvem
fi
```But when i run the script i get
./2M-Locatel_system_overview_script: line 165: syntax error near unexpected token `else'
./2M-Locatel_system_overview_script: line 165: `else if [ "$L2" == "0" ]'

And i cant quite spot the problem. Hope their is someone who can point maybe the obvious out for me :p
The strange thing is that your error message (''else") doesn't match your code ("elif") (on my version of bash, it is about "elif").

In any case your first "else" (line 162)  closes the whole set of tests for the "if", so one would expect "fi" and not another "elif".

---

### Post by Drenriza on 2011-11-18
> **ofnuts said:**
> I don't know where you line 165 is but after your first "else", that closes the whole set of tests for the "if", one would expect "fi" and not another "elif"?

I see where your headed.
uhmmm

What i was trying to do ( i see my own problem now ) was to create a if statement ( long ) with 3 statements.

If statement #1 was true it would break the two others.
if statement #1 wasn't true it would run #2 and #3.

But yes ofc when #2 then is true #3 will never be reached.

Is their another way of doing what i want?

Since. If #1 is true now, it will stop #2. But #3 will run anyway, giving some silly output
```
if [[ "$L1" == 0 && "$L2" == 0 ]]
  then
     echo "logfiles are within acceptable limits" >> $hvem
elif [ "$L1" == "0" ]
  then
     echo "error.log is within acceptable limits" >> $hvem
  else
     log1=$(du -h /home/nice/etc/error.log)
     echo "${log1}" >> $hvem
fi
if [ "$L2" == "0" ]
  then
     echo "/home/nice/etc/logs/* is within acceptable limits" >> $hvem
  else
     log2=$(du -h /home/nice/etc/logs/* |grep -Ev ^0)
     echo "${log2}" >> $hvem
fi
```

---

### Post by ofnuts on 2011-11-18
> **Drenriza said:**
> I see where your headed.
uhmmm

What i was trying to do ( i see my own problem now ) was to create a if statement ( long ) with 3 statements.

If statement #1 was true it would break the two others.
if statement #1 wasn't true it would run #2 and #3.

But yes ofc when #2 then is true #3 will never be reached.

Is their another way of doing what i want?

Since. If #1 is true now, it will stop #2. But #3 will run anyway, giving some silly output
```
if [[ "$L1" == 0 && "$L2" == 0 ]]
  then
     echo "logfiles are within acceptable limits" >> $hvem
elif [ "$L1" == "0" ]
  then
     echo "error.log is within acceptable limits" >> $hvem
  else
     log1=$(du -h /home/nice/etc/error.log)
     echo "${log1}" >> $hvem
fi
if [ "$L2" == "0" ]
  then
     echo "/home/nice/etc/logs/* is within acceptable limits" >> $hvem
  else
     log2=$(du -h /home/nice/etc/logs/* |grep -Ev ^0)
     echo "${log2}" >> $hvem
fi
```I think you want something like:
```

if [I]both_logs_OK
[/I]then
  echo  both logs OK
else
   if log1_OK
   then 
    echo log1 OK
   else
     write log1 size
   fi
   if log2_OK
   then 
    echo log2 OK
   else
     write log2 size
   fi
fi

```However my personal style is to be more exhaustive for this kind of acitvity, even it it means more messages (i.e., one message per log checked):
```

for log in $logs
do
   if $log_OK
    then 
     echo log $log OK
    else
      write $log size
    fi
 done

```

---

### Post by Drenriza on 2011-11-18
I can also see an idea in writing an "OK" remark for each log. Even this would give more output.

Well another quick question, if no one mind :p

I got some output like the following
```

0anetserv
0appl
0banner
0ccpay
0ckhioc
0clima
0extern
0extres
0game
0gps
0misc
0pmsif
0syslog
0vcrctrl
1tvnet
```

How do you split the word from the number in a way that is easy readable.

---

### Post by ofnuts on 2011-11-18
> **Drenriza said:**
> I can also see an idea in writing an "OK" remark for each log. Even this would give more output.

Well another quick question, if no one mind :p

I got some output like the following
```

0anetserv
0appl
0banner
0ccpay
0ckhioc
0clima
0extern
0extres
0game
0gps
0misc
0pmsif
0syslog
0vcrctrl
1tvnet
```How do you split the word from the number in a way that is easy readable.[http://tldp.org/LDP/abs/html/string-manipulation.html](http://tldp.org/LDP/abs/html/string-manipulation.html)

---

### Post by Drenriza on 2011-11-18
> **ofnuts said:**
> I think you want something like:
```

However my personal style is to be more exhaustive for this kind of acitvity, even it it means more messages (i.e., one message per log checked):
[code]
for log in $logs
do
   if $log_OK
    then 
     echo log $log OK
    else
      write $log size
    fi
 done

```

tried your solution
```
LOG=$(du -b /path/logs/*)

for log in $LOG
do
if [ "$log" \> "1073741824" ]
then
echo "$log is to big" >> $hvem
else
echo "$log OK" >> $hvem
fi
done
```

but i got output as
```

2123 is to big
/path/test.log OK
2152 is to big
/path/test.log OK
2152 is to big
/path/test.log OK
19459 is to big
/path/test.log OK
48 is to big
/path/test.log OK
48 is to big
/path/test.log OK
192 is to big
/path/test.log OK
725 is to big
/path/test.log OK
5654185 is to big
/path/test.log OK
64 is to big
/path/test.log OK
```

I guess this is because it tests the if statement on both words and not the number in the first column. How i get past this and get a better output.

---

