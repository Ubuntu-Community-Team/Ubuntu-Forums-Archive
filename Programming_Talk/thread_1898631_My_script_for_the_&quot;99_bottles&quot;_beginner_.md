---
title: "My script for the &quot;99 bottles&quot; beginner challenge"
date: 2011-12-21
forum: Programming Talk
---

### Post by /b/ryce on 2011-12-21
Here is my first bash script ever (aside from the obligatory "Hello, world!" one :) )
I originally got to the first challenge, read it, look up all sorts of guides on  loops and finally get some code to work, only to try to post it and find that the thread is  locked, so I decided to show it here and ask for help on my final error that I can't seem to fix that looks like it does nothing.
```

#!bin/bash
clear
x="99" #set variable for amount of beer.
y="bottles"
z="bottle"    
while [ $x -gt 0 ]; do #while [ $var -(GreaterThan) 0]
    echo "$x $y of beer on the wall, $x $y of beer."
    let x=x-1 #take a bottle away.
    #start grammar changes here
    if [ $x = 1 ]; then
        y=bottle
    fi
    if [ $x == 0 ]; then
        y=bottles
    fi
    if [ $x == 0 ]; then
        x="no more"
    fi
    echo "Take one down and pass it around, $x $y of beer on the wall."
    sleep 6 #gives enough time to sing the song
done
echo "No more bottles of beer on the wall, no more bottles of beer.
Go to the store and buy some more, 99 bottles of beer on the wall."
read -p "Press enter to end the script..."

```
After the loop, but before the final echo, I get this error:

/home/bryce/bta/99_bottles.sh: line 6: [: too many arguments

I don't quite know how to get the error to go away, any help would be appreciated.
To play to the end just comment the line that says 'sleep 6'(line 20)

---

### Post by CoffeeRain on 2011-12-21
What would happen if you took out your comment about greater than and then would your loop work with an actual '<' sign?

---

### Post by /b/ryce on 2011-12-21
Removing the comment does nothing, it's a comment. :P
and when I replace "-gt" with the sign for greater than ">", I get this error:
/home/bryce/bta/99_bottles.sh: line 6: [: no: unary operator expected
Edit:the script still works, it just throws the error after the loop.

---

### Post by pl@yer on 2011-12-21
Hi b/ryce

I think your problem is when you change "x" to be "no more". Then the test fails on line 6 - [ $x -gt 0 ]


You could probably just quote your variable so test doesnt think you are trying to test no and more.

```

if [ "$x" == 0 ] ...

```

OR

Put your final echo from inside the loop at this test and then break the loop.
```


if [ $x == 0 ]; then
        x="no more"

```

---

### Post by /b/ryce on 2011-12-30
Yes! I got it! I took a few days off to get a fresh look at it because I felt like I was ramming into a brick wall, and then I tried something new and I got it! That blasted error is gone!\\:D/

What I did was I took the final if...then statement and put it right after I declared the variables and before the loop.

Here's the finished code if anyone wants to try it out :)
```

#!bin/bash
clear
X=99 #set variable for amount of beer.
Y="bottles"
if [ $X == 0 ]; then
    X="no more"
fi
while [ $X -gt 0 ]; do #while [ $var -(GreaterThan) 0]
    echo "$X $Y of beer on the wall, $X $Y of beer."
    let X=X-1 #take a bottle away.
    #start grammar changes here
    if [ $X == 1 ]; then
        Y=bottle
    fi
    if [ $X == 0 ]; then
        Y=bottles
    fi
    echo "Take one down and pass it around, $X $Y of beer on the wall."
    sleep 6 #gives enough time to sing the song
done
echo "No more bottles of beer on the wall, no more bottles of beer.
Go to the store and buy some more, 99 bottles of beer on the wall."
read -p "Press enter to end the script..."

```
I think I'll do the next challenge in Common Lisp.

---

### Post by pbrane on 2011-12-31
One other thing.... I'm not sure why your script works, the first line *#!bin/bash* really should be #!**/**bin/bash. This script won't run on my machine without the '/' before 'bin/'
```

./beer.sh 
bash: ./beer.sh: bin/bash: bad interpreter: No such file or directory

```

Edit: this seems to work.
```

#!/bin/bash
clear
x=99 #set variable for amount of beer.
y="bottles"
z="bottle"    
while [ $x -gt 0 ]; do #while [ $var -(GreaterThan) 0]
    echo "$x $y of beer on the wall, $x $y of beer."
    let x=x-1 #take a bottle away.
    #start grammar changes here
    if [ $x = 1 ]; then
        y=bottle
    fi
    if [ $x == 0 ]; then
        y=bottles
    fi
#    if [ $x == 0 ]; then
#        x="no more"
#    fi
    echo "Take one down and pass it around, $x $y of beer on the wall."
    #sleep 6 #gives enough time to sing the song
done
echo "No more bottles of beer on the wall, no more bottles of beer.
Go to the store and buy some more, 99 bottles of beer on the wall."
read -p "Press enter to end the script..."

```
'x' is being interpreted as an integer in the beginning, then you assign it as a string and try to compare it to numerical 0 (zero).

---

