---
title: "Bash help: assign variable to an expression"
date: 2009-08-12
forum: Programming Talk
---

### Post by soulbazz on 2009-08-12
Hi all, I'm not sure if this is the best title for my question but i'll give it a go. 

I having a problem with one of my scripts. Essentially I want to assign a variable to an average (scalar). But I use awk and bc to compute the average, and for some reason bash doesn't like it.  

Here is an example: 
 I have a list (TEST.txt) 
 I use the following expression to get the average:
     **echo "`awk '{print $2}' TEST.txt | awk '{SUM += $1} END {print SUM}'`/2" | bc**
              
             This works fine....I get what I want (actually now that I'm typing it /2 actually needs to be /number of rows.....but that is besides the point, I can fix that)

So this leaves me with a scalar .... say 151

Now I want to assign this number a variable
So that 
     avg=151
 
I have done this, but it doesn't work,

[B]avg=`echo "`awk '{print $2}' TEST.txt | awk '{SUM += $1} END {print SUM}'`/2" | bc`
[/B]
neither does this,

[B]avg=echo"`echo "`awk '{print $2}' TEST.txt | awk '{SUM += $1} END {print SUM}'`/2" | bc`"
[/B]
what am I doing wrong?

Thanks in advance for your help, hope my post was clear enough.

---

### Post by unutbu on 2009-08-12
```
avg=$(echo "$(awk '{print $2}' TEST.txt | awk '{SUM += $1} END {print SUM}')/2" | bc)
```
Seems to work for me...

Though wouldn't this be better:```

avg=$(awk '{SUM += $2} END {print int(SUM/NR)}' TEST.txt)
```

---

### Post by soulbazz on 2009-08-12
Excellent!! Thank you very much, the first one worked great. The second one gave me the wrong answer, maybe its the way the text files are set up in my script. Either way thank you!

---

