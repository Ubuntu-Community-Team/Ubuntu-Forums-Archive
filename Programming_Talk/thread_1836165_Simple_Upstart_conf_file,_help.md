---
title: "Simple Upstart conf file, help?"
date: 2011-08-30
forum: Programming Talk
---

### Post by mikeym on 2011-08-30
Hi,

I've come across a problem with **knockd** failing to start on Ubuntu because the service was starting before the network was setup. Taking my cue from a similar problem I'd encountered with *mediatomb* that someone else had resolved by creating an Upstart conf file for it rather than a **/etc/init.d** file, I've had a go at converting the **/etc/init.d/knockd** file to an upstart conf file. 

It seems to work on my system and has resolved the problem but I'm not sure about how well it has been written and I don't think the test for a startup flag in the defaults file is handled properly. 

It should be pretty basic as knockd is a very basic program. Anyway any help would be most appreciated:

```

description "knockd - a port-knocking server"
author      "Judd Vinet <jvinet@zeroflux.org>"

start on (local-filesystems and net-device-up IFACE!=lo)
stop on runlevel [!2345]
respawn

env LOGFILE=/var/log/knockd.log
env DEFAULT=/etc/default/knockd
env DAEMON=/usr/sbin/knockd
#env OPTIONS=" -d"
env OPTIONS=""

umask 0037

script
	[ -r $DEFAULT ] && . $DEFAULT
	[ $START_KNOCKD -ne 1 ] && exit
	[ "$KNOCKD_OPTS" ] && OPTIONS="$OPTIONS $KNOCKD_OPTS"
	exec $DAEMON $OPTIONS
end script

```

And here's the original /etc/init.d/knockd startup script:

```

#! /bin/sh

### BEGIN INIT INFO
# Provides:          knockd
# Required-Start:    $network $syslog
# Required-Stop:     $network $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: port-knock daemon
### END INIT INFO

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/knockd
NAME=knockd
PIDFILE=/var/run/$NAME.pid
DEFAULTS_FILE=/etc/default/knockd
DESC="Port-knock daemon"
OPTIONS=" -d"

umask 0037

test -f $DAEMON || exit 0

set -e

[ -f $DEFAULTS_FILE ] && . $DEFAULTS_FILE

. /lib/lsb/init-functions

[ "$KNOCKD_OPTS" ] && OPTIONS="$OPTIONS $KNOCKD_OPTS"

start_if_configured() {
	if [ $START_KNOCKD -ne 1 ]; then
                log_warning_msg "$NAME disabled: not starting. To enable it edit $DEFAULTS_FILE"
                exit 0
	else
		log_daemon_msg "Starting $DESC" "$NAME"
		if ! START_ERROR=`start-stop-daemon --start --oknodo --quiet --exec $DAEMON -- $OPTIONS 2>&1`; then
			# don't fail the upgrade if it fails to start
			echo -n " "
			log_action_end_msg 1 "$START_ERROR"
			exit 0
		else
			log_end_msg 0
		fi
        fi
}

case "$1" in
  start)
	start_if_configured
	;;
  stop)
	log_daemon_msg "Stopping $DESC" "$NAME"
	start-stop-daemon --stop --oknodo --quiet --exec $DAEMON
	log_end_msg 0
	;;
  restart|reload|force-reload)
	log_daemon_msg "Stopping $DESC" "$NAME"
	start-stop-daemon --stop --oknodo --quiet --exec $DAEMON
	log_end_msg 0
	sleep 1
	start_if_configured
	;;
  *)
        log_warning_msg "Usage: $0 {start|stop|restart|reload|force-reload}" >&2
	exit 1
	;;
esac

exit 0

```

---

### Post by mikeym on 2011-08-31
Never mind. I've submitted the working but probably wrong Upstart script along with my bug report for knockd:

[https://bugs.launchpad.net/ubuntu/+source/knockd/+bug/837954](https://bugs.launchpad.net/ubuntu/+source/knockd/+bug/837954)

---

