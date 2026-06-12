---
title: "Can anyone write me a super quick script?"
date: 2005-11-11
forum: Programming Talk
---

### Post by flipz on 2005-11-11
Hi all! I was hoping everyone can write me a script. :D 

I am a total newb, so it's not really something I could do unless someone gave me very detailed and explicit directions. Basically my problem is that my wireless card doesn't seem to completely function in Ubuntu. I have followed all the different tutorials, removed and reloaded the drivers, etc, etc, etc and nothing works. My card works fine when it boots up, but at some point (sometimes 30 seconds later, sometimes 24 hrs later) it just stops. I still have a full signal to my router, and I can still send packets, but nothing gets received. 

Anyways, I have found that if I just re-run the script that I use to initialize my card when I first boot up, it beings working again. So I was wondering if anyone can write me a script that will check to see if I have an internet connection, and if not to run that script.

I did a search and found an old post talking about it. The response was:

> You'd want it running as a daemon, sort of like an init script. Use an existing Init script as a reference: /etc/init.d/cupsys is a very clean one. 
Let's call it
/usr/local/bin/internetd
You'd also want a /etc/init.d/internetd, which is modeled off cupsys to start/stop internetd.
Your internet keepalive script should be an infinite loop with the following logic:
1. Check for internet access. Do so by pinging a well-known site, or by using regular expressions to parse ifconfig output. (Doesn't the first option sound SO much easier?)
A: YES: Do nothing
B: NO: Initiate an internet connection.
2. Sleep for x amount of time. Use the sleep or usleep command to do so. This is to prevent the script from going TOO quickly and slowing down the rest of your system! 1 second should be appropriate.


Unfortunatly that's not enough information for me to know what to do considering I would need step-by-step instructions, aka having it be written! lol. So can anyone write me a script that will ping google every so often (60 seconds?) and then if it doesn't get a response, to run the script that I have located at /home/flipz/acx100-0.2.0pre8_plus_fixes_57/scripts/start_net . 

Thanks for anyone who can help out! By the way, I'm on Ubuntu 5.10. Thanks again!!!

-flipz

---

### Post by audax321 on 2005-11-12
Just out of curiosity what wireless card do you have? I had similar problems with my Intel 2200 B/G and there is a fix here that might work for you if you have that particular card... [http://www.ubuntuforums.org/showthread.php?t=75612](http://www.ubuntuforums.org/showthread.php?t=75612) Just scroll down to read xMetaRidley's reply.

---

### Post by flipz on 2005-11-12
Hi audax,
I have the Netgear wg311v2.

Ubuntu recognized it on install and set it up with ndiswrapper and it works fine except for cutting out like I said! I went to ndiswrapper's wiki and followed the instructions to completely uninstall and re-install it. When that didn't work, I followed another guide that was highly recommended which involved doing everything manually. It works much better, but still cuts out.

While it is a rough work around, this script should fix my problems until I figure out something better!

Thanks,
-flipz

---

### Post by audax321 on 2005-11-12
Okay, I have never made an init script before so BEWARE!!! 

This is the /usr/bin/internetd script:

```

#!/bin/sh

# Script for /usr/bin/internetd to check for internet connection and if not present,
# execute the script in variable bring_interface_up

website_to_ping="www.google.com"
bring_interface_up="/home/flipz/acx100-0.2.0pre8_plus_fixes_57/scripts/start_net"
seconds_to_sleep="60"
number_of_times_to_ping="3"

#do not change the infinite_loop_value variable/constant
infinite_loop_value="1"
while [ "$infinite_loop_value" = "1" ];
do
	ping -c "$number_of_times_to_ping" "$website_to_ping"

	while [ "$?" = "0" ];
	do
		#nothing, but wait and check again
		sleep "$seconds_to_sleep"
		ping -c "$number_of_times_to_ping" "$website_to_ping"
	done

	#if loop is broken, execute script to bring interface up
	sh "$bring_interface_up"
	echo Interface Brought Up: $(date) >> "/tmp/internetd.log"
done

```



And this is the /etc/init.d/internetd script:

```

#!/bin/sh

# Init script to run /usr/bin/internetd as daemon and provide start/stop commands

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/bin/internetd
NAME=internetd
DESC="Interface Up/Down"

test -f $DAEMON || exit 0

set -e

. /lib/lsb/init-functions

start() {
	log_begin_msg "Starting $DESC: $NAME"
        start-stop-daemon --start --quiet --background -m --pidfile /var/log/internetd.pid --exec $DAEMON -- -F
        log_end_msg $?
}

stop() {
	log_begin_msg "Stopping $DESC: $NAME"
        start-stop-daemon --stop --quiet --pidfile /var/log/internetd.pid
        rm -f /var/log/internetd.pid
        log_end_msg $?
}

restart_force() {
	log_begin_msg "Restarting $DESC: $NAME"
        if start-stop-daemon --stop --quiet --pidfile /var/log/internetd.pid; then
                rm -f /var/log/internetd.pid
                start-stop-daemon --start --quiet --background -m --pidfile /var/log/internetd.pid --exec $DAEMON -- -F
        fi
        log_end_msg $?
}

case "$1" in
  start)
	start
    	;;
  stop)
	stop
        ;;
  restart|force-reload)
	restart_force
        ;;
  *)
        N=/etc/init.d/$NAME
        echo "Usage: $N {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

exit 0

```

I haven't tested these at all, so there could be typographical errors that might not let the execute... but give it a try and see what happens (hopefully nothing bad :) ). If anyone notices anything wrong with these or can improve it please do so. Also, after you copy the files to their locations make sure you set their permissions to 755.  And finally, make sure this path is correct:

/home/flipz/acx100-0.2.0pre8_plus_fixes_57/scripts/start_net

because the script in /usr/bin/internetd will execute it when a ping fails (it will ping three times to check for an internet connection).

---

### Post by audax321 on 2005-11-12
Just corrected an error in the /etc/init.d/internetd file so make sure you get the new version..

Oh and to start the scripts once you have them copied to /usr/bin and /etc/init.d just do the following:

sudo /etc/init.d/internetd start

to stop:

sudo /etc/init.d/internetd stop

to restart/force-reload:

sudo /etc/init.d/internetd restart
OR
sudo /etc/init.d/internetd force-reload

Edit: changed path from /usr/init.d to /etc/init.d  :)

---

### Post by flipz on 2005-11-12
Awesome!! Thanks!!!

Quick question (although I suppose I'll see it once I install it! lol) but will it be running in the background? Or in a terminal so that I could maybe look back at it and see how many times that day I got disconnected and just to confirm that it's still running?

Seriously audax, thank you so much!!!!!

-flipz

Edit: And in your commands to start/stop it, did you mean for the dir path to be /etc/init.d/ ?  :) I just started it up, we'll see how it goes!! *fingers crossed*

Edit 2: Well I installed different firmware for my card (again!), and have been online without being disconnected (from gaim at least) for almost 12 hours. But I don't know if it's because of your script or the new firmware. lol. I would guess your script though! So thanks. And I know now that it doesn't run in a terminal for me to see, but is there a way for me to know how many times it ran? Or if it had to?

Thanks again, you're me hero!!!  :-D

---

### Post by audax321 on 2005-11-12
For a log file of the number of times the interface has been brought up, add this line to /usr/bin/internetd after the line that says: sh "$bring_interface_up" but before the done (I'll edit the script in the post above if you just want to copy that).

echo Interface Brought Up: $(date) >> "/tmp/internetd.log"

you can change /tmp/internetd.log to any path you want and it will output the date/time the script to bring up the interface was run to the file internetd.log. /tmp is a good location because the log file will be removed after a reboot preventing it from getting huge after some time.

I'm glad its working for you and a little surprised, I almost always make retarded mistakes like forgetting a " or something that prevents a script from running the first time! :)

---

### Post by flipz on 2005-11-12
Alright, I got the logging setup! I'll keep you updated and let you know how it goes.  :)

Thanks again!

-flipz

Edit: Well I have to say, it works!!  :)

Here is part of my log. I added an echo earlier in the /usr/bin script too so that I could see that it was succesfully running. It replies with "ping success" if so. The script pinged successfully from 16:04 to 16:32 when it failed for the first time.

> ping success: Sat Nov 12 16:31:36 EST 2005
PING FAILED: Sat Nov 12 16:32:39 EST 2005
INTERFACE BROUGHT UP: Sat Nov 12 16:32:39 EST 2005
ping success: Sat Nov 12 16:32:39 EST 2005
Interface Brought Up: Sat Nov 12 16:32:42 EST 2005
Google pinged: Sat Nov 12 16:32:42 EST 2005
ping success: Sat Nov 12 16:33:41 EST 2005
Interface Brought Up: Sat Nov 12 16:33:49 EST 2005
ping success: Sat Nov 12 16:34:43 EST 2005


And as you can see, it was a success after that. So again, THANK YOU! The only problem is that it appears as if I have 2 different versions of the script running, because you see "INTERFACE BROUGHT UP" and "Interface Brought Up" at 2 different times. When I added in the "ping success" part I changed it to the all caps version. So I have since stopped the script and restarted it. We'll see next time it fails.

Thanks AGAIN!!!

-flipz

EDIT 2:
Well the script is working great, but the "stop" command doesn't seem to work. lol. It executes succesfully, but it's not actually stopping.

> ping success: Sat Nov 12 16:43:07 EST 2005
ping success: Sat Nov 12 16:43:39 EST 2005
ping success: Sat Nov 12 16:44:02 EST 2005
ping success: Sat Nov 12 16:44:42 EST 2005

I ran the stop command 3-4 times, and got [ok] each time, but that was at 16:40 and as you can see I'm still getting 2 different versions of the script running. lol. I'm sure a reboot will fix it, but I just wanted to point it out. 

By the way, I am NOT complaining!! lol. It does exactly what I need it to do!!!

---

### Post by audax321 on 2005-11-12
I'll look into why its not stopping... probably because of the infinite loop I have going on... try this:

sudo /etc/init.d/internetd stop
sudo killall internetd

That should kill all running instances of the script.

EDIT:  Okay, the start-stop-daemon command to stop the process was wrong. I updated the /etc/init.d/internetd file and it should work now :)

---

### Post by flipz on 2005-11-13
Great work audax. It works better than I thought, and I've actually stopped looking for a fix to my problem, because this was it!!!  :)

> ping success: Sun Nov 13 11:42:10 EST 2005
ping success: Sun Nov 13 11:43:12 EST 2005
PING FAILED: Sun Nov 13 11:44:46 EST 2005
INTERFACE BROUGHT UP: Sun Nov 13 11:44:46 EST 2005
Google pinged: Sun Nov 13 11:44:48 EST 2005
ping success: Sun Nov 13 11:44:48 EST 2005

**THANK YOU!!!!**

I don't even notice it happening! I'll buy you a case of beer, mountain dew, coffee, whatever your drink of choice is! lol

-flipz

---

### Post by audax321 on 2005-11-13
Glad to help. I've actually been wanted to learn how to make daemons so thanks for having a good problem to learn from ;)

---

### Post by HumBug on 2006-02-26
I tried this script also but it doesn't work yet. I changed some things:

----------------------
#!/bin/sh

# Script for /usr/bin/internetd to check for internet connection and if not present,
# execute the script in variable bring_interface_up

website_to_ping="192.168.1.1"
bring_interface_up="ifup wlan0"
seconds_to_sleep="60"
number_of_times_to_ping="3"

#do not change the infinite_loop_value variable/constant
infinite_loop_value="1"
while [ "$infinite_loop_value" = "1" ];
do
	ping -c "$number_of_times_to_ping" "$website_to_ping"

	while [ "$?" = "0" ];
	do
		#nothing, but wait and check again
		sleep "$seconds_to_sleep"
		ping -c "$number_of_times_to_ping" "$website_to_ping"
	done

	#if loop is broken, execute script to bring interface up
	sh "$bring_interface_up"
	echo Interface Brought Up: $(date) >> "/tmp/internetd.log"
done
---------------------------------

So website_to_ping="192.168.1.1" is my routers IP, and i think the problem lies here:
bring_interface_up="ifup wlan0"
Can a simple command be used instead of a script and is this the correct command to enable wlan0 again?

---

### Post by audax321 on 2006-02-26
This should fix it (since you're running a command rather than a script like the other person):

```

#!/bin/sh

# Script for /usr/bin/internetd to check for internet connection and if not present,
# execute the command in variable bring_interface_up

website_to_ping="192.168.1.1"
bring_interface_up="ifup wlan0"
seconds_to_sleep="60"
number_of_times_to_ping="3"

#do not change the infinite_loop_value variable/constant
infinite_loop_value="1"
while [ "$infinite_loop_value" = "1" ];
do
	ping -c "$number_of_times_to_ping" "$website_to_ping"

	while [ "$?" = "0" ];
	do
		#nothing, but wait and check again
		sleep "$seconds_to_sleep"
		ping -c "$number_of_times_to_ping" "$website_to_ping"
	done

	#if loop is broken, execute command to bring interface up
	"$bring_interface_up"
	echo Interface Brought Up: $(date) >> "/tmp/internetd.log"
done

```

I modified the script a little to work with a command (changed line 25 from sh "bring_interface_up" to just "$bring_interface_up"). The original one was working with a script and so needed the sh, but with a command you don't. So the command it was running was "sh ifup wlan0" which isn't right. Now it will run just "ifup wlan0". Also make sure you run this script as root. So when you start the daemon:

```

sudo /etc/init.d/internetd start

```

otherwise ifup won't be able to do anything useful and will just give an error to run it as root.

Also, I'm not sure about this, but you probably want to make sure that if you are setting website_to_ping to 192.168.1.1 and it is a router that it will respond to your ping. Some routers tend to ignore pings. Otherwise use an actual website.

---

### Post by HumBug on 2006-03-02
Yup, removing "sh" did the trick. It's working fine now. Thx!

---

