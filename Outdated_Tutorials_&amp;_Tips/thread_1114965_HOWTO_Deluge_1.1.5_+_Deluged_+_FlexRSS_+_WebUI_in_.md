---
title: "HOWTO: Deluge 1.1.5 + Deluged + FlexRSS + WebUI in Intrepid"
date: 2009-04-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Kilbasar on 2009-04-03
Intrepid's repos only have deluge 0.5. Although it works okay, it is very buggy, and is missing many of the nice features of the new 1.1.5 version. But getting all the features of 1.1.5 working was a hassle, so here's a guide. This will set up Deluge (and FlexRSS) so that the daemon part and the webUI part run on boot. The GTK interface can be run as needed.

1. If you currently have deluge installed, remove it. This will NOT delete your currently running torrents, although you WILL have to reconfigure your preferences. Also, the new FlexRSS will not work with an old FlexRSS config file, so we'll need to get rid of that.
```
sudo aptitude remove deluge
sudo mv ~/.config/deluge/flexrss.dat ~/.config/deluge/flexrss.dat.bak
```

2. Add the PPA repositories to your sources file. If you are using something other than intrepid, this will probably still work, but you will need to change "intrepid" to your distro.
```
sudo gedit /etc/apt/sources.list
Add the following two lines:
deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu intrepid main
```
Save the file, then run:
```
sudo aptitude update
```

3. Install the new deluge:
```
sudo aptitude install deluge
sudo aptitude install deluge-webui
```

4. Download the new FlexRSS plugin from [here]("https://forum.deluge-torrent.org/viewtopic.php?f=9&t=10185") (direct link [here]("https://forum.deluge-torrent.org/download/file.php?id=1165")), and place it in ~/.config/deluge/plugins/. Or, from the command line:
```
wget --no-check-certificate -O ~/.config/deluge/plugins/flexRSS-0.1.egg 'https://forum.deluge-torrent.org/download/file.php?id=1165'
```

5. Fire up Deluge. Set up your settings, and your FlexRSS. You must then configure Deluge to run the daemon and client separately. Edit -> Preferences -> Interface -> UNcheck "Classic Mode Enable". Then shut down deluge.

6. Create a startup script. Directions for how to do this are stolen from [here]("http://dev.deluge-torrent.org/wiki/InitScript"). To edit the files mentioned, you can use "sudo gedit", like so:
```
sudo gedit /etc/default/deluge-daemon
(edit file, save, close)
sudo gedit /etc/init.d/deluge-daemon
(edit file, save, close)
```

To /etc/default/deluge-daemon, add:
```
# Configuration for /etc/init.d/deluge-daemon

# The init.d script will only run if this variable non-empty.
DELUGED_USER="<username>"             # !!!CHANGE THIS!!!!

# Should we run at startup?
RUN_AT_STARTUP="YES"
```
Be sure to replace <username> with your actual user name.

To /etc/init.d/deluge-daemon, add:
```
#!/bin/sh
### BEGIN INIT INFO
# Provides:          deluge-daemon
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Should-Start:      $network
# Should-Stop:       $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Daemonized version of deluge and webui.
# Description:       Starts the deluge daemon with the user specified in
#                    /etc/default/deluge-daemon.
### END INIT INFO

# Author: Adolfo R. Brandes 

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="Deluge Daemon"
NAME1="deluged"
NAME2="deluge"
DAEMON1=/usr/bin/deluged
DAEMON1_ARGS="-d"
DAEMON2=/usr/bin/deluge
DAEMON2_ARGS="-u web"
PIDFILE1=/var/run/$NAME1.pid
PIDFILE2=/var/run/$NAME2.pid
PKGNAME=deluge-daemon
SCRIPTNAME=/etc/init.d/$PKGNAME

# Exit if the package is not installed
[ -x "$DAEMON1" -a -x "$DAEMON2" ] || exit 0

# Read configuration variable file if it is present
[ -r /etc/default/$PKGNAME ] && . /etc/default/$PKGNAME

# Load the VERBOSE setting and other rcS variables
[ -f /etc/default/rcS ] && . /etc/default/rcS

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

if [ -z "$RUN_AT_STARTUP" -o "$RUN_AT_STARTUP" != "YES" ]
then
   log_warning_msg "Not starting $PKGNAME, edit /etc/default/$PKGNAME to start it."
   exit 0
fi

if [ -z "$DELUGED_USER" ]
then
    log_warning_msg "Not starting $PKGNAME, DELUGED_USER not set in /etc/default/$PKGNAME."
    exit 0
fi

#
# Function that starts the daemon/service
#
do_start()
{
   # Return
   #   0 if daemon has been started
   #   1 if daemon was already running
   #   2 if daemon could not be started
   start-stop-daemon --start --background --quiet --pidfile $PIDFILE1 --exec $DAEMON1 \
      --chuid $DELUGED_USER --user $DELUGED_USER --test > /dev/null
   RETVAL1="$?"
   start-stop-daemon --start --background --quiet --pidfile $PIDFILE2 --exec $DAEMON2 \
      --chuid $DELUGED_USER --user $DELUGED_USER --test > /dev/null
   RETVAL2="$?"
   [ "$RETVAL1" = "0" -a "$RETVAL2" = "0" ] || return 1

   start-stop-daemon --start --background --quiet --pidfile $PIDFILE1 --make-pidfile --exec $DAEMON1 \
      --chuid $DELUGED_USER --user $DELUGED_USER -- $DAEMON1_ARGS
   RETVAL1="$?"
        sleep 2
   start-stop-daemon --start --background --quiet --pidfile $PIDFILE2 --make-pidfile --exec $DAEMON2 \
      --chuid $DELUGED_USER --user $DELUGED_USER -- $DAEMON2_ARGS
   RETVAL2="$?"
   [ "$RETVAL1" = "0" -a "$RETVAL2" = "0" ] || return 2
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

   start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --user $DELUGED_USER --pidfile $PIDFILE2
   RETVAL2="$?"
   start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --user $DELUGED_USER --pidfile $PIDFILE1
   RETVAL1="$?"
   [ "$RETVAL1" = "2" -o "$RETVAL2" = "2" ] && return 2

   rm -f $PIDFILE1 $PIDFILE2

   [ "$RETVAL1" = "0" -a "$RETVAL2" = "0" ] && return 0 || return 1
}

case "$1" in
  start)
   [ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME1"
   do_start
   case "$?" in
      0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
      2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
   esac
   ;;
  stop)
   [ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME1"
   do_stop
   case "$?" in
      0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
      2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
   esac
   ;;
  restart|force-reload)
   log_daemon_msg "Restarting $DESC" "$NAME1"
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
   echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
   exit 3
   ;;
esac

:
```

Finally, set it to be executable, set it to run on boot, and start it up:
```
sudo chmod 755 /etc/init.d/deluge-daemon
sudo update-rc.d deluge-daemon defaults
sudo /etc/init.d/deluge-daemon start
```

All done! The daemon and the web interface are now running, and the GTK client will connect to the daemon when you start it. Note that in the connection manager that comes up when you start the GTK client, you can configure it to auto-connect without prompting you, so it behaves as it did pre-daemon.

To use the WebUI, go to [http://localhost:8112]("http://localhost:8112") . The default password is "deluge". Once inside you can change the password, the default port number, and whatever else. Remember to restart if you change the port (sudo /etc/init.d/deluge-daemon restart).

Good luck, and enjoy!
-Kilbasar

---

### Post by lovinglinux on 2009-04-03
> **Kilbasar said:**
> Intrepid's repos only have deluge 0.5. Although it works okay, it is very buggy, and is missing many of the nice features of the new 1.1.5 version.

IMO, version 0.5 is much more stable. Versions 1.1.x introduces a nice set of new features, but not all of them work as expected. For example, the Blocklist plugin and UPnP.

I'm using 0.5.x for months and it works like a charm.

---

### Post by Kilbasar on 2009-04-03
If 0.5.x works for you, by all means stick with it. But I personally had nothing but headaches. For example, half the time the folder select dialog didn't work, and results in the torrent not being added. Deluge itself crashed fairly often, and when it did so the webUI would keep running. This meant the next time Deluge was run it would mysteriously fail because it couldn't bind to the port. The blocklist plugin also didn't work for me in 0.5.x, but if you're going to use blocklists, you might as well just run moblock.

On the other hand, 1.1.5 has been completely stable for me, so for anyone who's experienced issues with 0.5.x, I strongly suggest the upgrade. But if you're satisfied with 0.5.x, stick with that.

---

### Post by insanepenguin on 2009-04-04
great!!! this works beautifully. one question (and I know it does not belong here): why is this not just set up by default? The instructions are straight forward enough, but one should not have to do this by hand. I have been under the impression for months now that the web-ui was broken in 1.1.*!

---

### Post by lovinglinux on 2009-04-05
> **Kilbasar said:**
> If 0.5.x works for you, by all means stick with it. But I personally had nothing but headaches. For example, half the time the folder select dialog didn't work, and results in the torrent not being added. Deluge itself crashed fairly often, and when it did so the webUI would keep running. This meant the next time Deluge was run it would mysteriously fail because it couldn't bind to the port. The blocklist plugin also didn't work for me in 0.5.x, but if you're going to use blocklists, you might as well just run moblock.

On the other hand, 1.1.5 has been completely stable for me, so for anyone who's experienced issues with 0.5.x, I strongly suggest the upgrade. But if you're satisfied with 0.5.x, stick with that.

Believe me or not, 0.5 started to crash today :) I guess it was an issue with the blocklist file. Anyways, I decided to give 1.1.5 a try and it is working fine, including the blocklist plugin and UPnP. I still miss the option to add torrents from a watched folder in paused state.

BTW, I have moblock too, but I like to use a different list on deluge.

---

### Post by binbash on 2009-04-05
1.1.2 and 1.1.5 is totally stable for me, uptime = 34 days now.BTW great howto

---

### Post by fjf on 2009-04-07
Yes, thanks for this!. This is the amateurish flavor of linux software: it does not work well until some wizard tells you how to set it up properly.

---

### Post by solexious on 2009-04-18
> **fjf said:**
> Yes, thanks for this!. This is the amateurish flavor of linux software: it does not work well until some wizard tells you how to set it up properly.

Or is included on the site the software is from, like software for any OS...

[http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient]("http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient")

Sol

---

### Post by brodiepearce on 2009-05-14
The init script does not start the webui for me.  I cannot access the webui till I su to my deluge user and do *deluge -u web* myself.  Anyone else getting this?

*edit*
Problem was that I was running it as myself with sudo.  Running it su'd to root works.

I do have another issue getting WebUI to use https though.  Everything is set up, deluge.cert.pem and deluge.key.pem files sitting in ~/.config/deluge/ssl, https box ticked in WebUI, correct port etc. etc.  Yet every time I try to access WebUI through https I get the following error:

```

An error occurred during a connection to localhost:<port>.

SSL received a record that exceeded the maximum permissible length.

(Error code: ssl_error_rx_record_too_long)

```

Apparently sometimes firefox will freak if you try to access a non-standard port, so I've added my port and the default deluge port to the network.security.ports.banned.override string in about:config.  Also made sure the necessary ports are open in iptables.  

Apparently this error can occur if the server is talking plaintext on the secure port instead of SSL.  But that would indicate a problem with deluge (https is enabled).  Has anyone here got deluge working with https in Intrepid with say version 1.1.6 or 1.1.7?

---

### Post by piju on 2009-08-11
> **Kilbasar said:**
> Intrepid's repos only have deluge 0.5. Although it works okay, it is very buggy, and is missing many of the nice features of the new 1.1.5 version. But getting all the features of 1.1.5 working was a hassle, so here's a guide. This will set up Deluge (and FlexRSS) so that the daemon part and the webUI part run on boot. The GTK interface can be run as needed.

1. If you currently have deluge installed, remove it. This will NOT delete your currently running torrents, although you WILL have to reconfigure your preferences. Also, the new FlexRSS will not work with an old FlexRSS config file, so we'll need to get rid of that.
```
sudo aptitude remove deluge
sudo mv ~/.config/deluge/flexrss.dat ~/.config/deluge/flexrss.dat.bak
```

2. Add the PPA repositories to your sources file. If you are using something other than intrepid, this will probably still work, but you will need to change "intrepid" to your distro.
```
sudo gedit /etc/apt/sources.list
Add the following two lines:
deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu intrepid main
```
Save the file, then run:
```
sudo aptitude update
```

3. Install the new deluge:
```
sudo aptitude install deluge
sudo aptitude install deluge-webui
```

4. Download the new FlexRSS plugin from [here]("https://forum.deluge-torrent.org/viewtopic.php?f=9&t=10185") (direct link [here]("https://forum.deluge-torrent.org/download/file.php?id=1165")), and place it in ~/.config/deluge/plugins/. Or, from the command line:
```
wget --no-check-certificate -O ~/.config/deluge/plugins/flexRSS-0.1.egg 'https://forum.deluge-torrent.org/download/file.php?id=1165'
```

5. Fire up Deluge. Set up your settings, and your FlexRSS. You must then configure Deluge to run the daemon and client separately. Edit -> Preferences -> Interface -> UNcheck "Classic Mode Enable". Then shut down deluge.

6. Create a startup script. Directions for how to do this are stolen from [here]("http://dev.deluge-torrent.org/wiki/InitScript"). To edit the files mentioned, you can use "sudo gedit", like so:
```
sudo gedit /etc/default/deluge-daemon
(edit file, save, close)
sudo gedit /etc/init.d/deluge-daemon
(edit file, save, close)
```

To /etc/default/deluge-daemon, add:
```
# Configuration for /etc/init.d/deluge-daemon

# The init.d script will only run if this variable non-empty.
DELUGED_USER="<username>"             # !!!CHANGE THIS!!!!

# Should we run at startup?
RUN_AT_STARTUP="YES"
```
Be sure to replace <username> with your actual user name.

To /etc/init.d/deluge-daemon, add:
```
#!/bin/sh
### BEGIN INIT INFO
# Provides:          deluge-daemon
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Should-Start:      $network
# Should-Stop:       $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Daemonized version of deluge and webui.
# Description:       Starts the deluge daemon with the user specified in
#                    /etc/default/deluge-daemon.
### END INIT INFO

# Author: Adolfo R. Brandes 

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="Deluge Daemon"
NAME1="deluged"
NAME2="deluge"
DAEMON1=/usr/bin/deluged
DAEMON1_ARGS="-d"
DAEMON2=/usr/bin/deluge
DAEMON2_ARGS="-u web"
PIDFILE1=/var/run/$NAME1.pid
PIDFILE2=/var/run/$NAME2.pid
PKGNAME=deluge-daemon
SCRIPTNAME=/etc/init.d/$PKGNAME

# Exit if the package is not installed
[ -x "$DAEMON1" -a -x "$DAEMON2" ] || exit 0

# Read configuration variable file if it is present
[ -r /etc/default/$PKGNAME ] && . /etc/default/$PKGNAME

# Load the VERBOSE setting and other rcS variables
[ -f /etc/default/rcS ] && . /etc/default/rcS

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

if [ -z "$RUN_AT_STARTUP" -o "$RUN_AT_STARTUP" != "YES" ]
then
   log_warning_msg "Not starting $PKGNAME, edit /etc/default/$PKGNAME to start it."
   exit 0
fi

if [ -z "$DELUGED_USER" ]
then
    log_warning_msg "Not starting $PKGNAME, DELUGED_USER not set in /etc/default/$PKGNAME."
    exit 0
fi

#
# Function that starts the daemon/service
#
do_start()
{
   # Return
   #   0 if daemon has been started
   #   1 if daemon was already running
   #   2 if daemon could not be started
   start-stop-daemon --start --background --quiet --pidfile $PIDFILE1 --exec $DAEMON1 \
      --chuid $DELUGED_USER --user $DELUGED_USER --test > /dev/null
   RETVAL1="$?"
   start-stop-daemon --start --background --quiet --pidfile $PIDFILE2 --exec $DAEMON2 \
      --chuid $DELUGED_USER --user $DELUGED_USER --test > /dev/null
   RETVAL2="$?"
   [ "$RETVAL1" = "0" -a "$RETVAL2" = "0" ] || return 1

   start-stop-daemon --start --background --quiet --pidfile $PIDFILE1 --make-pidfile --exec $DAEMON1 \
      --chuid $DELUGED_USER --user $DELUGED_USER -- $DAEMON1_ARGS
   RETVAL1="$?"
        sleep 2
   start-stop-daemon --start --background --quiet --pidfile $PIDFILE2 --make-pidfile --exec $DAEMON2 \
      --chuid $DELUGED_USER --user $DELUGED_USER -- $DAEMON2_ARGS
   RETVAL2="$?"
   [ "$RETVAL1" = "0" -a "$RETVAL2" = "0" ] || return 2
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

   start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --user $DELUGED_USER --pidfile $PIDFILE2
   RETVAL2="$?"
   start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --user $DELUGED_USER --pidfile $PIDFILE1
   RETVAL1="$?"
   [ "$RETVAL1" = "2" -o "$RETVAL2" = "2" ] && return 2

   rm -f $PIDFILE1 $PIDFILE2

   [ "$RETVAL1" = "0" -a "$RETVAL2" = "0" ] && return 0 || return 1
}

case "$1" in
  start)
   [ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME1"
   do_start
   case "$?" in
      0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
      2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
   esac
   ;;
  stop)
   [ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME1"
   do_stop
   case "$?" in
      0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
      2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
   esac
   ;;
  restart|force-reload)
   log_daemon_msg "Restarting $DESC" "$NAME1"
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
   echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
   exit 3
   ;;
esac

:
```

Finally, set it to be executable, set it to run on boot, and start it up:
```
sudo chmod 755 /etc/init.d/deluge-daemon
sudo update-rc.d deluge-daemon defaults
sudo /etc/init.d/deluge-daemon start
```

All done! The daemon and the web interface are now running, and the GTK client will connect to the daemon when you start it. Note that in the connection manager that comes up when you start the GTK client, you can configure it to auto-connect without prompting you, so it behaves as it did pre-daemon.

To use the WebUI, go to [http://localhost:8112]("http://localhost:8112") . The default password is "deluge". Once inside you can change the password, the default port number, and whatever else. Remember to restart if you change the port (sudo /etc/init.d/deluge-daemon restart).

Good luck, and enjoy!
-Kilbasar

thanks dude.
this is really great

---

### Post by orduek on 2009-08-23
May I suggest replacing the flexRSS with feeder?
The new flexRSS has no output folder option.
If you use feeder, which can be accessed only through the webUI, you can filter the folders also.
give it a try.
[https://forum.deluge-torrent.org/viewtopic.php?f=9&t=14115](https://forum.deluge-torrent.org/viewtopic.php?f=9&t=14115)

Looks better.

---

### Post by fimbar on 2009-11-21
Hi guys,

Many thanks for the howto. It was all looking good until I tried to run FlexRSS. It installed OK but when I try to run it from the interface I get the following error:

"Fault : <Fault 1: "<type 'exceptions.AttributeError'>:'Config' object has no attribute 'get_config'">"

I'm not sure if this is helpful but it also dumps this:
```
--Deluge Error--
Fault : <Fault 1: "<type 'exceptions.AttributeError'>:'Config' object has no attribute 'get_config'">
path : /config/flexrss
file : /usr/lib/pymodules/python2.6/deluge/xmlrpclib.py in close, line 786

--Input--
<Storage {}>

--Versions--
WebUi : 1.1.9r
Python 2.6.4rc2 (r264rc2:75497, Oct 20 2009, 02:55:11) 
[GCC 4.4.1]:

--Traceback--
  File "/usr/lib/pymodules/python2.6/deluge/ui/webui/lib/webpy022/webapi.py", line 310, in wsgifunc
    result = func()
  File "/usr/lib/pymodules/python2.6/deluge/ui/webui/lib/webpy022/request.py", line 131, in <lambda>
    func = lambda: handle(inp, fvars)
  File "/usr/lib/pymodules/python2.6/deluge/ui/webui/lib/webpy022/request.py", line 61, in handle
    return tocall(*([x and urllib.unquote(x) for x in args] + fna))
  File "/usr/lib/pymodules/python2.6/deluge/ui/webui/page_decorators.py", line 87, in deco
    return func(self, name) #check_session:ok
  File "/usr/lib/pymodules/python2.6/deluge/ui/webui/page_decorators.py", line 105, in deco
    return func(self, name) #check_connected:ok
  File "/usr/lib/pymodules/python2.6/deluge/ui/webui/page_decorators.py", line 60, in deco
    res = func(self, name) #deluge_page_noauth
  File "/usr/lib/pymodules/python2.6/deluge/ui/webui/config_forms.py", line 88, in GET
    f = form_class()
  File "/usr/lib/pymodules/python2.6/deluge/ui/webui/lib/newforms_plus.py", line 84, in __init__
    data = self.initial_data()
  File "/home/ian/.config/deluge/plugins/flexRSS-0.1.egg/flexrss/webui.py", line 52, in initial_data
    return sclient.flexrss_get_config()
  File "/usr/lib/pymodules/python2.6/deluge/xmlrpclib.py", line 1150, in __call__
    return self.__send(self.__name, args)
  File "/usr/lib/pymodules/python2.6/deluge/xmlrpclib.py", line 1440, in __request
    verbose=self.__verbose
  File "/usr/lib/pymodules/python2.6/deluge/ui/client.py", line 93, in request
    return self._parse_response(h.getfile(), sock)
  File "/usr/lib/pymodules/python2.6/deluge/xmlrpclib.py", line 1343, in _parse_response
    return u.close()
  File "/usr/lib/pymodules/python2.6/deluge/xmlrpclib.py", line 787, in close
    raise Fault(**self._stack[0])

```If it helps I'm running 1.1.9 of deluge-core and deluge-webui on Karmic 9.10.

I can't make head nor tail of the error so do not have a clue what to do next.

Has anyone else had this and/or does anyone know how to solve it?

Many thanks guys.

---

### Post by bobb0 on 2010-02-14
bump.  i'm having the same problem.

deluge v1.1.9
flexRSS plugin for 1.x
karmic koala server ed x64
python2.6

should I switch to python2.5?

---

### Post by fimbar on 2010-02-19
> **bobb0 said:**
> bump.  i'm having the same problem.

deluge v1.1.9
flexRSS plugin for 1.x
karmic koala server ed x64
python2.6

should I switch to python2.5?

I gave up trying to get FlexRSS to work and decided to go with [_**FlexGet**_]("http://havetheknowhow.com/Install-the-software/Install-RSS-for-Deluge.html") instead. It works beautifully :)

Note: that guide I used shows how to get it working with either v1.1.9 or v1.2.0

---

### Post by Redsandro on 2010-05-02
Did anyone get Deluged to run at startup? I guess I need to copy config files to root for that? Anyway I couldn't get it to work with deluge-daemon. :(

---

