---
title: "[SOLVED] Wicd doesn't load at startup"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by behindtheeye on 2008-10-18
To cut a long story short, since Wicd updated itself it doesn't automatically load when I startup. I have to open a terminal and "sudo wicd" manually.

Can anyone tell me how to get it to load on startup (and the tray icon too preferably)? I've tried tinkering around with startup programs in "sessions" without success. Currently I've got these 2 in startup programs:

/var/run/wicd
wicd-client

Thanks in advance!

---

### Post by hyper_ch on 2008-10-18
run
```

sudo update-rc.d wicd remove && sudo update-rc.d wicd defaults

```

---

### Post by behindtheeye on 2008-10-18
Thanks, but it doesn't appear to have worked. When I run that I get the following:

```
update-rc.d: /etc/init.d/wicd exists during rc.d purge (use -f to force)

```

---

### Post by hyper_ch on 2008-10-18
run those two command seperately.

---

### Post by behindtheeye on 2008-10-18
When I run the first command I get the error message above. When I run the second I get:

```
System startup links for /etc/init.d/wicd already exist.

```

Any idea?

---

### Post by hyper_ch on 2008-10-18
sudo apt-get remove --purge wicd && sudo apt-get install wicd

---

### Post by behindtheeye on 2008-10-18
Sorry to be a pain, I'm a beginner, but in my understanding the above 2 commands will remove and then re-install wicd.

Won't I lose my internet connection after removing Wicd and so be unable to install it?

---

### Post by hyper_ch on 2008-10-18
you should have the wicd.deb in /var/cache/apt/archive - so reinstall works :)

---

### Post by behindtheeye on 2008-10-18
It's not my lucky day is it? :confused: OK, after running the first I get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  wicd*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1774kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 210029 files and directories currently installed.)
Removing wicd ...
Stopping wicd daemon...
invoke-rc.d: initscript wicd, action "stop" failed.
dpkg: error processing wicd (--purge):
 subprocess pre-removal script returned error exit status 1
Stopping any running daemons...
Starting wicd daemon...
Errors were encountered while processing:
 wicd
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Then after the second I get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wicd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I restarted the PC and still the same.

---

### Post by hyper_ch on 2008-10-18
sudo apt-get purge wicd

---

### Post by bodhi.zazen on 2008-10-18
go to system -> preferances -. sessions

Hit the "Add" button.

Name = Wicd

Command = /opt/wicd/tray.py

Comment = what ever you want (wireless ?)

Save the changes, log off and back on 

:)

---

### Post by behindtheeye on 2008-10-18
```
sudo apt-get purge wicd
```
gives the following
```
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages will be REMOVED
  wicd*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1774kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 210029 files and directories currently installed.)
Removing wicd ...
Stopping wicd daemon...
invoke-rc.d: initscript wicd, action "stop" failed.
dpkg: error processing wicd (--purge):
 subprocess pre-removal script returned error exit status 1
Stopping any running daemons...
Starting wicd daemon...
Errors were encountered while processing:
 wicd
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Am I doing something wrong here? I appreciate your help!

---

### Post by behindtheeye on 2008-10-18
> **bodhi.zazen said:**
> go to system -> preferances -. sessions

Hit the "Add" button.

Name = Wicd

Command = /opt/wicd/tray.py

Comment = what ever you want (wireless ?)

Save the changes, log off and back on 

:)

Just tried this, still no joy I'm afraid :confused:

---

### Post by bodhi.zazen on 2008-10-18
With all that purging, is it installed ?

---

### Post by hyper_ch on 2008-10-18
there is something seriously wrong with your installation of wicd

---

### Post by behindtheeye on 2008-10-18
Well it seems to be installed as I am writing this from the PC in question now! I just have to start it manually each time I login.

It all started when I upgraded it, about a month ago. I've seen posts on a couple of forums having problems with this upgrade. Stuck!

---

### Post by bodhi.zazen on 2008-10-18
How are you starting it manually ?

Any error messages in your terminal ?

I am running wicd and have not had a problem.

[http://wicd.sourceforge.net/punbb/](http://wicd.sourceforge.net/punbb/)

There is a (long) discussion and several suggestions on this thread :

[http://wicd.net/punbb/viewtopic.php?id=187](http://wicd.net/punbb/viewtopic.php?id=187)

---

### Post by behindtheeye on 2008-10-18
> **bodhi.zazen said:**
> How are you starting it manually ?

Any error messages in your terminal ?

I am running wicd and have not had a problem.

[http://wicd.sourceforge.net/punbb/](http://wicd.sourceforge.net/punbb/)

There is a (long) discussion and several suggestions on this thread :

[http://wicd.net/punbb/viewtopic.php?id=187](http://wicd.net/punbb/viewtopic.php?id=187)

```
sudo wicd
```

That's all. It connects straight away. There's no tray icon though. I'll take a look at that link, thanks.

---

### Post by imdano on 2008-10-18
Use ```
wicd-client
``` to launch the tray icon.  Edit /etc/init.d/wicd so it looks like this ```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          wicd
# Required-Start:    dbus
# Required-Stop:     
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Starts and stops Wicd
# Description:       Starts and stops Wicd, a network manager
### END INIT INFO

# Author: Adam Blackburn <compwiz18@users.sourceforge.net>
#

# Do NOT "set -e"

# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/usr/sbin:/usr/bin:/sbin:/bin
DESC="Network connection manager"
NAME=wicd
DAEMON=/usr/sbin/$NAME
DAEMON_ARGS=""
PIDFILE=/var/run/wicd/wicd.pid
SCRIPTNAME=/etc/init.d/wicd

# Exit if the package is not installed
[ -x "$DAEMON" ] || exit 0

# Read configuration variable file if it is present
[ -r /etc/default/$NAME ] && . /etc/default/$NAME

# Load the VERBOSE setting and other rcS variables
[ -f /etc/default/rcS ] && . /etc/default/rcS

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

# Perhaps not the best idea
# but a confirmation is nice
# when starting/stopping the daemon
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
	#   vvvv -- don't do this -- vvvv
	#   [ -e $PIDFILE ] && return 1
	start-stop-daemon --start --quiet --pidfile $PIDFILE --startas $DAEMON --test > /dev/null \
		|| return 1
	start-stop-daemon --start --quiet --pidfile $PIDFILE --startas $DAEMON -- \
		$DAEMON_ARGS > /dev/null 2> /dev/null\
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
	start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --pidfile $PIDFILE --name $NAME
	RETVAL="$?"
	[ "$RETVAL" = 2 ] && return 2
	# Wait for children to finish too if this is a daemon that forks
	# and if the daemon is only ever run from this initscript.
	# If the above conditions are not satisfied then add some other code
	# that waits for the process to drop all resources that could be
	# needed by services started subsequently.  A last resort is to
	# sleep for some time.
	start-stop-daemon --stop --quiet --oknodo --retry=0/30/KILL/5 --exec $DAEMON
	[ "$?" = 2 ] && return 2
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
	start-stop-daemon --stop --signal 1 --quiet --pidfile $PIDFILE --name $NAME
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

```I think you should be all set then.

---

### Post by behindtheeye on 2008-10-19
That appears to have fixed it! Thanks a lot!

---

