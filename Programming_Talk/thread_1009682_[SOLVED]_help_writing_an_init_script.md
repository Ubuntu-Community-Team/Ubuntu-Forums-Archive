---
title: "[SOLVED] help writing an init script"
date: 2008-12-12
forum: Programming Talk
---

### Post by iggykoopa on 2008-12-12
I'm working on a power management gui here [http://ubuntuforums.org/showthread.php?t=988309](http://ubuntuforums.org/showthread.php?t=988309) . I just split the program up into the gui and a daemon, now I need to write an init script for the daemon but have no idea what I'm doing. I tried modifying the skeleton init script but it didn't end up working right, any help would be appreciated as shell scripting is not my strong point.

---

### Post by mssever on 2008-12-12
> **iggykoopa said:**
> I'm working on a power management gui here [http://ubuntuforums.org/showthread.php?t=988309](http://ubuntuforums.org/showthread.php?t=988309) . I just split the program up into the gui and a daemon, now I need to write an init script for the daemon but have no idea what I'm doing. I tried modifying the skeleton init script but it didn't end up working right, any help would be appreciated as shell scripting is not my strong point.
Please post your code. Otherwise, it isn't possible to help you. EDIT: Also, please define "didn't end up working right."

When I need an init script, I usually just copy an existing script and modify it to suit my needs.

---

### Post by iggykoopa on 2008-12-12
Sorry here is what I tried:
```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          skeleton
# Required-Start:    $remote_fs
# Required-Stop:     $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Example initscript
# Description:       This file should be used to construct scripts to be
#                    placed in /etc/init.d.
### END INIT INFO

# Author: Foo Bar <foobar@baz.org>
#
# Please remove the "Author" lines above and replace them
# with your own name if you copy and modify this script.

# Do NOT "set -e"

# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/sbin:/usr/sbin:/bin:/usr/bin
DESC="WattOS power manager daemon"
NAME=wattospm-daemon.py
DAEMON=/usr/sbin/$NAME
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

#
# Function that starts the daemon/service
#
do_start()
{
	# Return
	#   0 if daemon has been started
	#   1 if daemon was already running
	#   2 if daemon could not be started
	start-stop-daemon --start --quiet --pidfile $PIDFILE --exec $DAEMON --test > /dev/null \
		|| return 1
	start-stop-daemon --start --quiet --pidfile $PIDFILE --exec $DAEMON -- \
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
If you want the python code the svn instructions are in the thread I linked. I'm not getting any errors, but when I try:
```

sudo /etc/init.d/wattospm-daemon start

```
It just doesn't do anything, no terminal output. I appreciate the help.

edit: also to double check incase it was starting the daemon silently I checked with ps aux and the daemon isn't running.

---

### Post by mssever on 2008-12-12
> **iggykoopa said:**
> It just doesn't do anything, no terminal output. I appreciate the help.

edit: also to double check incase it was starting the daemon silently I checked with ps aux and the daemon isn't running.
try putting set -x at the beginning of the script. That will make the script print each line before executing it, which will allow you to trace what's happening. Also, check the script's exit status, as that could be useful info: ```
/etc/init.d/your-script start; echo "Exit status: $?"
```EDIT: Also, why are you calling start-stop-daemon twice in do_start and another two times in do_stop? That might cause problems.

---

### Post by slavik on 2008-12-12
does your daemon process actually daemonize itself?

---

### Post by iggykoopa on 2008-12-12
ok here is the output with set -x:
```

eric@lappy:~/Desktop$ sudo /etc/init.d/wattospm-daemon.py start
+ PATH=/sbin:/usr/sbin:/bin:/usr/bin
+ DESC=WattOS power manager daemon
+ NAME=wattospm-daemon.py
+ DAEMON=/usr/bin/wattospm-daemon.py
+ PIDFILE=/var/run/wattospm-daemon.py.pid
+ SCRIPTNAME=/etc/init.d/wattospm-daemon.py
+ [ -x /usr/bin/wattospm-daemon.py ]
+ exit 0

```
so it's returning 0 which means it thinks the daemon started correctly, but it isn't. And the reason start-stop-daemon is in there twice is I just modified the skeleton init script and thats how it was written.

---

### Post by mssever on 2008-12-12
> **slavik said:**
> does your daemon process actually daemonize itself?
If it didn't daemonize itself, the init script wouldn't exit until the daemon did.

---

### Post by iggykoopa on 2008-12-12
yes the daemon daemonizes, I used an example that I found and that portion works correctly if I manually launch the daemon.

---

### Post by mssever on 2008-12-12
> **iggykoopa said:**
> ok here is the output with set -x:
```

eric@lappy:~/Desktop$ sudo /etc/init.d/wattospm-daemon.py start
+ PATH=/sbin:/usr/sbin:/bin:/usr/bin
+ DESC=WattOS power manager daemon
+ NAME=wattospm-daemon.py
+ DAEMON=/usr/bin/wattospm-daemon.py
+ PIDFILE=/var/run/wattospm-daemon.py.pid
+ SCRIPTNAME=/etc/init.d/wattospm-daemon.py
+ [ -x /usr/bin/wattospm-daemon.py ]
+ exit 0

```so it's returning 0 which means it thinks the daemon started correctly, but it isn't.Not so fast. It's exiting 0 because it was told to. But that doesn't necessarily mean that the daemon started correctly. Did you follow the execution path? It tested whether the file referenced by $DAEMON exists and is executable. Apparently the test failed, because it got to the exit 0 statement. So the script never even got close to trying to start the daemon.

> And the reason start-stop-daemon is in there twice is I just modified the skeleton init script and thats how it was written.But perhaps the skeleton is just illustrating several options. At any rate, you don't want to start the deamon twice. Once is enough. So modify it as appropriate. (Read the man page for start-stop-daemon for documentation.)

---

### Post by iggykoopa on 2008-12-12
ok I looked into it some more and tried manually using start-stop-daemon, this is what I get:
```

sudo start-stop-daemon --start --pidfile /var/run/wattospm-daemon.py.pid --exec /usr/bin/wattospm-daemon.py
start-stop-daemon: Unable to start /usr/bin/wattospm-daemon.py: Permission denied (Permission denied)

```
I did notice one thing that may be causing it, my daemon doesn't create a pid file so I'll have to see how to make one and do that. I tried launching start-stop-daemon with -m though which is supposed to create the pid file for it and it still said permission denied.

---

### Post by mssever on 2008-12-12
> **iggykoopa said:**
> ok I looked into it some more and tried manually using start-stop-daemon, this is what I get:
```

sudo start-stop-daemon --start --pidfile /var/run/wattospm-daemon.py.pid --exec /usr/bin/wattospm-daemon.py
start-stop-daemon: Unable to start /usr/bin/wattospm-daemon.py: Permission denied (Permission denied)

```I did notice one thing that may be causing it, my daemon doesn't create a pid file so I'll have to see how to make one and do that. I tried launching start-stop-daemon with -m though which is supposed to create the pid file for it and it still said permission denied.
A permission denied error means (surprisingly enough) that there's a problem with your permissions. Check your permissions.

EDIT: Without a pidfile, how do you propose to kill your daemon?

---

### Post by iggykoopa on 2008-12-13
lol I figured that part out (with the permissions) but I ran it as sudo so thats why I was confused by it, if I run the daemon by itself as sudo it runs fine. I'm just learning how the whole daemon thing is working now, this is my first project I'm coding so I'm learning as I go.

edit: ok I feel stupid now, at one point I had copied a new version of the daemon and didn't set it as executable again. With the new start-stop-daemon command I used it is now working. Once I figure out how to create the pid file correctly I should be all set now. I appreciate the help and should be able to stumble through the rest

---

### Post by mssever on 2008-12-13
> **iggykoopa said:**
> lol I figured that part out (with the permissions) but I ran it as sudo so thats why I was confused by it, if I run the daemon by itself as sudo it runs fine. I'm just learning how the whole daemon thing is working now, this is my first project I'm coding so I'm learning as I go.

edit: ok I feel stupid now, at one point I had copied a new version of the daemon and didn't set it as executable again. With the new start-stop-daemon command I used it is now working. Once I figure out how to create the pid file correctly I should be all set now. I appreciate the help and should be able to stumble through the rest
I'm not 100% certain, but I believe that your daemon has to create the pidfile (by convention in /var/run), because the process of daemonizing changes the pid. Just create a file with a known name (/var/run/your-program.pid or something) and insert the pid into the file (nothing else). Then, determining the pid of your daemon is easy when you want to kill it. Of course, this approach doesn't work if you simultaneously run multiple instances of your daemon, so you'll have to decide an appropriate way to handle that case. Also, your daemon should delete its pidfile as part of its exit process.

---

### Post by slavik on 2008-12-13
> **mssever said:**
> If it didn't daemonize itself, the init script wouldn't exit until the daemon did.
that was the point. the idea was that maybe the daemon dies or something ... but seems like you figured out the real issue.

---

### Post by iggykoopa on 2008-12-13
ok got everything working now, thanks for your help.

---

