---
title: "Bash Shell Script Help! Add uptime logged users."
date: 2012-03-07
forum: Programming Talk
---

### Post by AprendizZ on 2012-03-07
Hi!
Sorry if this is not the place to put my problem.
I'm newbie in Linux Shell Script and I need to create a special script.
From the var/log/wtmp file, I need to know, for each user, how many 
times has she/he entered in the system and the total usage time. 
If the user has not logged out, count the time until the present 
moment.

I already do above:

First I maked a last -f /var/log/wtmp > teste.wtmp

The script:
#!/bin/bash
cut -c1-6 teste.wtmp |sort -buf > zteste.txt
cat zteste.txt
array=($(< zteste.txt))
for (( i = 0 ; i < ${#array[@]} ; i++ ))
  do
    echo ${array[$i]}
    var=${array[$i]}
    echo `grep -o $var teste.wtmp |wc -w`
done

But this only give me how many times has user entered.
Now I can't find a solution to add de times.
Any help?
Thanks.

---

