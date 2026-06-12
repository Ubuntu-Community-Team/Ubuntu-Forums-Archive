---
title: "Any help?"
date: 2016-12-03
forum: Programming Talk
---

### Post by mandeamarian on 2016-12-03
Hey, i'm new on codeing and i am stuck
I have a code in bash and i want to make it to increment or decrement, but i can t make it right
When i run the script, it\s workin' but increments only 1 number
Exemple: 
1
1
1
1


This is the code

```
#!/bin/bash#
#Alchimie Fibonacci




nrstreak=0
bet=0.00000000




id=$1




echo "BET $bet"
won=`./bet 0.1 49 "<"`




############# CURRENTSTREAK #######################
if [ "$won" == "true" ] && [ "$nrstreak" -ge 0 ];
then
((nrstreak++))
echo "WON! +++"
elif [ "$won" == "true" ] && [ "$nrstreak" -lt 0 ];
then
echo "WON!"
fi






if [[ "$won" == "false" && "$nrstreak" -le 0 ]];
then
((nrstreak--))
echo "LOSE! ---"
elif [[ "$won" == "false" && "$nrstreak" -gt 0 ]];
then
echo "LOSE!"
fi
####################################################




echo "Nr_Streak = $nrstreak"


echo "---------------------------"
sleep 0.5



```

This in the result

```

BET 0.1
LOSE!
Nr_Streak = -1
---------------------------
BET 0.1
LOSE!
Nr_Streak = -1
---------------------------
BET 0.1
WON!
Nr_Streak = 1
---------------------------
BET 0.1
WON!
Nr_Streak = 1
---------------------------
```








Thank you, please excuse my bad english.

---

### Post by Rocket2DMn on 2016-12-07
Every time you execute this script it starts from the beginning, with nrstreak being set to 0.  There is no loop in the script, so nstreak can only ever be be 1 or -1 after it finishes.  The lifetime of the variable nstreak is limited to that of the script.

If you want to run multiple times, you need to put your "betting" in a loop (perhaps taking the number of iterations as an argument to the script).

---

