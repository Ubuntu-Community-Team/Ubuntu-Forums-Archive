---
title: "[SOLVED] How to to make an if loop to start again in bash"
date: 2008-01-25
forum: Programming Talk
---

### Post by victorbrca on 2008-01-25
Hi all,

  I have a quick one. Is there a way to make an if loop to start the script again if it fails?? 

  Please bear in mind that I'm just starting to learn bash. This is an exercise from a book I've been reading.

```
$ cat calc2.sh | nl -w7 | expand | tr -s '[:blank:]'
 1 #!/bin/bash
 
 2 echo "Enter the value to be calculated"
 
 
 3 while read expression
 4 do 
 5 if [ "$expression" = "quit" -o "$expression" = "exit" ]
 6 then clear ; exit 0
 7 fi
 
 8 echo "$expression" | grep -e '[0-9]' > /dev/null
 
 9 if [ "$?" -eq "1" ]
 10 then 
 11 echo
 12 echo "Stop screwing around and enter a number"
 13 read expression
 14 fi
 
 15 echo "computing..."
 16 sleep 3
 
 17 echo "still computing..."
 18 sleep 3
 
 19 echo "I'm almost as slow as Windows..."
 20 sleep 3
 
 21 echo "Finally!! "
 22 sleep 1 
 23 echo
 
 24 echo "The result is `/usr/bin/expr "$(( expression ))"`"
 25 sleep 1
 26 echo
 
 27 echo "Enter another or type "exit" to exit"
 
 28 done
```

  It only interprets loop 9 once.

Thanks,

Vic

---

### Post by stroyan on 2008-01-25
It seems that you want line 13 to go back to the top of the while loop at line 3.
You can do that by changing line 13 from 'read expression' to 'continue'.
The continue builtin will go around for another iteration of an enclosing loop.

---

### Post by victorbrca on 2008-01-26
> **stroyan said:**
> It seems that you want line 13 to go back to the top of the while loop at line 3.
You can do that by changing line 13 from 'read expression' to 'continue'.
The continue builtin will go around for another iteration of an enclosing loop.

Awesome... that works perfectly... 

Thanks a lot stroyan!!!  :)


Vic

---

### Post by Cappy on 2008-01-26
I'm just going to share an alternate way of doing the same thing:

```
#!/bin/bash
 
echo "Enter the value to be calculated"

while read expression; do 
    if [ "$expression" = "quit" -o "$expression" = "exit" ]; then 
        clear; exit
    fi

    if [ -z "`echo "$expression" | grep '[0-9]'`" ]; then
        echo
        echo "Stop screwing around and enter a number"
        continue
    fi
 
 15 echo "computing..."
 16 sleep 3
 
 17 echo "still computing..."
 18 sleep 3
 
 19 echo "I'm almost as slow as Windows..."
 20 sleep 3
 
 21 echo "Finally!! "
 22 sleep 1 
 23 echo
 
 24 echo "The result is `/usr/bin/expr "$(( expression ))"`"
 25 sleep 1
 26 echo
 
 27 echo "Enter another or type "exit" to exit"
 
 28 done
```

---

### Post by victorbrca on 2008-01-26
Thanks for taking the time and writing a better script for me Cappy.

I did some research and found this:

> [ -z STRING ]	True of the length of "STRING" is zero.
[ -n STRING ] or [ STRING ]	True of the length of "STRING" is non-zero.

On my script on line 9 I'm checking if line 8 fails or not. Now by adding an "if" condition "-z", is it only checking the length of the string?? (confused) 


Vic.

---

### Post by ghostdog74 on 2008-01-26
here's a "neater" way. 
```

while true
do
    echo "Enter the value to be calculated"
    read expression
    case "$expression" in
        [0-9]*[^a-zA-Z]) 
             echo "Only simple check for digit"
             break;;
        quit|exit ) clear;exit ;;
        [^0-9]* ) 
             echo "Stop screwing around and enter a number"
             continue;;        
    esac
done
# further processing.

```

---

### Post by victorbrca on 2008-01-27
> **ghostdog74 said:**
> here's a "neater" way. 


Is this shell scripting as well?

---

