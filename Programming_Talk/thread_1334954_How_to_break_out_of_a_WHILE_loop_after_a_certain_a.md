---
title: "How to break out of a WHILE loop after a certain amount of time?"
date: 2009-11-23
forum: Programming Talk
---

### Post by negativ on 2009-11-23
I have a script that checks many subdirectories looking for "foo.txt".  

I'm an utter novice, so I'm probably going about it all wrong.

we have:

/working/path/abc
/working/path/xyz
/working/path/random
/working/path/unpredictable
/working/path/blah

When foo.txt is found in one of those subdirectories, the subdirectory is moved.  Eventually, foo.txt will exist in all subdirectories and /working/path will become empty, but it might take 10 seconds, or 2 hours.  My script works, but I'd rather not be stuck in a loop for 2 hours checking for foo.txt.  

Is there a way to have the script give up after, oh say 30 seconds?

edit:

sorry, this is a bash script.  Should have mentioned.

---

### Post by mo.reina on 2009-11-23
deleted, didn't read the question right

---

### Post by Nevon on 2009-11-23
It wouldn't be exact, but I suppose you could just check the starting time and do something like:
```
while ($starttime < ($starttime+30)) {
    do stuff
}
```

---

### Post by mo.reina on 2009-11-23
i'm not sure if there is a built-in function that handles this

you can do a rough kind of time check through the `date +%s` command, where you the output to one variable in the beginning and keep it static (this is your reference point), then have another variable keep running `date +%s` until X number of seconds have passed (you reference with the first variable).

something like this:

```
counter=0
temp=1


while [ $temp != 0 ]; do
        if [ $temp == 1 ]; then #ensures that this is only done on the first pass
                starttime=$(date +%s) #start time of the loop
        fi
        runningtime=$(date +%s) #this is your running time
        if [ $runningtime == $[$starttime+30] ]; then #if running time = start time + 30 seconds
                echo "30 seconds have elapsed in the while loop"
                break
        fi
        temp=$[$temp+1]
done

```

just adjust depending on how many seconds you want it to run

---

### Post by Nevon on 2009-11-23
Eh, I don't know what I was thinking when I wrote that. I was pretty stressed and on my way to the bus. I guess that's why.

Anyway, what I meant was more like this:
```
while ($currenttime < $starttime+30) {
    do stuff
}
```

---

