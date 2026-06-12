---
title: "seelct case based on current time"
date: 2015-07-19
forum: Programming Talk
---

### Post by peter_brickles on 2015-07-19
HI Guys im tring to write a bash sccript which will give me the time of the next us from my local stop 

i have a list of times as below 

> 
0735
0805
0835
0905
0935
0950
1020
1050
1120
1150
1220
1250
1320
1350
1420
1450
1520
1550
1620
1650
1650
1720
1800
1840
1922
1942
2002
2022
2102


but have no dea how to do thia using a select case of if then statment can any one give me a heads up ? 

any help would be appreciated 

Pete

---

### Post by Lars Noodén on 2015-07-19
here's one way using an if statement and storing the times in a file

```

#!/bin/sh

now="$(date +'%H%M')";
for time in $(cat times.list);
do
 if [ "$now" -lt "$time" ]; then
   echo $time;
   exit 0;
 fi
done;
echo You missed the last bus
exit 1;

```

---

