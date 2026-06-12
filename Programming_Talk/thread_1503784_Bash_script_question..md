---
title: "Bash script question."
date: 2010-06-07
forum: Programming Talk
---

### Post by j_arquimbau on 2010-06-07
I've got this script which generates random passwords:

```
#!/bin/bash

MAXSIZE=2

array1=(
a b c
)


MODNUM=${#array1[*]}

pwd_len=0

while [ $pwd_len -lt $MAXSIZE ]

do

  index=$(($RANDOM%$MODNUM))

  password="${password}${array1[$index]}"
  ((pwd_len++))

done

echo $password >> log
```

Now I'd like to modify it so that the script writes the new password into log unless it already exists. I don't know how to make a search for this (I've already tried and I've found nothing).

Any help so far?

---

### Post by disabledaccount on 2010-06-07
> **j_arquimbau said:**
> I don't know how to make a search for this (I've already tried and I've found nothing).

Any help so far?
There are tents of possible solutions, here you have one:
```

if [ ! -z "$(sed '/'$password'/ !d' </$path/$logfile)" ] ;then
echo "password exist"
fi

```;)

---

### Post by j_arquimbau on 2010-06-07
Thank you! I'm going to try!

---

### Post by DaithiF on 2010-06-07
Hi, maybe a little neater would be:
```
grep -q $password log || echo $password >> log

```

ie. append the password to the logfile unless the log file already contains it.

---

### Post by j_arquimbau on 2010-06-07
The grep option worked, while the other one didn't... I'm now trying to understand both commands. Thank you you two!

---

### Post by disabledaccount on 2010-06-07
> **j_arquimbau said:**
> The grep option worked, while the other one didn't... I'm now trying to understand both commands. Thank you you two!
Sed method must work, unless you have made typing errors or your bach rc is badly messed.

In fact , both solutions are bad. First rule in bash-scripting is to use build-in commands as often as possible - you will get memory-hungry and slow solutions otherwise (because of forking and separating child processes by creation of additional instancess of "current" process). So, I suggest, you should use something like that:

```

path=$HOME/logs
file=log

while read  word; do
if [ "$word" = "$passwd" ]; then
    echo "passwd exist"
    break
fi
done </$path/$file
```

The difference is, thant no subprocess will be launched and less memory will be used -> built-ins are faster.

---

### Post by j_arquimbau on 2010-06-08
I probably didn't type the right parameters. When I find a moment I'll check the manual and see why it didn't work. ;)

Thank you again!

---

