---
title: "Issue with text/parameters being excluded in writing file from script."
date: 2014-08-08
forum: Programming Talk
---

### Post by derek23 on 2014-08-08
Hi All,

I'm trying to create a somewhat simple bash script to install a headless vncserver on a machine.  I have ALMOST everything perfect except for one part that keeps giving me problems.  I can't seem to find a way to write to a file that has all of the parameters i'm including in the script.  Here is the part of the script i'm having issues with, can someone give me any suggestions on how to make this work properly?  I'm attempting to use process sub with cat but it seems that all the parameters within the file i want to write are breaking it and not allowing them to write.  Here is what i want to write and how it appears in my script.

```
#Create the process for VNC to start on startup, without password or monitor needed
cat << EOF > /etc/init.d/vncserver
#!/bin/bash
### BEGIN INIT INFO
# Provides:          tightvncserver
# Required-Start:    $syslog
# Required-Stop:     $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: vnc server
# Description: http://www.namhuy.net
#
### END INIT INFO
 
unset VNCSERVERARGS
VNCSERVERS=""
[ -f /etc/vncserver/vncservers.conf ] && . /etc/vncserver/vncservers.conf
prog=$"VNC server"
start() {
 . /lib/lsb/init-functions
 REQ_USER=$2
 echo -n $"Starting $prog: "
 ulimit -S -c 0 >/dev/null 2>&1
 RETVAL=0
 for display in ${VNCSERVERS}
 do
 export USER="${display##*:}"
 if test -z "${REQ_USER}" -o "${REQ_USER}" == ${USER} ; then
 echo -n "${display} "
 unset BASH_ENV ENV
 DISP="${display%%:*}"
 export VNCUSERARGS="${VNCSERVERARGS[${DISP}]}"
 su ${USER} -c "cd ~${USER} && [ -f .vnc/passwd ] && vncserver :${DISP} ${VNCUSERARGS}"
 fi
 done
}
stop() {
 . /lib/lsb/init-functions
 REQ_USER=$2
 echo -n $"Shutting down VNCServer: "
 for display in ${VNCSERVERS}
 do
 export USER="${display##*:}"
 if test -z "${REQ_USER}" -o "${REQ_USER}" == ${USER} ; then
 echo -n "${display} "
 unset BASH_ENV ENV
 export USER="${display##*:}"
 su ${USER} -c "vncserver -kill :${display%%:*}" >/dev/null 2>&1
 fi
 done
 echo -e "\n"
 echo "VNCServer Stopped"
}
case "$1" in
start)
start $@
;;
stop)
stop $@
;;
restart|reload)
stop $@
sleep 3
start $@
;;
condrestart)
if [ -f /var/lock/subsys/vncserver ]; then
stop $@
sleep 3
start $@
fi
;;
status)
status Xvnc
;;
*)
echo $"Usage: $0 {start|stop|restart|condrestart|status}"
exit 1
esac
EOF
```

Here is what i'm left with in the file after the script runs.  As you can see it doesn't contain a LOT of the arguments, i'd say pretty much all of them...

```
#!/bin/bash
### BEGIN INIT INFO
# Provides:          tightvncserver
# Required-Start:    $syslog
# Required-Stop:     $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: vnc server
# Description: http://www.namhuy.net
#
### END INIT INFO
 
unset VNCSERVERARGS
VNCSERVERS=""
[ -f /etc/vncserver/vncservers.conf ] && . /etc/vncserver/vncservers.conf
prog=$"VNC server"
start() {
 . /lib/lsb/init-functions
 REQ_USER=
 echo -n $"Starting : "
 ulimit -S -c 0 >/dev/null 2>&1
 RETVAL=0
 for display in 
 do
 export USER=""
 if test -z "" -o "" == root ; then
 echo -n " "
 unset BASH_ENV ENV
 DISP=""
 export VNCUSERARGS=""
 su root -c "cd ~root && [ -f .vnc/passwd ] && vncserver : "
 fi
 done
}
stop() {
 . /lib/lsb/init-functions
 REQ_USER=
 echo -n $"Shutting down VNCServer: "
 for display in 
 do
 export USER=""
 if test -z "" -o "" == root ; then
 echo -n " "
 unset BASH_ENV ENV
 export USER=""
 su root -c "vncserver -kill :" >/dev/null 2>&1
 fi
 done
 echo -e "\n"
 echo "VNCServer Stopped"
}
case "" in
start)
start 
;;
stop)
stop 
;;
restart|reload)
stop 
sleep 3
start 
;;
condrestart)
if [ -f /var/lock/subsys/vncserver ]; then
stop 
sleep 3
start 
fi
;;
status)
status Xvnc
;;
*)
echo $"Usage: /etc/init.d/vncserver {start|stop|restart|condrestart|status}"
exit 1
esac
```

Any help would be appreciated.  THANK YOU!

---

### Post by ofnuts on 2014-08-08
[http://www.unix.com/shell-programming-and-scripting/178298-bash-how-can-script-create-script.html](http://www.unix.com/shell-programming-and-scripting/178298-bash-how-can-script-create-script.html)

---

### Post by derek23 on 2014-08-08
Wow, that was extremely simple.  Thank you for pointing me in the right direction!

---

