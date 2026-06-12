---
title: "First  Bash Script"
date: 2008-05-14
forum: Programming Talk
---

### Post by anotherdisciple on 2008-05-14
I am writing my first bash script. It is mostly made for me and people who don't know how to set up Ubuntu once they freshly install it. I got it to do everything I wanted so far. Now, I want to give the user the option to install the Compiz settings manager and Avant Window Navigator. How do I write the script to where it will only install if the user says they want eye candy?

---

### Post by unutbu on 2008-05-14
```
#!/bin/bash
read -p "Eye candy? ([Y]/n) ";
if [ "$REPLY" = "n" ]; then
    echo "You pressed 'n'"
else
    echo "You pressed anything but 'n'"
fi

```

---

### Post by anotherdisciple on 2008-05-14
hmmm... so would this work?

```
#!/bin/bash
read -p "Would you like to install Compiz Effects? (Y/n) ";
if [ "$REPLY" = "Y" ]; then
    sudo aptitude install compizconf-settings-manager
if [ "$REPLY" = "n" ]; then
    echo "You chose to skip installation"
fi
```

---

### Post by BlueSkyNIS on 2008-05-14
```
#!/bin/bash
read -p "Would you like to install Compiz Effects? (Y/n) ";
if [ "$REPLY" = "Y" ]; then
    sudo aptitude install compizconf-settings-manager
if [ "$REPLY" = "n" ]; then
    echo "You chose to skip installation"
fi
```

You need one 'fi' just before second if

```
#!/bin/bash
read -p "Would you like to install Compiz Effects? (Y/n) ";
if [ "$REPLY" = "Y" ]; then
    sudo aptitude install compizconf-settings-manager
[COLOR="Red"]fi[/COLOR]
if [ "$REPLY" = "n" ]; then
    echo "You chose to skip installation"
fi
```

---

### Post by anotherdisciple on 2008-05-14
cool... what happens if they type "x" or something? will it ask them the question again?... that's what I want it to do.

---

### Post by ghostdog74 on 2008-05-14
then you will need a loop. Personally i use case/esac instead of if/else 
```

while true
do

 read ......
 case $REPLY in
   N|n ) #do something ;;
   Y|y ) # do something ;;
   Q|q ) exit;;
   * ) echo "huh??" ;;
 esac

done

```

---

### Post by dtmilano on 2008-05-14
Your prompt gives the idea that 'Y' is the default, and it isn't.
This would be safer and better:

> 
#!/bin/bash

DONE=false
while [ "$DONE" != true ]
do
	read -p "Would you like to install Compiz Effects? (Y/n): ";
	case "$REPLY" in
		""|Y|y)
    		        sudo aptitude install compizconf-settings-manager
			DONE=true
	 		;;
	
		n|N)
    		        echo "You chose to skip installation"
			DONE=true
			;;

		*)
			echo "Invalid input" >&2
			;;
	esac
done


---

### Post by anotherdisciple on 2008-05-14
```
#!/bin/bash

DONE=false
while [ "$DONE" != true ]
do
read -p "Would you like to install Compiz Effects? (Y/n): ";
case "$REPLY" in
""|Y|y)
sudo aptitude install compizconf-settings-manager
DONE=true
;;

n|N)
echo "You chose to skip installation"
DONE=true
;;

*)
echo "Invalid input" >&2
;;
esac
done 
```


Okay... I'm really new at this... so tell me if this is what the code is saying.

It asks "Would you like to install Compiz Effects? (Y/n)". The reply can be upper case or lower case? If Y or y... it installs. If n or N it says "You chose to skip installation". If the input is not Y,y,n,or N it says "Invalid input" and asks them again?

I need some direction in finding out how to read this stuff!!!! HAHA!

---

### Post by BlueSkyNIS on 2008-05-14
> I need some direction in finding out how to read this stuff!!!! HAHA!

Google is your best friend for this ;)


Cheers :)

---

