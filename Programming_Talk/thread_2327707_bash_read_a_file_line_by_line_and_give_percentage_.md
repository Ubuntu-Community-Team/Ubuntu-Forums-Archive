---
title: "bash read a file line by line and give percentage of task completed"
date: 2016-06-13
forum: Programming Talk
---

### Post by peter_brickles on 2016-06-13
hi guys im trying to read  file line by line which i have successfully done before but as Im using a large file i want to update the terminal with a % completed message on each iteration so far i have 


> 

#!/bin/bash 

filename="$1" #take the file name as an arguement 

linecount=$(wc -l $filename) #count the lines of the file 

echo $linecount

while read -r line #the loop
do
counter=$((counter + 1)) #increement counter so we know which line were on 
taskpercent=$((counter/linecount*100)) #calculate percentage complete 

echo "Reading line $counter of $linecount currently % $taskpercent done" #update with details 

done < "$filename"



when i run this with a large file 

> ./test postcode.csv




i get the following error 

> 
./test: line 13: 2869 postcode.csv: syntax error: invalid arithmetic operator (error token is ".csv")




can any one give me a heads up ? 

Cheers Pete

---

### Post by sudodus on 2016-06-13
What happens if you start with ```
counter=0
``` (before the loop)?

-o-

There is also ***pv***, which can be used to monitor read/write progress.

```
sudo add-apt-repository universe  # if standard Ubuntu
sudo apt-get update

sudo apt-get install pv
```

---

### Post by peter_brickles on 2016-06-13
setting the variable to 0  has no affect on the error message im not really up to speed with running it with the script ie 

> pv ./test 

and in the loop the % bar just came up at the end of the script

---

### Post by sudodus on 2016-06-13
1. I found 3 errors, that needed fixing (see *text*)

#!/bin/bash

```
filename="$1" #take the file name as an arguement

linecount=$(wc -l $filename |cut -d ' ' -f1) #count the lines of the file *you must have a clean number, not a number plus a file name*

echo $linecount
counter=0  # *you need a numeric start value*
while read -r line #the loop
do
counter=$((counter + 1)) #increement counter so we know which line were on
echo $counter
taskpercent=$((100*counter/linecount)) #calculate percentage complete *you should multiply by 100 at once, otherwise it will be truncated to zero until the end*

echo "Reading line $counter of $linecount currently % $taskpercent done" #update with details

done < "$filename"
```

-o-

Using pv to copy to the file **ttt**:

```
pv postcode.csv > ttt
```

but it might be too fast for you to see what happens, so try with a big file, for example an Ubuntu iso file

```
pv ubuntu-16.04-desktop-amd64.iso > ttt
1,38GiB 0:00:27 [50,6MiB/s] [==================================================================================>] 100%
```

---

### Post by steeldriver on 2016-06-13
The error is because 

```

wc -l $filename

```

includes the filename as well as the count - you can suppress that by redirecting i.e.

```

linecount=$(wc -l [COLOR=#0000ff]**<**[/COLOR] $filename)

```

For the actual calculation part, you will probably find that ORDER is important (because of rounding, counter/linecount will always be 0) i.e.

```

taskpercent=$((counter*100/linecount))

```

---

### Post by peter_brickles on 2016-06-13
> **steeldriver said:**
> The error is because 

```

wc -l $filename

```

includes the filename as well as the count - you can suppress that by redirecting i.e.

```

linecount=$(wc -l [COLOR=#0000ff]**<**[/COLOR] $filename)

```

For the actual calculation part, you will probably find that ORDER is important (because of rounding, counter/linecount will always be 0) i.e.

```

taskpercent=$((counter*100/linecount))

```

thanks for the heads up guys 

@steeldriver worked a treat marked as solved

---

