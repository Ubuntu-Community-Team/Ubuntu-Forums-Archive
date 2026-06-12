---
title: "Timing sections of a shell script"
date: 2009-06-14
forum: Programming Talk
---

### Post by kaibob on 2009-06-14
I have been measuring the time it takes to run variations of specific sections of a shell script. I researched this a bit and came up with the following code. This  works (and typically meets my needs), but I have not been able to find a way to display decimal fractions of a second.

```
#!/bin/bash
commands
TIME1=$(date +%s)
commands being timed
TIME2=$(date +%s)
TIMETOTAL=$(($TIME2-$TIME1))
echo ""$0" took $TIMETOTAL seconds" >> scripttime.txt
```

As an alternative, I looked at the time command but couldn't figure out how to get it to work with shell scripts as above. Is there a way to use the time command or to display decimal fractions of a second with the date command?

As an aside, I occasionally use the Dash shell, so any bash-specific commands would not work for me. 

Thanks for the help. 

kaibob

---

### Post by stroyan on 2009-06-15
You could use "date +%s.%N" for subsecond precision.
But bash or dash alone won't do floating point math.
You could use awk for that.

---

### Post by unutbu on 2009-06-15
How about this?
[PHP]#!/bin/bash
time {
echo "Begin commands"
sleep 5
echo "End commands"
}

echo
echo

time {
echo "Some more commands"
sleep 5
echo "End Some more commands"
}
[/PHP]

---

### Post by bigboy_pdb on 2009-06-15
bc can be used to perform floating point calculations in bash.

```

i=3.4
j=2.3
echo "sqrt($i + $j)" | bc

# Outputs 2.3

```

**EDIT:** If you want greater precision, just add zeros (ie. i=3.400 and j=2.300)

---

### Post by bigboy_pdb on 2009-06-15
Some more complete code would be:

```

start="$(date +%s.%N)"

sleep 5 # Put your script here

stop="$(date +%s.%N)"

echo "$stop - $start" | bc

```

Based on what you wrote, I'm sure you could figure it out, but a more complete example couldn't hurt.

---

### Post by kaibob on 2009-06-16
Thanks stroyan, unutbu, and bigboy_pdb for the responses. I tried both suggested solutions and both worked great. The time command is easy to use and provides nicely formatted data but appears not to work with Dash. So, the date +%s.%N solution will also be very useful.

Thanks again,

kaibob

---

