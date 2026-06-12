---
title: "Regex pattern matching"
date: 2013-11-17
forum: Programming Talk
---

### Post by termvrl on 2013-11-17
Hi All,

I tried to use regex to do a pattern matching for CPU % usage. i only need the value, 0.0.

The command i use: 
```

top -bn1 | grep "Cpu(s)" | grep ".\.." | grep ".\..%us"

```
The result:
```

Cpu(s):  [COLOR=#ff0000]0.0%us[/COLOR],  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st

```

After some time, i managed to get the right regex for the pattern matching but its not work in my server.
The error prompt out:
```
top -bn1 | grep \d.\d(?=%us)
-bash: syntax error near unexpected token `('

```

Any way i can solve this?
Thanks

---

### Post by MG&amp;TL on 2013-11-17
For your error, that's because your shell (bash) attempts to parse the expression you give to grep, and fails. To avoid that, use quotes:

```
top -bn1 | grep '\d.\d(?=%us)'
```

However, that doesn't seem to work, at least not on my system, and I don't know enough about grep's pattern matching to fix it. Instead, I used a combination of grep (to get the right line), awk (to get the right column), and sed (trim excess rubbish):

```
$ top -bn1 | grep 'Cpu(s)' | awk '{print $2}' | sed 's/%us,//g'
7.4

```

---

### Post by vasa1 on 2013-11-17
In this specific instance ```
top -bn1 | awk 'NR==3 { print $2}'
``` seems to do as well.

---

### Post by steeldriver on 2013-11-17
You are trying to use a perl-style regular expression - grep supports that to some extent, but you need to add the -P switch

```

$ top -bn1 | grep **-P** '\d.\d(?=%us)'
Cpu(s):  [COLOR=#ff0000]7.5[/COLOR]%us,  5.0%sy,  0.0%ni, 87.2%id,  0.2%wa,  0.0%hi,  0.0%si,  0.0%st

```

If you want just the matching number, add -o

```

$ top -bn1 | grep **-oP** '\d.\d(?=%us)'
7.5

```

Note that '\d.\d' will match 2 digits separated by ANY single character - if you want to match just the decimal point, you should escape the period, either '\d**\.**\d' or '\d**[.]**\d'

---

### Post by termvrl on 2013-11-17
Hi,

Thanks for the response.
It works.

I will find more into 'awk' , 'sed' . its usefull.

---

### Post by termvrl on 2013-11-17
Hi steeldriver,

Thanks for your explanation.
I dont know that regex has different style. Thanks again.

---

### Post by vasa1 on 2013-11-18
> **steeldriver said:**
> ...
If you want just the matching number, add -o

```

top -bn1 | grep -oP  '\d.\d(?=%us)'

```
...
That code doesn't work for me but this does:
```
top -bn1 | grep -oP '\d\.\d +(?=us)'
```
I tried both on a regular desktop Xubuntu.

When I checked **man pcre**, I found this:
>   Lookahead assertions

       Lookahead assertions start with `(?=` for positive assertions and `(?!` for
       negative assertions. For example,

         `\w+(?=;)`

       matches  a word followed by a semicolon, but does not include the semi&#8208;
       colon in the match, ... 
This is my grep:
```
[12:56 PM] ~ $ grep --version
grep (GNU grep) 2.14
Copyright (C) 2012 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by Mike Haertel and others, see <http://git.sv.gnu.org/cgit/grep.git/tree/AUTHORS>.

```

---

### Post by steeldriver on 2013-11-18
@vasa1 your expression matches a different pattern (digit-period-digit *followed by one or more spaces*) - is your 'top' output different i.e. '7.5 %us' instead of '7.5%us'?

FWIW for matching a floating point  number in general I'd suggest something like

```
grep -oP '**[\d.]+**(?=%us)'
```

which will match a wider range of possible field widths and precisions i.e. 7%us, 7.5%us, 17%us, 27.5%us etc. (note that the period is treated as literal when inside a [ ] character set, so no need to escape it). If you need to allow for *optional* trailing whitespace beween the number and the % sign, you could add \s* i.e.

```
grep -oP '[\d.]+**\s***(?=%us)'
```

or maybe more perlish

```
grep -oP '[\d.]+**\s+?**(?=%us)'
```

---

### Post by vasa1 on 2013-11-18
This is what I get when I run **top -bn1**

```
[06:06 PM] ~ $ top -bn1
top - 18:06:09 up  2:27,  2 users,  load average: 0.04, 0.04, 0.05
Tasks: 133 total,   1 running, 132 sleeping,   0 stopped,   0 zombie
%Cpu(s):  2.7 us,  0.6 sy,  0.0 ni, 95.5 id,  1.2 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   4010624 total,  1106888 used,  2903736 free,    46644 buffers
KiB Swap:  6159668 total,        0 used,  6159668 free,   660436 cached
```

So our **top** outputs do differ. Any idea why? My **top** is whatever came with the system.

---

### Post by steeldriver on 2013-11-18
I don't know - top has *lots* of configuration options (plus optional global / personal rc files)... or it could just be the top version? mine is

```

$ top --version
    top: procps version 3.2.8

```

---

### Post by vasa1 on 2013-11-18
> **steeldriver said:**
> I don't know - top has *lots* of configuration options (plus optional global / personal rc files)... or it could just be the top version? mine is

```

$ top --version
    top: procps version 3.2.8

```
Mine is:
```
[06:32 PM] ~ $ top -v
	procps-ng version 3.3.3
usage:	top -hv | -bcHiSs -d delay -n limit -u|U user | -p pid[,pid] -w [cols]
[06:32 PM] ~ $ 

```
and it didn't like **top --version**!

---

### Post by vasa1 on 2013-11-18
As for the use of **+** before (or as part of) the look ahead assertion, maybe **-P** is also different?
```

       -P, --perl-regexp
              Interpret  PATTERN  as  a  Perl  regular  expression  (PCRE, see
              below).  This is highly experimental and grep  -P  may  warn  of
              unimplemented features.

```

---

### Post by termvrl on 2013-11-19
Hi all,
i try to put in on a bash script.
But i encountered an error.
Here my script:
```

#!/bin/bash
cpu=$(top -bn1 | grep -oP '\d.\d(?=%us)')
#echo "Test $cpu "
if[$cpu > 0.0];then
echo "High CPU usage : $cpu "
else
echo "CPU is normal : $cpu "
fi

```

The error:
```

./cpu.sh: line 4: syntax error near unexpected token `then'
./cpu.sh: line 4: `if[$cpu > 0.0];then'

```

I think the if else is correct. Maybe because of the variable in format 0.0 ?

---

### Post by sisco311 on 2013-11-19
The syntax of the if statement is:
```
if COMMANDS; then OTHER COMMANDS; fi
```

You need a space after `if'. 

Also BASH arithmetic uses integers only. For floating point numbers you have to use an external program like bc or dc:
 ```
if (( $(bc <<< "$cpu > 0.0") )); then ...
```

See:
[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Blocks_.28if.2C_test_and_.5B.5B.29](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Blocks_.28if.2C_test_and_.5B.5B.29)
and BashFAQ 022 (link in my signature).

---

### Post by termvrl on 2013-11-19
Hi,

Thanks for your reply.
This script is work for me, but need to install 'bc' first.
```

#!/bin/bash
cpu=$(top -bn1 | grep -oP '\d\d.\d(?=%us)')
#echo "Test $cpu "
if (( $(bc <<< "$cpu > 0.0") )); then
    echo "High CPU usage : $cpu "
else
    echo "CPU is normal : $cpu "
fi

```

And use this code to generate some CPU load to test.

```

#!/bin/bash

while : ; do
true
done

```

Thanks again.

p/s: i edit the regex pattern to match 00.0 format.

---

