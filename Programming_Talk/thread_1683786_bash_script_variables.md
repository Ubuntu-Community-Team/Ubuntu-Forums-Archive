---
title: "bash script variables"
date: 2011-02-08
forum: Programming Talk
---

### Post by kartabosh on 2011-02-08
i'm puzzled as to why the first part of the script doesn't work...

```
#! /bin/bash
Num=3
function back-me-up {
Num=$(( $Num +22 ))
lenght=${#string}
echo "$@ $Num
"
}
clear
export -f back-me-up

find /home/ali/tmp -execdir bash -c "back-me-up {}" \;
echo "

try again

"
LIST=`find /home/ali/tmp`
for X in $LIST 
do
back-me-up $X
done
```

output:
```
ali@alimobile:~$ ./bin.sh

/home/ali/tmp 22

./update 22

./scrot 22

./email 22



try again


/home/ali/tmp 25

/home/ali/tmp/update 47

/home/ali/tmp/scrot 69

/home/ali/tmp/email 91

ali@alimobile:~$ 

```

---

### Post by Rany Albeg on 2011-02-08
I **think** the problem is by invoking another instance of Bash.
> find /home/ali/tmp -execdir **bash -c** "back-me-up {}" \;.

---

### Post by Arndt on 2011-02-08
> **kartabosh said:**
> i'm puzzled as to why the first part of the script doesn't work...

```
#! /bin/bash
Num=3
function back-me-up {
Num=$(( $Num +22 ))
lenght=${#string}
echo "$@ $Num
"
}
clear
export -f back-me-up

find /home/ali/tmp -execdir bash -c "back-me-up {}" \;
echo "

try again

"
LIST=`find /home/ali/tmp`
for X in $LIST 
do
back-me-up $X
done
```

output:
```
ali@alimobile:~$ ./bin.sh

/home/ali/tmp 22

./update 22

./scrot 22

./email 22



try again


/home/ali/tmp 25

/home/ali/tmp/update 47

/home/ali/tmp/scrot 69

/home/ali/tmp/email 91

ali@alimobile:~$ 

```

With the 'find' command, you invoke a new bash process for every file, so each time, the Num variable starts at 0.

---

