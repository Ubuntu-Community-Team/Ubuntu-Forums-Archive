---
title: "Help writing a bash script"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by zombifier25 on 2012-04-21
Well, for some unknown reason when I want to start Conky, it keeps segfaulting, but when I try again 5 minutes later, it works. It's rather annoying to add Conky to startup only to run it again later, so total scripting noob here needs your help in writing a script that tries to start Conky and waits for a period of time, if Conky crashes, the script will run it again, and if Conky manages to run, exits gracefully.

---

### Post by NikTh on 2012-04-21
Hi , 
I can help with the delay option and add it to startup applications. For the other parameter with "if crashes" i don't know .
Open gedit and

```
#! /bin/sh -e
sleep 10
conky
exit 0

```sleep 10 is the delay option . 10 are seconds . Change it at will. 

Save the file with name .. conky.sh . Give file permissions to execute 
```
chmod a+x conky.sh
```Go to startup applications and click add . Then give a name and at the command box write ```
./conky.sh
``` .

---

### Post by hakermania on 2012-04-21
Very good answer from [NikTh,]("http://ubuntuforums.org/member.php?u=1566509") only to add that in order to check whether conky has crashed or not and in order to repeat the launching till conky launches successfully, the scipt should go as following:

```

#!/bin/bash
sleep 10
runs=0
while (( $runs != 1 )); do
   conky&
   sleep 5;
   #checking if conky runs after 5 seconds, if not retry
   if pidof conky; then runs=1; else echo "It doesn't run"; fi
done
exit 0

```
[]("http://ubuntuforums.org/member.php?u=1566509")

---

### Post by zombifier25 on 2012-04-21
Thanks hakermania!

---

### Post by hakermania on 2012-04-21
> **zombifier25 said:**
> Thanks hakermania!

:popcorn:

---

