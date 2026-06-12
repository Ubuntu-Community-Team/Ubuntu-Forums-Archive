---
title: "bash scripting / (standard_in) 1: syntax error"
date: 2017-04-11
forum: Programming Talk
---

### Post by Biscarri on 2017-04-11
I'm learning bash scripting. 

The following command...

```
Uavg=echo "scale=6; $Qavg/$Oarea" | bc`
```

does not assign a value to Uavg and gives this error...

```
 (standard_in) 1: syntax error
```

previously, the variables  $Qavg and $Oarea have been assigned with the expressions...

```
Qavg=`cat Uavg.dat | grep "areaIntegrate(outlet)" | head -1 | xargs | cut -d' ' -f7 | tr ')' ' '`

Oarea=`cat Uavg.dat | grep "total area" | cut -d'=' -f2`
```

I have checked that $Qavg and $Oarea have numerical values, but maybe previous command lines have an eol problem and the resulting variables are strings. 

Any idea about this problem?

Thanks a lot
Lluis

---

### Post by sisco311 on 2017-04-11
Hi,

Your code is overcomplicated hence is error-prone. You're a beginner, so there is nothing wrong with that.

It would be much more constructive if you could post the task what you want achieve (some example input files and desired output), so we can direct you to the sources where you can find your answers.

Note: We are happy to help with hints and suggestion with your homework, but don't expect someone else to solve it for you.

---

### Post by rogervn on 2017-04-11
You missed the ` at the start.

Uavg=`echo "scale=6; $Qavg/$Oarea" | bc`

---

### Post by Biscarri on 2017-04-12
Thank you very much for the answers!

In the script I have  Uavg=`echo "scale=6; $Qavg/$Oarea" | bc`. The ' missing was an error transcribing the command to the forum thread :(

What I'm trying to do is to read a couple of values from file Uavg.dat and assign them to the variables Qavg and Oarea, and then divide them to get the value of Uavg.

I wonder if the following commands may produce a string of characters instead of a number (by typing $Qavg and $Oarea they show as numbers):
Qavg=`cat Uavg.dat | grep "areaIntegrate(outlet)" | head -1 | xargs | cut -d' ' -f7 | tr ')' ' '`

Oarea=`cat Uavg.dat | grep "total area" | cut -d'=' -f2`

[FONT=arial]Maybe the first command is doing something wrong at the end, when is substituing ')' by ' ', and it results in a string rather than a number. [/FONT]

---

### Post by Biscarri on 2017-04-12
I've found a way to solve the problem with a perl command, it seems that bash arithmetics can deal only with integer numbers.

The follwing command works:
```
Uavg=$(perl -e "print $Qavg/$Oarea")
```

Thank's again
Lluis

---

### Post by slickymaster on 2017-04-12
*Thread moved to **Programming Talk**.*

---

