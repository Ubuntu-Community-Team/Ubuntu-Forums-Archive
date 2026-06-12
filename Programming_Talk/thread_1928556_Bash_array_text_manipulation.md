---
title: "Bash array text manipulation"
date: 2012-02-20
forum: Programming Talk
---

### Post by DavidRLu on 2012-02-20
Working in BASH
I have a requirement to take a number of command line arguments, append text to the end of each, and assign them to an array.
What it should do:
        append.sh alpha beta gamma           should result in:
  server[1] = alphaAPPENDEDTEXT
  server[2] = betaAPPENDEDTEXT
  server[3] = gammaAPPENDEDTEXT

what I've got now:
--------------------------------------------
#!/bin/bash
dbnames=("$@")
for dbnames
 do
  eval server$[n]=${dbnames[n++]}"APPENDEDTEXT"
 done
 
#The following lines will correctly echo the desired argument with appended text
# however, they are separate variables, not array elements
echo $server0
echo $server1
echo $server2 
---------------------------------------------
What do I need to do to get it to assign the results of the "eval" line above to an array?
(Or - is there a simpler way to accomplish this?)
Thanks!

---

### Post by ofnuts on 2012-02-20
> **DavidRLu said:**
> Working in BASH
I have a requirement to take a number of command line arguments, append text to the end of each, and assign them to an array.
What it should do:
        append.sh alpha beta gamma           should result in:
  server[1] = alphaAPPENDEDTEXT
  server[2] = betaAPPENDEDTEXT
  server[3] = gammaAPPENDEDTEXT

what I've got now:
--------------------------------------------
#!/bin/bash
dbnames=("$@")
for dbnames
 do
  eval server$[n]=${dbnames[n++]}"APPENDEDTEXT"
 done
 
#The following lines will correctly echo the desired argument with appended text
# however, they are separate variables, not array elements
echo $server0
echo $server1
echo $server2 
---------------------------------------------
What do I need to do to get it to assign the results of the "eval" line above to an array?
(Or - is there a simpler way to accomplish this?)
Thanks!
You don't need an "eval"...

The size of an array x is ${#x[@]}

There is a C-ish form of the for loop: "for (( x=0; x<limit;x++))"

The mere existence of an assignment such as "a[$x]=foo" declares "a" as an array.

Draw you conclusions.

---

### Post by DavidRLu on 2012-02-20
Thanks, but...
Without "eval" bash4.1.10 (under cygwin) attempts to execute the statement rather than populating the variables.

Output of the exact same code without eval is:
 
apend.sh: line 5: server0=alphaAPPENDEDTEXT: command not found
apend.sh: line 5: server1=betaAPPENDEDTEXT: command not found
 
etc.
 
Also, I'm pretty sure that $server0 is not the same as ${server[0]}

---

### Post by ofnuts on 2012-02-20
Because you have spaces around the "=" sign. Remove them.

---

### Post by DavidRLu on 2012-02-21
Similar behavior with or without the spaces.
Without the eval statement the responses are:

With spaces:
apend.sh: line 5: server0: command not found
apend.sh: line 5: server1: command not found

Without spaces:
apend.sh: line 5: server0=alphaAPPENDEDTEXT: command not found
apend.sh: line 5: server1=betaAPPENDEDTEXT: command not found

---

### Post by ofnuts on 2012-02-21
> **DavidRLu said:**
> Similar behavior with or without the spaces.
Without the eval statement the responses are:

With spaces:
apend.sh: line 5: server0: command not found
apend.sh: line 5: server1: command not found

Without spaces:
apend.sh: line 5: server0=alphaAPPENDEDTEXT: command not found
apend.sh: line 5: server1=betaAPPENDEDTEXT: command not found
```

>>x[1]=foo
>>echo ${x[1]}
foo

>>sh
>>x[1]=foo
sh: x[1]=foo: not found


```
Are you really using bash (#! /bin/bash)?

---

### Post by DavidRLu on 2012-02-21
Here's what I wound up with - which works:
 
[SIZE=3][FONT=Calibri]#!/bin/bash[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]declare -i COUNT[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]COUNT=0[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]     for name in $*[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]         do[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]             CURRENTDB=$(echo ${name}DBPVS | tr -s '[:lower:]' [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]'[:upper:]')  #convert string to upper and assign to temporary variable[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]             dbserver[$COUNT]=$CURRENTDB  #insert temporary variable value into dbserver array[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]             COUNT=COUNT+1[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]     done[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]for output in "${dbserver[@]}"[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]     do[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]     echo $output[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]done[/FONT][/SIZE]

---

### Post by DavidRLu on 2012-02-21
BTW - Thanks for your input!

---

