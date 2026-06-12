---
title: "simple bash construct"
date: 2009-07-09
forum: Programming Talk
---

### Post by monkeyking on 2009-07-09
Hi i got a pretty basic bash problem,
but I was wondering if there were some nice way of doing it.

I got 100 files and I need to run a program on each of them,
but I want to start more that one job at a time, I have 8 cores, so running 8 jobs at a time, would seem nice.

I was thinking something like (just for 4 files)

[PHP]
for i in $(ls *.qed); do
    ./prog $i &
    ./prog $i &
    ./prog $i &
    ./prog $i #dont bg the last job
done
[/PHP]
But this will start the job on the same file.

I could elaborate on this with something like
[PHP]
c=0
for i in $(ls *.qed); do
    if[ c == 0 ]
      ./prog $i
      $c=4
    else
      $c--
      ./prog $i &
    fi
done
[/PHP]
But it seems overly complicated

thanks

---

### Post by ghostdog74 on 2009-07-09
```

ls *qed| head -4 | while read FILE
do
 ....
done

```

---

### Post by stylishpants on 2009-07-09
How about reading the filenames from a fifo to keep them ordered, with a simple producer/consumer design?

Something like this:

```

# Create fifo
mkfifo /tmp/fifo1

# Define a shell function that does the actual work
consume() {
> 	i=$1; input=$2;
> 
> 	while read -e f; do 
> 
> 		if [ -e "${f}" ]
> 		then
> 			echo "consumer $i consumes $f";
> 		else
> 			echo "consumer $i cannot consume nonexistent file $f";
> 		fi
> 
> 	done < $input
> 	echo "consumer $i is all done"
> }

# Create 8 consumers that are instances of the shell function
for i in `seq 1 8`; do consume $i /tmp/fifo1 &  echo "consumer $i created"; done


# Dump filenames into the fifo
for f in *.qed; do echo $f > /tmp/fifo1; done

```

Note that most of the code in the consume() shell function is only there to help me convince myself that the code is actually working as expected without corruption. 


You could reduce it down to this:

```
consume() {
> 	while read -e f; do 
> 		./prog $f
> 	done < $1
> }

```
You need the -e on the read command, without that the fifo reads don't seem to block, so you get partial filenames sometimes.

---

### Post by croto on 2009-07-09
How about something simple like:
```

#!/bin/bash

# enter the maximum number of processes you wanna run simultaneously
maxcount=4

count=0
for i in $(ls *.qed); do
    if [ $count -ge $maxcount ]; then
	# wait for all children to finish
	wait
	count=0
    fi
    $count=$(($count+1))

    # here goes the meat
    ./prog $i &

done

```

I didn't test it... but the idea is ok.

---

### Post by ghostdog74 on 2009-07-10
> **croto said:**
> How about something simple like:
```

for i in $(ls *.qed); do
   ....

```


no need to use ls. 
```

for i in *.qed

```

---

### Post by geirha on 2009-07-10
[http://mywiki.wooledge.org/ProcessManagement](http://mywiki.wooledge.org/ProcessManagement)

---

### Post by monkeyking on 2009-07-10
Thanks ppl

---

### Post by stroyan on 2009-07-10
Here is a very different approach.
The make command has a -j option for the level of parallelism.
You could use make to start your arbitrary command.
```

make -r -j 8 -f - *.qed <<<$'.PHONY: FORCE\n%: FORCE\n\t./prog $@'

```

---

### Post by Yuzem on 2009-07-11
Not tested:
```
ls *.qed | {
    while read file; do
        for ((i=1;i<=4;i+=1)); do
            ./prog $file &
            read file
        done
        ./prog $file
    done
}
```

---

### Post by Yuzem on 2009-07-11
This one is much better, it should always keep 4 jobs running, it checks every 5 seconds:

```
for i in *.qed; do
    ./prog $i &
    ((n++))

    while [[ $n > 3 ]]; do
        sleep 5

        n=
        for i in $(jobs -p); do
            ((n++))
        done
    done
done
```

---

