---
title: "Bash question: piecing together variables"
date: 2009-08-02
forum: Programming Talk
---

### Post by Noahdj on 2009-08-02
I am completely new to both linux, ubuntu, and BASH. I'm trying to create a simple program and was doing okay until the past 4 hours. For the life of me I can't find a solution...

I'm trying to refer to a variable list in a loop. My program starts by asking for a list of words:

```
#!/bin/bash 

WDNUM=0
WORKAROUND=1
until [ $WORKAROUND = 0 ]; do
let WDNUM+=1
echo "Enter word #"$WDNUM", or type 0:"
read WORKAROUND
export WD$WDNUM=$WORKAROUND
done
```once I'm done entering a list of words, I'd like to echo the list I've typed. This is what I tried:

```
NOTIFY=1
WDPROCESS=1
until [ $NOTIFY = 0 ]; do
echo WD$WDPROCESS
WORD=$WD2
NOTIFY=$WORD
let WDPROCESS+=1
done

exit
```the idea behind the line [echo WD$WDPROCESS] is that the first iteration would be [echo WD1], then [echo WD2] etc. but instead of treating the WD$WDPROCESS as a single variable, it treats it as the value of $WDPROCESS concatenated to the characters WD.
[COLOR=Black]
[/COLOR][COLOR=Navy][COLOR=Black]So when I run it, this is what I get:[/COLOR]
Enter word #1, or type 0:
[COLOR=Green]one[/COLOR]
Enter word #2, or type 0:
[COLOR=Green]0[/COLOR]
WD1[/COLOR]

[COLOR=Black]Where "WD1" is output, I want to get "one."

Could somebody tell me how to declare the string as a single variable? Eventually I am going to try to replace the echo with a function, where I would have the same problem.

A similar issue I had was trying to piece variables together to assign new variables like so:
a=one
b=TWO
c=three
d=FOUR
$a$b=$c$d 
#where [/COLOR][COLOR=Black][COLOR=Navy]$a$b=$c$d[/COLOR] is equivalent to[COLOR=Navy] oneTWO=threeFOUR[/COLOR][/COLOR]
[COLOR=Black]
Obviously I don't know what I'm doing. Any help appreciated.
[/COLOR]

---

### Post by Tek-E on 2009-08-02
which segment of code is your script???

---

### Post by lswb on 2009-08-02
I'm not really sure what you're trying to do, but perhaps search for "indirection" in the bash man page and see it that helps.

---

### Post by sisco311 on 2009-08-02
use an array.

[http://tldp.org/LDP/abs/html/arrays.html]("http://tldp.org/LDP/abs/html/arrays.html")

---

### Post by Habbit on 2009-08-02
You need to use indirect references: instead of "echo WD$WDPROCESS", you need to use "eval echo \$WD$WDPROCESS". Note the escaped $ for the final expansion: the first (pre-eval) expansion substs WDPROCESS, then the shell executes "eval echo \$WD1", which is evaluated to "echo $WD1", which prints "one".

---

### Post by stroyan on 2009-08-02
You need to use the eval builtin to do indirect variable assignment.
But you can use either eval or ${!VAR} for reading indirect variable values.
Here are examples of assigning to and reading from an indirect variable
and an array element.
```

N=3
VALUE=three
NAME=WD$N
eval $NAME="$VALUE"
echo $NAME
echo "${!NAME}"
A[$N]=$VALUE
echo "${A[$N]}"

```
There are more flexible ways to loop over the elements of an array or of a set of variable names with a common prefix.
You can get a list of array index values with ${!A[@]}.
You can get a list variable names matching a prefix with ${!prefix@}.
```

for INDEX in ${!A[@]}; do echo $INDEX ${A[$INDEX]};done
for NAME in ${!WD@}; do echo $NAME ${!NAME};done

```

---

### Post by Noahdj on 2009-08-02
Wow, thanks everyone. I never expected so many replies so quickly. Sorry if my question was confusing, I only decided to ask after it had gotten to 3am.

I used the eval with \ to accomplish my goal. I'm sure my program is not very elegant, but it now works for my design. The finished code follows:

```
#!/bin/bash 

WDNUM=0
WORKAROUND=1
until [ $WORKAROUND = 0 ]; do
let WDNUM+=1
echo "Enter word #"$WDNUM", or type \"0\" to finish:"
read WORKAROUND
export WD$WDNUM=$WORKAROUND
done

function repeater {
echo $1
}

echo ""; echo "###################### START ######################"

CHECK=1
until [ $CHECK = 0 ]; do
eval repeater \$WD$WDPROCESS
let WDPROCESS+=1
eval CHECK=\$WD$WDPROCESS
done

echo ""; echo "######################  END  ######################"
exit
```This is an example of me using it:

> Enter word #1, or type "0" to finish:
Hello
Enter word #2, or type "0" to finish:
Ubuntu
Enter word #3, or type "0" to finish:
Forum
Enter word #4, or type "0" to finish:
0

###################### START ######################

Hello
Ubuntu
Forum

######################  END  ######################I have yet to learn the code in the other replies, which I'll do now. Thank you all so much.

BTW, could anybody hint how I could place the "read" inline with the "Enter word..."?

And/or how do I accept read input with spaces?
This is what happens now:
> Enter word #1, or type "0" to finish:
hello world
[COLOR=Purple]tester.sh: line 5: [: too many arguments[/COLOR]

---

### Post by stroyan on 2009-08-02
You can use read -p to specify a prompt string instead of using echo.
You will need to add quoting around several instances of $VAR to handle spaces.
Here is a diff of the changes you would make to use read -p and more quoting.
```

--- t.sh	2009-08-02 20:22:13.000000000 -0600
+++ t2.sh	2009-08-02 20:29:39.000000000 -0600
@@ -2,11 +2,10 @@
 
 WDNUM=0
 WORKAROUND=1
-until [ $WORKAROUND = 0 ]; do
+until [ "$WORKAROUND" = 0 ]; do
 let WDNUM+=1
-echo "Enter word #"$WDNUM", or type \"0\" to finish:"
-read WORKAROUND
-export WD$WDNUM=$WORKAROUND
+read -p "Enter word #$WDNUM, or type \"0\" to finish:" WORKAROUND
+export WD$WDNUM="$WORKAROUND"
 done
 
 function repeater {
@@ -16,8 +15,8 @@
 echo ""; echo "###################### START ######################"
 
 CHECK=1
-until [ $CHECK = 0 ]; do
-eval repeater \$WD$WDPROCESS
+until [ "$CHECK" = 0 ]; do
+eval repeater \"\$WD$WDPROCESS\"
 let WDPROCESS+=1
 eval CHECK=\$WD$WDPROCESS
 done

```

---

### Post by Noahdj on 2009-08-03
Thank you Stroyan, that worked perfectly. The diff was a very informative way of showing me. LOL, I had to look up what diff meant before I could even start.

All my questions have been satisfied, and my cheesy little program is exactly how I wanted it. This is so much fun! Thanks to all for putting up with someone with two days of programming experience.

Finally I get to start work on the actual function.

---

