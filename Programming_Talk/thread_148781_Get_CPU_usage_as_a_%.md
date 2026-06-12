---
title: "Get CPU usage as a %"
date: 2006-03-22
forum: Programming Talk
---

### Post by Randomskk on 2006-03-22
Heya
I'm making a script to control some LEDs attached to my pc, I want them to serve as a kinda bar graph for CPU usage (four LEDs, so none for 0%, one for 25%, two for 50%, etc...).
However, the biggest problem I'm having right now is getting a script to see the CPU usage.
While it's easy to see using a GUI program, I've tried to get a script /C program to do so and failed..
/proc/loadavg doesn't seem to relate to the CPU usage, and while "ps -e -o pcpu" will show me a list of %s, I have no idea how I could add them together.

I've searched for any programs to do so and come up blank ](*,) 

So, does anyone know of any way I could have a BASH/Python script, or a C program, get the load avarage and output it as a %? Because I'm stumped :(

---

### Post by JmSchanck on 2006-03-22
The first line in /proc/stat says cpu and then has several numbers after it. The first 4  numbers are user, nice, system, and idle times (these values are simply the amount of time the cpu has spent in each since last boot). 

Should look something like this:
```

cpu  **3637881 11829 781587 33547506** 219684 71147 256792 0

```
(We're only concerned with the bolded values)

To get the average system load over any given amount of time you read those four values into variable (for example, ill call them u1, n1, s1, and i1). Then when you're ready you read the values again into new variables, u2, n2, s2, and i2. Now your total usage time is equal to (u2-u1) + (n2 - n1) + (s2 - s1). And your total time overall is the usage time + (i2-i1). Take (100*usage)/total and you have your percent CPU Usage. :)

---

### Post by supirman on 2006-03-22
I don't know if this is useful or not, I just whipped it together.  I make no claims as to its accuracy, but it seems decent:

you can put this as a bash script:  
ps aux|awk 'NR > 0 { s +=$3 }; END {print "cpu %",s}'

That just sums up the cpu% column from the output of ps aux.

---

### Post by jerome bettis on 2006-03-23
^ that won't give you an accurate measure.

i wrote a python script for someone a while ago to do this.  i read some stuff on how to calculate it.  i'm 100% sure this is correct - i adapted it from a C program someone who knows what they're talking about wrote.

[php]#!/usr/bin/env python

import time

TIMEFORMAT = "%m/%d/%y %H:%M:%S"
INTERVAL = 2

def getTimeList():
    statFile = file("/proc/stat", "r")
    timeList = statFile.readline().split(" ")[2:6]
    statFile.close()
    for i in range(len(timeList))  :
        timeList[i] = int(timeList[i])
    return timeList

def deltaTime(interval)  :
    x = getTimeList()
    time.sleep(interval)
    y = getTimeList()
    for i in range(len(x))  :
        y[i] -= x[i]
    return y

if __name__ == "__main__"  :
    while True  :
        dt = deltaTime(INTERVAL)
        timeStamp = time.strftime(TIMEFORMAT)
        cpuPct = 100 - (dt[len(dt) - 1] * 100.00 / sum(dt))
        print timeStamp + "\t" + str('%.4f' %cpuPct)[/php]

---

### Post by Randomskk on 2006-03-23
[QUOTE=supirman]I don't know if this is useful or not, I just whipped it together.  I make no claims as to its accuracy, but it seems decent:

you can put this as a bash script:  
ps aux|awk 'NR > 0 { s +=$3 }; END {print "cpu %",s}'

That just sums up the cpu% column from the output of ps aux.[/QUOTE]
Would this be accurate to within 25%? Seeing as that's about as accurate as four LEDs can get, this would be the simplest solution.
But yea, if it wouldn't be quite accurate enough I can probably play with that python script to get it outputting what I need :D

Thanks for the help guys :KS

---

### Post by Randomskk on 2006-03-23
Ok, well I decided to go with the Python script based on accuracy. I modified it to just output the current CPU % with no extra text once then quit (just take out "while True  :" and change "print timeStamp + "\t" + str('%.4f' %cpuPct)" to "print int(cpuPct)")

However, now I have a different (and much more basic :P) problem: how can I have my BASH script run this file and read the output into a variable?

---

### Post by jerome bettis on 2006-03-23
x=`/path/cpupct.py`

those are back quotes ` ` the key in the top left corner, next to 1.

---

### Post by Randomskk on 2006-03-23
Sweet, thanks a load :D

---

