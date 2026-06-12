---
title: "My first bash script, help needed."
date: 2010-04-30
forum: Programming Talk
---

### Post by Bladtman242 on 2010-04-30
Hi everyone, for my first bash script I wanted to do something useful.
So I am trying to use the synclient to enable/disable a touchpad, so that us laptop users wont need a mouse to our computers without a mouse:P

The script currently looks like this:
```
#!/bin/sh

tpCheck=`synclient -l | grep -i 'touchpadoff'`
if [ "$tpCheck" == "TouchpadOff = 1" ]
then
    synclient TouchpadOff=0
else
    synclient TouchpadOff=1
fi
exit
```When i run it from the terminal i get this output:
```
[: 9:     TouchpadOff             = 1: unexpected operator
``` (depending on weather or not the touchpad is active the output differs between 1 and 0)

Oddly, it disables the touchpad all right, but it cant activate it?
Also I get that error output^^ both when enabling and disabling the touchpad.

Any help will be much appreciated.

---

### Post by weresheep on 2010-04-30
Hello,

I think the problem may be that the output of the synclient command has multiple spaces/tabs in its output and the string your comparing it to does not. I've modified your script to strip the output of the synclient command to extract only the result we're interested in (using awk to match like your grep but also only print the number after the = ).

In works on my computer :D

```

#!/bin/sh --

if [ $(synclient -l | awk -F'=' '/TouchpadOff/ { print $2 }') -eq 0 ] ; then
  echo "Touch pad off, turning on" 
  synclient TouchpadOff=1
else
  echo "Touch pad on, turning off" 
  synclient TouchpadOff=0
fi

```

-weresheep

---

### Post by Bladtman242 on 2010-04-30
I got it working by only using one '=' instead of two, odd huh?

Anyway, I'm not sure I fully understand your code, but I will use that chance to learn:)
Thank you fore your response:)

---

### Post by weresheep on 2010-05-01
Hello again,

If your script is working then great, however I do agree that it is odd that using a single '=' worked as that is the assignment operator whereas '==' is the string comparison operator.

The only complicated part of my script is the contents of the if statement, but its actually quite simple.

```

if [ $(synclient -l | awk -F'=' '/TouchpadOff/ { print $2 }') -eq 0 ] ; then

```

I prefer to use $() over the old style `` but as far as I know they do the same thing (although I seem to recall reading that $() is the preferred style for new scripts).

The output of synclient -l is e.g.
```

    TouchpadOff             = 1

```

which is some space, "TouchpadOff" some space or tabs, then "= 1". Once we find the line containing the "TouchpadOff" variable, we're only interested in whether it is currently set at 1 or 0, so the rest of the line is really just noise that we want to get rid of. Unix has a number of tools that can be used to perform text processing e.g. grep, sed, cut, tr etc. One of my favourites is awk which is actually a programming language itself that you can embed inside shell scripts.

So, what we want to do is find the line with "TouchpadOff" in it, and then extract the number after the "=".

```

awk -F'=' '/TouchpadOff/ { print $2 }'

```
The above line is actually a small awk program that is used to find the correct line and then print only the number after the "=". By default awk splits each input line into variables ($1, $2 etc.) based on whitespace. I used the -F argument to awk to tell it to split the line based on the "=" character. For the output of synclient, this means that the awk variable $1 will contain "TouchpadOff" part and $2 will contain just the "1" part.

After the -F command line argument comes the actual awk program defined between single quotes to prevent the shell from trying to interpret it as shell code. As synclient -l outputs multiple lines and we only want one, we can use awk's grep like // operator to skip lines we are not interested in (/TouchpadOff/ in awk is like doing grep "TouchpadOff"). In awk you can partner a grep like filter // with some actions enclosed in {}. So what we do above is when the // matches a line, we print the awk variable $2, which due to the automatic line splitting awk does is now just the part of the string after the "=" character.

Once we have the value for the synclient "TouchpadOff" variable we need to compare it. The shell operator '==' compares things as strings whereas if we want to compare two things as numbers we have to use the operators like '-eq', '-gt' and '-lt'. By telling the shell to compare as numbers we ignore any extra space and interpret the strings as actual numbers.

See, simple :)

-weresheep

---

### Post by Vox754 on 2010-05-01
> **weresheep said:**
> Hello again,

If your script is working then great, however I do agree that it is odd that using a single '=' worked as that is the assignment operator whereas '==' is the string comparison operator.

...


From the bash(1) manual
```

CONDITIONAL EXPRESSIONS
       Conditional  expressions  are  used  by the [[ compound command and the
       test and [ builtin commands to test file attributes and perform  string
       and  arithmetic comparisons.

       ...
       string1 == string2
       string1 = string2
              True  if  the strings are equal.  = should be used with the test
              command for POSIX conformance.

```

Remember that the left bracket **"["**, is actually the command **"test"**.

From the test(1) manual
```

       STRING1 = STRING2
              the strings are equal

       STRING1 != STRING2
              the strings are not equal

```

An unrelated note: don't name your executable "test" when learning to program in C, you may be calling the wrong program!

For more advanced comparison you should use the bash-specific **[[** expression **]]** because it performs Pattern Matching.
```

       [[ expression ]]
              ...

              When the == and != operators are used, the string to  the  right
              of the operator is considered a pattern and matched according to
              the rules described below under Pattern Matching.

```

---

