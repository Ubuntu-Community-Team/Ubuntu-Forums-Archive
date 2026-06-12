---
title: "Bash - Checking on server's"
date: 2011-09-10
forum: Programming Talk
---

### Post by lordfirex on 2011-09-10
Ok so i'm having a few problems with my bash coding.

Mainly from what i can tell whenever i set the variable 'set' inside an if statement, it doesn't seem to be set outside of that specific if statement.

General Run-down of what im doing:

A computer uses wget to initiate some php programming on this server. The php writes the computer that connected to it, it's ip down in ipaddr.txt (It writes down 10.0.0.x is now online. I have a bash script that checks if that file exists, if it does then it espeaks whats written down in the file. Then proceeds to delete the file, so other computers can 'check-in'.


Currently my code stands at:

```
#!/bin/bash


##Set Variables
i="0"; ## as i never increases the entire script never ends


d='10.0.0.' ##Sub-Domain, make sure you put in the '.' at the finish
f='8' ##Starting Ip address to check

fmin='0' ##Minimum IP address to check
fmax='10' ##Maximum ip Address to check




set="asdf";
while [ $i -lt 1 ] ##infinite loop
do




while [ $f -lt $fmax ] ##This checks that the domain is less than or equal to it.
do
ch='up'$f;
#echo "ch is $ch";
#echo "set is $set";
#echo "d is $d";
x="$d$f"; ## This is the 'sub-domain' + the IP ADDR
( ##Start check 
if [ $set = $ch ]
then

if ping -c 1 -w 1 $x &> /dev/null
then
  : # colon is a null and is required
set="up$f"
else
	: # colon is a null and is required
    echo "server down at: $x"
  (echo "The server at $x is down") | espeak -s 155 -g 7 -z &> /dev/null
  set="down$f"
fi


else
if ping -c 1 -w 1 $x &> /dev/null
then
  : # colon is a null and is required
  echo "server up at: $x"
  (echo "The server at $x is up") | espeak -s 155 -g 7 -z &> /dev/null
  set="up$f"
else
  : # colon is a null and is required
  set="down$f"
fi

fi
) ## End check
f=$[$f+1]

done ##This is the end of the check that makes sure f is less than fmax

f=$fmin ## Reset f to it's minimum value, then continues :)

done
exit

```

The problem being that once outside of any of the if statements that check if the server is up, the variable 'set' is 'asdf' or whatever you initially enter it as.

---

### Post by SeijiSensei on 2011-09-10
Try using "export set='string'" and see if that helps.  For more details, see the ENVIRONMENT section in "man bash".

---

### Post by sisco311 on 2011-09-10
( COMMANDS ) runs the commands in a sub-shell, therefor the changes made to the environment variable are only seen by the sub-shell, but not by the parent shell. See:  [http://mywiki.wooledge.org/SubShell](http://mywiki.wooledge.org/SubShell)

Why do you run the check in a sub-shell? I don't see any obvious reason for that.

---

### Post by rolandrock on 2011-09-10
```
#!/bin/bash


##Set Variables
i="0"; ## as i never increases the entire script never ends

```

You do not need 'i'

```

d='10.0.0.' ##Sub-Domain, make sure you put in the '.' at the finish
f='8' ##Starting Ip address to check

fmin='0' ##Minimum IP address to check
fmax='10' ##Maximum ip Address to check


set="asdf";

```

Always avoid using shell built-ins as variable names.  It is bad form, can create problems and makes your code less legible.

```

while [ $i -lt 1 ] ##infinite loop
do

```

Replacing this with:

```
 
while true ; do

```

is more elegant.

```

while [ $f -lt $fmax ] ##This checks that the domain is less than or equal to it.
do
ch='up'$f;
#echo "ch is $ch";
#echo "set is $set";
#echo "d is $d";
x="$d$f"; ## This is the 'sub-domain' + the IP ADDR
( ##Start check

```

Variables defined in function () only exist inside () as pointed out by sisco311.  So remove (.

```

if [ $set = $ch ]
then

if ping -c 1 -w 1 $x &> /dev/null
then
  : # colon is a null and is required

```

The colon means 'do nothing' and is only necessary if you have a conditional clause that is required to do nothing.  This usually means you have a poorly constructed test.  In this case it is not necessary because the following line does something.

```

set="up$f"
else
	: # colon is a null and is required 
```(no it isn't)```

    echo "server down at: $x"
  (echo "The server at $x is down") | espeak -s 155 -g 7 -z &> /dev/null
  set="down$f"
fi


else
if ping -c 1 -w 1 $x &> /dev/null
then
  : # colon is a null and is required
  echo "server up at: $x"
  (echo "The server at $x is up") | espeak -s 155 -g 7 -z &> /dev/null
  set="up$f"
else
  : # colon is a null and is required
  set="down$f"
fi

fi
) ## End check
f=$[$f+1]

```

The closing bracket is not required when you get rid of the opening one.  The f= assignment should be written: f=$(($f+1))

```

done ##This is the end of the check that makes sure f is less than fmax

f=$fmin ## Reset f to it's minimum value, then continues :)

done
exit

```

You need to remove the round brackets, change a variable name, get your indentation right - it should be consistent in if-then-else and inside loops.  Then we will know if the meat of the program (ping and espeak) is performing as required.

On the upside, you get extra credit for good annotation.

Good luck

---

### Post by ofnuts on 2011-09-10
All of the above, plus wondering why you have this infinite loop with an addition on the last part of the ip address. You can easily generate all the necessary values this way:

```

for f in $(seq $fmin $fmax)
do
   # your loop body
done

```

---

