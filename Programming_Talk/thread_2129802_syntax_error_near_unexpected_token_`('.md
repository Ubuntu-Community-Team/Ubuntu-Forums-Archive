---
title: "syntax error near unexpected token `('"
date: 2013-03-27
forum: Programming Talk
---

### Post by thedawg on 2013-03-27
Hi there,

so I've a program to define the Date of Easter Sunday for the year of choice.
Originally I've written this program in Powershell, because in school we have to use PS.
Now I have to rewrite it into a Linux Script, and I'm getting these two failure massages:

"./Input-test: line 8: syntax error near unexpected token `( 
./Input-test: line 8: `$Jahr=(( 12 + "$Year" / 100 -"$Year" / 400 - ( 8* "$Year" / 100 + 13) / 25 ) %30 + 19* ( "$Year" %19 )) %30 "

I've tried a few things but my knowledge of Linux is still a bit short so I hope you guys can help me a bit.


My code:
"
#!/bin/bash


echo "Enter Year"

read Year

$Jahr=(( 12 + "$Year" / 100 -"$Year" / 400 - ( 8* "$Year" / 100 + 13) / 25 ) %30 + 19* ( "$Year" %19 )) %30 
  $Platzhalter = ("$Year" %17) 

if["$Jahr" -eq 29] 
  then $D=28

elseif ["$Jahr" -eq 28 && "$Plantzhalter" -ge 11]
  then $D=27
else [$D=$Jahr]

fi
fi
fi

$E=(2*("$Year"%4)+4*("$Year"%7)+6*$D+(6+"$Year"/100 -"$Year"/400 -2)%7)%7

$Tag=("$E" + "$D" +1)+21

if ["$Tag" -gt 31]
  then $Tag = $Tag - 31
  if ["$Tag" -lt 10]
  echo "Ostersonntag fällt auf den 0$Tag.04.$Year"
    else echo "Ostersonntag fällt auf den $Tag.03.$Year"

fi 
fi 

"


Good hunting 

TheDawg

---

### Post by r.stiltskin on 2013-03-27
Declare your integer variables, e.g.
```
declare -i Year
```
otherwise use **let** for assignments.

Don't use $ with the variable name on the lhs of =, e.g.
```
D=27
#not $D=27
```

Every if needs a then.
Every if gets exactly one fi, e.g.
```
if [ expr ]
then something
elif [ expr ]
then something
else something
fi
```

Put double-quotes around arithmetical expressions that contain blank spaces, e.g.
```
Jahr="(( ((12 + $Year / 100 - $Year / 400 - ( 8 * $Year / 100 + 13 ) / 25 ) % 30 + 19 * ($Year % 19)) % 30 ))"
```
otherwise eliminate the spaces and precede the expression with a $
```
Jahr=$(( ((12+$Year/100-$Year/400-(8*$Year/100+13)/25)%30+19*($Year%19))%30 ))
```
(Blank spaces to offset the outer double parens (( )) are OK.)

Be sure that spelling of your variable names is consistent.  (Plantzhalter?)

---

### Post by oldos2er on 2013-03-27
Moved to Programming Talk.

---

### Post by Vaphell on 2013-03-27
OP, wrap your code in [c****ode][/code] tags, so the formatting is preserved and the script more readable.

as poster above explained, think of $ with variable names as a 'get value of'
```
x=1    # assignment
echo $x     # getting value of x
```

if you want to assign expression value to a variable you need to use $ as well (another case that fits the 'get value of' line of thinking)
```
x=$( some_command )  # capture the output of some_command
y=$(( a/b*c+1 ))   # do integer math, $s are not needed inside the integer math (( ))
```


conditions using [] require spaces between all parts of expression. [ is simply a command that needs a clear-cut list of parameters
[ "$var" = 1 ]  => "[", "$var", "=", "1", "]"

---

### Post by schragge on 2013-03-27
Also, this code
```
[ "$Jahr" -eq 28 && "$Platzhalter" -ge 11 ]
``` won't work because **[** is just a command as **Vaphell** explained above. You can either replace it with **[[**...**]]** ```
[[ $Jahr -eq 28 && $Platzhalter -ge 11 ]]
``` or split it in two commands
```
[ 28 -eq "$Jahr" ] && [ 11 -le "$Platzhalter" ]
```

But the best option IMO is to use arithmetic evaluation here
```
((Jahr==28 && Platzhalter>=11))
```

---

### Post by Vaphell on 2013-03-27
i'll add that in case of [] booleand operators AND and OR can be achieved by -a and -o.
```
$ Jahr=28; Platzhalter=20;
$ [ "$Jahr" -eq 28 **-a** "$Platzhalter" -ge 11 ] && echo true || echo false
true
$ Jahr=27; Platzhalter=20;
$ [ "$Jahr" -eq 28 **-a** "$Platzhalter" -ge 11 ] && echo true || echo false
false
```

&& and || are reserved by shell for other things (unless you go [[ ]] route which applies different logic inside the brackets)
*cmd1 && cmd2 || cmd3* is an equivalent of *if cmd1 then cmd2 else cmd3* (success = TRUE, failure = FALSE and the expression is evaluated according to the rules of boolean logic where you can skip calculating FALSE && ??? and TRUE || ??? ).

---

### Post by thedawg on 2013-03-28
Oh wow, 
a lot of posts since yesterday :) 

So I gonna try it step by step

but thank you all so far for the response :)

---

