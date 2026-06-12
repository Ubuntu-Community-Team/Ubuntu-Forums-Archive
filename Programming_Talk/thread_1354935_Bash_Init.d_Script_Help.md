---
title: "Bash Init.d Script Help"
date: 2009-12-14
forum: Programming Talk
---

### Post by gamerteck on 2009-12-14
I'm trying to create an init.d script to for the VNC service. It works for the most part but I'm getting an error.
```
vncserver: The HOME environment variable is not set
```

I'm a complete beginner so pardon the messy code.
```
X11_VNC=`ps -A | egrep Xtightvnc | awk '{print $2}'`
NETSTAT=`netstat -tap | egrep 6345`
STARTVNC=`vncserver -rfbport 6344 -depth 8 -geometry 1100x800 :1`
case "$1" in
  start)
        sudo -u user -H -s "$STARTVNC"
        
        ;;

  status)
        if [ -n "$X11_VNC" ] ; then
                echo "VNC Service is running:"
                echo $NETSTAT

        else
                echo "VNC Service is not running."
        fi
        ;;

   stop)
        if [ -n "$X11_VNC" ] ; then
                echo "Stopping Vnc on Server :1"
                sudo -u rmote -H -s "kill $X11_VNC"
        else
                echo "Vnc on Server :1 is not running"
        fi
        ;;
esac
exit 0

```


I know I'm doing something completly off in the start) and it could probably work if called an .sh script but I'd like to keep it in this init script without creating .sh, if it's possible?
Thanks for the help.

---

### Post by Barriehie on 2009-12-14
Google and forum search yielded a few hits that might help!  See this [forum post](http://ubuntuforums.org/showthread.php?t=1249881&highlight=vncserver) and this [google hit](http://www.abdevelopment.ca/blog/start-vnc-server-ubuntu-boot).

HTH,
Barrie

---

### Post by gamerteck on 2009-12-15
That second link helped - Thank you.
I ended up just running the command inside start) instead, which fixed my problem.
Here is my new script.

```
#!/bin/bash

X11_VNC=`ps -A | egrep Xtightvnc | awk '{print $1}'`
STAT=`ps -A | egrep Xtightvnc | awk '{print $1 ; print $2 ; print $13}'`
NETSTAT=`netstat -tap | egrep 6345`
YESVNC="VNC is running: $STAT"
NOVNC=" VNC is not running "
LINES=`printf -v f "%22s" ; printf "%s\n" "${f// /-}"`

case "$1" in
  start)
        if [ -n "$X11_VNC" ] ; then
                echo -e "$LINES\n$RUNNING"
                echo -e "$NETSTAT\n$LINES"
        else
        echo -e "$LINES\nLoading Display :1\n$LINES"
        sudo -u user -H -s "vncserver -rfbport 6345 -depth 8 -geometry 1100x800 :1"
        fi
        ;;

  status)
        if [ -n "$X11_VNC" ] ; then
                echo -e "$LINES\n$RUNNING"
                echo -e "$NETSTAT\n$LINES"
        else
                echo -e "$LINES\n$NOVNC\n$LINES"
        fi
        ;;

   stop)
        if [ -n "$X11_VNC" ] ; then
                echo -e "$LINES\nVNC Stopping\n$LINES"
                sudo -u rmote -H -s "vncserver -kill :1"
        else
                echo -e "$LINES\n$NOVNC\n$LINES"
        fi
        ;;

   restart)
                echo -e "$LINES\nVNC Server restarting\n$LINES"
        $0 stop
        $0 start
        ;;
        *)
                echo -e "$LINES\nPost Fix Needed: {start | stop | status | restart}\n$LINES"
                exit 1
esac
exit 0

```

---

