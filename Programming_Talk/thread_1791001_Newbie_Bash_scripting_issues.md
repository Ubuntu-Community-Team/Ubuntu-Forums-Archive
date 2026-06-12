---
title: "Newbie Bash scripting issues"
date: 2011-06-26
forum: Programming Talk
---

### Post by Johnny-Gear on 2011-06-26
Hi All,

I am extremely unexperienced in writing in bash and not very experienced coding at all, but I have no issue learning.

I am currently trying to implement a mail alert for when any of my GPU temperature sensors go below a certain centigrade. I plan on using a cron job which runs every 10-15 minutes or so and sends mail through exim and a smarthost if pre-mentioned conditions are met.

Below is the bash script I have so far:

```

#!/bin/bash
MIN="80"
TEMP0= DISPLAY=:0 aticonfig --odgt --adapter=0 | sed -n '/[0-9][0-9]\.[0-9][0-9]/,$p' | sed 's/.*\([0-9][0-9]\)\..*/\1/'
TEMP1= DISPLAY=:0 aticonfig --odgt --adapter=1 | sed -n '/[0-9][0-9]\.[0-9][0-9]/,$p' | sed 's/.*\([0-9][0-9]\)\..*/\1/'
TEMP2= DISPLAY=:0 aticonfig --odgt --adapter=2 | sed -n '/[0-9][0-9]\.[0-9][0-9]/,$p' | sed 's/.*\([0-9][0-9]\)\..*/\1/'
TEMP3= DISPLAY=:0 aticonfig --odgt --adapter=3 | sed -n '/[0-9][0-9]\.[0-9][0-9]/,$p' | sed 's/.*\([0-9][0-9]\)\..*/\1/'
echo $TEMP0
echo $TEMP1
echo $TEMP2
echo $TEMP3
echo $MIN
if [ "$TEMP0" -lt "$MIN" ]; then
        echo "something is not right..."
else
        echo "everything looks ok"
fi

```Everything below line 6 is simply testing that variables are grabbed correctly and whether my condition is working. 

The condition I plan on using would be all 4 temperature's being checked against $MIN using an || operator.

When I run this script currently I get the following:

```

76
74
70
74




80
tempCheck.sh: line 12: [: : integer expression expected
everything looks ok

```Now, I would expect that the if statement would be executed, rather than the else statement. I am assuming the else statement is being triggered because there is some sort of error in my comparison but I can't work it out.

For reference, here is the output for the DISPLAY=:0 aticonfig cmd before sed gets to it:
```
 
:~# DISPLAY=:0 aticonfig --odgt --adapter=0

Adapter 0 - ATI Radeon HD 5800 Series
            Sensor 0: Temperature - 76.00 C

```Any help would be greatly appreciated.

JG

EDIT: I also realise how messy my sed / regex is and would appreciate if someone could help me clean it up, thanks again.

---

### Post by Vaphell on 2011-06-26
you don't capture the output so if sees null value
notice 4 empty lines in output, that's your echo $temp0 ... echo $temp3 sequence. As you can see your variables are empty
```
TEMP0=$( DISPLAY=:0 aticonfig --odgt --adapter=0 .... )
```

if you are sure that there is only 1 occurence of [0-9]{2}.[0-9]{2} you can use grep -o that returns only matching part (76.00), that would simplify next part where fraction part is dropped.

```
echo $'test 6.66\ntest 76.00\ntest 112.99'
test 6.66
test 76.00
test 112.99

echo $'test 6.66\ntest 76.00\ntest 112.99' | grep -oE '[0-9]{2,3}[.][0-9]{2}' | sed -r 's/([0-9]*).*/\1/g'
76
112
``` note that i used {2,3} to allow numbers above 100
sed -r allows dropping that painful escaping thing of dots, parentheses and stuff as it assumes that they have their regex meaning.

---

### Post by Johnny-Gear on 2011-06-26
> **Vaphell said:**
> you don't capture the output so if sees null value
notice 4 empty lines in output, that's your echo $temp0 ... echo $temp3 sequence. As you can see your variables are empty
```
TEMP0=$( DISPLAY=:0 aticonfig --odgt --adapter=0 .... )
```if you are sure that there is only 1 occurence of [0-9]{2}.[0-9]{2} you can use grep -o that returns only matching part (76.00), that would simplify next part where fraction part is dropped.

```
echo $'test 6.66\ntest 76.00\ntest 112.99'
test 6.66
test 76.00
test 112.99

echo $'test 6.66\ntest 76.00\ntest 112.99' | grep -oE '[0-9]{2,3}[.][0-9]{2}' | sed -r 's/([0-9]*).*/\1/g'
76
112
``` note that i used {2,3} to allow numbers above 100
sed -r allows dropping that painful escaping thing of dots, parentheses and stuff as it assumes that they have their regex meaning.

Thanks Vaphell,

You have helped me a lot and I should be able to implement my alerts now. Thanks for actually taking the time to explain everything as well :)

JG

---

