---
title: "How to find/display out last Friday's date of the month"
date: 2013-03-21
forum: Programming Talk
---

### Post by sunnysthakur on 2013-03-21
[COLOR=#000000][FONT=Verdana]Hello,[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Can you please help me find/display out last Friday's date of the month using command in Unix/Linux[/FONT][/COLOR]

---

### Post by CaptainMark on 2013-03-21
Yes ```
date --date="last Fri"
```This will accept arguments found in the man date page, for example```
mark@desktop ~/ $ date --date="last Fri" +%x
15/03/13

```

---

### Post by schragge on 2013-03-21
This will show the last Friday counting from now. What the OP wants is something like what you get in ksh93 with
```
ksh93 -c 'printf "%(%x)T\n" "last fri in apr 2013"'
```
or in perl with
```
 perl -MDate::Manip -e 'print UnixDate(ParseDate("last fri in apr 2013"), "%F"),"\n"'
```

---

### Post by sunnysthakur on 2013-03-21
> **CaptainMark said:**
> Yes ```
date --date="last Fri"
```This will accept arguments found in the man date page, for example```
mark@desktop ~/ $ date --date="last Fri" +%x
15/03/13

```

This shows previous friday's date...not last friday's date of the month.
I already tried this option...The output date should be 29 march....

---

### Post by sunnysthakur on 2013-03-21
Hi schragge.

Appreciating your help..
this logic works for me.

Is there any method that we don't have to manually change "[COLOR=#000000][FONT=Ubuntu Mono]last fri in apr 2013[/FONT][/COLOR]" every time..just execute the command in any month and will show last day's date of month.

---

### Post by schragge on 2013-03-21
In ksh93, you can simply change the example to
```
ksh93 -c 'printf "%(%x)T\n" "last fri in this month"'
```
This doesn't work in perl, better read up [the documentation]("http://search.cpan.org/~sbeck/Date-Manip-6.39/lib/Date/Manip/Date.pod") and experiment a bit.

Or you can do it like this:
```
cal -h|cut -c16,17|sed '/^ *$/d'|tail -1
```

---

### Post by diesch on 2013-03-21
```
 cal -N |awk '/^Fr/ {print $(NF)}'
``` prints just the day of month.
Use something like
```
date +"%Y-%m-$(cal -N |awk '/^Fr/ {print $(NF)}')"
``` to get a full date.

---

### Post by malspa on 2013-03-21
> **sunnysthakur said:**
> The output date should be 29 march....

> **diesch said:**
> Use something like
```
date +"%Y-%m-$(cal -N |awk '/^Fr/ {print $(NF)}')"
``` to get a full date.

So then:

```
$ **date +"$(cal -N |awk '/^Fr/ {print $(NF)}') %B"**
29 March
```

---

### Post by ofnuts on 2013-03-21
Bit of a brute force approach using the "nth day" syntax of date: find the Nth day of week in the future that is still the right month:
```

thismonth=$(date +%m)
for i in {5..0};
do 
    trymonth=$(date -d "$i friday" +%m)
    if [[ $trymonth == $thismonth ]] 
    then 
        goodone=$i 
        break
    fi
done
[[ -z $goodone ]] || date -d "$goodone friday"

```
Of course, plenty of interesting things happen if you are on or past that last day ($goodone empty:)

---

### Post by schragge on 2013-03-21
Why would $goodone be empty on the last Friday? Isn't *-d "0 friday"* aka *-d "this friday"* supposed to return the current month number on that day?

---

### Post by ofnuts on 2013-03-21
Because in the last days of the month, '0 friday' could fall in the next month so $trymonth would never be equal to $thismonth. No?

---

### Post by schragge on 2013-03-21
Yes, in the days after the last Friday, but not _on_ that last Friday. No? E.g the last Friday is 29th of this month. Your script will still work on this day, but not on 30th.

---

### Post by CaptainMark on 2013-03-21
Sorry, last fridays date of the month is what you asked for, I see you wanted the date of the last friday in the month

---

### Post by ofnuts on 2013-03-21
> **schragge said:**
> Yes, in the days after the last Friday, but not _on_ that last Friday. No? E.g the last Friday is 29th of this month. Your script will still work on this day, but not on 30th.
Hmm, yes. Never tested what happened with "date -d "0 $(date +%A)"". So iterating to 0 can be a solution.

---

### Post by sunnysthakur on 2013-03-29
This also works for me

cal 03 2013 | awk 'NR==1 {m=substr($1, 1, 3); y=$2} NF>5 {d=$6} END {print "Friday", m, d, y}'

---

### Post by schragge on 2013-03-29
Combining this with the [post=12567206]code[/post] suggested by **diesch**, I get
```
ncal -h|awk 'NR==1{m=substr($1,1,3);y=$2}/^Fr/{print"Friday,",m,$NF,y}'
```
Just for fun, the same in sed:
```
ncal -h|sed -nr '1h;/^Fr/{G;s/.*( \w+) *\n *(\w{3})\w*/Friday, \2\1/p}'
```

---

