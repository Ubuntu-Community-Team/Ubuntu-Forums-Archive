---
title: "Help with a shell script"
date: 2011-04-16
forum: Programming Talk
---

### Post by msjones on 2011-04-16
Afternoon all. I am having a little fun with some shell scripts and I have hit a wall, wondered if anyone can help. Here is my script:

```
#!/bin/bash

FORTUNE=`fortune`

while [ $(echo $FORTUNE | wc -m) -lt 140 ]
do
echo $FORTUNE
exit 0
done

```

So as you can see I am using the fortune application you can get from the repos. If the output of fortune is less than 140 characters then it will echo the $FORTUNE variable. If the output is greater than 140 the program will exit.

What I want to happen is that if the $FORTUNE variable is greater than 140 to re-run the fortune app again until it gets an output of less than 140. How can I do this?

---

### Post by hakermania on 2011-04-16
```
#!/bin/bash
FORTUNE=`fortune`
while [ 1 ]; do
if [  $(echo $FORTUNE | wc -m) -lt 140 ]; then
echo $FORTUNE
exit 0
else
FORTUNE=`fortune`
fi
done
```

---

### Post by hakermania on 2011-04-16
By the way, the fortune command has a -n argument for this. See
```
man fortune
```

---

### Post by lloyd_b on 2011-04-16
> **msjones said:**
> Afternoon all. I am having a little fun with some shell scripts and I have hit a wall, wondered if anyone can help. Here is my script:

```
#!/bin/bash

FORTUNE=`fortune`

while [ $(echo $FORTUNE | wc -m) -lt 140 ]
do
echo $FORTUNE
exit 0
done

```

So as you can see I am using the fortune application you can get from the repos. If the output of fortune is less than 140 characters then it will echo the $FORTUNE variable. If the output is greater than 140 the program will exit.

What I want to happen is that if the $FORTUNE variable is greater than 140 to re-run the fortune app again until it gets an output of less than 140. How can I do this?

First off, no shell script is required for this - you can accomplish the same thing just by using the options of the 'fortune' command:```
fortune -sn 140
```will give you a "short" fortune, with short being defined as "less than 140 characters".

As to how to make the script work, I'd go with an "endless loop", repeating until it finds a short enough fortune:```
#!/bin/bash

# This loop will run forever - use a break to get out of it
while true; do
    FORTUNE=`fortune`

    # The test below is a cheat to determine if the fortune is more
    # than 140 characters long - ${FORTUNE:140} returns the substring starting
    # at the 140'th character - if the string is shorter than 140, it will
    # return an empty string ("").  
    if [ "${FORTUNE:140}" == "" ]; then
        # Shorter than 140 - break out of the loop
        break
    fi
done

echo $FORTUNE
```

Lloyd B.

---

### Post by msjones on 2011-04-16
Thanks for the help on this guys. I want to keep a fortune to under 140 characters because I am going to put the fortune into a script that will send it as an sms text message.

Your help is much appreciated.

---

### Post by hakermania on 2011-04-16
please mark the thread as solved! :)

---

