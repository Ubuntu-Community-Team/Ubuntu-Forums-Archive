---
title: "Bash while loop and user input"
date: 2012-06-11
forum: Programming Talk
---

### Post by thatdamkid on 2012-06-11
So this one is bugging me. I know exactly why it doesn't work i 
just don't know how to work around it.

```

#!usr/bin/bash

set -e
trap "echo 'Exiting...'; sleep 1; clear" EXIT

clear

Master_Loop ()
{

while [ 1 ];do
        answer="x"; read -p "Skip forward? (y) or (n)" -t 3 answer
                if [ $answer = y ];then
                        echo 'Skipping...'
                        date
                        sleep 2
                        clear
                        Master_Loop
                elif [ $answer = n ];then
                        echo 'Waiting 5 secods...'
                        sleep 5
                        date
                        sleep 2
                        clear
                        Master_Loop
                else
                        echo 'You Waited...'
                        sleep 2
                        clear
                        Master_Loop
                fi
done
}

Master_Loop


```

Basically I nee 1 of 3 things to happen

1. $answer is = to 'y' and the date is printed immediately
2. $answer is = to 'n' and we wait 5 more seconds to print the date
3. $answer is left blank and we clear the screen and start all over again

1 and 2 work just fine 3 on the other hand fails miserably and exits.



Im sure that the problem is in this line, but what it is i am not clear on.
```
read -p "Skip forward? (y) or (n)" -t 3 answer
```

This is my first time working with loops so I'm sorry for the bad code.

---

### Post by Vaphell on 2012-06-12
```
if [ $answer = y ]
```
with empty value it becomes
```
if [ = y ]
```

in other words - quote your variables
you could use case instead of if/elif/else too

---

### Post by sisco311 on 2012-06-12
+1

Also, you call your function recursively from inside an infinite loop . This is probably not what you want to do. ;) Either use recursion or an infinite while loop.

The syntax of while is:
```
while COMANNDS
do
    COMMANDS
done
```

You use the test command (`[') simply to return true. For that there are two more appropriate commands, the true and the null command `:'
```
while :;do something; done
while true; do something; done
```

Here are some links for you: :)
[http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)
[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)
and of course the  BashFAQ and BashPitfalls from my signature.

---

### Post by thatdamkid on 2012-06-12
Making progress i think

```
#!usr/bin/bash

set -e
trap "echo 'Exiting...'; sleep 1; clear" EXIT

clear
answer=z

while : ;do
        if [ "$answer" = "g" ];then
                echo 'please wait...'
                bash ~/tools/t
        else
        read -p "Skip forward? (y) or (n)" -t 3 answer
                if [ "$answer" = "y" ];then
                        echo 'Skipping...'
                        date
                        sleep 2
                        clear

                elif [ "$answer" = "n" ];then
                        echo 'Waiting 5 secods...'
                        sleep 5
                        date
                        sleep 2
                        clear
                break
                fi
        let answer=g
        fi
done

```

---

