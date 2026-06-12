---
title: "Really rather useful bash script for games needs help"
date: 2008-02-12
forum: Programming Talk
---

### Post by mikeym on 2008-02-12
Hi,

I'm trying to clean up a script that I have for launching games into a new xserver running a minimal setup. The bit I'm really stuck with is making it install itself and perform the steps necessary to make it run.

This is what I have so far and the comments near the beginning are what I'm looking to do by way of install. I hope someone more experienced with bash than me will be able to help because this script runs great for me and I would like to share the joy of game for ubuntu that just work with others.

**x.game**
```
#!/bin/bash
PIDFILE="/home/mikey/.xgame.pid"
WMPATH="/usr/bin/openbox"
BGIMAGE="/home/mikey/Images/Desktop/full_919-linux-background.jpg"

#BATCH FUNCTIONS TO BE CARRIED OUT ON INSTALL
#get the values for the variables above 
#su edit /etc/X11/Xwrapper.config and
#replace "allowed_users=console"
#with "allowed_users=anybody"
#groupadd chvt
#sudo usermod -a -G chvt <user>
#sudo visudo
#and insert "%chvt ALL= NOPASSWD: /usr/bin/chvt"
#sudo apt-get install openbox
#sudo apt-get install feh
#create this file and make it exacutable and put it in the path

function start {
	if [ -f "/tmp/.X1-lock" ]; then
		echo "X Display :1 already open"
		sudo chvt 12
		DISPLAY=:1
	else
		echo "Starting Daemon:"
		start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --make-pidfile --name xgame --startas /usr/bin/xinit -- $WMPATH -- :1 vt12 &
		sleep 2s
		DISPLAY=:1
		feh --bg-scale "$BGIMAGE" & 
	fi
	PROGRAM=$1
	echo "Program: $PROGRAM"
	if [ "$PROGRAM" != "" ]; then
		execute $*
	fi
}
function stop {
	echo "Stoping Daemon:"
	start-stop-daemon --stop --quiet --oknodo --pidfile $PIDFILE --name xinit --startas /usr/bin/xinit 
}
function execute {
	if [ -f "/tmp/.X1-lock" ]; then
		echo "Switching to display :1"
		sudo chvt 12
		DISPLAY=:1
	else
		echo "Display :1 is not running!"
		echo "Try 'x.game start PROGRAM'"
		exit 1	
	fi
	PROGRAM=$1
	shift
	if [ "$PROGRAM" == "" ]; then
		echo "Usage: "
		echo "x.game [start | stop] [PROGRAM] [parameters]"
		exit 1
	else
		while (( "$#" )); do
			if [[ -n "$1" && $1 == *\ * ]]; then
				ARGS="$ARGS \"$1\""
			else
				ARGS="$ARGS $1"
			fi
			shift
		done
	fi
	echo $PROGRAM $ARGS
	echo $ARGS | xargs $PROGRAM
}
#START OF SCRIPT
IFS="
"
SS=$1
echo "Selecting: $SS"
case "$SS" in
	start)
		echo "Starting:"
		shift
		start $*
		;;
	stop)
		echo "Stoping:"
		shift
		stop $*
		;;
	restart)
		echo "Restarting:"
		shift
		stop $*
		start $*
		;;
	*)
		echo "Executing:"
		execute $*
esac
exit 0

```

PS I do actually have one gripe about the way that this script runs on my system and that is that I'm not happy about the way that parameters are passed. So any suggestions on that would also be appreciated.

---

### Post by mikeym on 2008-02-13
OK this is what I've come up with so far.

#BATCH FUNCTIONS TO BE CARRIED OUT ON INSTALL
#get the values for the variables above 
#su edit /etc/X11/Xwrapper.config and
#replace "allowed_users=console"
#with "allowed_users=anybody"

```
sudo awk '{ if ($1 ~ /^allowed_users=/) { printf "#"; print; print "allowed_users=anybody"; } else print }' /etc/X11/Xwrapper.config > /tmp/Xwrapper.config
sudo mv /tmp/Xwrapper.config /etc/X11/Xwrapper.config
```

```
groupadd chvt
current_user=`id | sed 's/uid=[0-9][0-9]*(\([^)]*\)).*/\1/'`
sudo usermod -a -G chvt $current_user
```

#sudo visudo
#and insert "%chvt ALL= NOPASSWD: /usr/bin/chvt"

```
sudo cat /etc/sudoers > /tmp/sudoers; echo "%chvt ALL= NOPASSWD: /usr/bin/chvt" >> /tmp/sudoers
sudo visudo -c -f /tmp/sudoers
if [ $? != 0 ]; then exit 1; fi
if [ -e /etc/sudoers.tmp ]; then exit 1; fi
sudo mv /tmp/sudoers /etc/sudoers
```

I'm really quite dubious about this last line as I'm not sure you're allowed to do this. But I can't see any other way of editing sudoers from bash. Is there a better way?
```

sudo apt-get install openbox
sudo apt-get install feh
```

still looking for way of installing the file into the path itself and the parameters problem and getting the variables at the start automatically.

---

