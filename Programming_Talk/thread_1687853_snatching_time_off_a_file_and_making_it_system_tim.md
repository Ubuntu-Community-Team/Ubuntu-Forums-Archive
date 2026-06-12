---
title: "snatching time off a file and making it system time."
date: 2011-02-14
forum: Programming Talk
---

### Post by asorron on 2011-02-14
Hey, im experiencing some issues developing a small script, it isnt that tough but im unaware of some commands to use since the target computer that im gonna use the code on isnt having ubuntu, so most of the updated commands wont work (unless it's installed on it)

well anyway, i'm getting a date&time off a file, iv'e managed to do so, and i only need the time part (not day/month/year)
the file is a proccess running, so i need the last and most update one (for sync purposes)
the output of that proccess will have some un-needed parts at the start, and then it starts to post date&time in this format, while its repeative and updating its lifespan ;
```
day = 31
month = 12
year = 1999
secs = 79200
day = 31
month = 12
year = 1999
secs = 79201
```so it looks like this so far;
```
#!/bin/bash
function cutter
{
cat /usr/test/target|grep secs |tr -d "secs ="|tail -n 1
}
cutter
```the output of the file will eventually be the last integer stripped from "secs =", so in the case above, it should be "79201".

The help i need is, transforming the "79201" into a date format that i can input it to system's date by ```
/bin/date
``` command

I've tried working around with bc, but as far as i seen, the output of bc calculations are all integers, and i must have it as double because it must be exact as much as possible (syncing reasons)

in depth: the thing that it will have to do in order to calculate it is 79201 divided by 60, 
which is 1320.0167, taking the remainder and multiply it by 60 will give me the current seconds, (0.0167*60=1.002 < can ignore the remainder if it goes milisec) and doing the same for the minutes and hours... so it turns out as 22:00:01 in the latter case above.
Also, once "secs = xxxxx" reaches 86400 it makes "day =1" "month =1" and "year =2000", plus theres an exception of 2 hours, so when its 22:00:00, it should be 00:00:00 on the system clock..

I know it gets complex but ill try to rephrase that if someone will want to give a hand :]

I'm kinda new into programming and I've always liked it, just need some help knowing getting along with it..

ps; i tried using "sed' instead of "tr -d", it took me over 3 hours with no success :( lucky iv'e found "tr -d" somewhere :lolflag:

Thanks in advance;

Ron

---

### Post by Vaphell on 2011-02-14
1. you don't need doubles, integer arithmetic is enough and in fact more suitable. Your way introduces rounding errors while in integer math there is no way to get fractions.
2. date can do the calculation easily, you don't want to mess with numbers of days in months, leap years and stuff.

[php]#!/bin/bash

yr=1999
mon=12
day=31
secs=86399

hr=$((secs/3600))
min=$(((secs-hr*3600)/60))
sec=$((secs-hr*3600-min*60))
echo $secs: $hr:$min:$sec

secs=111111
echo "${mon}/${day}/${yr} +${secs}seconds"
date -d "${mon}/${day}/${yr} +${secs}seconds"[/php]

3. example of sed returning a number from line in name=value format
```
echo $'something = 3000\nsecs = 2500'
echo $'something = 3000\nsecs = 2500' | grep secs | sed 's/[^0-9]*//'
```

's/[^0-9]*//' = replace any non-digit sequence with nothing ('name = ' matches)

---

### Post by asorron on 2011-02-15
thank god, you confirmed my suspections that date has "+amountoftime" expansions...
im going to include it in the code and do a simulation without the updating logfile, i think i should change the tail -n to about 6, so it keeps the last 6 strings without showing the whole log (which takes a little bit longer...)

---

### Post by asorron on 2011-02-15
```
#!/bin/bash
function cutter
{
 cat /home/ron/logfile | tail -n 5| tr -d " "
}

#lets say it contains
#secs = 12268
#day = 3
#month = 8
#year = 1999
#secs = 16868
#day = 3
#month = 8
#year = 1999
#it has some sentences at start, but im counting on ignoring them while the tail gets them off, the tail of the logfile should contain only the time format.

cutter
#i think im doing wrong here while using cat to get the file, because it just echoes them and wont use it in the script (for my suspections) because it wont work

hr=$((secs/3600))
min=$(((secs-hr*3600)/60))
sec=$((secs-hr*3600-min*60))
echo $secs: $hr:$min:$sec

echo "${mon}/${day}/${yr} +${secs}seconds"
date -d "${mon}/${day}/${yr} +${secs}seconds"

``````
Output of: /home/ron/cutter
year=1999
secs=16868
day=3
month=8
year=1999
: 0:0:0
// +seconds
date: invalid date `// +seconds'

```so the problem now is that it wont really take the logfile into the script and use the date as variables, it just echoes them to the terminal and nullify it.

edit:solved it out by redirecting it and calling another bash script, like so;
```
function cutter
{
echo "#!/bin/bash">/home/ron/newerlog
echo declare day variable>>/home/ron/newerlog
echo declare month variable>>/home/ron/newerlog
echo declare year variable >>/home/ron/newerlog
echo declare secs variable >>/home/ron/newerlog
 cat /home/ron/newlog|tail -n 5|tr -d " ">>/home/ron/newerlog
chmod 777 /home/ron/newerlog

}
. /home/ron/newerlog
hr=$((secs/3600))
min=$(((secs-hr*3600)/60))
sec=$((secs-hr*3600-min*60))
echo $secs: $hr:$min:$sec
echo "${mon}/${day}/${yr} +${secs}seconds"
date -d "${mon}/${day}/${yr} +${secs}seconds"

```problem is, it gets me some errors ;
```
Output of: bash -x /home/ron/cutter
+ . /home/ron/newerlog
++ declare day variable
++ declare month variable
++ declare year variable
++ declare secs variable
++ year=1999
++ secs=16868
++ day=3
++ month=8
++ year=1999
+ hr=4
+ min=41
+ sec=8
+ echo 16868: 4:41:8
16868: 4:41:8
+ echo '/3/ +16868seconds'
/3/ +16868seconds
+ date -d '/3/ +16868seconds'
date: invalid date `/3/ +16868seconds'

```as you can see, for some reason it "forgets" the date variables...

stupid me, i called the wrong variable, i declared it as "month" on the subscript, and it's mon on the main, anything works now.
just need to know:

if im doing ```
sec=$((secs-hr*3600-min*60**+****7200**))
```, will it cure the 2 hours offset? i hope it wont cause any overflow errors.

---

### Post by geirha on 2011-02-15
You never tell bash to capture the output. See [http://mywiki.wooledge.org/BashFAQ/002](http://mywiki.wooledge.org/BashFAQ/002)

I'd just use bash to parse that file though.
```

#!/bin/bash

while read -r line; do
  case $line in
    "year = "*) year=${line#*= };;
    "month = "*) month=${line#*= };;
    "day = "*) day=${line#*= };;
    "secs = "*) secs=${line#*= };;
  esac
done < <(the_command_that_produces_the_output)

date -d "$year-$month-$day +$secs seconds"

```

Read [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide) to get to grips with bash. It's not a good idea to simply guess on the syntax.

---

### Post by Vaphell on 2011-02-15
> **asorron said:**
> if im doing ```
sec=$((secs-hr*3600-min*60**+****7200**))
```, will it cure the 2 hours offset? i hope it wont cause any overflow errors.

you don't need to go the hr/min/sec route at all, i merely showed how to calculate the hh:mm:ss out of seconds just so you know. It's completely unnecessary as the date can do it even better with no hassle as it handles overflows right off the but while hr/min/sec route doesn't. Get your raw seconds, add 7200 and use that number in +Xseconds part of date command, don't bother with intermediate hr/min/sec variables.

---

### Post by asorron on 2011-02-15
okay its done, fixed the 2 hour offset by adding 7200 to secs value, (i didnt even knew how to do math before this vaphell, so thanks alot for brightning that out (i almost tried bc -l #include <math.h> >_<!)
```
#!/bin/bash
declare secs variable
function cutter
{
echo "#!/bin/bash">/home/ron/newerlog
echo declare day variable>>/home/ron/newerlog
echo declare month variable>>/home/ron/newerlog
echo declare year variable >>/home/ron/newerlog
echo declare secs variable >>/home/ron/newerlog
 cat /home/ron/newlog|tail -n 5|tr -d " ">>/home/ron/newerlog
chmod 777 /home/ron/newerlog
}
cutter
. /home/ron/newerlog
secs=$(($secs+7200))
#i included it at the inputted variable from the other script so it save some hassle :]
hr=$((secs/3600))
min=$(((secs-hr*3600)/60))
sec=$((secs-hr*3600-min*60))
#the echoes are just reference to myself to see what im having according to the other syncing system time...
echo $secs: $hr:$min:$sec
echo "${month}/${day}/${year} +${secs}seconds"
date -d "${month}/${day}/${year} +${secs}seconds"
rm /home/ron/newerlog

```

---

### Post by geirha on 2011-02-15
Lose the chmod 777. That's pointless, and introduces an unnecessary security issue.

---

### Post by Vaphell on 2011-02-15
you also need to figure out how to set time, date -d works like a calculator with arbitrary dates but doesn't do anything with them, in **date --help** lists a **-s** switch to set the date.

---

### Post by asorron on 2011-02-16
yeah just never knew you can tweak the date with +${value} , thanks for the tip its working here, i need it for my work and i have issues with it there, the code is perfect but im having trouble getting it off a proccess needs to be called at, which wont work before the system load (it must be before the system load)
it catches it from a serial port, which when i call the proccess itself, it doesnt know which port to use, unless the system load and sets the port for it.

i'll consult the os programmers at work and see how we can sort it out...

thanks, ill mark this one as solved.

---

