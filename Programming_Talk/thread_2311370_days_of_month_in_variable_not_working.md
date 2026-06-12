---
title: "days of month in variable not working"
date: 2016-01-26
forum: Programming Talk
---

### Post by peter_brickles on 2016-01-26
Hi guys i want to get the number of days in next month in a variable so i can loop through it so far i have 

> 
cal $(date +"%m %Y" --date "next month") | awk 'NF {DAYS = $NF}; END {print DAYS}' > temp
DAYS_IN_NEXT_MONTH=$(cat temp)



for (( c=1; c<=$DAYS_IN_NEXT_DATE; c++ ))
do

echo $c

done 
 


but it s giving the error 

>  

((: c<=: syntax error: operand expected (error token is "<=")



Ive used variable in a for next loop before so don't understand why this isn't working ? any give me a heads up[ and id be grateful

Cheers Pete

---

### Post by spjackson on 2016-01-26
If what you've pasted is exactly what you are doing, then the problem is that DAYS_IN_NEXT_MONTH is not the same as DAYS_IN_NEXT_DATE.

---

