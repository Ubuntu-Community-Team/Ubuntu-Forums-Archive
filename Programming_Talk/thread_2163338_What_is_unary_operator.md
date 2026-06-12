---
title: "What is unary operator?"
date: 2013-07-18
forum: Programming Talk
---

### Post by bkpsusmitaa on 2013-07-18
I tried to contact [s1ightcrazed]("http://ubuntuforums.org/member.php?u=247182") because I saw his ability to explain things simply, in his posts [assign the exit status of a command to a variable]("http://ubuntuforums.org/showthread.php?t=373657"). I failed to get in touch with him.

I wrote a script that when run as daemon checks whether pppd is running, otherwise boots it, iteratively
Copied in a file pppdchk.sh
#!/bin/bash
done=0
while:
do
x=0
x='pidof pppd'
if [$x != "\n"]
then
sleep 1
else
pon dsl-provider
sleep 1
fi
done

The script runs, I get the result I want, but I get an output ...unary operator expected...
Why?

---

### Post by sudodus on 2013-07-18
I think 'while' wants something to evaluate (true or false). Try this script

```
tmp=hello;while [ "$tmp" != "q" ]; do echo "$tmp (q to quit)";read tmp;done
```

If you want the script to run forever, use something that will always be true (and quit with ctrl c).

Compare these two script lines:
```
tmp=hello;while false ; do echo "$tmp (q to quit)";read tmp;done
```
which does nothing and
```
tmp=hello;while true ; do echo "$tmp (q to quit)";read tmp;done
```
which continues until ctrl +c.

*Edit*: See this link for a definition of unary operator/operation

[https://en.wikipedia.org/wiki/Unary_operation](https://en.wikipedia.org/wiki/Unary_operation)

---

### Post by prodigy_ on 2013-07-18
> **bkpsusmitaa said:**
> unary operator expected... Why?
Because $x is either not defined or (in this case) contains an empty string. When possible, always protect vars with double quotes in bash. Example:
```
[ "$foo" != "" ] && echo "bar"
```

---

### Post by bkpsusmitaa on 2013-07-18
> **prodigy_ said:**
>  When possible, always protect vars with double quotes in bash. 
I have tested with quotes. It ruins the script.
Thanks, Sudodus, for the concepts of unary operator in unix and the while command in bash.
Let us brainstorm further. I believe we will arrive at a solution soon.
Thanks to all of you once again!

---

### Post by steeldriver on 2013-07-18
1. if you want to evaluate pidof pppd and store the result, you need backticks (backquotes) not regular single quotes

```
x=[COLOR=#0000ff]**`**[/COLOR]pidof pppd[COLOR=#0000ff]**`**[/COLOR]
```

or in bash you can use 

```
x=$(pidof pppd)
```

2. as well as quotes around the variables, you need space around the [ and ] i.e.

```
if [ "$x" != "\n" ]
```

3. a better way to test for an empty return value might be to use the -z (zero length string) or -n (non-zero length string) tests e.g.

```
$ x=`pidof pppd`
$ if [ -z "$x" ]; then echo "empty"; else echo "not empty"; fi
empty
$ 
$ x=`pidof firefox`
$ if [ -z "$x" ]; then echo "empty"; else echo "not empty"; fi
not empty

```

or

```

$ x=`pidof pppd`
$ if [ -n "$x" ]; then echo "not empty"; else echo "empty"; fi
empty
$ 
$ x=`pidof firefox`
$ if [ -n "$x" ]; then echo "not empty"; else echo "empty"; fi
not empty 

```

---

### Post by bkpsusmitaa on 2013-07-18
> **steeldriver said:**
>  ... you need backticks (backquotes) not regular single quotes...

I am sorry, I have indeed used backticks in the original script. I just typed wrong here.

I have to say I have tried the double quote around the variable, and this makes the script useless! You could see for yourself.

And for the rest of the script, **Superb! Brilliant!** Thanks.

I was just reading the man page of bash. I hope I will have to have a printed version of it. Thanks for the help.

Regards

---

### Post by Vaphell on 2013-07-19
if double quoted variable breaks your script you are doing something wrong. Variables have no business dangling in the open unquoted, because that only buys you whitespace related errors.

---

### Post by bkpsusmitaa on 2013-07-20
> **Vaphell said:**
> if double quoted variable breaks your script you are doing something wrong...
As I stated earlier, it reported about unary operator: "unary operator expected"
If you don't have pressing work at hand could you look into this please? [ Script hat manipulates strings within it ](http://ubuntuforums.org/showthread.php?t=2163911&p=12738253#post12738253)

---

### Post by Vaphell on 2013-07-20
not seeing your true code but its version typed by hand, i can't say what you did wrong but you did something wrong.
*[ $x = 'something' ]* when $x is whitespace only will expand to *[ = 'something' ]* and that's a broken condition - and it even might return unary operator expected as it sees = but has only 1 other param.
*[ "$x" = 'something' ]* will expand to *[ "<some whitespace>" = 'something' ]* and that's legit

---

