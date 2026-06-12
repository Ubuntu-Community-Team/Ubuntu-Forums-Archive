---
title: "Shell/bash script, if prompt"
date: 2014-03-20
forum: Programming Talk
---

### Post by rhss6-2011 on 2014-03-20
Hello,
It has been a while since I started writing shell/bash scripts and it is painfully obvious I have lost my touch. Anyways, I'd appreciate it if someone can help me fix the errors in my script.
First I will post the script itself and below that the errors my terminal is giving me.

```
#!/bin/bash
    printf "Are you in the correct directory where you want to inventory files?\n"
    read -p "Y/n --> " ans
if [ $ans == y ] ;then
    printf "Your Inventory will be created in a moment. Please wait...\n\n"
    ls -Rl | sort -dbm > ~/Documents/Inventory.txt
elif [ $ans = Y ] ; then
    printf "Your Inventory will be created in a moment. Please wait...\n\n"
    ls -Rl | sort -dbm > ~/Documents/Inventory.txt
elif [ $ans = yes ] ; then
    printf "Your Inventory will be created in a moment. Please wait...\n\n"
    ls -Rl | sort -dbm > ~/Documents/Inventory.txt
elif [ $ans = YES ] ; then
    printf "Your Inventory will be created in a moment. Please wait...\n\n"
    ls -Rl | sort -dbm > ~/Documents/Inventory.txt
else
    currentdir=`pwd`
    printf "Please type the path to the location you would like to inventory.\nIf this path contains spaces place a back-slash in
    front of EVERY space as in the example\n"
    read -p "/this/is/how\ to\ make\ spaces/in/a/path/to\ a\ directory " location
    cp $currentdir/inventory2.sh $location
fi
```

[B]AND NOW IN MY TERMINAL...

[/B]
```
USER@COMPUTER:/mnt/DATA/01-SCRIPTS$ sh inventory2.sh
Are you in the correct directory where you want to inventory files?
Y/n --> _**y**_

inventory2.sh: 4: [: y: unexpected operator
Please type the path to the location you would like to inventory.
If this path contains spaces place a back-slash in
    front of EVERY space as in the example
/this/is/how\ to\ make\ spaces/in/a/path/to\ a\ directory _**/home/USER/Documents**_
USER@COMPUTER:/mnt/DATA/01-SCRIPTS$ 
```

**According to my script**
What should have happened is that after using **y/Y/yes/YES** the script should have created a recursive inventory of ALL my files in that directory. My issue... I used an **if/then statement** the way it *should* work yet my terminal is telling me... What exactly???

If I could get past this obstacle, after the script is copied to the correct location it will execute the proper command (which is in my script) to create a sorted inventory of files in the directory where the script has been copied...

It's been about 2 years since I did ANY shell/bash coding and I see that I am in need of serious help here...

Any pointers?

---

### Post by Tristan_Williams on 2014-03-20
I noticed your problem right away.

On lines 4, 7, 10, & 13

You have the following:
```

if [ $ans = y ] ;then

```

It should be:
```

if [ "$ans" == "y" ]; then
    do crap
elif [ "$ans" == "n" ]; then
    don't do crap
fi

```

You MUST have the quotation marks around "$ans" and "y" or "n".
This is because when you don't, it takes it litterally. $ans is not the exact same character set as y.

When you put quotation marks, it says "Ok, $ans actually equals y, and "y" is equal to "y".

That's the only problem in the script.

---

### Post by steeldriver on 2014-03-20
Your shebang says

```
#!/bin/bash
```

but by invoking the script as

```
**sh** inventory2.sh
```

you actually tell the system to run the script using /bin/sh - which is a symlink to /bin/dash. The bash shell has a number of features that dash doesn't support as noted here --> [DashAsBinSh]("https://wiki.ubuntu.com/DashAsBinSh") in particular

> 
**[**

 The [ command (a.k.a. test) must be used carefully in portable scripts. [COLOR=#ff0000]**A very common pitfall is to use the == operator, which is a bashism; use = instead.**[/COLOR]


So while quoting is good practice, the actual issue is your use of ==

In bash:
```

$ read -p "Y/n --> " ans
Y/n --> y
$ if [ $ans == y ]; then echo "true"; fi
true

```

In dash:
```

$ sh
$ read -p "Y/n --> " ans
Y/n --> y
$ if [ $ans == y ]; then echo "true"; fi
sh: 2: [: y: unexpected operator
$ 
$ if [ "$ans" == "y" ]; then echo "true"; fi
sh: 4: [: y: unexpected operator
$ 
$ if [ $ans = y ]; then echo "true"; fi
true

```

EDIT: having said that, it would be much neater imho to use a case...esac construction instead of all the ifs

---

### Post by rhss6-2011 on 2014-03-20
I don't think that's the issue, because that is how I had it before this modified version and same error....

```
stephen@Stephen-HP-Pavilion:/mnt/DATA/01-SCRIPTS$ sh inventory2.shAre you in the correct directory where you want to inventory files?
Y/n --> y
inventory2.sh: 4: [: y: unexpected operator
Please type the path to the location you would like to inventory.
If this path contains spaces place a back-slash in
    front of EVERY space as in the example
/this/is/how\ to\ make\ spaces/in/a/path/to\ a\ directory ^C
stephen@Stephen-HP-Pavilion:/mnt/DATA/01-SCRIPTS$
```

**The script Code...**

```
#!/bin/bash    printf "Are you in the correct directory where you want to inventory files?\n"
    read -p "Y/n --> " ans
if [ $ans == "y" ] ;then
    printf "Your Inventory will be created in a moment. Please wait...\n\n"
    ls -Rl | sort -dbm > ~/Documents/Inventory.txt
elif [ $ans = "Y" ] ; then
    printf "Your Inventory will be created in a moment. Please wait...\n\n"
    ls -Rl | sort -dbm > ~/Documents/Inventory.txt
elif [ $ans = "yes" ] ; then
    printf "Your Inventory will be created in a moment. Please wait...\n\n"
    ls -Rl | sort -dbm > ~/Documents/Inventory.txt
elif [ $ans = "YES" ] ; then
    printf "Your Inventory will be created in a moment. Please wait...\n\n"
    ls -Rl | sort -dbm > ~/Documents/Inventory.txt
else
    currentdir=`pwd`
    printf "Please type the path to the location you would like to inventory.\nIf this path contains spaces place a back-slash in
    front of EVERY space as in the example\n"
    read -p "/this/is/how\ to\ make\ spaces/in/a/path/to\ a\ directory " location
    cp $currentdir/inventory2.sh $location
fi
```

---

### Post by Vaphell on 2014-03-20
**always quote your variables**

Pressing enter with null value will simply ignore unquoted $ans and produce something that bash will see as
```
if [ == y ]
```
long story short, it's going to fail
In bash you can use [[ ]] where unquoted variables work correctly.

commands under variants of 'yes' are redundant, you should avoid copy-pastas. Modification  = keeping track of all occurences and repeating changes n times. That's bad for correctness, readability and maintainability. Just compress these conditions into 1, eg with case
```
read -p "Y/n " ans
ans=${ans:-Y}  # default to Y if null
# alternative: read in recent versions of bash supports -i <default_value> 

case $ans in
  [yY]|[yY][eE][sS])  printf "Your Inventory will be created in a moment. Please wait...\n\n"
                      ls -Rl | sort -dbm > ~/Documents/Inventory.txt
                      ;;
      [nN]|[nN][oO])  printf "nope\n"
                      ;;
                  *)  printf "unknown option\n"
                      ;;
esac
```


backticks `` are deprecated and $() should be used instead.
in bash you can use $PWD instead of calling external command (pwd)
you are doing some funny stuff with $location.

```
read -p "type path with no escaping nonsense: " location
cp [COLOR="#0000FF"]"[/COLOR]$PWD[COLOR="#0000FF"]"[/COLOR]/inventory2.sh [COLOR="#0000FF"]"[/COLOR]$location[COLOR="#0000FF"]"[/COLOR]
```

---

### Post by rhss6-2011 on 2014-03-21
I solved the issue - After reading through the responses (thank you) I realized I never tried using ONE "=" instead of two. That solved the issue.

```

#!/bin/bash   
    printf "Are you in the correct directory where you want to inventory files?\n"
    read -p "Y/n --> " ans
if [ $ans = "y" ] ;then
    printf "Your Inventory will be created in a moment. Please wait...\n\n"
    ls -Rl | sort -dbm > ~/Documents/Inventory.txt
elif [ $ans = "Y" ] ; then
    printf "Your Inventory will be created in a moment. Please wait...\n\n"
    ls -Rl | sort -dbm > ~/Documents/Inventory.txt
elif [ $ans = "yes" ] ; then
    printf "Your Inventory will be created in a moment. Please wait...\n\n"
    ls -Rl | sort -dbm > ~/Documents/Inventory.txt
elif [ $ans = "YES" ] ; then
    printf "Your Inventory will be created in a moment. Please wait...\n\n"
    ls -Rl | sort -dbm > ~/Documents/Inventory.txt
else
    currentdir=`pwd`
    printf "Please type the path to the location you would like to inventory.\nIf this path contains spaces place a back-slash in
    front of EVERY space as in the example\n"
    read -p "/this/is/how\ to\ make\ spaces/in/a/path/to\ a\ directory " location
    cp $currentdir/inventory.sh $location
    read -p "Is the script now in the correct location?" ans2
if [ $ans2 = "y" ] ;then
    cd $location
    printf "Your Inventory will be created in a moment. Please wait...\n\n"
    ls -Rl | sort -dbm > ~/Documents/Inventory.txt
elif [ $ans2 = "Y" ] ; then
    cd $location
    printf "Your Inventory will be created in a moment. Please wait...\n\n"
    ls -Rl | sort -dbm > ~/Documents/Inventory.txt
elif [ $ans2 = "yes" ] ; then
    cd $location
    printf "Your Inventory will be created in a moment. Please wait...\n\n"
    ls -Rl | sort -dbm > ~/Documents/Inventory.txt
elif [ $ans2 = "YES" ] ; then
    cd $location
    printf "Your Inventory will be created in a moment. Please wait...\n\n"
    ls -Rl | sort -dbm > ~/Documents/Inventory.txt
else
    printf "I'm sorry, please try running the script again once you have placed the script in the correct location.\n
    Once the script is in the correct location, open the terminal in that folder and type 'sh inventory.sh'\n"
fi
```

---

