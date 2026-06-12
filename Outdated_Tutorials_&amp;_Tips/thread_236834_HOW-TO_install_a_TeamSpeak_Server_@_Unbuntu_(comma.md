---
title: "HOW-TO: install a TeamSpeak Server @ Unbuntu (command-line)"
date: 2006-08-15
forum: Outdated Tutorials &amp; Tips
---

### Post by tja on 2006-08-15
this post describes how to set up a **teamspeak server daemon** on Ubuntu.
[COLOR="YellowGreen"](any corrections welcome !)[/COLOR]

[SIZE="4"]be aware ...[/SIZE]
[LIST]
[*]that teamspeak server is a foreign (not GPL'ed) binary program that may (or may not) imply security constraints on your system, especially if your sys is (as likely for a teamspeak-server) exposed to the internet (see below for strategies to reduce risks).
[*]that your usage of the teamspeak server binary is bound to the licensing terms of "TeamSpeak Systems".
[/LIST]

k, after all that "youre-on-your-own"-chitchat lets start this.

[SIZE="4"]Prerequisites:[/SIZE]
[LIST][*]seems to work "out-of-the-box" on a Ubuntu-Server (with LAMP) installation, should work on Ubuntu Desktop too.
[*]teamspeak server archive from [http://www.goteamspeak.com/]("http://www.goteamspeak.com/"), go down to ***TeamSpeak 2 Server (RC2) 2.0.20.1*** (see Download if you use Ubuntu Server)[/LIST]

[SIZE="4"]Download:[/SIZE]
first step is to download the archive. if your Ubuntu Server is hosted on the net like mine there is an easy ways to do this.
[LIST=1][*]use the browser on your desktop machine and just click yourself thru the teamspeak-site till you reach the license page, go to the bottom and
[*]right-click [COLOR="SeaGreen"]I AGREE[/COLOR] and copy the link into your clipboard,
[*]go to your (ssh-ed) terminal session,
[*]enter ***wget "***,
[*]insert the copied url,
[*]enter ***"***,
[*]you'll get a commandline roughly like ***wget "ftp://ftp.freenet.de/pub/4players/teamspeak.org/releases/ts2_server_rc2_20201.tar.bz2"***,
[*]<RETURN> and wget downloads the archive, voila[/LIST]

[SIZE="4"]Installation:[/SIZE]
now its time to install the software to its final path and to create an account for the daemon (in the shell you will see your own username instead of "user" and your own server name instead of "server").
[LIST=1][*]unpack the archive
```
user@server:~$ tar xvjf ts2_server_rc2_20201.tar.bz2
```
[*]move the unpacked directory with the teamspeak software to /opt
```
user@server:~$ sudo mv tss2_rc2/ /opt
```
[*]for secuity reasons you should not run [COLOR="Red"]**- under no circumstances, not even to test it -**[/COLOR] the teamspeak server binary as root. so lets create an user who will run our daemon.
```
user@server:~$ sudo adduser teamspeak
Password:
Adding user `teamspeak'...
Adding new group `teamsp' (1001).
Adding new user `teamspeak' (1001) with group `teamspeak'.
Creating home directory `/home/teamspeak'.
Copying files from `/etc/skel'
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
Changing the user information for teamspeak
Enter the new value, or press ENTER for the default
        Full Name []: TeamSpeak Daemon Runner
        Room Number []:
        Work Phone []:
        Home Phone []:
        Other []:
Is the information correct? [y/N] y
```
the password will not matter but to be paranoid we use a long and fairly complicated one.
[*]the teamspeak server will store some files in the /opt/tss2_rc2 directory but otherwise just need read and executable rights on the files there, so we will just change ownership of the directory itself
```
user@server:~$ sudo chown teamspeak /opt/tss2_rc2
```
and let the other files there untouched (they should be owned by the user you use to access the server by now).
[*]we dont want to let our teamspeak user log in interactively so we will change his log-in shell to /bin/false
```
sudo usermod -s /bin/false teamspeak
```
[*]lets recheck everything we made so far:
first the teamspeak software directory:
```
user@server:~$ ls -la /opt/tss2_rc2/
total 1520
drwxr-xr-x 7 teamspeak user        4096 2006-08-15 10:08 .
drwxr-xr-x 3 root      root        4096 2006-08-14 17:50 ..
-rw-r--r-- 1 user      user       11391 2004-03-09 12:40 changelog.txt
drwxr-xr-x 4 user      user        4096 2004-03-09 12:41 httpdocs
-rw-r--r-- 1 user      user        2546 2004-03-09 12:40 INSTALL
-rw-r--r-- 1 user      user        2577 2004-03-10 01:38 INSTALL.mysql
-rw-r--r-- 1 user      user      234289 2004-03-09 12:40 libsqlmy.so
drwxr-xr-x 2 user      user        4096 2004-03-09 12:41 Manual
-rw-r--r-- 1 user      user         353 2004-03-09 12:40 manual.html
drwxr-xr-x 2 user      user        4096 2004-03-09 13:04 mysql_sql
-rw-r--r-- 1 user      user        4040 2004-03-09 12:40 README
-rwxr-xr-x 1 user      user      941456 2004-03-09 12:40 server_linux
-rw-r--r-- 1 user      user      251908 2004-03-09 12:40 sqlite.so
drwxr-xr-x 2 user      user        4096 2004-03-09 13:04 sqlite_sql
drwxr-xr-x 2 user      user        4096 2004-03-09 12:42 tcpquerydocs
-rwxr-xr-x 1 user      user        2465 2004-03-09 12:40 teamspeak2-server_startscript
```
everything ok - we own the files but the teamspeak user is the owner of the directory.
now the teamspeak users account:
```
user@server:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
...
teamspeak:x:1001:1001:,,,:/home/teamspeak:/bin/false
```
ok, the teamspeak user is not able to log on interactively.[/LIST]

[SIZE="4"]Initial Start and Setup:[/SIZE]
lets start the teamspeak server first time, test it and configure access to it.
[LIST=1][*]start the daemon first time. we will use a tool called **start-stop-daemon** for it:
```
user@server:~$ sudo start-stop-daemon --chuid teamspeak --chdir /opt/tss2_rc2 --start --exec /opt/tss2_rc2/server_linux
```
[*]you should see your server now in the process list:
```
user@server:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.4   1564   528 ?        S    10:07   0:00 init [2]
...
1001      3610  0.0  1.4  45280  1796 ?        Sl   10:07   0:03 /opt/tss2_rc2/server_linux
```
remember 1001 is the UID (User ID) of the user teamspeak [COLOR="Red"](somebody know why he wrote the UID instead of "teamspeak" ???)[/COLOR]
[*]if you point your web browser to the hosts ip address (or dns-name if you have one) followed by the port 14534 like
```
http://<server's ip>:14534/
```
you should get the web-interface of the teamspeak server.
[*]to configure the servers appearance (name, number of users etc) you need to log-on as **superadmin** - but whats the password ? you will find it in the newly created server log-file:
```
user@server:~$ cat /opt/tss2_rc2/server.log
---------------------------------------------------------------
-------------- log started at 14-08-06 18:11 -------------
---------------------------------------------------------------
14-08-06 18:11:29,ALL,Info,server,      Server init initialized
14-08-06 18:11:29,ALL,Info,server,      Server version: 2.0.20.1 Linux
14-08-06 18:11:29,WARNING,Info,SQL,     created table ts2_servers
14-08-06 18:11:29,WARNING,Info,SQL,     created table ts2_server_privileges
14-08-06 18:11:29,WARNING,Info,SQL,     created table ts2_channels
14-08-06 18:11:29,WARNING,Info,SQL,     created table ts2_channel_privileges
14-08-06 18:11:29,WARNING,Info,SQL,     created table ts2_clients
14-08-06 18:11:29,WARNING,Info,SQL,     created table ts2_bans
14-08-06 18:11:29,ALL,Info,server,      Starting VirtualServer id:1 with port:8767
14-08-06 18:11:29,WARNING,Info,SERVER,  Default VirtualServer created
14-08-06 18:11:29,WARNING,Info,SERVER,  admin account info: username: admin password: apapap
14-08-06 18:11:29,WARNING,Info,SERVER,  superadmin account info: username: superadmin password: sapsap
14-08-06 18:11:30,ALL,Info,server,      Server init finished
14-08-06 18:11:30,WARNING,Info,server,  TeamSpeak Server daemon activated

```
for example the teamspeak server generated the superadmin-password "sapsap". go to "superadmin login", log on with user "superadmin" and the password from the logfile and configure your teamspeak server.
**at least set the server name, the number of allowed users and create one user for yourself with admin rights.**
for further infos consult the documentation on the teamspeak-site, as this is beyond the scope of this how-to.
[*]check if teamspeak works, log on with your teamspeak client and your just created admin-user.
[*]stop your teamspeak server again with the help of **start-stop daemon**:
```
sudo start-stop-daemon --chuid teamspeak --chdir /opt/tss2_rc2 --stop --exec /opt/tss2_rc2/server_linux
```[/LIST]

[SIZE="4"]Securing and Logging:[/SIZE]
for security reasons we want to disable the web-interface and tie down the server-logfile (with the admins/superadmins passwords !).
[LIST=1][*]turn off the servers web-interface is accomplished thru editing the **server.ini** file in /opt/tss2_rc2. we use vi for example:
```
user@server:~$ sudo vi /opt/tss2_rc2/server.ini
```
we edit the line **HTTPServer Enabled=1** and replace the **1** with **0**.
while we are at it we change the logging parameters to get more infos in the logfile. replace all **0** in the **log**-section with **1**.
```
[Main Config]
...
HTTPServer Port=14534
HTTPServer Enabled=0
...
[log]
access_r=1
access_u=1
channel_registerred=1
channel_unregisterred=1
sa=1
chat=1
kick_server=1
kick_channel=1
```
[*]change the rights on the server-logfile that nobody despite root and the teamspeak-user can read it.
```
user@server:~$ sudo chmod 600 /opt/tss2_rc2/server.log
```
[/LIST]
you could recheck if everything works as expected by starting the teamspeak-daemon with the **start-stop-daemon**-commands above. the web-interface shouldnt be reachable anymore and you should get more logging in the **server.log**-file - you will need sudo to view this file now.

[SIZE="4"]Starting the daemon at boot-time:[/SIZE]
we want to start the teamspeak server at boot and stop it on shutdown.
[LIST=1][*]i just modified a copy of **/etc/init.d/skeleton** for this purpose:
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          teamspeak
# Required-Start:    networking
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:      S 0 1 6
# Short-Description: TeamSpeak Server Daemon
# Description:       Starts/Stops/Restarts the TeamSpeak Server Daemon
### END INIT INFO

set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="TeamSpeak Server"
NAME=teamspeak
USER=teamspeak
DIR=/opt/tss2_rc2
DAEMON=$DIR/server_linux
#PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME

# Gracefully exit if the package has been removed.
test -x $DAEMON || exit 0

d_start() {
        start-stop-daemon --start --quiet \
                --chuid $USER \
                --chdir $DIR \
                --exec $DAEMON \
                > /dev/null \
                || echo -n " already running"
}

d_stop() {
        start-stop-daemon --stop --quiet \
                --chuid $USER \
                --chdir $DIR \
                --exec $DAEMON \
                || echo -n " not running"
}

case "$1" in
  start)
        echo -n "Starting $DESC: $NAME"
        d_start
        echo "."
        ;;
  stop)
        echo -n "Stopping $DESC: $NAME"
        d_stop
        echo "."
        ;;
  restart|force-reload)
        echo -n "Restarting $DESC: $NAME"
        d_stop
        sleep 15
        d_start
        echo "."
        ;;
  *)
        echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
        exit 3
        ;;
esac

exit 0
```
put this (via sudo) into a file named **/etc/init.d/teamspeak**.
(EDIT)use **chown root:root /etc/init.d/teamspeak** and **chmod 775 /etc/init.d/teamspeak** to set the right permission (see below [cazsans post]("http://www.ubuntuforums.org/showpost.php?p=1453104&postcount=4") - thx cazsan)(/EDIT)
**sudo /etc/init.d/teamspeak start** should now start the daemon while **sudo /etc/init.d/teamspeak stop** should stop it.
[*]put the daemon into the service-levels via symbolic links:
```
cd /etc/rc0.d
sudo ln -s ../init.d/teamspeak K21teamspeak
cd /etc/rc1.d
sudo ln -s ../init.d/teamspeak K21teamspeak
cd /etc/rc2.d
sudo ln -s ../init.d/teamspeak S21teamspeak
cd /etc/rc3.d
sudo ln -s ../init.d/teamspeak S21teamspeak
cd /etc/rc4.d
sudo ln -s ../init.d/teamspeak S21teamspeak
cd /etc/rc5.d
sudo ln -s ../init.d/teamspeak S21teamspeak
cd /etc/rc6.d
sudo ln -s ../init.d/teamspeak K21teamspeak

```[/LIST]

[SIZE="4"]Further Security and advanced Paranoia:[/SIZE]
if your server runs other (mission-critical) services and/or you are paranoid (as i am) you could do several things:
[LIST][*]run the teamspeak daemon inside an chroot'ed environment
[*]run the teamspeak daemon in his own VM via VMWare-Server[/LIST]
i've done both, the former for some years and the later for some months and i didnt run into security problems (or didnt see any so this is no proof). i will write an article about my current setup later.



[COLOR="Blue"]**[SIZE="2"]so, have fun.[/SIZE]**[/COLOR]

---

### Post by roguetrick on 2006-08-17
Excellent guide, you've helped me learn alot.  One thing I'm not so sure about though, to get it to run on startup we use gedit(I belive its called) to create a file? One again many many thanks.

---

### Post by tja on 2006-08-23
> **roguetrick said:**
> Excellent guide, you've helped me learn alot.  One thing I'm not so sure about though, to get it to run on startup we use gedit(I belive its called) to create a file? One again many many thanks.
yeah if one has a desktop-ubuntu one could surely use all the desktop apps including gedit - i used vi (or one could use nano) because the guide is primarily for ubuntu-server with just command-line and no desktop at all. this aims at hosted servers in the net, like my own.
nice that it works for you.

have fun :D

---

### Post by cazsan on 2006-09-02
Hi there, any tip for autoboot:

Look at your priority scrip
As me, you should get wrong parameters for teamspeak, well if command : ```
sudo /etc/init.d/teamspeak start
``` doesn't work, follow my instructions

execute :
```
sudo chown root:root /etc/init.d/teamspeak
```
and then :
```
sudo chmod 775 /etc/init.d/teamspeak
```

You've done =D> 
Now the script would work like a charm :D

See you, 
Caz

---

### Post by MacboyX on 2006-09-02
! THANK YOU ! This is a very good guide.  I have installed it before but never thought of doing the stuff you did.  I have a Ubuntu Server 6.06 LAMP installation in a VMware enviroment. It works great on my local network but I can't get to the teamspeak server through my router and it is configure correctly since I have had it working before with my non-Vmware Ubuntu Server 5.10 box.   ](*,)   I have a 2Wire router that is very simple, so it is either on or it is not. Now I have heard of people having issues with Telnet Server after successfully installing it on Ubuntu server, so I wonder if there is anything else I should do? Any help or suggestions will be great.  Thanks for the great guide! Ubuntu roCkS!=D>

---

### Post by m00ndancer on 2006-10-15
Hi!

I'm new at this and are following your excellent how to. But, I have a serious problem when I try to start the deamon with start-stop-deamon i get this error message:

start-stop-daemon: Unable to start /opt/tss2_rc2/server_linux: Exec format error (Exec format error)

Any idea what causing it?

](*,) 

when I try to manually exec the teamspeak include script I get the error message that the says something like "cannot start the binary file in line 29: server_linux (in swedish so I'm not sure if that's the correct translation) 

any clues?

Best regards
Hans

---

### Post by tja on 2006-10-26
> **cazsan said:**
> Hi there, any tip for autoboot:

Look at your priority scrip
As me, you should get wrong parameters for teamspeak, well if command : ```
sudo /etc/init.d/teamspeak start
``` doesn't work, follow my instructions

execute :
```
sudo chown root:root /etc/init.d/teamspeak
```
and then :
```
sudo chmod 775 /etc/init.d/teamspeak
```

You've done =D> 
Now the script would work like a charm :D

See you, 
Caz

thx for that mate. :)

---

### Post by tja on 2006-10-26
> **MacboyX said:**
> ! THANK YOU ! This is a very good guide.  I have installed it before but never thought of doing the stuff you did.  I have a Ubuntu Server 6.06 LAMP installation in a VMware enviroment. It works great on my local network but I can't get to the teamspeak server through my router and it is configure correctly since I have had it working before with my non-Vmware Ubuntu Server 5.10 box.   ](*,)   I have a 2Wire router that is very simple, so it is either on or it is not. Now I have heard of people having issues with Telnet Server after successfully installing it on Ubuntu server, so I wonder if there is anything else I should do? Any help or suggestions will be great.  Thanks for the great guide! Ubuntu roCkS!=D>

hard to say without knowing your net.
first the vm should have "bridged" network - so its fully visible on the lan.
second thing is to open the now bridged hosts ip/ports for TS on the router. but this is very router specific so i cant help you there much.

---

### Post by tja on 2006-10-26
> **m00ndancer said:**
> Hi!

I'm new at this and are following your excellent how to. But, I have a serious problem when I try to start the deamon with start-stop-deamon i get this error message:

start-stop-daemon: Unable to start /opt/tss2_rc2/server_linux: Exec format error (Exec format error)

Any idea what causing it?

](*,) 

when I try to manually exec the teamspeak include script I get the error message that the says something like "cannot start the binary file in line 29: server_linux (in swedish so I'm not sure if that's the correct translation) 

any clues?

Best regards
Hans

hmm try to re-download teamspeak and compare sizes and md5-sums (dunno if the ts people show any on their site).
or - if you are on 64-bit - you must run the ts-server in a 32-bit chroot, like flash etc.

---

### Post by kuleali on 2006-10-26
good guide

---

### Post by TitanKing on 2006-11-21
If you get an error like this :

[PHP]/bin/sh^M: bad interpreter: No such file or directory[/PHP]

Try removing the "!" in this string in init.d/teamspeak, it worked for me, don't know why though.

[PHP]#! /bin/bash[/PHP]

Cheers,
Jason

---

### Post by UlixesTNT on 2007-02-18
How uninstall it once installed?

Thanks

---

### Post by mylescarrick on 2007-02-20
Don't forget that the easiest way to get the daemon to run at all runlevels in Ubuntu is simply:

```
sudo update-rc.d teamspeak defaults
```

---

### Post by Spin180pro on 2007-05-07
Awesome guide. I got TS up and running as expected. Thanks for the great tut!

I have run into a problem.

```
administrator@killhq:/tmp$ sudo /etc/init.d/teamspeak start
Starting TeamSpeak Server: teamspeak already running.
```

TS is not running. I was changing the server.ini and attempted a stop / start and got the above situation.

force-reload produces this:

```
administrator@killhq:/opt/tss2_rc2$ sudo /etc/init.d/teamspeak force-reload
Restarting TeamSpeak Server: teamspeak not running already running.
```

I don't see a *.pid in /var/run and I have no idea where to look for a *.lock file ... help!

```
root@killhq:/var/lib# sudo start-stop-daemon --chuid teamspeak --chdir /opt/tss2_rc2 --start --exec /opt/tss2_rc2/server_linux
Error, Either an old instance of teamspeak is still running, or
       an other application is using the tcpquery port!
Error, Server was not started!
```

One other question:

I modified the server.ini to bind to multiple ip's due to external users not being able to connect by noip.com address ... does this conflict with the ExternalIPDectection=1? Should I set that to 0 instead of 1 since I manually set external ip?

```
[Main Config]
BoundToIp1=127.0.0.1
BoundToIp2=192.168.1.2
BoundToIp3=***.***.***.***
ExternalIPDectection=1
```

I also am using the the latest beta version ... I assume that this guide works the same with the new version? I did a chmod +x on it ... do I need to do anything else to it?

Thanks,
     Scott ](*,)

---

### Post by btdown on 2007-07-01
Thank you for this tutorial. It was invaluable in setting up my ts server.

Could I impose on you to do one for a Ventrilo server? I tried to follow the same examples to set up ventrilo and it would not automatically start/stop by modifing the script. 

Thank you
BT

---

### Post by the red krawler on 2007-08-23
Great guide, helped me setup my TS2 server without too much trouble.

The only issue I did have was that I'm running 64bit, and TeamSpeak is 32bit. 

The solution?
sudo apt-get install libc6-i386 lib32stdc++6 lib32z1 ia32-libs lib32gcc1

Hope this helps anyone else out there who's followed the guide under 64bit and still cant get the thing to load :)

---

### Post by maitredede on 2007-08-28
A wonderfull tuto, but...

If I want to go further, like using mysql with TS, with a feisty ?

I've taken some parts of this tuto : [http://forum.teamspeak.com/showthread.php?t=37500]("http://forum.teamspeak.com/showthread.php?t=37500")

I've downloaded the libs, the server.ini is filled, the mysql db is OK, but I have a connection error... Grrr !

```
28-08-07 09:58:18,ALL,Info,server,      Server init initialized
28-08-07 09:58:18,ALL,Info,server,      Server version: 2.0.23.19 Linux
28-08-07 09:58:18,ERROR,All,SQL,        Database initialization error: EDatabaseError.dbExpress Error: Invalid Username/Password
28-08-07 09:58:18,ERROR,All,SERVER,     Start_Server: unable to open database

```

May I have to cheat with mysql ?

EDIT : Misconfiguration in server.ini... Please buy me some brain ;)

---

### Post by Symbolis on 2007-08-29
Very nice guide!

However, when attempting to start the daemon for the first time, I get the following error:

```
sudo start-stop-daemon --chuid teamspeak --chdir /opt/tss2_rc2 --start --exec /opt/tss2_rc2/server_linux
start-stop-daemon: Unable to start /opt/tss2_rc2/server_linux: Permission denied (Permission denied)
```

Any ideas? Running Ubuntu 7.04 desktop.

---

### Post by maitredede on 2007-08-29
> **Symbolis said:**
> Very nice guide!

However, when attempting to start the daemon for the first time, I get the following error:

```
sudo start-stop-daemon --chuid teamspeak --chdir /opt/tss2_rc2 --start --exec /opt/tss2_rc2/server_linux
start-stop-daemon: Unable to start /opt/tss2_rc2/server_linux: Permission denied (Permission denied)
```

Any ideas? Running Ubuntu 7.04 desktop.

chown all files and dir (including) in /opt/tss2_rc2 to user teamspeak (and its group). I've done it when I installed.

---

### Post by The_smiley on 2007-09-05
im running ubuntu fiesty desktop and having the exact same problem

```
sudo start-stop-daemon --chuid teamspeak --chdir /opt/tss2_rc2 --start --exec /opt/tss2_rc2/server_linux
start-stop-daemon: Unable to start /opt/tss2_rc2/server_linux: Permission denied (Permission denied)
```

---

### Post by maitredede on 2007-09-06
Here is my launch script /etc/init.d/teamspeak (owner root:root) :

```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          teamspeak
# Required-Start:    networking
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:      S 0 1 6
# Short-Description: TeamSpeak Server Daemon
# Description:       Starts/Stops/Restarts the TeamSpeak Server Daemon
### END INIT INFO

set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="TeamSpeak Server"
NAME=teamspeak
USER=teamspeak
DIR=/opt/tss2_rc2
DAEMON=$DIR/server_linux
#PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME

# Gracefully exit if the package has been removed.
test -x $DAEMON || exit 0

d_start() {
        start-stop-daemon --start --quiet \
                --chuid $USER \
                --chdir $DIR \
                --exec $DAEMON \
                > /dev/null \
                || echo -n " already running"
}

d_stop() {
        start-stop-daemon --stop --quiet \
                --chuid $USER \
                --chdir $DIR \
                --exec $DAEMON \
                || echo -n " not running"
}

case "$1" in
  start)
        echo -n "Starting $DESC: $NAME"
        d_start
        echo "."
        ;;
  stop)
        echo -n "Stopping $DESC: $NAME"
        d_stop
        echo "."
        ;;
  restart|force-reload)
        echo -n "Restarting $DESC: $NAME"
        d_stop
        sleep 15
        d_start
        echo "."
        ;;
  *)
        echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
        exit 3
        ;;
esac

exit 0

```

With this script, my TS Server is launched on startup, and killed on shutdown (like other services).

My TS Server is installer in /opt/tss2_rc2. All files under /opt/tss2_rc2 (including folder /opt/tss2_rc2) are owned by teamspeak:teamspeak (user and group created for TS, with shell=/bin/false).

---

### Post by al2cane on 2007-10-03
Running mine off a spare work PC on a desktop system, good guide tho, less confusing than most I've read.

---

### Post by BlackCow on 2007-10-21
Argh, I created a sepreate user call teamspeak like you said but for some reason if refuses to log into the user, it doesn't say wrong password it just takes the password and does nothing. ARGH >_<

It's annoying because everyone else is saying it all works, I thought I followed your instructions.

---

### Post by Symbolis on 2007-12-17
Just a note for those running the updated server file:

After extracting the main server stuff, move the file into the directory and change the permissions to set it as an executable.

If you have a GUI interface:

Right click on server_linux
Click 'Properties'
Click the 'Permissions' tab
Check the box beside "Execute:"

I don't recall, off the top of my head, the right terminal command for this, but I'm sure someone'll chime in. :)

---

### Post by MaxDSterling on 2007-12-26
> **TitanKing said:**
> If you get an error like this :

[PHP]/bin/sh^M: bad interpreter: No such file or directory[/PHP]

Try removing the "!" in this string in init.d/teamspeak, it worked for me, don't know why though.

[PHP]#! /bin/bash[/PHP]

Cheers,
Jason

The ^M is a control character found when copying directly from the forum.  The character is right after /bin/sh, hence the weird error

There are also ^M chars at line 11,12,and 22, at least those are the ones I've found.

---

### Post by Braytok on 2007-12-30
> **maitredede said:**
> chown all files and dir (including) in /opt/tss2_rc2 to user teamspeak (and its group). I've done it when I installed.

I did this too and so far its working but I was wondering if this is a security risk in any way?

I used:
```
sudo chown -hR teamspeak /opt/tss2_rc2
```

---

### Post by kendase3 on 2008-01-24
Hey thanks for the great how-to, but I was dinking around before reading the guide and attempted to run the server as root.  Though it said another application was using the port it needed and didn't work, I was wondering if I opened up any security holes by doing so, and if I did, how I might go about closing them.  I'd appreciate any feedback I could get as I'd rather not have to reinstall everything to ensure my settings are intact =/.

---

### Post by GoldenEye006 on 2008-02-21
10000 THX, for this nice working TUT ;)

---

### Post by 2010 on 2008-03-19
Hi there,

i get

```
sudo start-stop-daemon --chuid teamspeak --chdir /opt/tss2_rc2 --start --exec /opt/tss2_rc2/server_linux
start-stop-daemon: Unable to start /opt/tss2_rc2/server_linux: Permission denied (Permission denied)
```

I did:

```
sudo chown root:root /etc/init.d/teamspeak
sudo chmod 775 /etc/init.d/teamspeak
```

What`s wrong?

Thanks in advance!

---

### Post by AvWijk on 2008-04-19
I'm trying to get there with this tutorial :)

I booked progress by using **chown teamspeak /opt/tss2_rc2/***

```

root@phobos:/opt/tss2_rc2# chown teamspeak /opt/tss2_rc2/*
root@phobos:/opt/tss2_rc2# ls -la
total 1508
drwxr-xr-x 7 teamspeak root        4096 2008-04-20 02:12 .
drwxr-xr-x 3 root      root        4096 2008-04-20 02:07 ..
-rw-r--r-- 1 teamspeak teamspeak      7 2008-04-20 02:12 bad_names.txt
drwxr-xr-x 4 teamspeak root        4096 2008-04-20 02:07 httpdocs
-rw-r--r-- 1 teamspeak root        2601 2008-04-20 02:07 INSTALL
-rw-r--r-- 1 teamspeak root        3083 2008-04-20 02:07 INSTALL.mysql
-rw-r--r-- 1 teamspeak root      234289 2008-04-20 02:07 libsqlmy.so
-rw-r--r-- 1 teamspeak root       20507 2008-04-20 02:07 LICENSE
drwxr-xr-x 2 teamspeak root        4096 2008-04-20 02:07 Manual
-rw-r--r-- 1 teamspeak root         353 2008-04-20 02:07 manual.html
drwx------ 2 teamspeak root        4096 2008-04-20 02:07 mysql_sql
-rw-r--r-- 1 teamspeak root        3964 2008-04-20 02:07 README
-rw-r--r-- 1 teamspeak teamspeak   2048 2008-04-20 02:12 server.dbs
-rw-r--r-- 1 teamspeak teamspeak     77 2008-04-20 02:12 server.ini
-rwxr--r-- 1 teamspeak root      948232 2008-04-20 02:07 server_linux
-rw-r--r-- 1 teamspeak teamspeak   2622 2008-04-20 02:12 server.log
-rw-r--r-- 1 teamspeak root      251908 2008-04-20 02:07 sqlite.so
drwx------ 2 teamspeak root        4096 2008-04-20 02:07 sqlite_sql
drwxr-xr-x 2 teamspeak root        4096 2008-04-20 02:07 tcpquerydocs
-rwxr-xr-x 1 teamspeak root        2465 2008-04-20 02:07 teamspeak2-server_startscript
root@phobos:/opt/tss2_rc2# start-stop-daemon --chuid teamspeak --chdir /opt/tss2_rc2 --start -
-exec /opt/tss2_rc2/server_linux
TeamSpeak Server Daemon started with PID 4417



```

Just to make sure teamspeak is the owner of every file within the teamspeak directory.
IMPORTANT: Make also sure that the .sql files within \mysql_sql and \sqlite_sql are owned by teamspeak.

---

### Post by prepstyles on 2008-05-10
> **Braytok said:**
> I did this too and so far its working but I was wondering if this is a security risk in any way?

I used:
```
sudo chown -hR teamspeak /opt/tss2_rc2
```


That worked for me as well! Thanks!

---

### Post by minuxx on 2008-05-16
Thank you very much for this magnificent guide!
Set it up in no time :).
Mind that post on the 64bit Server Edition. Made my teamspeak run!

---

### Post by corey32 on 2008-06-14
Hello, this is my first time posting on the Ubuntu forums.

First off, wonderful guide. Even a new-comer like myself was able to set up the teamspeak 2 server in a very short amount of time. I did, however, run into one small problem. When I use this:
```

sudo start-stop-daemon --chuid teamspeak --chdir /opt/tss2_rc2 --start --exec /opt/tss2_rc2/server_linux
```

I receive the following error.

```
Error, Either an old instance of teamspeak is still running, or an other application is using the tcpquery port!
Error, server was not started!
```

I browsed the thread for help and thought I would check my process to see if an instance of teamspeak was running, and it was not.

```
ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.1  0.1   2844  1692 ?        Ss   18:43   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   18:43   0:00 [kthreadd]
... ...
corey     4350  0.0  0.1   8056  1524 ?        R    18:45   0:00 sshd: corey@pts
corey     4351  0.0  0.2   5512  2920 pts/0    Ss   18:45   0:00 -bash
corey     4377  0.0  0.0   2644  1008 pts/0    R+   18:55   0:00 ps aux

```

Any help would be appreciated. Thank you in advance.

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-08-17
This is an awsome tutoral!! thanks

To get this to work i needed to run ```
sudo chmod -R 775 /opt/tss2_rc2/
```witch just changes the file permissions in /opt/tss2_rc2 so that anyone can run or read them

this may make a small security hole,that anyone can now run teamspeak.But the other option is to change every thing in the file so that it is owned by the teamspeak user

you can use ```
cat /opt/tss2_rc2/server.log | grep pass*
```
too get just the 2 lines that your looking for in the log file

---

### Post by Drake2k on 2008-11-12
I understand that this thread is pretty old but I have a question.

I followed the steps to the letter and it 
**[SIZE="4"]WORKED PERFECT!!![/SIZE]**

So here is my question / problem.  I have a ventrilo server running on the same computer.  It no longer runs when the computers starts in the same way that TS is working now.  The only thing I did to get Vent to startup (other then the whole running as user ventrilo without having rights to log into the system like we did with the teamspeak user) is added the following code to /etc/init.d/rc.local inserted on line 2.

```
VENPATH=/home/ventrilo
VENBIN=$VENPATH/ventrilo_srv

su ventrilo -c "$VENBIN -f$VENPATH/ventrilo_srv -d"

renice -5 `cat $VENPATH/ventrilo_srv.pid`
```

Is there anything we did that would cause this to stop working?



Here is a copy of the entire /etc/init.d/rc.local

```
#! /bin/sh
VENPATH=/home/ventrilo
VENBIN=$VENPATH/ventrilo_srv

su ventrilo -c "$VENBIN -f$VENPATH/ventrilo_srv -d"

renice -5 `cat $VENPATH/ventrilo_srv.pid`

PATH=/sbin:/bin:/usr/sbin:/usr/bin
[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions

do_start() {
	if [ -x /etc/rc.local ]; then
		log_begin_msg "Running local boot scripts (/etc/rc.local)"
		/etc/rc.local
		log_end_msg $?
	fi
}

case "$1" in
    start)
	do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
```

---

### Post by Drake2k on 2008-11-12
Well, I don't know what the deal was. But it's working now.  I swear I didn't make ANY changes.  I did restart the system again just because I have to move it.  But it's working perfectly

Both Teamspeak & Ventrilo servers are running on the same machine without having to log in to the system.


whew.

---

### Post by dauthimaster on 2009-03-24
Something else to add for x64 users:

```
sudo apt-get install ia32-libs
```

This will give you the libraries teamspeak needs to run and allow to bypass messing with chroot.

Also, make sure your server.ini file and sqlite_sql (or mysql_sql) directory are owned by your teamspeak user, otherwise the server won't be able to run because it can't edit its databases.

---

### Post by twin_rotor on 2009-06-27
I'm a new user to Ubuntu and I'm having problems with TeamspeakRC2(current version) with 9.04.

I can either use the package manager or this tutorial to install and run the sever with no problems, unitill I reboot.

Once the machine is back up, the first thing I try is to connect via a client on two other computers.  No connection.  Then I try to access the Admin panel and get an error...  

I've tried manual commands to no avail.  I get the same errors listed through out this thread.  

You can leave it on for days and its fine.. Reboot, its stops working.. I use the package manager to remove, then reinstall and it works fine once setup..  You can also use the start - restart - and stop script before a reboot and they work fine..

I'm not sure what I need to list as errors or logs. I'll be happy to list whatever is needed to diagnose the problem.  At this poiint, its pretty much a stock install, beides what I've done in this ariticle(which is dlelted now, I think).

Any ideas?  

Thanks,
Ben

---

### Post by Gallager44 on 2009-08-11
I too am recieving this same problem.](*,)](*,)](*,)

> **corey32 said:**
> Hello, this is my first time posting on the Ubuntu forums.

First off, wonderful guide. Even a new-comer like myself was able to set up the teamspeak 2 server in a very short amount of time. I did, however, run into one small problem. When I use this:
```

sudo start-stop-daemon --chuid teamspeak --chdir /opt/tss2_rc2 --start --exec /opt/tss2_rc2/server_linux
```

I receive the following error.

```
Error, Either an old instance of teamspeak is still running, or an other application is using the tcpquery port!
Error, server was not started!
```

I browsed the thread for help and thought I would check my process to see if an instance of teamspeak was running, and it was not.

```
ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.1  0.1   2844  1692 ?        Ss   18:43   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   18:43   0:00 [kthreadd]
... ...
corey     4350  0.0  0.1   8056  1524 ?        R    18:45   0:00 sshd: corey@pts
corey     4351  0.0  0.2   5512  2920 pts/0    Ss   18:45   0:00 -bash
corey     4377  0.0  0.0   2644  1008 pts/0    R+   18:55   0:00 ps aux

```

Any help would be appreciated. Thank you in advance.

---

