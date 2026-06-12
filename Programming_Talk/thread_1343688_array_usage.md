---
title: "array usage"
date: 2009-12-02
forum: Programming Talk
---

### Post by mo.reina on 2009-12-02
i have these lines of code in a script.
```
#scans for wifi connections, isolates wifi ID, and writes results to list.temp
sudo iwlist scan 2>/dev/null | grep ESSID | sed 's/.*\(ESSID\)/\1/g' >> list.temp

#replaces spaces in essid names with *, otherwise "select" statement will output incorrectly
sed -i 's/ /\*/g' list.temp

#menu of wifi connections
select item in $(cat list.temp); do

```

someone over at the LQ forums suggested i use arrays instead, so as to eliminating the need of replacing spaces with *

```
list=( $(sudo iwlist scan 2>/dev/null |grep ESSID | sed 's/.*ESSID:"\(.*\)".*/\1/') )

...

select item in "${list[@]}"
do
...
done
```

i've created a test script with the array solution and it works perfectly: 
```
#!/bin/bash

list=("one" "two three" "four")
select item in "${list[@]}"; do
	echo $item
done
```

however once i incorporate it into the main script, any SSID names with spaces aren't displayed properly by select.  i think the issue is in populating the array....

---

### Post by mo.reina on 2009-12-02
*bump

---

### Post by Arndt on 2009-12-03
> **mo.reina said:**
> i have these lines of code in a script.
```
#scans for wifi connections, isolates wifi ID, and writes results to list.temp
sudo iwlist scan 2>/dev/null | grep ESSID | sed 's/.*\(ESSID\)/\1/g' >> list.temp

#replaces spaces in essid names with *, otherwise "select" statement will output incorrectly
sed -i 's/ /\*/g' list.temp

#menu of wifi connections
select item in $(cat list.temp); do

```

someone over at the LQ forums suggested i use arrays instead, so as to eliminating the need of replacing spaces with *

```
list=( $(sudo iwlist scan 2>/dev/null |grep ESSID | sed 's/.*ESSID:"\(.*\)".*/\1/') )

...

select item in "${list[@]}"
do
...
done
```

i've created a test script with the array solution and it works perfectly: 
```
#!/bin/bash

list=("one" "two three" "four")
select item in "${list[@]}"; do
	echo $item
done
```

however once i incorporate it into the main script, any SSID names with spaces aren't displayed properly by select.  i think the issue is in populating the array....

Try to narrow the problem down. Can you cut out irrelevant pieces of your actual script so you get something small enough to post here?

---

### Post by mo.reina on 2009-12-03
ok, this is what is in the script right now:
```
sudo iwlist scan 2>/dev/null | grep ESSID | sed 's/.*\(ESSID\)/\1/g' >> list.temp
sed -i 's/ /\*/g' list.temp
select item in $(cat list.temp); do
```
it catches the names of wifi APs and redirects STDOUT to a file.  then it reads the file and replaces all spaces with *, so that the select statement will output correctly.  finally select reads the edited file.


somebody suggested doing it this way instead, doing away with the need to replace the spaces in the wifi AP names.
```
list=( $(sudo iwlist scan 2>/dev/null |grep ESSID | sed 's/.*ESSID:"\(.*\)".*/\1/') )
select item in "${list[@]}"
```

i tried his suggestion in a sample script, and the output is correct.  however when i try it on the main script, the output screws up if there are spaces in any of the AP names.  i'm guessing the problem is populating the array, because if i hard code the AP names into the array, even with spaces, everything is ok.

---

### Post by Arndt on 2009-12-04
> **mo.reina said:**
> ok, this is what is in the script right now:
```
sudo iwlist scan 2>/dev/null | grep ESSID | sed 's/.*\(ESSID\)/\1/g' >> list.temp
sed -i 's/ /\*/g' list.temp
select item in $(cat list.temp); do
```
it catches the names of wifi APs and redirects STDOUT to a file.  then it reads the file and replaces all spaces with *, so that the select statement will output correctly.  finally select reads the edited file.


somebody suggested doing it this way instead, doing away with the need to replace the spaces in the wifi AP names.
```
list=( $(sudo iwlist scan 2>/dev/null |grep ESSID | sed 's/.*ESSID:"\(.*\)".*/\1/') )
select item in "${list[@]}"
```

i tried his suggestion in a sample script, and the output is correct.  however when i try it on the main script, the output screws up if there are spaces in any of the AP names.  i'm guessing the problem is populating the array, because if i hard code the AP names into the array, even with spaces, everything is ok.

Sometimes the answer to why things work differently is that one script is executed by /bin/sh and the other by /bin/bash. Could it be the case here?

---

### Post by ghostdog74 on 2009-12-04
why can't you do this and do away with the useless greps and seds.
```

iwlist scan 2>/dev/null | awk -F":" '/ESSID/{print $2}'

```

---

### Post by openuniverse on 2009-12-04
.

---

### Post by Arndt on 2009-12-04
> **openuniverse said:**
> thanks for this mo.reina, i had no idea that bash could do so many things natively. (rather i always think i do, then someone does even more.)

by the way, can i judge from this thread that sed is "easier" to use than awk? i've been meaning to learn whichever one has a less complicated syntax, but which one is more ubiquitous across 300 distros is also a factor. hope the off-topic question is alright with you, apologies otherwise (though at least it might keep you from having to bump it again.)

Both have "always" been there.

---

### Post by ghostdog74 on 2009-12-04
> **openuniverse said:**
> 
by the way, can i judge from this thread that sed is "easier" to use than awk? 
easier? definitely not. Use sed for simple substitution. Anything beyond, use awk. Better still, you can totally forget about sed. Bold claim?? NO. you can use awk to replace command unix tools like wc, grep, sed, cut, seq, head etc ( to name a few ). This way, you can cut down your learning curve.

---

### Post by openuniverse on 2009-12-04
.

---

### Post by mo.reina on 2009-12-06
> **ghostdog74 said:**
> why can't you do this and do away with the useless greps and seds.
```

iwlist scan 2>/dev/null | awk -F":" '/ESSID/{print $2}'

```

this is in fact better code, i guess it's such a habit to use grep for pattern matching that i do it unconsciously.  

anyway for anyone who's interested, the solution to the array problem was:

```
**eval** list=( $(sudo iwlist scan 2>/dev/null |grep ESSID | sed 's/.*ESSID:\(".*"\).*/\1/')
```

the issue was that the quotes were being treated like regular text because they weren't hard coded, they were being picked up from regular text.  eval solves the problem

---

### Post by mo.reina on 2009-12-06
btw ghostdog i've incorporated your code in my script, link in my sig.

---

