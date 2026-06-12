---
title: "Please help to come up with a filter"
date: 2013-07-05
forum: New to Ubuntu
---

### Post by elementX on 2013-07-05
I have a folder in which several new files are created every day. What I need is some simple stats being created by a script that runs every few hours.

Specifics: the script needs to display the amount of files created on a specific date. So if I had 25 files created today(5th July) and 22 on the 4th and 7 on the 3rd I need the script to display sth along that line:
>3rd July 2013    7
>4th July 2013    22
>5th July 2013    25

Date needs to be taken automatically from lets say 'ls' command. I'd rather not have to provide it for the script(in this case I can write the code myself). I was thinking about incrementing but not sure how could it work with a date(I have some files from June as well).
I know how to use grep, awk, wc, etc but am struggling to put them together in a script :( 
Any help will be appreciated.

---

### Post by steeldriver on 2013-07-05
How about using find / sort / uniq?

```
find /path/to/dir -maxdepth 1 -type f -printf "%Ad %Ab %AY\n" | sort -k3n,3 -k2M,2 -k1n,1 | uniq -c
```

---

### Post by elementX on 2013-07-05
Wow! Awesome :D Thanks!

---

### Post by steeldriver on 2013-07-05
You're welcome :) If you need the counts to be last instead of first (where 'uniq -c' puts them), you could stick an awk on the end to reorder the fields 

```
... | awk '{print $2, $3, $4, $1}'
```

---

### Post by elementX on 2013-07-05
Nah, doesn't need to be pretty - it needs to work and display the right info ;) Thanks again!

---

