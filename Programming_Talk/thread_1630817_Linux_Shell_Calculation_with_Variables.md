---
title: "Linux Shell Calculation with Variables"
date: 2010-11-25
forum: Programming Talk
---

### Post by Peter.Paul on 2010-11-25
Hello Community,
I have a question towards the types of variables in Linux shell

```

min=4
hour=`sed -n '1p' 1.txt`
z2=$(( $hour + 1))

```
I like to calculate with the variable $hour, which I obtain with the sed command. When I print $hour out with 'echo' '300.1109' appear on the screen. However, if I want to calculate with this variable I reseive an error. Do you know, what the reason for this is? I thought there were no variable types in Linux shell....

Cheers

---

### Post by fct on 2010-11-29
The shell works with integers, no floating point arithmetic.

You can use "bc" though:

z2=`echo $hour + 1 |bc`

---

