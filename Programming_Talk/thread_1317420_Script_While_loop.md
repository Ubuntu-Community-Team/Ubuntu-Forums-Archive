---
title: "Script While loop"
date: 2009-11-06
forum: Programming Talk
---

### Post by SpinningAround on 2009-11-06
Is it possible to make a while loop check if a number inside a varible isn't equal to one? I'm trying to get this part of script to work but can't get the value from $?

```

#!/bin/bash

while [ $? != 1 ]
do
	ifconfig | grep -q eth0
	sleep 2
done 
echo date > network.txt

```

Code that $? in terminal return
```

:~$ $?
0: command not found

```

what i wish to return
```

:~$ echo $?
0


```

---

### Post by MadCow108 on 2009-11-06
string and integer comparisons have different operators
use -ne and quote your arguments
[http://tldp.org/LDP/abs/html/comparison-ops.html](http://tldp.org/LDP/abs/html/comparison-ops.html)

also $? will hold the return of sleep (which will always be 0 I guess) not of the above command
If you need the above save the value of $? in another variable (or break the loop directly)

---

### Post by lavinog on 2009-11-07
First the exit status from grep can be >1 if there is an error.  You should loop while status == 0
```

#!/bin/bash
status=true
while [ "$status" -eq "0" ]
do
	ifconfig | grep -q eth0
	status=$?

	sleep 2
done 
echo date > network.txt

```

---

### Post by SpinningAround on 2009-11-07
Thanks for the help, it is working now :D also thanks for the link

---

### Post by geirha on 2009-11-07
You really only need to save $? if you need to check for different type of error codes. If you just need to check if it succeeded or failed, run the while loop on the command rather than on a [-command.
```

while ifconfig | grep -q eth0; do 
  sleep 2 
done

```

---

