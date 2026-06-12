---
title: "ShoutCast as Service on Boot"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Korijn on 2008-05-21
I download sc_serv from the shoutcast website and I know how to start it manually (double clicking it, doh). The problem is I'd like it to either run in the background from the moment I switch on the computer or it should be possible for others to send some sort of signal to this pc which would make shoutcast start. I looked into services, but I am afraid I just didn't understand the whole shortcut-in-/etc/rcS/ thing. So yeah... anyone willing to help me? If you have an easier solution than the two things I've got above then please tell me! :) Thanks alot for the help.

---

### Post by Cypher on 2008-05-21
Create a file in /etc/init.d called "shoutcast" which will be the script that will startup the service. You can look at the other files in there for guidance. Look at the smallest one to create your own version.

Now in the /etc/rc5.d/ create a symlink to the newly created file like
```

sudo ln -s ../init.d/shoutcast S80shoutcast

```
Now everytime the PC boots up the service will start up automatically..

---

### Post by Korijn on 2008-05-22
Well, I created the file and link. This is what I put inside /etc/init.d/shoutcast, is it alright? I don't want the computer to fail during boot. xD

```
#!/bin/sh

# This starts shoutcast... hopefully

/bin/shoutcast/sc_serv_1.9.8_Linux/sc_serv
```

---

### Post by Cypher on 2008-05-22
You might have better luck taking a look at the file /etc/init.d/skeleton. It's a generic script. So first, copy that to a file called shoutcast, then modify the NAME variable to the exeuctable. Setup any arguments to the program in DAEMON_ARGS.

Once you've made your modifications, try it out with
```

sudo /etc/init.d/shoutcast start

```
If that works and nothing bad happens, you can then create the symlink like I previously suggested and reboot the machine.

---

### Post by Korijn on 2008-05-22
It doesn't work!

This is what I get when I try it out:
```
korijn@korijn:/etc/init.d$ /etc/init.d/shoutcast start
bash: /etc/init.d/shoutcast: Permission denied
korijn@korijn:/etc/init.d$ sudo /etc/init.d/shoutcast start
sudo: /etc/init.d/shoutcast: command not found
```

The file shows up in black if I use 'ls' in the terminal, unlike the other files which appear in a green font.

Here's the file (the modified part):
```
#!/bin/sh
### BEGIN INIT INFO
# Provides:          shoutcast
# Required-Start:    
# Required-Stop:     
# Default-Start:     
# Default-Stop:      
# Short-Description: Starts shoutcast
# Description:       See short-description
### END INIT INFO

# Author: Korijn van Golen <korijn@gmail.com>

# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/usr/sbin:/usr/bin:/sbin:/bin
DESC="ShoutCast Server"
NAME=sc_serv
DAEMON=/bin/shoutcast/sc_serv_1.9.8_Linux/$NAME
DAEMON_ARGS=""
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/shoutcast
```

---

### Post by Cypher on 2008-05-23
You need to make the file an executable with
```

sudo chmod 755 /etc/init.d/shoutcast

```

---

### Post by Nythain on 2008-05-25
you also need a sudo

sudo /etc/inid.d/shoutcast start | stop | restart

---

### Post by Korijn on 2008-05-27
Alright, I got this working. Now I am unable to point shoutcast to the correct configuration file. I presume I can't place it in init.d (doesn't seem very smart to me, anyways). So how do I get that to work?

Here's the script:

```
#!/bin/sh
# Fire up sc_serv

case "$1" in
'start')
	/home/korijn/shoutcast/sc_serv
	# this works but it does not
	# find the configuration file
	# sc_conf in the same directory
	# (because it's not run from there?)
	;;
'stop')
	killall sc_serv
	;;
'restart')
	killall sc_serv
	/home/korijn/shoutcast/sc_serv
	;;
*)
	echo "Usage: $0 { start | stop | restart }"
	;;
esac
exit 0
```

---

### Post by Korijn on 2008-07-15
bump?

I can start shoutcast in background mode

```

> ./sc_serv &

```

but that won't work if I issue that command during boot. Because everytime I shut down, I see the whole shoutcast output on screen before the computer switches off.

Also, the configuration file isn't used, using the startup script above.

What should I do about this?

---

### Post by mr.prozac on 2008-10-24
i don't know if i should bump this thread or make a new one, but i have almost the same issue. I'm trying to install shoutcast as a service so i gan put up my media server.

I'm using:
MPD (as back-end)
Jinzora
Shoutcast

I've installed the lastest shoutcast and runs perfectly, but when i close the SSH session Shoutcast shuts down.

I've followed all the steps above. I've made a new file in the /etc/init.d/ folder and put the following code in it.
```
#!/bin/sh
### BEGIN INIT INFO
# Provides:          shoutcast
# Required-Start:    
# Required-Stop:     
# Default-Start:     
# Default-Stop:      
# Short-Description: Starts shoutcast
# Description:       See short-description
### END INIT INFO

# Author: Korijn van Golen <korijn@gmail.com>

# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/usr/sbin:/usr/bin:/sbin:/bin
DESC="ShoutCast Server"
NAME=sc_serv
DAEMON=/home/oguzhan/sc_serv/$NAME
DAEMON_ARGS=""
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/shoutcast
CONFIG_FILE=/home/oguzhan/sc_serc/sc_serv.conf
#!/bin/sh
# Fire up sc_serv

case "$1" in
'start')
	/home/oguzhan/sc_serv/sc_serv
	# this works but it does not
	# find the configuration file
	# sc_conf in the same directory
	# (because it's not run from there?)
	;;
'stop')
	killall sc_serv
	;;
'restart')
	killall sc_serv
	/home/oguzhan/sc_serv/sc_serv
	;;
*)
	echo "Usage: $0 { start | stop | restart }"
	;;
esac
exit 0
```

When i try to run the following command i get the following error:
**/etc/init.d/shoutcast start**

error:
```
-bash: /etc/init.d/shoutcast: /bin/sh^M: bad interpreter: No such file or directory

```

Could some give me a push in the right direction please?

---

### Post by Korijn on 2008-10-25
In the end, I got this to work by installing Webmin on the linux server. It features a menu you can use to manage startup scripts. I found it easier to add a script for shoutcast that way. It worked but it would fire from whatever directory the system was at and therefore not find the configuration file. When shutting down the server it would also not exit properly.

I have learned a lot about scripts in Linux the past few months but I am currently in the middle of an exam week so I can't take the time to produce a decent script right now.

If you remind me next week I might write something up since my server could use an updated properly working script. :)


Basically: write a script using the skeleton file mentioned earlier as reference, place it in the correct folder and link to it properly (also mentioned above). That should do the trick. The script just needs to be flawless.

---

### Post by Det0Nat3 on 2008-11-20
Has anyone figured this out, I have a similar problem but slightly different. I use shoutcast to broadcast my DJ mix but I now have it setup as a relay from another station (for when I am not mixing) what I am trying to do is build a start script that will start/stop shoutcasts ./sc_serv with two different config files. one for relaying and one for my mixing. but the problem is I have no idea how to write scripts.

---

### Post by AngryMallard on 2009-01-17
Has anyone figured out the problem with the service locating the correct config file? When I run 

```
sudo /etc/init.d/shoutcast start
```

I also get

```
[conf] Couldn't find sc_serv.conf -- assuming defaults
```

The server starts fine, it's just that I can't get it to find the config file even if I place it in /etc/init.d.

---

### Post by pab10 on 2009-03-09
got to specify full path of config file as well

startproc -u username /path/to/sc_serv /path/to/sc_serv.conf > /dev/null 2>&1 &


[http://forums.opensuse.org/programming-scripting/388318-shoutcast-startup-script-2.html](http://forums.opensuse.org/programming-scripting/388318-shoutcast-startup-script-2.html)

not tested myself yet but...

---

### Post by pab10 on 2009-03-09
now what I want to know is does sc_serv work under xinetd...

I understand apache does not... might be wrong... ;)

---

### Post by pab10 on 2009-03-10
> **pab10 said:**
> got to specify full path of config file as well

startproc -u username /path/to/sc_serv /path/to/sc_serv.conf > /dev/null 2>&1 &


[http://forums.opensuse.org/programming-scripting/388318-shoutcast-startup-script-2.html](http://forums.opensuse.org/programming-scripting/388318-shoutcast-startup-script-2.html)

not tested myself yet but...

there is no startproc in ubuntu... its a red-hat/suse style thing...

but the command line is good if you just drop the startproc -u username bit. It stops output going to terminal with the output redirects.

I set the guid and suid to get the process to run as non-root user, I think thats right... chown 6751 owner is non supervisor status.

[http://forums.winamp.com/showthread.php?threadid=303010](http://forums.winamp.com/showthread.php?threadid=303010)

---

### Post by Siggma on 2009-09-03
Yawl missed it still. I didn't use start-stop-daemon with this binary because of the way it writes output but it will probably work with a little tweaking. To get it to release the console we redirect it's output to the big bucket in the sky so it will release the terminal and use an "&" to fork it to the background. With a few more changes you can add a PID file then alter the stop routine to kill the PID instead of looking for the process. With more tweaking you can save the output to a log file. 

This version will fail to start the program if run a second time because the port is already used. If it fails just use the "restart" option. If it's a huge deal to you, reply and I'll add a PID file and modify the stop command and maybe even add a logfile. But there won't be much in the thing.

The downside of this script is that it runs as root. If there are any requests I'll make a better version that uses start-stop-daemon and an appropriate unprivileged user. If you want we can even chroot it for better security.

```

#!/bin/sh
#
# Init script for SHOUTcast
# by caraoge, modified to work correctly by Thomas R Bailey
# Last edited Sept 3 2009

# Set config to config file location
# set daemon to sc_serv location
############################################################################
##  CHANGE THESE VALUES to match your setup
## CONFIG is the fully qualified location of your config file
## DAEMON is the fully qualified location of the sc_serv binary
## Note, the script will look for sc_serv and sc_serv.conf in /usr/lib/shout
############################################################################
CONFIG="/usr/lib/shout/sc_serv.conf"
DAEMON="/usr/lib/shout/sc_serv"

############# Don't fiddle below this line ##############
# Check for SHOUTcast binary
test -f $DAEMON || exit 0

# The init commands
case "$1" in
        start)
                echo "Starting SHOUTcast server..."
                $DAEMON $CONFIG  > /dev/null 2>&1 &
                ;;
        stop)
                echo "Stopping SHOUTcast server..."
                kill -9 `ps -C sc_serv -o pid --no-headers`
                ;;
        restart)
                echo "Stopping SHOUTcast server..."
                kill -9 `ps -C sc_serv -o pid --no-headers`
                echo "Starting SHOUTcast server..."
                $DAEMON $CONFIG  > /dev/null 2>&1 &
                ;;
        *)
                echo "usage: /etc/init.d/shoutcast"
                echo "$0 {start | stop | restart}"
                exit 1
                ;;
esac

```

Change the values for CONFIG and DAEMON so they point to your server and config and save the above to /etc/init.d/shoutcast

If it won't run do this:
```
chmod +x /etc/init.d/shoutcast
```

---

### Post by mikelet on 2009-11-28
@Siggma
I'd like that update! I run different stations from the same server, and it's painful restart all the single instances!

Thank you plenty

Mikelet

P.S. Hey! It's my first post! Wooha!, let's take a look 'round here!

---

### Post by crcrjbod on 2011-01-17
sorry im new here, so sorry for this huge bump
 im active mostly on linuxquestions.org.
but i saw your script here.
and was wondering if you would be able to add a pid and logfile redirection to it. 
if you can of course. i wouldn't want to impose. as im sure i would be able to figure it out on my own eventually :P

---

### Post by digihlp on 2011-04-20
My script like yours works great changed the parms
################################################## ##########################
CONFIG="/home/ces/shoutcast/sc_serv.conf"
DAEMON="/home/ces/shoutcast/sc_serv"

############# Don't fiddle below this line ##############

---

