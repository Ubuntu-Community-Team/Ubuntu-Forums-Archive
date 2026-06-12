---
title: "Bash help, probably easy"
date: 2012-03-04
forum: Programming Talk
---

### Post by CaptainMark on 2012-03-04
Hi, im just jotting a short script to sort photos (they get uploaded automatically from my cloud via my phone and the script is to place them into folders arranged in year and month slots) my bash scripting is beginner standard at best and i cant seem to figure out how to take only set characters from stdout, for example

```
jhead DSCN0132.JPG | grep Date/Time
```gives me ```
Date/Time    : 2012:01:11 18:32:53
```i need to set a variable of year and month, its always the same characters year being characters 16-19 and month being characters 21 & 22, im sure its simple but my google search brings up stuff that is way over my head, 

Thanks for any help
Mark

---

### Post by codemaniac on 2012-03-04
Hello friend ,

I guess you want to collect YEAR , MONTH attributes in different bash variables .Try like below .

```
YEAR=$(echo "Date/Time    : 2012:01:11 18:32:53" | cut -c 16-19)
MONTH=$(echo "Date/Time    : 2012:01:11 18:32:53" | cut -c 21-22)
```

---

### Post by Khayyam on 2012-03-04
I know, I know .. you have to use grep because awk gives you cancer :)

So, risking all potential hazards:

```
echo "Date/Time    : 2012:01:11 18:32:53" | awk -F ":" '{gsub(/ /,"",$2); print "YEAR="$2"\n""MONTH="$3}'
```I'd probably do a better job if I could see the output provided by 'jhead' .. the use of ":" as a seperator might break something. So, first we'll try with ":" ...

```
jhead DSCN0132.JPG |  awk -F ":" '/Date/{gsub(/ /,"",$2); print "YEAR="$2"\n""MONTH="$3}'
```If it doesn't work, then drop the use of -F ":" and just use space as FS ... should work the same as above but uses 'substr' to weed out the string

```
jhead DSCN0132.JPG | awk '/Date/{print "YEAR="(substr($3,1,4))"\n""MONTH="(substr($3,6,2))}'
```

HTH ... khay

---

### Post by CaptainMark on 2012-03-05
ah the cut command, ive used this before how i managed to forget about it i dont know, thanks

this also works,

```
timestamp=$(jhead $HOME/Pictures/$photo | grep Date/Time)
year=${timestamp:15:4}
month=${timestamp:20:2}
```

---

