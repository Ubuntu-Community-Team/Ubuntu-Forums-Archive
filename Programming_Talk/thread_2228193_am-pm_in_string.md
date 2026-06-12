---
title: "am-pm in string"
date: 2014-06-06
forum: Programming Talk
---

### Post by peter_brickles on 2014-06-06
HI guys 

i have a variable in bash which conatins a string with the time in 24 hour format as follows 

> [h=3]11:00 - 13:10[/h]

this is scraped from the web not piped from a linux command is there any way to easy add am pm to it ? 

> [h=3]11:00  AM - 13:10 PM[/h]

any help would be greatly appreciated

---

### Post by Vaphell on 2014-06-06
13pm? is that even a thing? am/pm relate to 12hr clock


```
$ h24to12() { local h m ampm=(am pm); IFS=: read h m <<< "$1"; echo $(( (h+23)%12+1 )):$m${ampm[h/12%2]}; }; 
$ t='11:00 - 13:10'
$ t1=${t%% -*}; t2=${t##*- }
$ echo "$(h24to12 "$t1") - $(h24to12 "$t2")"
11:00am - 1:10pm
```

---

### Post by dwhitney67 on 2014-06-06
You may have to decompose the string "11:00 - 13:10" into 3 parts that are separated by white-space.  Then reconstruct a new string with the the first token, followed by AM, then then the hyphen, and finally the last token with the trailing PM string.

```

time="11:00 - 13:00"

tokens=( $time )

echo ${tokens[0]} AM ${tokens[1]} ${tokens[2]} PM

```

Btw, if you are dealing with 24-hour clock representation, isn't it superfluous to use the AM and PM designations?

---

### Post by ajgreeny on 2014-06-06
Add **%p** to the string in your variable, though I'm not sure what exactly you mean by "**this is scraped from the web not piped from a linux command is there any way to easy add am pm to it ?**" so if this is not a standard bash variable it may not work as you want.

---

