---
title: "bash script"
date: 2011-10-15
forum: Programming Talk
---

### Post by Joufu on 2011-10-15
Hello, I need some help from you guys ;] Can someone help me write a bash scrip? Basically I need to write a script, where you input a date and the script shows files older then the inputed date. Can someone help me with this ? :]

---

### Post by Vaphell on 2011-10-15
date as in day or date as in day with hours, minutes, and seconds and is the day supposed to be included in the result or not.

assuming day alone
```
#!/bin/bash
# usage:
# ./script <folder> <date>

dir="$1"
date="$2"

touch -t **${date//[^0-9]/}0000.00** _older
find "$dir" ! -newer _older -type f
rm _older

```
in the bold part you have the nondigit characters from date string removed, so 2011-11-29 becomes 20111129, as required by touch command
if you want hours and minutes, tweak the bold part (now it's day+00:00:00). for details go to
```
find --help
time --help
```

---

### Post by ofnuts on 2011-10-16
> **Vaphell said:**
> date as in day or date as in day with hours, minutes, and seconds and is the day supposed to be included in the result or not.

assuming day alone
```
#!/bin/bash
# usage:
# ./script <folder> <date>

dir="$1"
date="$2"

touch -t **${date//[^0-9]/}0000.00** _older
find "$dir" ! -newer _older -type f
rm _older

```in the bold part you have the nondigit characters from date string removed, so 2011-11-29 becomes 20111129, as required by touch command
if you want hours and minutes, tweak the bold part (now it's day+00:00:00). for details go to
```
find --help
time --help
```
No need to create a temp file, you can use -newermt *date* (this is documented as "newerXY" in man find, and yes, the syntax is very strange and I'd love to know an explanation....), so for instance:
```
find . -newermt "20111014 1200"
```The date format is no too strict, it is whatever "date -d" accepts (see "info date")

---

### Post by Vaphell on 2011-10-16
cool, i didn't know that there is something like newerXY (though i was a bit surprised that only test against a file seemed possible), it's not mentioned in --help and i didn't bother reading man :-)

Syntax doesn't sound too strange to me. When you test against a file, X and Y are codes of timestamps (a/B/c/m) for tested file and timestamp_file respectively (eg 'ac' = access-time tested against change-time). When you test against a date, Y=t.
X != t for obvious reasons - tested file will never be a literal time.

---

### Post by ofnuts on 2011-10-16
> **Vaphell said:**
> cool, i didn't know that there is something like newerXY (though i was a bit surprised that only test against a file seemed possible), it's not mentioned in --help and i didn't bother reading man :-)

Syntax doesn't sound too strange to me. When you test against a file, X and Y are codes of timestamps (a/B/c/m) for tested file and timestamp_file respectively (eg 'ac' = access-time tested against change-time). When you test against a date, Y=t.
X != t for obvious reasons - tested file will never be a literal time.Ah, get it.... thanks for the heads up...

---

