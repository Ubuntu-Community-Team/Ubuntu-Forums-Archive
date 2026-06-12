---
title: "NOOB- Very simple Bash serial port issue"
date: 2008-08-13
forum: Programming Talk
---

### Post by MacD on 2008-08-13
This is my first attempt at a shell script.  Warning- I am not a programmer.

[PHP]
clear
echo "MASSLOGGER"
echo "ENTER FILENAME"	
read FILENAME
CONTINUE=0
while [ $CONTINUE -ne 1 ]
do
	echo "ENTER PLOT # or scan barcode"
	read PLOT
	echo "Press Print Button on Balance"
	read MASS < /dev/ttyS0
	clear
	echo "$PLOT,$MASS" >> $FILENAME
	cat $FILENAME
done
exit 0
[/PHP]

It reads an ID number from a CueCat barcode scanner or keyboard, then gets a weight from an OHAUS balance through the serial port and writes to a file.

It works, except I cannot figure out how to "open" the serial port.  My current workaround is to run:

Screen /dev/ttyS0

and then end that process from the system monitor.

Is there a simple way (getty?) to get the serial port open in proper form, or automate my hack.  i.e. how do I identify the process # for Screen and kill it from within a shell script?

Thanks.

---

### Post by pmasiar on 2008-08-13
More standard way is to get arguments from commandline, not to ask for them:

[http://www.ibm.com/developerworks/library/l-bash2.html](http://www.ibm.com/developerworks/library/l-bash2.html)

And why you want to kill current process? If you get out of loop, shell script will terminate.

Or did I missed something?

---

### Post by MacD on 2008-08-13
Thanks for the link, that looks like a good resource.

Opening screen, and then killing it is the only way I have found that a simple read from /dev/ttyS0 works.  There is some sort of initiation or opening of the serial port that this screen program does that works.  I found it by trial and error, but don't know what is happening.

---

