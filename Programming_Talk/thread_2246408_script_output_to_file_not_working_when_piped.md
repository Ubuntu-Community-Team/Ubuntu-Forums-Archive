---
title: "script output to file not working when piped"
date: 2014-09-30
forum: Programming Talk
---

### Post by kevin112 on 2014-09-30
I'll just put it out there now that I barely ever script anything and my knowledge of programming is only slightly above nothing...

That being said I'm currently writing a very simple script to pick out certain lines from a log file and save them to a separate file (filterout.log)

I wrote something for awk that works perfectly from the terminal (logtest.awk)
```

#!/usr/bin/awk -f


BEGIN {


FS=" "
outfile = "filterout.log"
        }


$2 == "AC/BATT_PWR" { print substr ($0,10,30) >> outfile}
$2 == "COMM-FAULT" { print substr ($0,10,30) >> outfile}

```

Now if I run this script against my alarm.log file any lines with those two strings get written to filterout.log

My problem is that eventually I want to monitor alarm.log in real time using tail -f.

To test this I use the following command:
```
tail -f alarm.log | logtest.awk
```
Then manually append events to the alarm.log file by:
```

cat dummyevents.log >> alarm.log

```
This results in nothing being written to my filtered output file.

I'm stumped as to what's happening here, can anyone help me out?

Thanks

---

### Post by Lars Noodén on 2014-09-30
Can you provide a line or two from your dummyevents.log file to see what kind of pattern is needed for the filter?

---

### Post by Lars Noodén on 2014-09-30
Ok.  I read now that your pattern is ok.  It is a matter of buffering.

Ubuntu uses [mawk](http://manpages.ubuntu.com/manpages/trusty/en/man1/mawk.1.html) and it has an option for unbuffered writes to stdout and line buffered reads from stdin.  Try starting mawk with the interactive option set.

```

awk -W interactive ...

```

It's not entirely portable, though.

---

### Post by Vaphell on 2014-09-30
bash equivalent of the script would be something along the lines of 

```
#!/bin/bash

outfile=test.log

while read -r line
do
    IFS=' ' read -ra split <<< "$line"
    [[ ${split[1]} == AC/BATT_PWR ]] && echo "${line:10:30}"
    [[ ${split[1]} == COMM-FAULT ]] && echo "${line:10:30}"
done >> "$outfile"
```

It definitely dumps data in realtime.

---

### Post by kevin112 on 2014-09-30
> **Lars Noodén said:**
> Can you provide a line or two from your dummyevents.log file to see what kind of pattern is needed for the filter?
The events I'm trying to inject look like this
```
000001CB AGC-INTERNL site name              SH:2 SL:2 Wed Dec  8 05:01:41 2004
000001CC SITE-INTRNL site name           SH:0 SL:0 Wed Dec  8 09:39:03 2004
000001CD AC/BATT_PWR site name           SH:0 SL:0 Wed Dec  8 09:39:03 2004
000001CE OCR-GLOBAL  site name       SH:1 SL:4 Wed Dec  8 12:57:32 2004
000001CF SITE-INTRNL site name         SH:0 SL:0 Wed Dec  8 15:43:14 2004
000001D0 AC/BATT_PWR site name           SH:0 SL:0 Wed Dec  8 15:43:14 2004

```
I didn't really explain what i was doing to well.

This is basically a proof of concept for processing serial events from an old NMS system and then pushing out particular events to a paging system. My dummylog file is just to simulate injecting events into a file where eventually the serial data is going to be directed. The only important information is the event and the site name, hence character positions 10-30 since that's the only range of text i need.

> **Vaphell said:**
> bash equivalent of the script would be something along the lines of 

```
#!/bin/bash

outfile=test.log

while read -r line
do
    IFS=' ' read -ra split <<< "$line"
    [[ ${split[1]} == AC/BATT_PWR ]] && echo "${line:10:30}"
    [[ ${split[1]} == COMM-FAULT ]] && echo "${line:10:30}"
done >> "$outfile"
```

It definitely dumps data in realtime.

Thanks a lot, I'll hopefully have a change to test this out later tonight and get back to you. As i mentioned i don't know that much about shell scripting and I'm sure this is pretty basic to you but would you be able to give me a breakdown of what you posted? I'd really like to understand instead of just copy and paste :). TIA

---

### Post by Vaphell on 2014-09-30
*while read* loop eats data on per line basis by default, if you don't give it any file or pipe it will just consume stdin.
*Read* is just a command that takes the first 'record' in the queue and saves it in the $line variable. It's possible to give more vars/array, which makes *read* split the data right off the bat. I initially did it here but noticed you want to use substring of the original record/line later. The while loop keeps going as long as *read* reports success (has things to do). Closing pipe = *read* reporting failure = loop ending.

in the loop body the current $line (equivalent of your $0) is sliced with the space delimiter and an array named split is created (which yields you the equivalent of $1+). It's done by feeding *read* with $line contents with *-a arrayname* params. Like i wrote earlier it was possible to use *read -a arrayname* right in the loop header portion.
$2 will be split[1] because arrays in bash are 0-based. Simple comparison ( [[ ]] are brackets marking conditionals ), if success execute echo with a substring.
Instead of individual echos, all output coming from the the whole loop is redirected to the desired file.

functionally and algorythmically it's pretty much a carbon copy of your awk code, the main difference being in bash you need to manage line reads while awk does it by default.

---

### Post by kevin112 on 2014-10-01
I tested your code and it works where my awk code wasn't

```
tail -f alarm.log | ./logtest.bsh
```

results in new events injected into alarm.log being reported in my filtered file. Thanks a lot

While I'm curious why i had the problem with awk I'm not going to be able to troubleshoot it for the next little while so I'm going to mark this thread solved.

---

