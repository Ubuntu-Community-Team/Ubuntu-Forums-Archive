---
title: "subshell"
date: 2009-08-19
forum: Programming Talk
---

### Post by navaneethan on 2009-08-19
> dated_fname(){
set --'date'
year='expr $6: '..\(..\)'
echo "$2$3_$year"
} 

$dated fname
jan28_03


In this program in 4th line what does it mean??

I don't know the knowledge about what 3,2 means in 4th line?

---

### Post by DaithiF on 2009-08-19
dated_fname(){
set --'date'
year='expr $6: '..\(..\)'
echo "$2$3_$year"
}

the date command on its own would give output like:
Wed Aug 19 13:31:45 GMTDT 2009

when you do set -- `date` [ or better again: set -- $(date)  ]
it assigns the result of the date command to N variables $1, $2, $3, ... etc, representing the constituent parts of the date, so
$1 = Wed
$2 = Aug
$3 = 19
....
$6 = 2009

line 3 applies a regular expression to the year variable to strip out the leading 2 digits.
line 4 prints out the month day _ year pieces

to be honest this is a bit convoluted and unnecessary -- you could just use the date command like so:
date +%b%d_%y
and you would get the same result
Aug19_09

---

