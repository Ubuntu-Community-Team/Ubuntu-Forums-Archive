---
title: "Date inserts carriage return in logfile"
date: 2007-07-12
forum: Programming Talk
---

### Post by Krijk on 2007-07-12
I'm pretty new at shellscripting and I run into some problems.

I created a script that also logs the results to a logfile. I use date to insert the date but it inserts a carriage return after inserting it. What should I do to change this? I can remove the CR afterwards, but there should be an easier way.

I use the following:

```
date=$(date +"%b %d %T")
echo "$date krijk1 check: apache is running " >>/var/log/check.log
```

The format it gives is:

```
Jul 12 12:43:38 
krijk1 check: apache is not running, restarted apache
```

It should be:

```
Jul 12 12:43:38 krijk1 check: apache is not running, restarted apache
```

---

### Post by Soybean on 2007-07-12
Well, that's interesting... I don't know much about shell scripting either, but I figured I could give it a shot. So I started with the following code (looks awfully similar to yours), and I'm not getting the extra linefeed.

```

#!/bin/bash

date=$(date +"%b %d %T")
echo "$date testing" >> test.log

```

```
Jul 12 08:35:45 testing
```


So... I guess the solution would be to run your script on my computer, because it works fine here. ;)

Oh, one thing -- the append >> kind of threw me off a bit. I had a typo in my script the first time I ran it... I fixed it, then checked again, and initially thought that it was still broken because the first thing I saw in test.log was the incorrect output from the last time. Kind of a silly mistake, but maybe you're getting caught by the same thing? That's all I can think of, because it doesn't seem reasonable that date would behave differently on different computers.

---

### Post by Krijk on 2007-07-12
I'm not running the script on Ubuntu, but on OpenBSD. Also I don't use bash but have tried it with sh and ksh. 

Oddly enough, when I tail the last lines in the logfile or cat it,  it only displays the text and not the date. When I open it in a texteditor the date is shown as it should. :confused:

---

### Post by crashie on 2007-07-12
Do you have Windows (CR,LF) line breaks in the source file? In some text editors you can change the line ending format (set it to "UNIX" or "LF"). If your text editor doesn't have this functionality you can copy your code into Firefox (in a text area somewhere) and then back to the text editor and you should get UNIX (LF) line breaks.

---

### Post by Krijk on 2007-07-12
Nope,

All systems I use are Linux or BSD. I get 0x0D (CR) in the file.

According to the manpages a /n is inserted after the formatting of the time. How to get rid of it after the formatting?

---

### Post by jyba on 2007-07-12
That's strange. The OpenBSD version of date must be different from the one installed by Ubuntu. If your version of 'date' is adding "\n" at the end of its string then perhaps the solution is to turn your script around, like this...

```
string="check: apache is running "
echo $(date +"%b %d %T $string")
```

---

### Post by Krijk on 2007-07-12
Thanks jyba,

I tried your solution and it works better than my own workaround. 

```
date=$(date +"%b %d %T" |cut -c1-15)
```

This works too, but sometimes it takes a lot longer than in the old situation.

---

### Post by cwaldbieser on 2007-07-13
> **Krijk said:**
> Nope,

All systems I use are Linux or BSD. I get 0x0D (CR) in the file.

According to the manpages a /n is inserted after the formatting of the time. How to get rid of it after the formatting?

Just remove the newline.
```

date=$(date +"%b %d %T" | tr -d "\n")

```

---

### Post by Mr. C. on 2007-07-13
Here's a little trick for you:

```
$date=$(date +"%b %d %T")$(echo) 
```

This works because newlines are stripped (and converted to spaces, except the last, which is removed) when assigning output to a variable.

Here's another option:
```
date=$(date +"%b %d %T")
date=${date/\n//}  
```

Neither of the two options above creates an additional process, so they are more efficient than using **tr** and a pipeline.

MrC

---

### Post by jyba on 2007-07-13
```
#! /bin/bash

echo "*********************************"
echo "AND THE WINNER IS...(wait for it)"
echo "*********************************"
echo "jyba"

time (for x in $(seq 1 500); do
string="krijk1 check: apache is running "
echo $(date +"%b %d %T $string")
done &>/dev/null)

echo "*********************************"
echo "Krijk-version-2"

time (for x in $(seq 1 500); do
date=$(date +"%b %d %T" |cut -c1-15)
echo "$date krijk1 check: apache is running "
done &>/dev/null)

echo "*********************************"
echo "cwaldbieser"

time (for x in $(seq 1 500); do
date=$(date +"%b %d %T" | tr -d "\n")
echo "$date krijk1 check: apache is running "
done &>/dev/null)

echo "*********************************"
echo "Mr. C.-version-1"

time (for x in $(seq 1 500); do
date=$(date +"%b %d %T")$(echo)
echo "$date krijk1 check: apache is running "
done &>/dev/null)

echo "*********************************"
echo "Mr. C.-version-2"

time (for x in $(seq 1 500); do
date=$(date +"%b %d %T")
date=${date/\n//}
echo "$date krijk1 check: apache is running "
done &>/dev/null)
echo "*********************************"
```

either jyba or Mr. C. :lolflag:

---

### Post by Mr. C. on 2007-07-13
Jyba, that's great.  How about showing the benchmark times for others too see as well; this is a fine lesson in simple performance benchmarks.

I'd recommend keeping the $date variable clear of other non-date related items; although your solution works fine, the extra text really isn't date-related, and this makes the solution problem-specific and less general. For example, one might want to use the value of $date in the context such as outputfile-$date, or as a parameter to a function.

Nice work,
MirC

---

### Post by efittery on 2011-11-22
If you use:

echo -n date >> logfile.txt

You will not get a carriage return in logfile.txt

The -n flag says to echo - suppress carriage returns

By the way, a new line is the same as a carriage return.

---

### Post by Arndt on 2011-11-22
> **efittery said:**
> If you use:

echo -n date >> logfile.txt

You will not get a carriage return in logfile.txt

The -n flag says to echo - suppress carriage returns

By the way, a new line is the same as a carriage return.

No, it is not. -n is fine, however.

And soon this thread will be closed.

---

