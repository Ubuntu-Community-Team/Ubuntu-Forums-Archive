---
title: "Set variable in script"
date: 2007-01-11
forum: Programming Talk
---

### Post by Waappu on 2007-01-11
Hi

How I can set ```
grep 'TEST' ~/MY.TEST -c -w
```to variable named MYINT in bash script and then use it in if statement e.g.
```
if [ $MYINT = 0 ]
then
echo 'varianle is null'
else
echo $MYINT
fi
```

---

### Post by gpolo on 2007-01-11
MYINT=`grep 'TEST' ~/MY.TEST -c -w`

---

### Post by Waappu on 2007-01-11
Hi

Thank you =)

---

### Post by kebes on 2007-01-11
gpolo's code is correct. Note carefully that the statement is surrouding not in normal quotes but in backtick characters (usually found on the upper-left of the keyboard). Surrounding a bash command with backtick characters means that the shell will execute the command and turn the return value into a string you can use elsewhere.

Hope that helps.

---

### Post by Waappu on 2007-01-11
Hi

Yes this help. I some how missed that backtick.
Thanks to both of you

---

### Post by po0f on 2007-01-11
Waappu,

The special variable '$?' contains the exit code of the last run command.  You could also use this instead of assigning to a new variable if you wish.  This works from the command line as well as from a script.

---

### Post by Waappu on 2007-01-11
> **po0f said:**
> Waappu,

The special variable '$?' contains the exit code of the last run command.  You could also use this instead of assigning to a new variable if you wish.  This works from the command line as well as from a script.

Hi

Sorry but I don't understand. Could you please post short sample how I should use it ?

Another question
How I serch match case for this ```
"TEST"
```I try this but syntax is wrong
```
MYINT=`grep '"TEST"' ~/my.test -c -w`
```

---

### Post by slavik on 2007-01-11
when grep runs, it returns 2 things, output and an exit code.

consider the following:
```
result = $(grep "TEST" ~/mytest -c -w)
exitcode $?
```

the first line will assign any output from grep to result. if grep output anything, result will be not empty. the exitcode variable will contain the exit code from the previous command, if grep ran perfectly (whether it found anything or not), exitcode will be 0.

---

### Post by po0f on 2007-01-11
Waappu,

```
[FONT="Courier New"]grep 'TEST' ~/MY.TEST -c -w

if [ $? = 0 ]; then
    echo 'variable is zero'
else
    echo $?
fi[/FONT]
```

The end result is the same, I was just letting you know.

BTW, null and zero are two different things.

---

### Post by Waappu on 2007-01-11
Hi

Thanks very much. Now I get it =) 
Also find answer/my mistake to other queston

---

