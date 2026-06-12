---
title: "Daemonizing a script."
date: 2009-11-15
forum: Programming Talk
---

### Post by Barriehie on 2009-11-15
Hello!  So I've got a .sh script that I want to have loaded at boot time and I want to be able to manage it via sudo /etc/init.d/scriptname {start|stop|restart}, just like the other daemons.  The daemon script will be root:root in my ~/bin dir and the 'manager' will be in the /etc/init.d dir, also root:root.

Below is the manager script, does anyone see any issues with this???

I'm not clear on the grep/delay part so for now it's commented out, what does that do???

TIA,
Barrie

```

#!/bin/sh

#
# Start picsdaemond daemon that renames and moves
# downloaded .jpg files.
#


PICSDAEMOND=/home/barrie/bin/picsdaemond
PIDFILE=/var/run/picsdaemond.pid

test -x $PICSDAEMOND || exit 0

. /lib/lsb/init-functions

case "$1" in
start)
log_begin_msg "Starting picsdaemond..."

#
#  No Clue On This Part!
#
#
#DELAY=`grep -v '^\s*#' $CONF | grep -i -m 1 "daemon" | awk -F '=' '{print $2}'`
#if [ -z "$DELAY" ] ; then
#DELAY="-daemon 300"
#else
#DELAY=''
#fi

start-stop-daemon -S -q -p $PIDFILE -x $PICSDAEMOND
log_end_msg $?
;;
stop)
if [ -f $PIDFILE ] ; then
log_begin_msg "Stopping ddclient..."
start-stop-daemon -K -q -p $PIDFILE
log_end_msg $?
rm -f $PIDFILE
fi
;;
restart|reload|force-reload)
$0 stop
$0 start
;;
*)
log_success_msg "Usage: $0 {start|stop|restart|reload|force-reload}"
exit 1
;;
esac

exit 0

```

---

### Post by falconindy on 2009-11-15
For determining settings, its a lot easier to use a configure file and then import it as such:
```
. /path/to/scriptname.conf
```
Define your settings as bash variables, and then you won't need to do any sort of parsing and redefinition.

Since you haven't posted your script, it's hard to tell what you're doing. However, if you're using some sort of delay to intermittently run the script, it might be easier to just set it up via cron. If you're using a library like inotify, then you shouldn't need a delay.

---

### Post by Barriehie on 2009-11-15
> **falconindy said:**
> For determining settings, its a lot easier to use a configure file and then import it as such:
```
. /path/to/scriptname.conf
```
Define your settings as bash variables, and then you won't need to do any sort of parsing and redefinition.

Since you haven't posted your script, it's hard to tell what you're doing. However, if you're using some sort of delay to intermittently run the script, it might be easier to just set it up via cron. If you're using a library like inotify, then you shouldn't need a delay.

Not really anything to configure.  Here's the script.

```

#!/bin/bash

touch /var/run/picsdaemond.pid
echo $$ >> /var/run/picsdaemond.pid

#
#  Variable Setup
#
LOOPER="TRUE"
OLDDIR="/home/barrie/Desktop/temp/pics/"
NEWDIR="/home/barrie/disk/temp/"
declare -a CHARSARRAY=( 'a' 'A' 'b' 'B' 'c' 'C' 'd' 'D' 'e' 'E' 'f' 'F' 'g' 'G' 'h' 'H' 'i' 'I' 'j' 'J' 'k' 'K' 'l' 'L' 'm' 'M' 'n' 'N' 'o' 'O' 'p' 'P' 'q' 'Q' 'r' 'R' 's' 'S' 't' 'T' 'u' 'U' 'v' 'V' 'w' 'W' 'x' 'X' 'y' 'Y' 'z' 'Z' '0' '1' '2' '3' '4' '5' '6' '7' '8' '9' )
declare -a CHARS
declare -i NUMBER=0
declare -i LOOPCOUNTER=0

cd $OLDDIR

while [ "$LOOPER" = "TRUE" ]
do
    find /home/barrie/Desktop/temp/pics/ -name *.jpg 1>/home/barrie/Desktop/temp/pics/go 2>/dev/null

   if [ -s $OLDDIRgo ]
   then

	rm /home/barrie/Desktop/temp/pics/go

	for file in *
	do
	    while [ $LOOPCOUNTER -lt 10 ]
	    do
		RANDOM=$(date +%N)
		NUMBER=$((RANDOM%62+1))
		CHARS[$LOOPCOUNTER]=${CHARSARRAY[$NUMBER]}
		LOOPCOUNTER+=1
	    done
	    LOOPCOUNTER=0         # ----------------------------- Reset name length counter
	    NEWFILENAME=${CHARS[0]}${CHARS[1]}${CHARS[2]}${CHARS[3]}${CHARS[4]}${CHARS[5]}${CHARS[6]}${CHARS[7]}${CHARS[8]}${CHARS[9]}.jpg

        mv $OLDDIR$file $NEWDIR$NEWFILENAME

        declare -a CHARS=  # ----------------------------- Reset CHARS array

	done               # ----------------------------- End of for file in
    else
	sleep 20
    fi

sleep 20                   # ----------------------------- Pause, load break!

done                       # ----------------------------- Infinite loop, never exit

```

---

### Post by falconindy on 2009-11-15
Oh, got it. You've copied the init script from somewhere else that had the delay section implemented. Wouldn't worry about it.

---

### Post by Barriehie on 2009-11-15
> **falconindy said:**
> Oh, got it. You've copied the init script from somewhere else that had the delay section implemented. Wouldn't worry about it.

Yes, I left the delay in and it made no difference.  I've found out that I can't/did it wrong? redirect STDOUT and STDERR via either the script launcher or the script so I'm going to step this up to C++.  For now I've commented out the whole thing except for the one liner that works from my desktop launcher.  It works but doesn't allow the control I'm endeavoring to implement.

Good thing GRUB has a recovery mode... :)

Barrie

---

