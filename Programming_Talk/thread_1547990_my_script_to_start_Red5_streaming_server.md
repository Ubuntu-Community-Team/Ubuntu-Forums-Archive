---
title: "my script to start Red5 streaming server"
date: 2010-08-07
forum: Programming Talk
---

### Post by tapas_mishra on 2010-08-07
```
#The script to start Red 5 Tapas Mishra
##Begin some thing some thing
### BEGIN INIT INFO
# Provides:          Red5
# Required-Start:    No idea
# Required-Stop:     No idea
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Red5 Streaming Server
# Description:       Ubuntu init script for Red5 server
### END INIT INFO

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON="/opt/red5/dist/red5.sh"
NAME="Red5"
RED5_HOME=/opt/red5/dist
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME
DESC="Tapas Red5 Server"

. /lib/lsb/init-functions
set -e

PROCESS_DIR="/opt/red5/dist"

case "$1" in
  start)
        log_daemon_msg "Starting $DESC" "$NAME"
        start-stop-daemon --start --pidfile $PIDFILE \
                --chdir $RED5_HOME --background --make-pidfile \
                --exec $DAEMON
        log_end_msg $?
        ;;
   stop)
        log_daemon_msg "Stopping $DESC" "$NAME"
        start-stop-daemon --stop --quiet --pidfile $PIDFILE \

               --name java
        rm -f $PIDFILE
        log_end_msg $?
        ;;
  restart|force-reload)
        echo -n "Restarting $DESC: $NAME"
        start-stop-daemon --stop --quiet --pidfile $PIDFILE \
                --name java
        rm -f $PIDFILE
        sleep 1
        echo -e
        $0 start
        ;;
  *)
        echo "Usage: $0 {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

exit 0

```
The problem in above script is if I stop it then stop it again without starting it does not give me any error message.
What should I do in this ?

---

