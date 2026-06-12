---
title: "[SOLVED] wicd problem"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by celticbhoy on 2008-10-07
I use wicd for my network manager, but after the last time it updated it doesn't work right. When I log in it no longer conects automatically, and wont run from the menu. If I open a terminal and run it with sudo it comes up :-
/var/run/wicd/wicd.pid
and then my pc connects t the internet fine, and I can run the application from the menu again.

How do I fix this ????

---

### Post by knattlhuber on 2008-10-07
The new version of the Wicd pacakage is somehow messed up.
Download an older version (e.g. 1.4.x) of the Wicd deb package from here:
[http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460](http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460)

Then do

```
sudo rm -r /var/lib/dpkg/info/wicd.prerm
sudo apt-get remove wicd
sudo dpkg -i nameofwicd.deb
```

---

### Post by imdano on 2008-10-07
Actually the new wicd package is fine.  It's the old one that is messed up and makes the upgrade fail in some cases.  Can you post the contents of /var/log/wicd/wicd.log and /etc/init.d/wicd?  The most likely cause of the issue is that your /etc/init.d/wicd script didn't get updated properly.  It should look like this ```
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

```

---

### Post by knattlhuber on 2008-10-07
Thanks, imdano. I stand corrected. It's not the Wicd package that's broken. The problem happens when you choose to not update the configuration files when updating to the package.
My above suggestion might be a bit radical but works OK. If he then reinstalls the latest version of Wicd and accepts to replace the configuration files, it should work fine.

---

### Post by celticbhoy on 2008-10-07
wicd log is empty, but I copied your version of the script, and will see if it works

---

### Post by celticbhoy on 2008-10-07
just read knattl's last post, and he is right I didnt update the config now I think of it. At the time I just presumed that the config meant my network setup info (not very clear on an update).

---

### Post by knattlhuber on 2008-10-07
Yeah, that was not quite clear whether one should use the new config files. I also chose to keep the files and then it stopped working. The OPs solution will work as well.
If you choose to remove Wicd as outlined above, just reinstall the latest version from the repos and this time not keep the config files. The update worked fine then for me.

---

### Post by celticbhoy on 2008-10-07
OK just tried a re-boot and still the same will try the first sugestion now

---

### Post by celticbhoy on 2008-10-07
Cheers guys thats it sorted.

---

### Post by CRIMPS on 2008-10-10
Imdano's recommendation to update /etc/init.d/wicd worked for me.  To be on the safe side, I went ahead and saved the original /etc/init.d/wicd as wicd_old.  Then, I created the new Wicd file.

Thanks for the help.  Im surprised that there hasn't been an update available to automatically fix this.  Anyway, thanks again.

Z

---

