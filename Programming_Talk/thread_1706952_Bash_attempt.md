---
title: "Bash attempt"
date: 2011-03-14
forum: Programming Talk
---

### Post by Hippytaff on 2011-03-14
If anyone is bored or just willing to help someone who has dabbled with scripting in many different forms adn cone to grips with none (mainly due to lack of time). Can you show my how I can make this better (or even just passable as a serious attempt at scripting)? :-D

```
#!/bin/bash

echo "This script will seek to return as much relevant information as possible to help diagnose the problem"
echo "press y then [enter] to continue or q then [enter] to quit- you may need to provide your password: "
read ans
if [ $ans == "y" ]; then

echo "probing..."

#the commands redirect to wireless.txt bit
echo "************************************" >> wireless-results.txt
echo "        pci wireless devices" >> wireless-results.txt
echo "************************************" >> wireless-results.txt
lspci | grep -i wirel >> wireless-results.txt
echo "************************************" >> wireless-results.txt
echo "        usb wireless devices" >> wireless-results.txt
echo "************************************" >> wireless-results.txt
lsusb | grep -i wirel >> wireless-results.txt
echo "************************************"  >> wireless-results.txt
echo "        List of network devices" >> wireless-results.txt
echo "************************************"
sudo lshw -C Network >> wireless-results.txt
sleep 3
echo "************************************" >> wireless-results.txt
echo "          List of drivers" >> wireless-results.txt
echo "************************************" >> wireless-results.txt
lsmod >> wireless-results.txt
echo "************************************" >> wireless-results.txt
echo "           network info" >>  wireless-results.txt
echo "************************************" >> wireless-results.txt
ifconfig >> wireless-results.txt
echo "************************************" >> wireless-results.txt
echo " Wireless specific network info" >> wireless-results.txt
echo "************************************" >> wireless-results.txt

iwconfig 1>> wireless-results.txt 2>&1

echo "probe complete...please see 'wireless-results.txt'"

#the else part of the clause

else
echo "Good luck!"
fi


``` Feeble...I know :roll:

The worst bit is I know there are much better ways,

Thanks

---

### Post by Arndt on 2011-03-14
> **Hippytaff said:**
> If anyone is bored or just willing to help someone who has dabbled with scripting in many different forms adn cone to grips with none (mainly due to lack of time). Can you show my how I can make this better (or even just passable as a serious attempt at scripting)? :-D

```
#!/bin/bash

echo "This script will seek to return as much relevant information as possible to help diagnose the problem"
echo "press y then [enter] to continue or q then [enter] to quit- you may need to provide your password: "
read ans
if [ $ans == "y" ]; then

echo "probing..."

#the commands redirect to wireless.txt bit
echo "************************************" >> wireless-results.txt
echo "        pci wireless devices" >> wireless-results.txt
echo "************************************" >> wireless-results.txt
lspci | grep -i wirel >> wireless-results.txt
echo "************************************" >> wireless-results.txt
echo "        usb wireless devices" >> wireless-results.txt
echo "************************************" >> wireless-results.txt
lsusb | grep -i wirel >> wireless-results.txt
echo "************************************"  >> wireless-results.txt
echo "        List of network devices" >> wireless-results.txt
echo "************************************"
sudo lshw -C Network >> wireless-results.txt
sleep 3
echo "************************************" >> wireless-results.txt
echo "          List of drivers" >> wireless-results.txt
echo "************************************" >> wireless-results.txt
lsmod >> wireless-results.txt
echo "************************************" >> wireless-results.txt
echo "           network info" >>  wireless-results.txt
echo "************************************" >> wireless-results.txt
ifconfig >> wireless-results.txt
echo "************************************" >> wireless-results.txt
echo " Wireless specific network info" >> wireless-results.txt
echo "************************************" >> wireless-results.txt

iwconfig 1>> wireless-results.txt 2>&1

echo "probe complete...please see 'wireless-results.txt'"

#the else part of the clause

else
echo "Good luck!"
fi


``` Feeble...I know :roll:

The worst bit is I know there are much better ways,

Thanks

There is not so much here to simplify, but one thing is that you can get rid of all the redirections. Study this example:

```
exec >> /tmp/hej
echo foo
date
echo bar

```

It redirects standard output to a file for the rest of the script.

---

### Post by Hippytaff on 2011-03-14
Excellent...cheers!

---

### Post by sisco311 on 2011-03-14
You probably want something like:
```

exec 6>&1
exec > /tmp/file

echo "redirect to /tmp/file"
echo "redirect to /tmp/file"

exec 1>&6 6>&-

echo "print to stdout"

```

I would put the commands in a new block and redirect the block to the file:
```

{
  echo line1
  echo line2
} > /tmp/file

echo "stdout"

```

For more details, check out: [http://wiki.bash-hackers.org/howto/redirection_tutorial](http://wiki.bash-hackers.org/howto/redirection_tutorial)

---

### Post by Hippytaff on 2011-03-14
> **sisco311 said:**
> You probably want something like:
```

exec 6>&1
exec > /tmp/file

echo "redirect to /tmp/file"
echo "redirect to /tmp/file"

exec 1>&6 6>&-

echo "print to stdout"

```I would put the commands in a new block and redirect the block to the file:
```

{
  echo line1
  echo line2
} > /tmp/file

echo "stdout"

```For more details, check out: [http://wiki.bash-hackers.org/howto/redirection_tutorial](http://wiki.bash-hackers.org/howto/redirection_tutorial)

Thanks sisco. I did a bit of reading to find out how to restore exec, and using file descriptors etc...excellent link though - bookmarked :-)

---

### Post by sisco311 on 2011-03-14
Cool!

You need to make your script more readable. Use some indentation and functions:
```

log () {
  echo "whatever"
  echo "and so on"
}

read -rn1 -p "[y/N]: " ans
if [[ $ans == [yY] ]]; then
  log > /path/to/file
else
  echo "..."
fi

```

---

### Post by Hippytaff on 2011-03-15
```
#!/bin/bash

echo "This script will seek to return as much relevant information as possible to help diagnose the problem"
echo "press y then [enter] to continue or q then [enter] to quit- you may need to provide your password: "
read ans
if [ $ans == "y" ]; then

echo "probing..."

#redirect stdout using file descriptor 5 - the 5>&1 bit
#and redirect errout exec 2>&1 bit 
WLESS=wireless-results.txt

exec 5>&1
exec > $WLESS

exec 2>&1

#commands to get info

echo "************************************"
echo "        pci wireless devices"
echo "************************************"
echo
lspci | grep -i wirel
echo
echo "************************************"
echo "        usb wireless devices"
echo "************************************"
echo
lsusb | grep -i wirel
echo
echo "************************************"
echo "        List of network devices"
echo "************************************"
echo
sudo lshw -C Network
echo
sleep 3 #wait for 3 seconds
echo "************************************"
echo "          List of drivers"
echo "************************************"
echo
lsmod
echo
echo "************************************"
echo "           network info"
echo "************************************"
echo
ifconfig
echo
echo "************************************"
echo " Wireless specific network info"
echo "************************************"
echo
iwconfig

date

#restore stdout

exec 1>&5 5>&-

echo "probe complete...please see 'wireless-results.txt'"

#the else part of the clause

else
echo "Good luck!"
fi


```This is where I got to...thanks for the advice and yes I should use indents and make things more readable etc...forming a bad habit :?

Anyway thanks for the advice and the links...the penny is dropping ;-)

---

### Post by gmargo on 2011-03-15
> **Hippytaff said:**
> Can you show my how I can make this better (or even just passable as a serious attempt at scripting)?

You've managed to code in two of my biggest peeves with amateur shell scripts:

1. Interactivity.
You query the user and ask him to type a 'y'.  Why? He already ran the script.  Don't waste time asking a pointless question.

2. Overwriting fixed-name file.
Just print to stdout!  User can redirect results if he wants.

---

### Post by Hippytaff on 2011-03-16
> **gmargo said:**
> You've managed to code in two of my biggest peeves with amateur shell scripts:

1. Interactivity.
You query the user and ask him to type a 'y'.  Why? He already ran the script.  Don't waste time asking a pointless question.

2. Overwriting fixed-name file.
Just print to stdout!  User can redirect results if he wants.

lol thanks for the feedback. It was mainly just an exercise to learn to use those functions, but I will bear that in mind if I ever reach a stage where my bash skills become useful for people to actually use :-)

---

