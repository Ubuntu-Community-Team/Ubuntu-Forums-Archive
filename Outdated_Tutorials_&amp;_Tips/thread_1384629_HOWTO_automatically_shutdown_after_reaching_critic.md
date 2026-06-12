---
title: "HOWTO: automatically shutdown after reaching critical temperature script"
date: 2010-01-18
forum: Outdated Tutorials &amp; Tips
---

### Post by DeusEx on 2010-01-18
Worked this out for my water cooled system (idea sparked after I saw my rig was almost out of fluid :D ):

EDITED @ jan 19. 2009


PREREQUISITES:

I am assuming you have lm-sensors set up correctly, and your temperatures appear as 'temp1' through 'temp3' when you type:
```

sensors |grep temp

```
Note: temperatures are in Celcius!


HOW TO INSTALL THE SCRIPT:

1. save this script (almost straight copy from /etc/init.d/skeleton) to ~/tempguard:

```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          tempguard
# Required-Start:    $local_fs $syslog
# Required-Stop:     $local_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: tempguard
# Description:       hardware temperature health guard
#
### END INIT INFO

# Author: Foo Bar <foobar@baz.org>
#
# Please remove the "Author" lines above and replace them
# with your own name if you copy and modify this script.

# Do NOT "set -e"

# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/sbin:/usr/sbin:/bin:/usr/bin
DESC="Hardware temperature health guard"
NAME=tempguardd
DAEMON=/usr/bin/$NAME
DAEMON_ARGS="--options args"
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME

# Exit if the package is not installed
[ -x "$DAEMON" ] || exit 0

# Read configuration variable file if it is present
[ -r /etc/default/$NAME ] && . /etc/default/$NAME

# Load the VERBOSE setting and other rcS variables
. /lib/init/vars.sh

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

VERBOSE=yes

#
# Function that starts the daemon/service
#
do_start()
{
	# Return
	#   0 if daemon has been started
	#   1 if daemon was already running
	#   2 if daemon could not be started
	#start-stop-daemon --start --quiet --pidfile $PIDFILE --exec $DAEMON --background --test > /dev/null \
	start-stop-daemon --start --exec $DAEMON --background --test > /dev/null \
		|| return 1
	#start-stop-daemon --start --quiet --pidfile $PIDFILE --exec $DAEMON --background -- \
	start-stop-daemon --start  --exec $DAEMON --background -- \
		$DAEMON_ARGS \
		|| return 2
	# Add code here, if necessary, that waits for the process to be ready
	# to handle requests from services started subsequently which depend
	# on this one.  As a last resort, sleep for some time.
}

#
# Function that stops the daemon/service
#
do_stop()
{
	# Return
	#   0 if daemon has been stopped
	#   1 if daemon was already stopped
	#   2 if daemon could not be stopped
	#   other if a failure occurred
	#start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --pidfile $PIDFILE --name $NAME
	# don't use PID files because they seem to get lost...
	start-stop-daemon --stop --retry=TERM/30/KILL/5 --name $NAME
	RETVAL="$?"
	[ "$RETVAL" = 2 ] && return 2
	# Wait for children to finish too if this is a daemon that forks
	# and if the daemon is only ever run from this initscript.
	# If the above conditions are not satisfied then add some other code
	# that waits for the process to drop all resources that could be
	# needed by services started subsequently.  A last resort is to
	# sleep for some time.
#	start-stop-daemon --stop --quiet --oknodo --retry=0/30/KILL/5 --exec $DAEMON
#	[ "$?" = 2 ] && return 2
	# Many daemons don't delete their pidfiles when they exit.
	rm -f $PIDFILE
	return "$RETVAL"
}

#
# Function that sends a SIGHUP to the daemon/service
#
do_reload() {
	#
	# If the daemon can reload its configuration without
	# restarting (for example, when it is sent a SIGHUP),
	# then implement that here.
	#
	#start-stop-daemon --stop --signal 1 --quiet --pidfile $PIDFILE --name $NAME
	start-stop-daemon --stop --signal 1 --name $NAME
	return 0
}

case "$1" in
  start)
	[ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME"
	do_start
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  stop)
	[ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
	do_stop
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  #reload|force-reload)
	#
	# If do_reload() is not implemented then leave this commented out
	# and leave 'force-reload' as an alias for 'restart'.
	#
	#log_daemon_msg "Reloading $DESC" "$NAME"
	#do_reload
	#log_end_msg $?
	#;;
  restart|force-reload)
	#
	# If the "reload" option is implemented then remove the
	# 'force-reload' alias
	#
	log_daemon_msg "Restarting $DESC" "$NAME"
	do_stop
	case "$?" in
	  0|1)
		do_start
		case "$?" in
			0) log_end_msg 0 ;;
			1) log_end_msg 1 ;; # Old process is still running
			*) log_end_msg 1 ;; # Failed to start
		esac
		;;
	  *)
	  	# Failed to stop
		log_end_msg 1
		;;
	esac
	;;
  *)
	#echo "Usage: $SCRIPTNAME {start|stop|restart|reload|force-reload}" >&2
	echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
	exit 3
	;;
esac

:


```

2. Save next code (the actual daemon) to ~/tempguardd:
```

#!/bin/sh

### Temperature guard
### Auto Shutdown if Temperature is over threshold

THRESHOLD=57			# Max temperature
SENSORS=/usr/bin/sensors
PATH=/bin:/usr/bin:/sbin:/usr/sbin

test -x $SENSORS || exit 0

echo "Temperature Guard started. Threshold temperature is $THRESHOLD °C"
logger "Temperature Guard started. Threshold temperature is $THRESHOLD °C "

while [ 1 ]
do

  ## Get Temperature using lm-sensors
  t1=`$SENSORS | nawk '/temp1/ {print substr($2,2,2)}'`
  t2=`$SENSORS | nawk '/temp2/ {print substr($2,2,2)}'`
  t3=`$SENSORS | nawk '/temp3/ {print substr($2,2,2)}'`

  # log every 15 minutes
  logger "Temperature Guard RUNNING. CASE: $t1°C CPU: $t2°C BOARD: $t3°C"

  for i in `seq 1 180`;
  do

      ## Get Temperature using lm-sensors
      t1=`$SENSORS | nawk '/temp1/ {print substr($2,2,2)}'`
      t2=`$SENSORS | nawk '/temp2/ {print substr($2,2,2)}'`
      t3=`$SENSORS | nawk '/temp3/ {print substr($2,2,2)}'`

      if [ $t1 -gt $THRESHOLD -o $t2 -gt $THRESHOLD -o $t3 -gt $THRESHOLD ]
      then
	echo -n "\rTemperature PANIC! CASE: $t1°C CPU: $t2°C BOARD: $t3°C Shutting down immediately!"
	logger "Temperature Guard: PANIC!. CASE: $t1°C CPU: $t2°C BOARD: $t3°C Shutting down immediately!"
	shutdown -h now    # requires %user ALL=NOPASSWD: /sbin/shutdown in visudo
      else
	echo -n "\rTemperature Guard: OK.  CASE: $t1°C CPU: $t2°C BOARD: $t3°C"
      fi
      sleep 5
  done
done

```

Note the threshold=57 value. Any value higher will shut the system down.

3. prepare the scripts 
```

cd ~
sudo cp tempguard /etc/init.d/tempguard
sudo cp tempguardd /usr/bin/tempguardd
sudo chmod +x /etc/init.d/tempguard
sudo chmod +x /usr/bin/tempguardd

```


4. make the script run at boottime (last script started, or 99. runs as root)
```

sudo update-rc.d tempguard start 99 S .

```

5. done. script should be running, to check type:
```
 ps -A |grep tempguard 
```
manual usage:
```
sudo /etc/init.d/tempguard
```




HOW TO REMOVE THE SCRIPT:
```
sudo update-rc.d -f tempguard remove
```


* edit: fixed typo "END INIT INF" --> "END INIT INFO" in tempguard init script

---

