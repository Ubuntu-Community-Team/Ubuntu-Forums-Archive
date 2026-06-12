---
title: "Help: Simple Bash if/then/else error."
date: 2008-02-27
forum: Programming Talk
---

### Post by ewanchic on 2008-02-27
I'm going to assume this really should be simple for someone. Simple, I know I must be doing something wrong.

only relevant info:
> 
discPtr=$(cdrskin dev=$discDrive -msinfo 2>/dev/null)
echo "Disc Ptr:" + $discPtr

if ["$discPtr" = ""]

then
  mkisofs -v -o $discBurn/track.iso -R $backupLoc

else
  mkisofs -v -o $discBurn/track.iso -R -C $discPtr -M $discDrive $backupLoc

fi


It does go through both conditions...and then all of a sudden it's like i have a syntax error somewhere:

> 
+ echo 'Disc Ptr:' + 326400,489728
Disc Ptr: + 326400,489728
+ '[326400,489728' = ']'
./burn.zimbra: line 16: [326400,489728: command not found
+ mkisofs -v -o /tmp/discBurn/track.iso -R -C 326400,489728 -M /dev/scd0 /media/sdc1/raws/backups/zimbra


I've studied other code, it for the most part, the program executes correctly. What am I doing wrong to produce the funny string comparison?

The Whole Script, in case anyone is interested:
> 
#!/bin/bash -x

echo "Initializing Burn.Zimbra"
discDrive=/dev/scd0
discBurn=/tmp/discBurn
discPtr=$(cdrskin dev=$discDrive -msinfo 2>/dev/null)
backupLoc=/media/sdc1/raws/backups/zimbra

echo "Disc Ptr:" + $discPtr

rm -R $discBurn
mkdir -p $discBurn

wait
echo "Creating Track"
if ["$discPtr" = ""]

then
  mkisofs -v -o $discBurn/track.iso -R $backupLoc

else
  mkisofs -v -o $discBurn/track.iso -R -C $discPtr -M $discDrive $backupLoc

fi

echo "Burning Disc"
cdrskin dev=$discDrive -v padsize=300k -multi -tao -eject $discBurn/track.iso

rm -R $discBurn
echo "Backup Complete"



Thanks for the help :)

---

### Post by lloyd_b on 2008-02-27
For the "if" condition, try
```
if test -z "$discPtr"
```

"test -z ..." returns TRUE if the associated string is zero length.

Lloyd B.

---

### Post by ewanchic on 2008-02-27
Still Strange :confused:

> 
....
+ discPtr=326400,489728
+ backupLoc=/media/sdc1/raws/backups/zimbra
+ echo 'Disc Ptr:' + 326400,489728
Disc Ptr: + 326400,489728
+ rm -R /tmp/discBurn
rm: cannot remove `/tmp/discBurn': No such file or directory
+ mkdir -p /tmp/discBurn
+ wait
+ echo 'Creating Track'
Creating Track
+ t -z 326400,489728
./burn.zimbra: line 16: t: command not found
+ mkisofs -v -o /tmp/discBurn/track.iso -R -C 326400,489728 -M /dev/scd0 /media/sdc1/raws/backups/zimbra
....


---

### Post by WW on 2008-02-27
Try putting spaces before and after the square brackets.

---

### Post by ewanchic on 2008-02-27
Code 1:
> 
if [ "$discPtr" = '' ]


Result 1:
> 
+ '[' 326400,489728 = '' ']'
+ mkisofs -v -o /tmp/discBurn/track.iso -R -C 326400,489728 -M /dev/scd0 /media/sdc1/raws/backups/zimbra

Is this correct output?!
-----

Code 2:
> 
if ( "$discPtr" = '' )


Result 2:
> 
+ 326400,489728 = ''
./burn.zimbra: line 16: 326400,489728: command not found

-----

Code 3:
> 
if [ "$discPtr" = "" ]


Result 3:
> 
+ 326400,489728 = ''
./burn.zimbra: line 16: 326400,489728: command not found

---------

Code 4:
> 
if [ test -z "$discPtr" ]


Result 4:
> 
+ '[' test -z 326400,489728 ']'
./burn.zimbra: line 16: [: -z: binary operator expected

--------

---

### Post by Mr. C. on 2008-02-27
Code 1 is missing a final double quote.
Code 2 executes the evaluation of the variable in trailing stuff in a subshell
Code 3 should not output what you indicate - something is wrong with the test...
Code 4 a left bracket [ and test are the same thing - use only the left bracket with its matching right bracket, or only use test:
```

if [ -z "$discPtr" ]
if test -z "$discPtr"
```

```

$ discPtr='326400,489728'
if [ "$discPtr" = "" ] ; then echo empty; else echo not empty; fi
not empty
$ if [ -z "$discPtr" ] ; then echo empty; else echo not empty; fi     
not empty
$ discPtr=
$ if [ -z "$discPtr" ] ; then echo empty; else echo not empty; fi
empty
```

MrC

---

### Post by ewanchic on 2008-02-27
> **Mr. C. said:**
> Code 1 is missing a final double quote.
That wasn't a double quote, that was two single quotes, sorry.

> **Mr. C. said:**
> Code 2 executes the evaluation of the variable in trailing stuff in a subshell
Can you explain this one a little more to me. Thanks (^_^)

> **Mr. C. said:**
> Code 3 should not output what you indicate - something is wrong with the test...
That is why I'm so confused. I'm 99.99% sure this should be working. In most cases it does. It's like the bash doesn't want to work anymore?!, but I am assuming it really me that created the problem.

> **Mr. C. said:**
> Code 4 a left bracket [ and test are the same thing - use only the left bracket with its matching right bracket, or only use test:
```

if [ -z "$discPtr" ]
if test -z "$discPtr"
```
Thanks for the Correction  (^_^)



> **Mr. C. said:**
> ```

$ discPtr='326400,489728'
if [ "$discPtr" = "" ] ; then echo empty; else echo not empty; fi
not empty
$ if [ -z "$discPtr" ] ; then echo empty; else echo not empty; fi     
not empty
$ discPtr=
$ if [ -z "$discPtr" ] ; then echo empty; else echo not empty; fi
empty
```

MrC

Confirmed. I received the same results from commandline as you did. I aslo did:
```
discPtr=$(cdrskin dev=/dev/scd0 -msinfo 2>/dev/null)
```

from command line, same good,correct results

New Program:
```

#!/bin/bash -x

discDrive=/dev/scd0
discPtr=$(cdrskin dev=$discDrive -msinfo 2>/dev/null)

if [ "$discPtr" = "" ]; then echo empty; else echo not empty; fi
if [ -z "$discPtr" ]; then echo empty; else echo not empty; fi


discPtr='326400,489782'
if [ "$discPtr" = "" ]; then echo empty; else echo not empty; fi
if [ -z "$discPtr" ]; then echo empty; else echo not empty; fi


discPtr=
if [ "$discPtr" = "" ]; then echo empty; else echo not empty; fi
if [ -z "$discPtr" ]; then echo empty; else echo not empty; fi

```

Results:
```

+ discDrive=/dev/scd0
++ cdrskin dev=/dev/scd0 -msinfo
+ discPtr=0,163216
+ '[' 0,163216 = '' ']'
+ echo not empty
not empty
+ '[' -z 0,163216 ']'
+ echo not empty
not empty
+ discPtr=326400,489782
+ '[' 326400,489782 = '' ']'
+ echo not empty
not empty
+ '[' -z 326400,489782 ']'
+ echo not empty
not empty
+ discPtr=
+ '[' '' = '' ']'
+ echo empty
empty
+ '[' -z '' ']'
+ echo empty
empty

```

So it works on commandline, but not in a bash script?! Or is it really working?!

---

### Post by Mr. C. on 2008-02-27
> **ewanchic]That wasn't a double quote, that was two single quotes, sorry.[/quote]

Wow, in my browser window, two single quotes and one double quote are indistinguishable.  This is the first time I've been tripped up by this.  Time to change my mono-spaced font.

Anyway, 

[quote=ewanchic]Can you explain this one a little more to me. Thanks (^_^)[/quote]

When a command is finished executing, it returns a status.  The **if ( *some_command* ) said:**
> 
So it works on commandline, but not in a bash script?! Or is it really working?!
Of course it works, and will work the same either way.  If it is failing, you have an error somewhere.  At this point, I'm not sure what your script looks like, and what the exact output is.  If this doesn't clarify the problems, please post the script and output without modification.

MrC

---

