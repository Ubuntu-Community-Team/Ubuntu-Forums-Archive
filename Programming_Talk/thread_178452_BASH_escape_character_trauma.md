---
title: "BASH escape character trauma"
date: 2006-05-17
forum: Programming Talk
---

### Post by pablored on 2006-05-17
I'm trying to read one character at a time from user input and when they press ESC I want to exit.  This seemed remarkably simple, but I am having issues with the other escape/control characters.  Pressing F1, or an arrow key is also recognised as ESC.  

^[ ... basically it seems like the 'read -sn 1 userInput' is reading the ESC command as two separate inputs.  

HELP!

Stripped down code, that has no possiblity of exit (beware! remove the trap... ctrl-c is disabled etc)

```
#!/bin/bash

trap "echo -n 'Control-Character | '" SIGQUIT SIGHUP SIGINT SIGTERM SIGTSTP
echo -e '\E[40;32m'
let COUNTER=0
while [ $COUNTER -lt 10 ]; do
read -sn 1 SELECTION
case "$SELECTION" in
        "R" | "r" )
                echo
                echo "Running"
        ;;
        "V" | "v" )
                clear
                echo "LAST FIVE RUNS"
        ;;
        "H" | "h" )
                clear
                echo "HELP"
        ;;
        "^[" )
                clear
                echo "Are you sure you want to turn off the machine? [y/n]"
        ;;
        * )
                # Default option.
                echo
                echo "Not yet in database."
        ;;
esac
done
exit 0
```

---

### Post by pablored on 2006-05-17
Revising things a little the escape key is read successfully as = ^[ . 

The left arrow = ^[OD ... which is actually more than one character according to BASH... so it gets read as the ESC key has been pressed and then some extra input.

I need to either,
1: disable all other keys starting with this.
2: set the escape key to something new and very unique that is one character
3: deal with the extra input made after the first char... a second check after escape to catch the new input?

I am hoping someone else has had to deal with this, surely?

Thanks in advance

---

### Post by llonesmiz on 2006-05-17
I think this link may be useful:

[http://lists.debian.org/debian-user/2003/10/msg01699.html]("http://lists.debian.org/debian-user/2003/10/msg01699.html")

---

### Post by pablored on 2006-05-17
Playing with the code in the example I get this, but it seems to basically substitute "^[" with "1b".  As it stands I have the same trouble with "1b" being the start (first char) of the arrow keys, F keys and the delete key.  

```
#!/bin/bash

read -sn 1 SELECTION
SELECTION=$( echo $SELECTION | od -t x1 | awk '{ print $2}' )
case "$SELECTION" in
"^[" )
        echo escape
;;
* )
        echo other
        echo "$SELECTION"
;;
esac
```

I really hope I'm not going to have to start coding again, but I can't see how a new language would be any better anyway.  It is more of an OS level trouble.  The last time I worked on a character reading command line app was Pascal under DOS and that went alright, lol.  

Thanks for the reply, its really nice to get a pointer and new avenue to try.

---

### Post by llonesmiz on 2006-05-18
I'm sorry, I think that I didn't really understood the script I referred you to. I'm really bad at bash scripting. Testing that script I've realized that it doesn't achieve what you want. I've made some modifications and I think that now it behaves according to your goals. If not, I'm really sorry for wasting your time. Here it is:

```
#!/bin/bash

read -sn 1  KEY
SELECTION=$( echo $KEY | od -t x1 | awk '{ print $2}' )
case "$SELECTION" in
"1b" )
        read -sn 1 -t 1 SELECTION2
        if [ $? -ne 0 ]
        then
            echo escape
        else
            while [ $? -eq 0 ]
            do
                read -sn 1 -t 1 SELECTION2
            done
            echo "arrow or something equally ugly"
        fi
;;
* )
        
    
        echo other
        echo "$KEY"
       
;;
esac
```

---

### Post by CyRaid on 2009-03-02
I know this is extremely old, but wouldn't it be useful to use C-Style strings? "\n" means a backslash and an 'n' in Bash.  It's only useful when you're using echo with the -e parameter.  On the other hand, C-Style strings are made like:

```

A=$'First Line\nSecond Line'

```

You could do something like this:

```

read -sn 1 Key
case "$Key" in
  $'\e') echo "Escape Key!";;
esac

```

Hope that helps anyone!

---

### Post by renepo on 2011-07-24
Here is the function code you are looking for (I had the same problem :P):

```

#!/bin/bash

IFS=$'\n'

while read -sn1 key
do
 ord_value=$(printf '%d' "'$key")
 pressed_key="$ord_value"

 if [[ $ord_value -eq 27 ]]; then
  old_tty_settings=`stty -g`
  stty -icanon min 0 time 0
  read key
  if [[ ${#key} -gt 0 ]]; then
   for (( i=0;i<${#key};i+=1 ))
   do
    ord_value=$(printf '%d' "'${key:$i:1}")
    pressed_key="$pressed_key:$ord_value"
   done
  fi
  stty "$old_tty_settings"
 fi

 echo "$pressed_key"
done

```

---

### Post by Perfect Storm on 2011-07-24
Necromancy is a forbidden art on the forums.

Thread closed.

---

