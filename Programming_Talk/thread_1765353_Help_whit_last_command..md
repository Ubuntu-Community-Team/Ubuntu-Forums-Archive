---
title: "Help whit last command."
date: 2011-05-23
forum: Programming Talk
---

### Post by MihaN on 2011-05-23
Hi, i am still learning i want to make a simple shell script.
I wish to make a function that will receive 2 arguments (two dates) and will return
all users who logged in during that period, how many times and how long were
they logged in.

I wish to call my function this way: ./functionName 29/05 30/05

This would print out all users that were logged in during that period
how many times did they login and how long were they logged in.

Result would be maybe like: username 5x 0 days 12:43

How can i go about this, thanks in advance.

---

### Post by papibe on 2011-05-23
This would be a good reading starts:
```
$ man last
```
[and, Very Simple Bash Scripts]("http://floppix.ccai.com/scripts1.html").

Regards.

---

### Post by MihaN on 2011-05-23
I know the use of command last but how do i
make use of the command "last" in a function or a for loop for instance : 

for "user" in last
do
echo user
done

---

### Post by papibe on 2011-05-23
Did you see the scripts examples?  Anyway, you could use something like this:
```
#!/bin/bash
last | \
while read -r line
do
    echo $line
done

```
That is because the lines have spaces and 'for' won't work that well. The best tool to parse the lines would be awk:
```
$ last | awk '{printf "USER: %s connected at %s\n", $1, $7}'
```
Regards.

---

### Post by hakermania on 2011-05-23
> **MihaN said:**
> I know the use of command last but how do i
make use of the command "last" in a function or a for loop for instance : 

for "user" in last
do
echo user
done
Actually, it is
```
for name in $(last); do #etc etc
```

---

