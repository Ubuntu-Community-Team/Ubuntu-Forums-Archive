---
title: "HOWTO: install freepops"
date: 2005-05-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Gandalf on 2005-05-21
Hello,

i've been fighting all day to get freepops working with ubuntu hoary, and finally i get it working, so it's cool to share it with others,

**Q.** What is freepops
[Freepops](http://www.freepops.org) is a webmail -> pop client, it allow to receive a lot of webmail using a pop client, like hotmail, gmail, aol etc.... check [this page](http://www.freepops.org/en/viewplugins.php) for all supported modules

let's begin by preparing the system, to get it compiled i had to install the following packages,
```

sudo apt-get install bison flex libc6-dev libcurl3-dev libexpat1-dev libidn11-dev libssl0.9.7 zlib1g-dev debconf

```

this way i could complie it without any problems,

let's download now the sources,
go to [http://sourceforge.net/projects/freepops/](http://sourceforge.net/projects/freepops/) and download the sources,, 

NOTE: i use /usr/src to always keep a copy of the compiled sources in case i want to uninstall it
NOTE2: this guide will presume that you have downloaded the build 0.0.27, if it isn't the case be sure you replace the version

```

cd ~
wget http://mesh.dl.sourceforge.net/sourceforge/freepops/freepops-0.0.27.tar.gz
sudo tar -xzvf freepops-0.0.27.tar.gz -C /usr/src
cd /usr/src/freepops-0.0.27
sudo ./configure.sh linux
sudo make
sudo make install

```

now the freepops is installed and working, to run it manually you must run freepopsd with root (sudo freepopsd &), but it's better to run it automatically!

so let's begin by building the automatic run script

```

sudo pico /etc/init.d/freepops

```

paste into these contents
```

#! /bin/sh
#
#  TODO:
#     To be in perfect debian style we should use start-stop-daemon also
#     for chrooting.
# 
#

### some default values ###

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

DEFAULT_DAEMON=/usr/local/bin/freepopsd
DEFAULT_PIDFILE=/var/run/freepopsd.pid
DEFAULT_CHROOTED_DAEMON_OPTS=" -n -s nobody.nogroup"
DEFAULT_DAEMON_OPTS=" -n"

NAME=freepopsd
DESC="freepops daemon"

### /etc/default/ loading ###

# Include freepops defaults if available. Used variables are:
# DAEMON, DAEMON_OPTS, CHROOTED_DAEMON_OPTS, PIDFILE, CHROOT
# all have a DEFAULT_ here, except CHROOT that is empty if the 
# daemon should run in the normal environment

if [ -f /etc/default/freepops ] ; then
	. /etc/default/freepops
fi

if [ -z "$DAEMON" ] ; then
	DAEMON=$DEFAULT_DAEMON
fi

if [ -z "$PIDFILE" ] ; then
	PIDFILE=$DEFAULT_PIDFILE
fi

if [ -z "$DAEMON_OPTS" ] ; then
	DAEMON_OPTS=$DEFAULT_DAEMON_OPTS
fi

if [ -z "$CHROOTED_DAEMON_OPTS" ] ; then
	CHROOTED_DAEMON_OPTS=$DEFAULT_CHROOTED_DAEMON_OPTS
fi

test -x $DAEMON || exit 0

set -e

### helpers ###

function start_freepopsd () {
	if [ -z "$CHROOT" ] ; then
		start-stop-daemon --start -b --quiet -m -p $PIDFILE \
			--exec $DAEMON -- $DAEMON_OPTS
	else
		echo -n "(chroot) "
		start-stop-daemon --start -b --quiet -m -p $PIDFILE \
			-r $CHROOT --exec $DAEMON -- $CHROOTED_DAEMON_OPTS
	fi

}

function stop_freepopsd () {
	if [ -z "$CHROOT" ] ; then
		start-stop-daemon --stop --quiet -p $PIDFILE 
	else
		echo -n "(chroot) "
		start-stop-daemon --stop --quiet -p $PIDFILE 
	fi
	rm $PIDFILE
}

### real code ###

case "$1" in
  start)
	echo -n "Starting $DESC: "
	start_freepopsd
	echo "$NAME."
	;;
  stop)
	echo -n "Stopping $DESC: "
	stop_freepopsd
	echo "$NAME."
	;;
  restart|force-reload)
	echo -n "Restarting $DESC: "
	stop_freepopsd
	sleep 1
	start_freepopsd
	echo "$NAME."
	;;
  *)
	N=/etc/init.d/freepops
	echo "Usage: $N {start|stop|restart}" >&2
	exit 1
	;;
esac

exit 0

```

then give it run permissions,
```

sudo chmod +x /etc/init.d/freepops

```

add it to rc*.d runlevels
```

sudo update-rc.d freepops defaults

```

now to restart, stop or start freepops type
```
sudo invoke-rc.d freepops { start | stop | restart }
```
instead of ```
sudo freepopsd &
```




A LITTLE BIT OF INFO ON HOW TO USE IT...
_________________________________________
when you install it, you must configure thunderbird, evolution, outlook or whatever pop client u use, 

SERVER
________
server must be 127.0.0.1 if installed on the same PC, or PC's ip if installed on another,

PORT
_____
you must use port 2000


USERNAME
___________

you must use your email as username, for example to receive [email]account@hotmail.com[/email] mails, your username is [email]account@hotmail.com[/email], samething for gmail, etc...

PASSWORD
___________
well your password [IMG]http://www.siemens-mobiles.org/forum/Smileys/default/rofl.gif[/IMG] 

and now you can receive your mails on your pop client.....




if you prefer not to install it, i have install it on my server, if you want to use it here's the config

server : mail.siemens-mobiles.org
port : 2000


i hope this guide will be usefull to you!



[TEMPORARY NOTE]
hotmail has changed the way to login (html login forms, javascript etc...) 2 days ago, freepops has updated it's script ans it's working but it's not included in their build, you must update them manually,
so let's replace them,

```

cd /usr/local/share/freepops/lua
sudo mv hotmail.lua hotmail.lua_old
sudo mv aol.lua aol.lua_old
sudo mv mailcom.lua mailcom.lua_old
sudo wget http://www.freepops.org/download.php?file=hotmail.lua
sudo wget http://www.freepops.org/download.php?file=aol.lua
sudo wget http://www.freepops.org/download.php?file=mailcom.lua

```
now it will work!!!

---

### Post by jasmuz on 2005-05-21
> **Gandalf]Hello,

i've been fighting all day to get freepops working with ubuntu hoary, and finally i get it working, so it's cool to share it with others,

**Q.** What is freepops
[Freepops](http://www.freepops.org) is a pop->webmail client, it allow to receive a lot of webmail using a pop client, like hotmail, gmail, aol etc.... check [this page](http://www.freepops.org/en/viewplugins.php) for all supported modules

let's begin by preparing the system, to get it compiled i had to install the following packages,
```

sudo apt-get install bison flex libc6-dev libcurl3-dev libexpat1-dev libidn11-dev libssl0.9.7 zlib1g-dev debconf

```

this way i could complie it without any problems,

let's download now the sources,
go to [http://sourceforge.net/projects/freepops/](http://sourceforge.net/projects/freepops/) and download the sources,, 

NOTE: i use /usr/src to always keep a copy of the compiled sources in case i want to uninstall it
NOTE2: this guide will presume that you have downloaded the build 0.0.27, if it isn't the case be sure you replace the version

```

cd ~
wget http://mesh.dl.sourceforge.net/sourceforge/freepops/freepops-0.0.27.tar.gz
sudo tar -xzvf freepops-0.0.27.tar.gz -C /usr/src
cd /usr/src/freepops-0.0.27
sudo ./configure.sh linux
sudo make
sudo make install

```

now the freepops is installed and working, to run it manually you must run freepopsd with root (sudo freepopsd &), but it's better to run it automatically!

so let's begin by building the automatic run script

```

sudo pico /etc/init.d/freepops

```

paste into these contents
```

#! /bin/sh
#
#  TODO:
#     To be in perfect debian style we should use start-stop-daemon also
#     for chrooting.
# 
#

### some default values ###

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

DEFAULT_DAEMON=/usr/local/bin/freepopsd
DEFAULT_PIDFILE=/var/run/freepopsd.pid
DEFAULT_CHROOTED_DAEMON_OPTS=" -n -s nobody.nogroup"
DEFAULT_DAEMON_OPTS=" -n"

NAME=freepopsd
DESC="freepops daemon"

### /etc/default/ loading ###

# Include freepops defaults if available. Used variables are:
# DAEMON, DAEMON_OPTS, CHROOTED_DAEMON_OPTS, PIDFILE, CHROOT
# all have a DEFAULT_ here, except CHROOT that is empty if the 
# daemon should run in the normal environment

if [ -f /etc/default/freepops ]  said:**
>  ; then
	DAEMON=$DEFAULT_DAEMON
fi

if [ -z "$PIDFILE" ] ; then
	PIDFILE=$DEFAULT_PIDFILE
fi

if [ -z "$DAEMON_OPTS" ] ; then
	DAEMON_OPTS=$DEFAULT_DAEMON_OPTS
fi

if [ -z "$CHROOTED_DAEMON_OPTS" ] ; then
	CHROOTED_DAEMON_OPTS=$DEFAULT_CHROOTED_DAEMON_OPTS
fi

test -x $DAEMON || exit 0

set -e

### helpers ###

function start_freepopsd () {
	if [ -z "$CHROOT" ] ; then
		start-stop-daemon --start -b --quiet -m -p $PIDFILE \
			--exec $DAEMON -- $DAEMON_OPTS
	else
		echo -n "(chroot) "
		start-stop-daemon --start -b --quiet -m -p $PIDFILE \
			-r $CHROOT --exec $DAEMON -- $CHROOTED_DAEMON_OPTS
	fi

}

function stop_freepopsd () {
	if [ -z "$CHROOT" ] ; then
		start-stop-daemon --stop --quiet -p $PIDFILE 
	else
		echo -n "(chroot) "
		start-stop-daemon --stop --quiet -p $PIDFILE 
	fi
	rm $PIDFILE
}

### real code ###

case "$1" in
  start)
	echo -n "Starting $DESC: "
	start_freepopsd
	echo "$NAME."
	;;
  stop)
	echo -n "Stopping $DESC: "
	stop_freepopsd
	echo "$NAME."
	;;
  restart|force-reload)
	echo -n "Restarting $DESC: "
	stop_freepopsd
	sleep 1
	start_freepopsd
	echo "$NAME."
	;;
  *)
	N=/etc/init.d/freepops
	echo "Usage: $N {start|stop|restart}" >&2
	exit 1
	;;
esac

exit 0

```

then give it run permissions,
```

sudo chmod +x /etc/init.d/freepops

```

add it to rc*.d runlevels
```

sudo update-rc.d freepops defaults

```

now to restart, stop or start freepops type
```
sudo invoke-rc.d freepops { start | stop | restart }
```
instead of ```
sudo freepopsd &
```




A LITTLE BIT OF INFO ON HOW TO USE IT...
_________________________________________
when you install it, you must configure thunderbird, evolution, outlook or whatever pop client u use, 

SERVER
________
server must be 127.0.0.1 if installed on the same PC, or PC's ip if installed on another,

PORT
_____
you must use port 2000


USERNAME
___________

you must use your email as username, for example to receive [email]account@hotmail.com[/email] mails, your username is [email]account@hotmail.com[/email], samething for gmail, etc...

PASSWORD
___________
well your password [IMG]http://www.siemens-mobiles.org/forum/Smileys/default/rofl.gif[/IMG] 

and now you can receive your mails on your pop client.....




if you prefer not to install it, i have install it on my server, if you want to use it here's the config

server : mail.siemens-mobiles.org
port : 2000


i hope this guide will be usefull to you!



[TEMPORARY NOTE]
hotmail has changed the way to login (html login forms, javascript etc...) 2 days ago, freepops has updated it's script ans it's working but it's not included in their build, you must update them manually,
so let's replace them,

```

cd /usr/local/share/freepops/lua
sudo mv hotmail.lua hotmail.lua_old
sudo mv aol.lua aol.lua_old
sudo mv mailcom.lua mailcom.lua_old
sudo wget http://www.freepops.org/download.php?file=hotmail.lua
sudo wget http://www.freepops.org/download.php?file=aol.lua
sudo wget http://www.freepops.org/download.php?file=mailcom.lua

```
now it will work!!!
 Why compile if there are DEB's for Debian Sid and Sarge?

---

### Post by Gandalf on 2005-05-21
[QUOTE=jasmuz]Why compile if there are DEB's for Debian Sid and Sarge?[/QUOTE]
 because i couldn't install debs becuase libcurl isn't the satisfying version, and if i installed the one for sarge i break my webserver which i don't want in any way to do it
```

wael@nasreddine:~$ sudo apt-get install freepops
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  freepops: Depends: libcurl3 (>= 7.13.1-1) but 7.12.3-2ubuntu3 is to be installed
            Depends: libidn11 (>= 0.5.13) but 0.5.2-3 is to be installed
E: Broken packages

```

---

### Post by RastaMahata on 2005-05-21
[QUOTE=Gandalf]**Q.** What is freepops
[Freepops](http://www.freepops.org) is a **pop->webmail** client, it allow to receive a lot of webmail using a pop client, like hotmail, gmail, aol etc.... [/QUOTE]

I think it should say webmail -> pop, as it allow you to check webmail from a pop client.
Besides, you dont need this for gmail, as gmail has a pop feature ;)

Great program. I hope someone uploads the deb somewhere for people who dont like to compile :P

(Added to the index)

---

### Post by Gandalf on 2005-05-22
[QUOTE=RastaMahata]I think it should say webmail -> pop, as it allow you to check webmail from a pop client.
Besides, you dont need this for gmail, as gmail has a pop feature ;)

Great program. I hope someone uploads the deb somewhere for people who dont like to compile :P

(Added to the index)[/QUOTE]
 exactly, sorry a typo mistake :D

---

### Post by bored2k on 2005-05-22
Off topic - Gandalf got a job already ? :?

---

### Post by Gandalf on 2005-05-22
[QUOTE=bored2k]Off topic - Gandalf got a job already ? :?[/QUOTE]
 <off topic>
f**k no!!!  :|  ](*,) 
</off topic>

---

### Post by Reeva on 2005-05-25
[QUOTE=Gandalf]<off topic>
f**k no!!!  :|  ](*,) 
</off topic>[/QUOTE]
 When I try to start freepops with " sudo freeposd & " .. I always have this error

```
Unable to bind on 0.0.0.0:2000
``` 

can someone help me?

thx alot

---

### Post by Gandalf on 2005-05-25
[QUOTE=Reeva]When I try to start freepops with " sudo freeposd & " .. I always have this error

```
Unable to bind on 0.0.0.0:2000
``` 

can someone help me?

thx alot[/QUOTE]
 do you have iptables, firestarter etc.... ? i mean do you have firewall installed?

---

### Post by Reeva on 2005-05-26
no I don't have a firewall ..

I reinstalled freepops .. but I still have the same problem :(

---

### Post by benplaut on 2005-05-26
the truth is... how many people are still using webmails without POP support?

---

### Post by Reeva on 2005-05-26
[QUOTE=benplaut]the truth is... how many people are still using webmails without POP support?[/QUOTE]
 hotmail doesn't have pop support ?

---

### Post by daedalus_nl on 2005-06-04
Hi,

Maybe this will help Ubuntu Freepops user:

[Freepops & Debian]("https://sourceforge.net/forum/forum.php?forum_id=408803")

There are new debian repositories and maybe we can use them too

```

 386: woody, sarge, sid and source 
 deb [http://tassi.web.cs.unibo.it/debian/freepops-woody]("http://tassi.web.cs.unibo.it/debian/freepops-woody") ./ 
 deb [http://tassi.web.cs.unibo.it/debian/freepops-sarge]("http://tassi.web.cs.unibo.it/debian/freepops-sarge") ./ 
 deb [http://tassi.web.cs.unibo.it/debian/freepops-sid]("http://tassi.web.cs.unibo.it/debian/freepops-sid") ./ 
 deb-src [http://tassi.web.cs.unibo.it/debian/freepops-src]("http://tassi.web.cs.unibo.it/debian/freepops-src") ./ 
  
 powerpc: woody, sarge, sid and source 
 deb [http://cocchiar.web.cs.unibo.it/debian/freepops-woody]("http://cocchiar.web.cs.unibo.it/debian/freepops-woody") ./ 
 deb [http://cocchiar.web.cs.unibo.it/debian/freepops-sarge]("http://cocchiar.web.cs.unibo.it/debian/freepops-sarge") ./ 
 deb [http://cocchiar.web.cs.unibo.it/debian/freepops-sid]("http://cocchiar.web.cs.unibo.it/debian/freepops-sid") ./ 
 deb-src [http://cocchiar.web.cs.unibo.it/debian/freepops-src./]("http://cocchiar.web.cs.unibo.it/debian/freepops-src./")

```

---

### Post by Gandalf on 2005-06-04
[QUOTE=daedalus_nl]Hi,

Maybe this will help Ubuntu Freepops user:

[Freepops & Debian]("https://sourceforge.net/forum/forum.php?forum_id=408803")

There are new debian repositories and maybe we can use them too

```

 386: woody, sarge, sid and source 
 deb [http://tassi.web.cs.unibo.it/debian/freepops-woody]("http://tassi.web.cs.unibo.it/debian/freepops-woody") ./ 
 deb [http://tassi.web.cs.unibo.it/debian/freepops-sarge]("http://tassi.web.cs.unibo.it/debian/freepops-sarge") ./ 
 deb [http://tassi.web.cs.unibo.it/debian/freepops-sid]("http://tassi.web.cs.unibo.it/debian/freepops-sid") ./ 
 deb-src [http://tassi.web.cs.unibo.it/debian/freepops-src]("http://tassi.web.cs.unibo.it/debian/freepops-src") ./ 
  
 powerpc: woody, sarge, sid and source 
 deb [http://cocchiar.web.cs.unibo.it/debian/freepops-woody]("http://cocchiar.web.cs.unibo.it/debian/freepops-woody") ./ 
 deb [http://cocchiar.web.cs.unibo.it/debian/freepops-sarge]("http://cocchiar.web.cs.unibo.it/debian/freepops-sarge") ./ 
 deb [http://cocchiar.web.cs.unibo.it/debian/freepops-sid]("http://cocchiar.web.cs.unibo.it/debian/freepops-sid") ./ 
 deb-src [http://cocchiar.web.cs.unibo.it/debian/freepops-src./]("http://cocchiar.web.cs.unibo.it/debian/freepops-src./")

```[/QUOTE]
 yes i know them i use them on my debian sarge box, but try to install it on ubuntu :) it will not work

---

### Post by omiazad on 2005-06-04
[QUOTE=Reeva]When I try to start freepops with " sudo freeposd & " .. I always have this error

```
Unable to bind on 0.0.0.0:2000
``` 

can someone help me?

thx alot[/QUOTE]

Did you try this?

 ```
sudo freepopsd -p 2000 -b 127.0.0.1 &
``` 

Try that. I think you don't have any LAN card installed in your machine. I faced the same problem from Windows and I installed MS Loopback Adapter. But I'm on Linux now and I have a LAN card, so try the above solution.

---

### Post by omiazad on 2005-06-04
I have downloaded freepops_0.0.28-1woody_i386.deb, libssl0.9.6_0.9.6m-1_i386.deb and libcurl2-ssl_7.9.5-2_i386.deb from some sources. After instelling libcurl2-ssl_7.9.5-2_i386.deb, libssl0.9.6_0.9.6m-1_i386.deb and freepops_0.0.28-1woody_i386.deb it's running successfully. But I have to start this manually.

I want to put Freepops at startup with Port 110 and Bind 192.168.100.112

Can anyone give me some suggestion?

Omi

---

### Post by helwitch on 2005-08-30
Couple tips for compiling and installing this for anyone else who has never complied something, which I figured out the hard way while.

right before or after the following step, do 
```

sudo apt-get install build-essential

```
> **Gandalf]
```

sudo apt-get install bison flex libc6-dev libcurl3-dev libexpat1-dev libidn11-dev libssl0.9.7 zlib1g-dev debconf

```
[/QUOTE]


After you've pasted in the following bit, ctrl+O saves the file, and ctrl+x closes the editor and gives you back your command line.
[QUOTE=Gandalf]
paste into these contents
```

#! /bin/sh
#
#  TODO:
#     To be in perfect debian style we should use start-stop-daemon also
#     for chrooting.
# 
#

### some default values ###

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

DEFAULT_DAEMON=/usr/local/bin/freepopsd
DEFAULT_PIDFILE=/var/run/freepopsd.pid
DEFAULT_CHROOTED_DAEMON_OPTS=" -n -s nobody.nogroup"
DEFAULT_DAEMON_OPTS=" -n"

NAME=freepopsd
DESC="freepops daemon"

### /etc/default/ loading ###

# Include freepops defaults if available. Used variables are:
# DAEMON, DAEMON_OPTS, CHROOTED_DAEMON_OPTS, PIDFILE, CHROOT
# all have a DEFAULT_ here, except CHROOT that is empty if the 
# daemon should run in the normal environment

if [ -f /etc/default/freepops ]  said:**
>  ; then
	DAEMON=$DEFAULT_DAEMON
fi

if [ -z "$PIDFILE" ] ; then
	PIDFILE=$DEFAULT_PIDFILE
fi

if [ -z "$DAEMON_OPTS" ] ; then
	DAEMON_OPTS=$DEFAULT_DAEMON_OPTS
fi

if [ -z "$CHROOTED_DAEMON_OPTS" ] ; then
	CHROOTED_DAEMON_OPTS=$DEFAULT_CHROOTED_DAEMON_OPTS
fi

test -x $DAEMON || exit 0

set -e

### helpers ###

function start_freepopsd () {
	if [ -z "$CHROOT" ] ; then
		start-stop-daemon --start -b --quiet -m -p $PIDFILE \
			--exec $DAEMON -- $DAEMON_OPTS
	else
		echo -n "(chroot) "
		start-stop-daemon --start -b --quiet -m -p $PIDFILE \
			-r $CHROOT --exec $DAEMON -- $CHROOTED_DAEMON_OPTS
	fi

}

function stop_freepopsd () {
	if [ -z "$CHROOT" ] ; then
		start-stop-daemon --stop --quiet -p $PIDFILE 
	else
		echo -n "(chroot) "
		start-stop-daemon --stop --quiet -p $PIDFILE 
	fi
	rm $PIDFILE
}

### real code ###

case "$1" in
  start)
	echo -n "Starting $DESC: "
	start_freepopsd
	echo "$NAME."
	;;
  stop)
	echo -n "Stopping $DESC: "
	stop_freepopsd
	echo "$NAME."
	;;
  restart|force-reload)
	echo -n "Restarting $DESC: "
	stop_freepopsd
	sleep 1
	start_freepopsd
	echo "$NAME."
	;;
  *)
	N=/etc/init.d/freepops
	echo "Usage: $N {start|stop|restart}" >&2
	exit 1
	;;
esac

exit 0

```

BTW Gandulf, thanks tons for this walkthrough! It was amazingly helpful, and I feel all ubergeeky now! I compiled something! Yay me! *silly geek girl grin*

---

### Post by greywolf73 on 2005-10-06
Thanks, the how to was easy to follow.

---

### Post by greywolf73 on 2005-10-06
Does freepops support SMTP?

---

### Post by sbarrax on 2005-11-07
Well, i found FreePOPs deb packages for ubuntu and kubuntu here:  [http://cybertech.altervista.org/freepops.php]("http://cybertech.altervista.org/freepops.php")

they work! :)

---

### Post by obscenic on 2005-11-10
[QUOTE=omiazad]I have downloaded freepops_0.0.28-1woody_i386.deb, libssl0.9.6_0.9.6m-1_i386.deb and libcurl2-ssl_7.9.5-2_i386.deb from some sources. After instelling libcurl2-ssl_7.9.5-2_i386.deb, libssl0.9.6_0.9.6m-1_i386.deb and freepops_0.0.28-1woody_i386.deb it's running successfully. But I have to start this manually.

I want to put Freepops at startup with Port 110 and Bind 192.168.100.112

Can anyone give me some suggestion?

Omi[/QUOTE]

sudo gedit /etc/init.d/freepops

There's a variable in there named $DEFAULT_DAEMON_OPS or something like that. Drop your switches in there..  -p 110 -b 192.168.100.112

Oh, and if you don't already have a freepops in your init.d then
sudo gedit /etc/init.d/freepops
make it 
```

#! /bin/sh
#
#  TODO:
#     To be in perfect debian style we should use start-stop-daemon also
#     for chrooting.
# 
#

### some default values ###

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

DEFAULT_DAEMON=/usr/local/bin/freepopsd
DEFAULT_PIDFILE=/var/run/freepopsd.pid
DEFAULT_CHROOTED_DAEMON_OPTS=" -n -s nobody.nogroup  -p 110 -b 192.168.100.112"
DEFAULT_DAEMON_OPTS=" -n  -p 110 -b 192.168.100.112"

NAME=freepopsd
DESC="freepops daemon"

### /etc/default/ loading ###

# Include freepops defaults if available. Used variables are:
# DAEMON, DAEMON_OPTS, CHROOTED_DAEMON_OPTS, PIDFILE, CHROOT
# all have a DEFAULT_ here, except CHROOT that is empty if the 
# daemon should run in the normal environment

if [ -f /etc/default/freepops ] ; then
	. /etc/default/freepops
fi

if [ -z "$DAEMON" ] ; then
	DAEMON=$DEFAULT_DAEMON
fi

if [ -z "$PIDFILE" ] ; then
	PIDFILE=$DEFAULT_PIDFILE
fi

if [ -z "$DAEMON_OPTS" ] ; then
	DAEMON_OPTS=$DEFAULT_DAEMON_OPTS
fi

if [ -z "$CHROOTED_DAEMON_OPTS" ] ; then
	CHROOTED_DAEMON_OPTS=$DEFAULT_CHROOTED_DAEMON_OPTS
fi

test -x $DAEMON || exit 0

set -e

### helpers ###

function start_freepopsd () {
	if [ -z "$CHROOT" ] ; then
		start-stop-daemon --start -b --quiet -m -p $PIDFILE \
			--exec $DAEMON -- $DAEMON_OPTS
	else
		echo -n "(chroot) "
		start-stop-daemon --start -b --quiet -m -p $PIDFILE \
			-r $CHROOT --exec $DAEMON -- $CHROOTED_DAEMON_OPTS
	fi

}

function stop_freepopsd () {
	if [ -z "$CHROOT" ] ; then
		start-stop-daemon --stop --quiet -p $PIDFILE 
	else
		echo -n "(chroot) "
		start-stop-daemon --stop --quiet -p $PIDFILE 
	fi
	rm $PIDFILE
}

### real code ###

case "$1" in
  start)
	echo -n "Starting $DESC: "
	start_freepopsd
	echo "$NAME."
	;;
  stop)
	echo -n "Stopping $DESC: "
	stop_freepopsd
	echo "$NAME."
	;;
  restart|force-reload)
	echo -n "Restarting $DESC: "
	stop_freepopsd
	sleep 1
	start_freepopsd
	echo "$NAME."
	;;
  *)
	N=/etc/init.d/freepops
	echo "Usage: $N {start|stop|restart}" >&2
	exit 1
	;;
esac

exit 0

```

sudo chmod +x /etc/init.d/freepops
sudo update-rc.d freepops defaults

[B]
Important note[/B]: I'm a total noob and have no idea what I'm doing. Before last week I had never spent more than a day using a linux system.

---

### Post by ikkinu on 2005-12-29
I have guarddog installed, and the same "Unable to bind on 0.0.0.0:2000". I use guarddog, and set a tcp:2000 allowed, but I can't connect. Can anyone help me?
bye

---

### Post by NeoFax on 2006-01-12
ikkinu:  Did you change the /etc/default/freepops file to have -p 2000 and -b 127.0.0.1?  If not, it will not connect.  I am using guarddog as well with the same setup of allowing packets across port 2000 with no problems.

---

### Post by DarkS0ul on 2006-10-28
Freepops keeps getting new updates, so another way to install it now is from the main site. Which states:
> 
Ubuntu and Kubuntu (amd64, i386)
[Blackmoon]("http://cybertech.altervista.org/en/freepops.php") provides up to date debs for Ubuntu and Kubuntu.
[http://cybertech.altervista.org/en/freepops.php]("http://cybertech.altervista.org/en/freepops.php")


After you have installed freepops you will then need to get the latest lua files such as hotmail.lua etc.

So find where it installed it the default location is: /usr/share/freepops/lua

Or you can search for it:
```

sudo find / -name "lua"

```

and it should bring up results of what paths are available.

Then you will need to go to the main site and grab the latest lua files as Gandalf shows you:
> **Gandalf said:**
> 
(First rename the originals so we can install the new ones):
sudo mv hotmail.lua hotmail.lua_old
sudo mv aol.lua aol.lua_old
sudo mv mailcom.lua mailcom.lua_old

cd browser
sudo mv browser.lua browser.lua_old
cd ..

(Now get the latest versions):
sudo wget [http://www.freepops.org/download.php?file=hotmail.lua](http://www.freepops.org/download.php?file=hotmail.lua)
sudo wget [http://www.freepops.org/download.php?file=aol.lua](http://www.freepops.org/download.php?file=aol.lua)
sudo wget [http://www.freepops.org/download.php?file=mailcom.lua](http://www.freepops.org/download.php?file=mailcom.lua)
cd browser
sudo wget [http://www.freepops.org/download.php?file=browser.lua](http://www.freepops.org/download.php?file=browser.lua)

NOTE: browser.lua and cookies.lua are located in the browser directory. (ex: /usr/share/freepops/lua/browser)

Get all the ones you need, the list of updates are on [http://www.freepops.org/](http://www.freepops.org/) it is best to grab them all. After that just follow what Gandalf has been nice enough to state :
> **Gandalf said:**
> 
add it to rc*.d runlevels
```

sudo update-rc.d freepops defaults

```

now to restart, stop or start freepops type
```
sudo invoke-rc.d freepops { start | stop | restart }
```
instead of ```
sudo freepopsd &
```

A LITTLE BIT OF INFO ON HOW TO USE IT...
_________________________________________
when you install it, you must configure thunderbird, evolution, outlook or whatever pop client u use, 

SERVER
________
server must be 127.0.0.1 if installed on the same PC, or PC's ip if installed on another,

PORT
_____
you must use port 2000


USERNAME
___________

you must use your email as username, for example to receive [email]account@hotmail.com[/email] mails, your username is [email]account@hotmail.com[/email], samething for gmail, etc...

PASSWORD
___________
well your password [IMG]http://www.siemens-mobiles.org/forum/Smileys/default/rofl.gif[/IMG] 

and now you can receive your mails on your pop client.....




if you prefer not to install it, i have install it on my server, if you want to use it here's the config

server : mail.siemens-mobiles.org
port : 2000


i hope this guide will be usefull (useful) to you!


---

### Post by kit2 on 2007-01-18
Hi, I'm unable to get frepops to work under ubuntu, I've tried using Gandalfs how-to, I think I have the necessary files installed, but when it comes to the final compile crunch, i get this

[I]sudo ./configure.sh linux
sudo make
sudo make install

Default is all
building lua
building luay
 compiling luay.c -> luay.c:19:17: error: lua.h: No such file or directory
In file included from luay.c:20:
luay.h:44: error: syntax error before ‘*’ token
luay.h:56: error: syntax error before ‘*’ token
luay.h:61: error: syntax error before ‘*’ token
luay.c:24: error: syntax error before ‘*’ token
luay.c: In function ‘luay_printtrace’:[/I]

I new to this, but its seems like it cant make the file lua.h, or cant include it, can anyone help??
Also instaling the Deb, from Freepops website, only gives me this error
Unable to bind on 0.0.0.0:2000
even if I bind it to the usual 
sudo freepopsd -b 127.0.0.1
Unable to bind on 127.0.0.1:2000


Sumit

---

### Post by hunnypot on 2007-03-08
Thanks Gandalf for your useful HOWTO!

I'm using Ubuntu Edgy, Evolution 2.8.1 and Freepops 0.2.0, and this is how I made it works.

1) Download .deb package of Freepops from [http://cybertech.altervista.org/en/freepops.php](http://cybertech.altervista.org/en/freepops.php) (otherwise you can download source and make it)

2) Install .deb package
$ sudo dpkg -i ./freepops_0.2.0-1-bkm_i386.deb

Password:
Selecting previously deselected package freepops.
(Reading database ... 119316 files and directories currently installed.)
Unpacking freepops (from .../freepops_0.2.0-1-bkm_i386.deb) ...
Setting up freepops (0.2.0-1) ...
Installing new version of config file /etc/freepops/config.lua ...
Installing new version of config file /etc/init.d/freepops ...
Removing local updates in /var/lib/freeopos/lua_updates/
 * Stopping freepops daemon freepopsd                                            
 * Starting freepops daemon freepopsd

3) I followed the steps originally posted by Gandalf. The version that he's using is freepops-0.0.27. I've tried to find the configuration steps for freepops-0.2.0 but couldn't find any, so I decided to follow what he did.

3.1) Edit /etc/init.d/freepops
$ sudo gedit /etc/init.d/freepops
==> I found that no change was necessary.

3.2) Give it run permissions
$ ls -l /etc/init.d/freepops
-rwxr-xr-x 1 root root 2672 2007-03-07 04:43 /etc/init.d/freepops
==> Have run permission by default.

3.3) Add it to rc*.d runlevels
$ sudo update-rc.d freepops defaults
 System startup links for /etc/init.d/freepops already exist.
==> Already done.

3.4) Now to restart, stop or start freepops type
$ sudo invoke-rc.d freepops restart
 * Stopping freepops daemon freepopsd                                 [ ok ] 
 * Starting freepops daemon freepopsd                                 [ ok ] 

4) Evolution setting
4.1) Edit -> Preferences -> Add -> use wizard to create your account
4.2) Receiving Email
	Server type: POP
	Server: 127.0.0.1:2000  (freepops is running at port 2000 by default)
	Username: [email]your_account@domain.com[/email] (for example: [email]sample@yahoo.com[/email])
	Security: No encryption
	Authentication type: Password

Remark: Freepops doesn't have SMTP facility. You have to use your ISP's SMTP server. For me, I use Gmail SMTP server and it works fine. 

However, my situation is I can retrieve Yahoo mails but when I send mails out from my Yahoo account (using Gmail SMTP), it appears to be sending from my Gmail account instead, not Yahoo. How can I make other people see that it's from Yahoo? Please suggest.

---

### Post by skirsman on 2007-04-14
Your Post is GREAT

but I've this error

Sending Username and Password did nos succeed. Mail server 127.0.0.1 responded
Unknown error. please fix.

Thanx:guitar:

---

### Post by Gandalf on 2007-04-17
> **skirsman said:**
> Your Post is GREAT

but I've this error

Sending Username and Password did nos succeed. Mail server 127.0.0.1 responded
Unknown error. please fix.

Thanx:guitar:

It depends, please refer to [http://freepops.diludovico.it/freepops-english/](http://freepops.diludovico.it/freepops-english/)

---

### Post by Yochanan on 2007-05-02
> **omiazad said:**
> Did you try this?

 ```
sudo freepopsd -p 2000 -b 127.0.0.1 &
``` 

Try that. I think you don't have any LAN card installed in your machine. I faced the same problem from Windows and I installed MS Loopback Adapter. But I'm on Linux now and I have a LAN card, so try the above solution.

I tried that and got this:

```

yochanan@MyPrecious:~$ sudo freepopsd -p 2000 -b 127.0.0.1 &
[2] 18281
yochanan@MyPrecious:~$ Unable to bind on 127.0.0.1:2000

```

> **NeoFax said:**
> ikkinu:  Did you change the /etc/default/freepops file to have -p 2000 and -b 127.0.0.1?  If not, it will not connect.  I am using guarddog as well with the same setup of allowing packets across port 2000 with no problems.

How?

---

### Post by regomodo on 2007-06-13
when i try to do this

$ sudo invoke-rc.d freepops { start | stop | restart }

i get
```

stop: missing job name
Try `stop --help' for more information.
bash: restart: command not found
/etc/init.d/freepops: 54: Syntax error: "(" unexpected
invoke-rc.d: initscript freepops, action "{" failed.
```

What exactly does that mean?

---

### Post by Shaun440 on 2008-02-08
I would like to bump this thread.

I've tried everything here and still cannot get freepops to work.

---

### Post by tattrat on 2008-05-09
me to - this is a rubbish howto!

---

### Post by DesiArnez6 on 2008-05-28
same here... I am getting similar errors, sigh

After typing:  sudo freepopsd -p 2000 -b 127.0.0.1

I receive the error: Unable to bind on 127.0.0.1:2000

Does this have to do wit firewall permissions, firestarter, etc?

---

### Post by Dhammikae on 2008-05-30
I am a newbee for Ubuntu but I have used Freepops for all my web mail for quite some time on Windows and here is how I got it working on Ubuntu.

Search Freepops in Synaptic package manager and select to install freepops and freepops-updater-fltk

After this do

sudo apt-get install build-essential

and that will install all the needed stuff.

Now update all lua packages to the latest using 

sudo freepops-updater-fltk

And now you can start the service using

sudo freepopsd -p 110 -b 127.0.0.1 &
(I used it for port 110 - you can use 2000 as in default setting)

Now all my hotmail, yahoo, AOL and Gmail are working great. I use port 110 because I use a shared Thunderbird profile between my Windows and Ubuntu and in wondows I have been using port 110 as that seems to be the port my Virus scanner scans. 

Hope this will help someone.

D.

---

### Post by ucro1263 on 2008-06-05
After typing: sudo freepopsd -p 2000 -b 127.0.0.1

I receive the error: Unable to bind on 127.0.0.1:2000

Can someone help us with these???

---

### Post by ucro1263 on 2008-06-05
> **ucro1263 said:**
> After typing: sudo freepopsd -p 2000 -b 127.0.0.1

I receive the error: Unable to bind on 127.0.0.1:2000

Can someone help us with these???


OK, solved my above question myself!!!:lolflag:

Here's what i did:
[PHP]sudo gedit /etc/default/freepops[/PHP]

in my file it contained the next data:
[PHP]#####################################
# configuration file for freepopsd.
#                                    
# man freepopsd for more info.     
DAEMON="/usr/bin/freepopsd"
DAEMON_OPTS=" -n -s nobody.nogroup"
PIDFILE="/var/run/freepops.pid"
CHROOTED_DAEMON_OPTS=" -n -s nobody.nogroup"[/PHP]

i changed tha last line to look like this:
[PHP]#####################################
# configuration file for freepopsd.
#                                    
# man freepopsd for more info.     
DAEMON="/usr/bin/freepopsd"
DAEMON_OPTS=" -n -s nobody.nogroup"
PIDFILE="/var/run/freepops.pid"
[COLOR="Red"]CHROOTED_DAEMON_OPTS=" -p 2000 -b 127.0.0.1 -n -s nobody.nogroup"[/COLOR][/PHP]

save, close, and to the next instruction in the howTo.

---

### Post by yateendra on 2010-05-17
To: Those who have gotten Freepops to work when guarddog is disabled, but not otherwise. There are two possible glitch points:

(1) The connection between your mail client and the freepops demon (freepopsd). I have set mine up using 127.0.0.1 (localhost) port 2000, and I recommend other messages here to troubleshoot that part (In my installation, no adjustments were necessary in guarddog to enable a connection to localhost port 2000).

(2) The connection between the freepops demon and the email server (in the INTERNET zone).
The general factor to consider is that, while Freepops is categorized as a means to access "http mail," it may actually use other protocols (than "http" or "https") to retrieve your mail. Here's some info. which may help.

I use freepops for yahoo mail, and did some troubleshooting using a log of blocked traffic (I used firestarter for this (?!)). My block occurred on Port 143.

As it turns out, the current Freepops "lua" (access script) uses IMAP protocol to access yahoo mail (Freepops may also use this method for other services). In guarddog, the corresponding selection is "Internet/Protocol/Imap" (You can verify this by entering "143" in the "Port Reference" Tab). Click to make the checkmark appear, then click "Apply."

I was able to download my yahoo mail after doing this. Unfortunately, there is a bug in the current [5/17/10] "yahoo.lua" file--keeps downloading the same messages ad infinitum--and I will have to install the update from the freepops bulletin board manually ([http://freepops.diludovico.it](http://freepops.diludovico.it)). The fix was published by a bulletin board participant and hasn't yet been added to the freepops update repository.

Now I will uninstall firestarter :(. If you would like to avoid the hassle, you can read the kernel log and get the "blocked packets" information directly (I was too much of a novice to identify this). Here's the corresponding log entry (/var/log/kern.log):
May 17 07:49:17 [machine-name] kernel: [10167.520079] DROPPED IN= OUT=eth0 SRC=192.168.0.198 DST=98.136.131.29 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=42835 DF PROTO=TCP SPT=4517 DPT=143 SEQ=508079533 ACK=0 WINDOW=5840 RES=0x00 SYN URGP=0 OPT (020405B40101040201030307) 

Apparently "DPT" means "destination port." "SRC" would be your local machine's network address.

Good Luck!
Cam

---

### Post by wnelson on 2010-07-30
Make sure the following in /etc/defaults/freepops is changed


DAEMON_OPTS=" -p 2000 -n -s nobody.nogroup"

This makes the localhost error go a way even with a firewall.

---

