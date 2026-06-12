---
title: "Need some help with sed/regexp and bash scripting"
date: 2007-07-19
forum: Programming Talk
---

### Post by AncientPC on 2007-07-19
If this would be better done with perl let me know.

What I want to do is output the current time, last minute load, and battery usage into a file (and then run every minute as a cron job).

What I have thus far is:
```
#!/bin/bash

#format: #time,battery %,load

tmp=~/battery.tmp
output=/var/log/battery.log

date %H:%M, > $tmp
acpi -b | sed -e 's/.*: //g' -e 's/[[:space:]]//g' >> $tmp
cat $tmp | sed -e 'N' -e 's/\n//g' >> $output
rm -f $tmp

exit
```

I have a few questions.

1) How do I extract information using sed as opposed to removing all unnecessary information?  I guess what I'm looking for is a function that returns a substring based off regexp.

For example I would something that did this:
```
acpi -b | <some command> [...%] | sed -e 's/[[:space:]]//g'
77%
```

2) I'm currently retrieving last minute's load by using
```
w | sed -e 's/.*, //g'
0.67
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
ting     :0       -                17:38   ?xdm?   2:49m  0.27s x-session-manag
ting     pts/0    :0.0             17:38   33:13m  5.27s  5.04s top
ting     pts/1    :0.0             17:39   31:42m  0.14s  0.14s bash
ting     pts/2    :0.0             17:40    3:38m  0.35s  0.35s bash
ting     pts/3    :0.0             17:56    1.00s  0.21s  0.01s w
ting     pts/4    :0.0             18:08   60.00s  0.16s  0.16s bash
```

How do I get rid of the other lines?

3) As you've noticed above I'm deleting pattern spaces using s/<regexp>//g'.  I still don't understand how to use sed -e /<regexp>/d correctly.

4) I read somewhere that you could store the stdout contents of a command in bash scripting by simply assigning a variable but it doesn't seem to work for me.
```
#/bin/bash

a='ls -al'
echo $a

exit
```

Running the above lines gives me:
```
./test.sh
ls -al
```

---

### Post by Ramses de Norre on 2007-07-19
1) Use sed's p command to print text, I don't really understand what you want to achieve so I can't help you better, give a detailed example if you still don't understand (I don't have acpi so I don't know what it outputs).

2) Use head, I'd do it like this: ** w|head -1|cut -f13 -d" "**, It's a bit more difficult with sed...

3) What is it you don't understand? **sed -e 's/<regex>//g'** does the same as **sed -e '/<regex>/d'**.

4) Instead of  **a='ls -la'** you should use **a=$(ls -la)**, it doesn't preserve newlines however, I'm not sure how to save the output with newlines, using a pipe might be your best option.

---

### Post by AncientPC on 2007-07-19
1)
```
ting@Kin:~$ acpi -b
     Battery 1: charging, 57%, 01:13:01 until charged
```

What's the best way to get 57%  from the above line?

Edit: After reading the rest of your post I got the result by doing this:
```
ting@Kin:~$ acpi -b | cut -f2 -d"," | sed -e 's/[[:space:]]//g'
62%
```

Is there an easier way to trim leading and trailing white space?

Is there anyway to get the information through regexp pattern matching (i.e. an in-line grep) as opposed to removing what I don't want?

2) Thanks, I didn't know about head or cut, they make it much easier.

3)
```
ting@Kin:~$ echo abc123def | sed -e 's/[[:digit:]]//g'
abcdef
ting@Kin:~$ echo abc123def | sed -e '/[[:digit:]]/d'
ting@Kin:~$
```

4) Thanks, exactly what I was looking for.

---

### Post by stylishpants on 2007-07-20
> **AncientPC said:**
> 1)
```
ting@Kin:~$ acpi -b
     Battery 1: charging, 57%, 01:13:01 until charged
```

What's the best way to get 57%  from the above line?

Edit: After reading the rest of your post I got the result by doing this:
```
ting@Kin:~$ acpi -b | cut -f2 -d"," | sed -e 's/[[:space:]]//g'
62%
```

Is there an easier way to trim leading and trailing white space?

Is there anyway to get the information through regexp pattern matching (i.e. an in-line grep) as opposed to removing what I don't want?


Sure, here are some ways:

```

# egrep uses POSIX regexps
# -o flag prints only the match, not the rest of the line
acpi -b | egrep -o '[0-9]+%'

# Perl uses perl-style regexps of course
# Remove the l flag if you don't want a newline automatically appended
# See these man pages for more info: perlre perlrun
acpi -b | perl -nle 'print $& if /\d+%/'

```

> **AncientPC said:**
> 1)

2) Thanks, I didn't know about head or cut, they make it much easier.

3)
```
ting@Kin:~$ echo abc123def | sed -e 's/[[:digit:]]//g'
abcdef
ting@Kin:~$ echo abc123def | sed -e '/[[:digit:]]/d'
ting@Kin:~$
```

4) Thanks, exactly what I was looking for.

---

### Post by Mr. C. on 2007-07-20
> **Ramses de Norre said:**
> 3) What is it you don't understand? **sed -e 's/<regex>//g'** does the same as **sed -e '/<regex>/d'**.

Convince yourself that your two sed expressions do not produce the same results.  Or let this convince you:

```
$ echo -e 'line one\nline two' | sed -e 's/one//g'               
line 
line two
$  echo -e 'line one\nline two' | sed -e '/one/d'   
line two
$ 
```

> **Ramses de Norre said:**
> 4) Instead of  **a='ls -la'** you should use **a=$(ls -la)**, it doesn't preserve newlines however, I'm not sure how to save the output with newlines, using a pipe might be your best option.

The two forms of are equivalent.  Output assigned to variables has newlines converted to spaces.  This behavior can be changed if necessary, but it rarely is.

AncientPC - no need to use temporary files when assigning output to a variable is cheaper, more convenience (no cleanup) and less error prone.

MrC

---

### Post by ghostdog74 on 2007-07-20
> **AncientPC said:**
> 1)
```
ting@Kin:~$ acpi -b
     Battery 1: charging, 57%, 01:13:01 until charged
```

What's the best way to get 57%  from the above line?

the best way: ```
acpi -b |awk '{print $NF}'
```
> 
Edit: After reading the rest of your post I got the result by doing this:
```
ting@Kin:~$ acpi -b | cut -f2 -d"," | sed -e 's/[[:space:]]//g'
62%
```

Is there an easier way to trim leading and trailing white space?

not necessary if using awk method

---

### Post by AncientPC on 2007-07-20
> **Mr. C. said:**
> The two forms of are equivalent.  Output assigned to variables has newlines converted to spaces.  This behavior can be changed if necessary, but it rarely is.

How come **echo 'ls -al'** doesn't return what I want but **echo $(ls -al)** does?

Thanks to everyone who replied.  This is what I've ended up with:
```
#/bin/bash
#format: #time,battery %,load

output=/var/log/battery.log

time=$(date +%H:%M,)
battery=$(acpi -b | gawk '{print $4}')
load=$(w | head -n1 | gawk '{print $NF}')

echo $time$battery$load >> $output

exit
```

---

### Post by Mr. C. on 2007-07-20
> **AncientPC said:**
> How come echo 'ls -al' doesn't return what I want but echo $(ls -al) does?

I thought they were backquotes -I see now they are single quotes. I was trying to clarify that backquotes anad $() command substitution were the same.  Sorry for the noise.

MrC

---

