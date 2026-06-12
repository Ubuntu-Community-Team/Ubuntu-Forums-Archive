---
title: "How To: SIMP server - encrypt IM chat"
date: 2008-04-16
forum: Outdated Tutorials &amp; Tips
---

### Post by ninocass on 2008-04-16
Blurb from the SIMP site:

> You are using instant messaging software to chat with your friends or colleagues. Did you know your messages are sent over the Internet in cleartext form?

SimpServer is the first lightweight instant messaging security gateway for Unix systems. Install SimpServer on a Unix system and configure IM clients on your local network, and conversations with Simp-equipped parties will be automatically encrypted. SimpServer can indeed accept simultaneous remote connections and thus secure local and/or remote clients.

With SimpServer, corporate environments can now benefit from centralized instant messenger encryption. Linux fans can now secure their MSN conversations. SimpServer is currently beta software and is free for any use. Link: [http://www.secway.fr/us/products/simpserver/](http://www.secway.fr/us/products/simpserver/)

As the blurb says simp can be used to encrypt IM conversations between 2 users, note that both users need to be running SIMP!

Onto the commandy fun!

First off grab the files needed from the SIMP site:
```
wget http://download.secway.com/public/products/simpserver/simpserver-2.1.5c-linux-x86.tgz
```now 

extract the files:
```
tar -xvvf simpserver-2.1.5c-linux-x86.tgz
```move the dir that contains the files to the /usr/local/ dir
```
sudo mv simp/ /usr/local/
```cd to the simp bin dir
```
cd /usr/local/simp/bin/
```start the simp server
```
sudo ./simpserver
```at this point the server will start, you shouldnt get any errors but if you do you might need to grab a different package its the aplha version you want: [http://www.secway.fr/us/products/simpserver/download.php](http://www.secway.fr/us/products/simpserver/download.php)

As the output will tell you the server opens various ports for the different IM programs:
```

MSN Service on 0.0.0.0:11863, mode 1
MSN Service on 0.0.0.0:1863, mode 0
AIM Service on 0.0.0.0:15191, mode 1
ICQ Service on 0.0.0.0:15190, mode 1
YAHOO Service on 0.0.0.0:15050, mode 1
Admin Service on 127.0.0.1:10023, mode 0

```at the minute we want the admin server so open a telnet connection to port 10023 on the localhost:
```
telnet localhost 10023
```you will be greated with a login prompt the default creds are admin:admin

the documentation will tell you how to change this password.

typing the **help** command will display the possible commands:

```

 ?,        help                  print this help
 list,     list_keys             [all, public, private]
 generate, generate_private_key  [-e<account>] [-s<service>] [-c<cipher>] [-b<size>] [-n<name>] [-p<password>]
 load,     load_private_key      -i<keyid> [-e<account>] [-s<service>] [-c<cipher>] [-p<password>]
 unload,   unload_private_key    -i<keyid> [-e<account>] [-s<service>] [-c<cipher>]
 change,   change_password       -i<keyid> [-e<account>] [-s<service>] [-c<cipher>] [-o<old_password>] [-p<new_password>]
 delete,   delete_key            -i<keyid> [-e<account>] [-s<service>] [-c<cipher>] [-force] [-pendinf]
 accept,   accept_pending_key    -i<keyid> [-e<account>] [-s<service>] [-c<cipher>]
 quit,     exit                  exit

```at the minute we want to generate a new private key, there are various options such as names and passwords but for testing just execute the **generate** command.

once executed run the **list** command to view the keys you should have something like:

```

Prv  Loaded KeyId             SHA-1 fingerprint                                   Date        Type         Srv  Name
--------------------------------------------------------------------------------------------------------------------
Yes  Yes    <numbers + letters>  <numbers + letters>   2008-04-16     RSA-2048    *  [admin] KeyPair

```Finally you need to configure your IM client to use SIMP, in AMSN click the accounts then preferences menu click the advanced tab and half way down theres an option for an initial MSN notification server, change this to use the SIMP port:

```

initial msn notification server : localhost:1863

```start a conversation with another SIMP user and you should see the encrypted and authenticated message:

```

[09:56:40] Nino says: 
*** (*) SimpServer Linux 2.2.1.5c - Encrypted and Authenticated (*) ***

test message

```enjoy!

---

### Post by jaccee on 2008-05-03
Verry nice! But i just get this:
jacob@jacob-desktop:/usr/local/simp/bin$ sudo ./simpserver/
sudo: ./simpserver/: command not found

anyone know what to do?

---

### Post by ninocass on 2008-05-20
wow, sorry for the delay

your trying to run a directory there not a binary you need to knock off the trailing /, my fault ive edited the original post

---

### Post by gornati on 2008-08-25
Mine is not showing the admin port...
I cant open telnet, it says connection refused.
Any ideas?

---

### Post by tact on 2008-08-25
As cool as this seems, installing a server, etc...  isn't it much easier just to enable the OTR plugin for pidgin?   I have private/encrypted conversations with my colleagues all the time using that functionality.

Cheers

---

### Post by trilobitomorph on 2009-01-12
alright.
im a newbie, so this might come out as somewhat retarded.
using ubuntu 8.10, need encryption.
cant get simp started.

"./simpserver: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory"

cant find libraries corresponding to my architecture.
amd64, hp pavillion harman kardon.

i386 package says dependencies are unstable.

any hints, ideas, directions, suggestions?

---

### Post by trilobitomorph on 2009-01-12
now i also got a broken libstdc++.so.5 package i dont know how to get rid of :D

---

### Post by dotkam on 2009-01-14
Hey Trilobitomorph, I installed simpserver on Ubuntu 8.10 a couple of months ago: [http://blog.dotkam.com/2008/11/10/configure-simp-server-to-encrypt-im-clients-in-linux/]("http://blog.dotkam.com/2008/11/10/configure-simp-server-to-encrypt-im-clients-in-linux/")
 
It also includes installing "C++ Standard Library":

```
sudo apt-get install libstdc++5
```

Let me know if it helps,
-- dotkam

---

### Post by kevdog on 2009-01-15
Cool concept but theoretically the OTR plugin used in pidgin may be theoretically better since it provides for plausible deniability.  There is an additional plugin for Pidgin that provides the exact RSA/SHA1 encryption/signing as this plugin: [http://pidgin-encrypt.sourceforge.net/](http://pidgin-encrypt.sourceforge.net/)  I don't think its actively maintained.

One benefit of the SIMP method however may be if you are not using pidgin since the other two options are require Pidgin

Gajim has another encryption method, however I'm not very knowledgeable about this.

In all cases both parties must have the plugins installed in order to provide for this functionality.

---

### Post by trilobitomorph on 2009-01-18
almost there.
when i try to connect
"expected integer but got 'localhost'"

also, can that be run with gtalk?
can't seem to get it started, still.

---

### Post by trilobitomorph on 2009-01-20
.skf extention required for keys on the other side (win)

i really need to get this working.

---

### Post by gotling on 2009-02-03
I have SimpServer installed and running as a service. I have attached the startup script I wrote from skeleton.

[PHP]
#! /bin/sh
### BEGIN INIT INFO
# Provides:          simpserver
# Required-Start:    simpserver
# Default-Start:     2 3 4 5
# Default-Stop:      S 0 1 6
# Short-Description: SimpServer initscript
# Description:       Script for launching SimpServer IM encryption.
#                    Placed in /etc/init.d.
#                    Activate with $ sudo update-rc.d simpserver defaults		     
### END INIT INFO

# Author: gotling

# Do NOT "set -e"

PATH=/usr/sbin:/usr/bin:/sbin:/bin
DESC="Proxy for encrypting IM conversations"
NAME=simpserver
DAEMON="/usr/local/simp/bin/$NAME"
DAEMON_ARGS=""
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME

# Exit if the package is not installed
[ -x "$DAEMON" ] || exit 0

# Read configuration variable file if it is present
[ -r /etc/default/$NAME ] && . /etc/default/$NAME

# Load the VERBOSE setting and other rcS variables
[ -f /etc/default/rcS ] && . /etc/default/rcS

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
	start-stop-daemon -b --start --quiet --pidfile $PIDFILE --exec $DAEMON --test > /dev/null \
		|| return 1
	start-stop-daemon -b --start --quiet --pidfile $PIDFILE --exec $DAEMON -- \
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
  restart|force-reload)
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
	echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
	exit 3
	;;
esac

:

[/PHP]


I have a problem with simpserver, using pidgin to connect to simpserver with SOCKS4. The authentication and encryption is working fine.

Though, quite often I loose connection to the MSN network and right after it is restored. Any one with the same problem? This only happens when using pidgin through the simpserver proxy.

Kind regards

---

### Post by KyleFx on 2009-02-24
> **gotling said:**
> 
I have a problem with simpserver, using pidgin to connect to simpserver with SOCKS4. The authentication and encryption is working fine.

Though, quite often I loose connection to the MSN network and right after it is restored. Any one with the same problem? This only happens when using pidgin through the simpserver proxy.

Kind regards


I'm having the same problem.  If anyone figures out how to fix it, I would really appreciate if you could let me know.  I would love it if I could get some version of simplite running on linux.

I can configure everything just fine, and it all works.  Pidgin is set up with the Socks4 proxy, and the keys for simpserver are generated.  The whole setup works, but it kicks on and off constantly, making it unuseable.

---

### Post by trilobitomorph on 2009-03-12
i still can't figure out how to configure it with gtalk. :(

what port does the simp server listen to for gtalk, any ideas?

---

### Post by chk9 on 2009-08-10
Thanks ninocass, dotkam and gotling, it's working for me now too!

_________________________________
Thanking someone is a great way to keep track of useful threads for yourself! :KS

---

### Post by sircurmudgeon on 2010-08-10
So, now that libstdc++5 is obsoleted, this doesn't work. I do have libstdc++6. Any way around this?

no dice on:
sudo apt-get install libstdc++5

I also checked synaptic but there is only libstdc++6 packages for 9.10  (haven't made the jump to 10.04 on my server yet since I've seen people have issues with mysql)

I want this to get around not having to use multiple IM clients with simplite since I have friends that use the pro version at work. They aren't able to use pidgin. (don't ask, it is stupid)


Edit:
Nevermind. Found the package here:[http://packages.ubuntu.com/search?keywords=libstdc%2B%2B5&searchon=names&suite=jaunty&section=all]("http://packages.ubuntu.com/search?keywords=libstdc%2B%2B5&searchon=names&suite=jaunty&section=all")

---

