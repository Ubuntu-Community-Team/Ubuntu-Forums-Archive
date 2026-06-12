---
title: "Why does it require two key strokes to exit this script?"
date: 2013-08-03
forum: Programming Talk
---

### Post by GrouchyGaijin on 2013-08-03
Hi Guys,

First, thanks to you in the Programming Talk sub-forum, I've learned a lot, but obviously not enough.

I have a couple of questions about bash scripting.

Here is the script:

```


#!/bin/bash
cd ~/gpodder
bin/gpo update && bin/gpo download
until [ "$x" = "Q" ]; do
echo "Press D to delete episodes, press S to sync or Q to quit. "
    read x
    if [ "$x" = "D" ]
    then
rm /home/john/gpodder-downloads/"Coast to Coast AM Podcast"/*.mp3
elif [ "$x" = "S" ]
    then 
    ~/gpodder/bin/gpo sync
    echo "Scroll up to see how things worked out."
    fi
    read x
if [ "$x" = "Q" ]
then
killall OldCoastScript
else
echo "Hey quit already "
fi 
done

```

Question #1:
Why is it that if I choose Q without having run S or D then I need to press the Q key two times to terminate the script?

Question #2:
How should I write the script if I want more than three options?  Example: S to sync, D to delete files on the computer, C to clean old files from the walkman and Q to quit.

Thanks guys,  I really appreciate the help.

---

### Post by alarme on 2013-08-03
Hi

You are using two read statements.

Try some like this:

```

#!/bin/bash

cd ~/gpodder
bin/gpo update && bin/gpo download

until false; do
    echo "Press D to delete episodes, press S to sync or Q to quit. "
    read x

    if [ "$x" = "D" ]; then
        rm /home/john/gpodder-downloads/"Coast to Coast AM Podcast"/*.mp3
    elif [ "$x" = "S" ]; then 
        ~/gpodder/bin/gpo sync
        echo "Scroll up to see how things worked out."
    elif [ "$x" = "Q" ]; then
        echo "Q"
        killall OldCoastScript      # ????
        break                       # exit loop
    else
        echo "Hey quit already "
        break
    fi 
done

```

---

### Post by alarme on 2013-08-03
One tip:

If you are unsure what are you doing, avoid sentences "dangerous" on tests.
If possible, comment lines containing sentences like "rm" and substitute with inoffensive ones as "echo here delete things"

Cheers

---

### Post by GrouchyGaijin on 2013-08-03
Thanks for the insight.
I removed the read command in:

```


 read x
if [ "$x" = "Q" ]


```

and now the script terminates correctly.

---

### Post by steeldriver on 2013-08-03
A *case... esac* construction is often a neater way to do this kind of thing

```

#!/bin/bash

echo -e "Choose one of the following options:\nA - do something\nB - do domething else\nQ - quit"

while true; do
read -p "Please enter your choice: " input;
case "$input" in

  a|A) echo "Doing something"
  ;;

  b|B) echo "Doing something else"
  ;;

  q|Q) echo "Quitting"
     break;
  ;;

  *) echo "Oops"
  ;;

esac
done

```

---

### Post by GrouchyGaijin on 2013-08-03
> **steeldriver said:**
> A *case... esac* construction is often a neater way to do this kind of thing

```

#!/bin/bash

echo -e "Choose one of the following options:\nA - do something\nB - do domething else\nQ - quit"

while true; do
read -p "Please enter your choice: " input;
case "$input" in

  a|A) echo "Doing something"
  ;;

  b|B) echo "Doing something else"
  ;;

  q|Q) echo "Quitting"
     break;
  ;;

  *) echo "Oops"
  ;;

esac
done

```

Hey thanks SteelDriver - I'll give your suggestion a try.

---

### Post by GrouchyGaijin on 2013-08-04
@alarme

Thank you so much.
This seems to be working exactly the way I wanted it to work.
```


#!/bin/bash


cd ~/gpodder
bin/gpo update && bin/gpo download


until false; do
    echo "Press D to delete episodes, press S to sync, C to clean or Q to quit. "
    read x


    if [ "$x" = "D" ]; then
        rm /home/john/gpodder-downloads/"Coast to Coast AM Podcast"/*.mp3
    elif [ "$x" = "S" ]; then 
        ~/gpodder/bin/gpo sync
        echo "Scroll up to see how things worked out."
   elif [ "$x" = "C" ]; then 
        rm /media/WALKMAN/MUSIC/"Coast to Coast AM Podcast"/*.mp3
        echo "The Walkman has been cleaned."   
    elif [ "$x" = "Q" ]; then
        echo "Going down"
        killall CoastTest2      # ???? This is just the name of the script.
        break                       # exit loop
    else
        echo "Hey quit already "
        break
    fi 
    done




```

I appreciate the help.
I don't know why but the first time I tried to add the clean option I got an error that [C wasn't a command.  I *thought* I had copied the syntax correctly, but I guess not. The odd thing was that I had the same error on quit, which came from your script.  So I copied and pasted the way you wrote the sync part of the script, because that worked, and changed the letters and commands.  The problem stopped after that.
One other thing is that until I added done at the end, I had an end of file error.  I'm not sure when exactly you need to add done and when you do not.

In any case, thank you :p

---

### Post by Vaphell on 2013-08-04
*done* tells bash where the loop body (which starts with *do*) ends, just like *fi* ends *if then*/*elsif then*/*else* block and *esac* ends *case* statement

```
while <condition>/until <condition>/for x in .../for(( ... ))/select x in ...
**do**
    stuff to repeat
**done**
```

---

