---
title: "HOWTO: Accurate timekeeping on Ubuntu"
date: 2005-11-30
forum: Outdated Tutorials &amp; Tips
---

### Post by david_finlayson on 2005-11-30
This HOWTO will keep your system clock synchronized to standard time servers to an accuracy of +/- 0.01 seconds or better (even over dial-up).

[COLOR="Red"]WARNING 1: (Dual booters BEWARE) These program settings assume that only one program is controlling the clock. Pick one and only one. That includes alternative operating systems!!![/COLOR]

[COLOR="Red"]WARNING 2: (Dual booters BEWARE) These instructions assume that your hardware clock is in UTC (GMT) and not local time. [/COLOR]

**Step 1: Finding time servers.**

If you mainly use your computer while connected to the Internet, you should use the following time servers (unless your Internet service provider has one of their own, in which case substitute accordingly):

0.pool.ntp.org
1.pool.ntp.org
2.pool.ntp.org

See [http://www.pool.ntp.org/](http://www.pool.ntp.org/) to learn more about these special, public, dynamically assigned time servers.

If you are frequently off line when you use your computer (laptop or dial-up for example) you will need to look up the Static IP Addresses of 3 Stratum 2 servers here (again, substitute the static IP of your ISP's time server if that is available to you):

[http://ntp.isc.org/bin/view/Servers/WebHome]("http://ntp.isc.org/bin/view/Servers/WebHome")

Be sure to read the rules of engagement as each server will have different instructions. Often, all that is required is asking permission to synchronize your computer to their server via email.

**Step 2: If you are mainly connected to the network and your computer is usually powered up, follow these instructions:**

[LIST=1]
[*]Click System > Administration > Time and Date
[*]Manually set the time to the best of your ability (estimate)
[*]Click Select Servers... and fill in and select the NTP server addresses from above.
[*]Check “Periodically synchronize clock with Internet servers”
[*]Click Synchronize Now
[/LIST]

You're done! If your clock is very far from the true time it may take a while for the time to slew into sync. Read about ntpd to learn more about controlling your clock and keeping track of statistics.

**Step 2: If you are frequently off line or you power down your computer for several hours or more, follow these instructions**

Under this scenario, you are relying on your system and RTC clock to run without access to accurate time synchronization for hours or days. You can periodically log in to update the clocks, but once you log off (particularly when you power down) your clocks will start drifting.

In order to keep accurate time during these periods you will need to install chrony. Chrony is software designed to keep your computer's clocks synchronized even when you do not have access to the net. Every time you ARE connected to the net, chrony keeps track of the rate your clocks gain or lose time. When you log off or power down, chrony can apply a correction factor to your clocks to account for this drift until you next log on. (chrony handles all of this behind the scenes).

To install chrony you will need to remove the NTPD software that comes standard with Ubuntu. Since chrony and NTPD do the same thing, they cannot both be installed (by the way if you later get an always-on connection to the net, chrony works great under this scenario too).

To install chrony and remove the ntpd tools:

```
sudo apt-get install chrony
```

**Step 3 Update the chrony configuration file**

We are now going to tell chrony which time servers to use. We need a static IP address rather than the domain name because we cannot guarantee that we will have a network connection when chrony is launched (to do a DNS lookup on the server name).

```
sudo gedit /etc/chrony/chrony.conf
```

Replace the three lines starting with “server 0.pool.ntp.org...”

with the NTP IP numbers you got in Step 1: 

```

server 123.XXX.XXX.XXX offline minpoll 8
server 456.XXX.XXX.XXX offline minpoll 8
server 789.XXX.XXX.XXX offline minpoll 8

```

save the file and restart chronyd:

```
sudo /etc/init.d/chrony restart
```

If you don't turn your computer off for long periods of time (< 5 hours), then your done! When you log on chrony will slew your system clock to match the best time server available from your list. When you log off, chrony will attempt to adjust for system clock drift. Note that in this configuration your hardware clock is not tracked by chrony. So if you leave your computer off for a long period of time > 5 hours, you should log on first-thing and allow chrony to re-sync your system clock.

**Step 4: If you DO turn off your computer overnight.**

If you do turn off your computer for long periods of time, you can stop at step 3 but do not trust your system clock until you have had a chance to log on for 30-minutes or so to allow chrony to re-sync your clock.

Another option is to allow chrony to track the hardware clock in addition to the system clock. Then when you reboot, chrony knows how bad your hardware clock is and adjusts accordingly. This requires a modification that the Debian maintainer of chrony does not recommend. (Probably for newbie issues) However, it is the principal reason that chrony was written in the first place (chrony can even keep a lab of computers synchronized without any Internet connection at all, see the documentation).

First we need to disable the part of shutdown where hwclock saves the system time to the RTC clock. We want chrony to do this and we don't want hwclock to come along behind chrony and muck things up.

```
sudo gedit /etc/init.d/hwclock
```

change the following section of the shell script:

```

	stop|restart|reload|force-reload)
		#
		# Updates the Hardware Clock with the System Clock time.
		# This will *override* any changes made to the Hardware Clock.
		#
		# WARNING: If you disable this, any changes to the system
		#          clock will not be carried across reboots.
		#

		if [ "$HWCLOCKACCESS" != no ]; then
		    log_begin_msg "Saving the system clock disabled for chrony..."
		    if [ "$GMT" = "-u" ]; then
			GMT="--utc"
		    fi
		    /sbin/hwclock --systohc $GMT $HWCLOCPARS $BADYEAR
		    log_verbose_success_msg "Hardware Clock not updated to `date` for chrony."
                    log_end_msg 0
		else
		    log_verbose_warning_msg "Not saving System Clock"
		fi
		;;

```

to this (changes are highlighted in blue):

```

	stop|restart|reload|force-reload)
		#
		# Updates the Hardware Clock with the System Clock time.
		# This will *override* any changes made to the Hardware Clock.
		#
		# WARNING: If you disable this, any changes to the system
		#          clock will not be carried across reboots.
		#

[COLOR="Blue"]		# I disregarded the warning above and disabled this so that chrony 
                #could set the Hardware Clock at shutdown[/COLOR]
		if [ "$HWCLOCKACCESS" != no ]; then
		    log_begin_msg "Saving the system clock disabled for chrony..."
		    if [ "$GMT" = "-u" ]; then
			GMT="--utc"
		    fi
		    [COLOR="Blue"]#/sbin/hwclock --systohc $GMT $HWCLOCPARS $BADYEAR
		    log_verbose_success_msg "Hardware Clock not updated to `date` for chrony."[/COLOR]
                    log_end_msg 0
		else
		    log_verbose_warning_msg "Not saving System Clock"
		fi
		;;

```

Next we need to set up chrony to save the RTC adjustment data at shutdown

```
sudo gedit /etc/chrony/chrony.conf
```

Ensure that dumponexit is uncommented as follows:

```

# Dump measurements when daemon exits.
dumponexit

```

And that the rtcfile is being recorded:

```

# Specify the file where real-time clock data is stored.  To use this you
# must have enhanced real-time clock support compiled into your kernel.
# Comment out the next line if you do not.  Note: I have seen problems with
# the rtc on some motherboards.  Please file a bug if this bites you.
rtcfile /var/lib/chrony/chrony.rtc

```

In addition, if you are on a modem. Let's command chrony to save RTC data as soon as we log off. That way we reduce the odds of a power failure preventing chrony from writing the RTC data for our next boot (it can recover from this error with the previous boot's RTC adjustment):

```
sudo gedit /etc/ppp/ip-down.d/chrony
```

add the keywords dump and writertc as shown (changes in blue):

```

/bin/pidof chronyd > /dev/null || exit 0
KEY=$(awk '$1 ~ /^commandkey$/ { print $2; exit}' /etc/chrony/chrony.conf)
PASSWORD=`awk '$1 ~ /^'$KEY'$/ {print $2; exit}' /etc/chrony/chrony.keys`
/usr/bin/chronyc << EOF
password $PASSWORD
offline[COLOR="Blue"]
dump
writertc[/COLOR]
EOF
exit 0

```

Now restart chronyd:

```
sudo /etc/init.d/chrony restart
```

and do a reboot. Watch the messages for errors.

You should now be able to keep very accurate time even over reboots and for long periods without connection to the Internet. There are several options for tracking time using the chronyc console monitor. Of particular note are rtcdata (which shows the slew of the hardware clock), tracking (which shows the connection to time servers when online) and sources and sourcestats which show the statistics of the time servers you are connected to. There are other interesting details that can be found in the (friendly) chrony documentation.

[B]To learn more about how your computer keeps time and the protocols that accomplish time synchronization, I recommend reading the chrony documentation:
[/B]

[http://chrony.sunsite.dk/guide/chrony.html](http://chrony.sunsite.dk/guide/chrony.html)

It is written for human beings, unlike the NTP documentation which can be found here (for masochists):

[http://ntp.isc.org/bin/view/Main/DocumentationIndex](http://ntp.isc.org/bin/view/Main/DocumentationIndex)

---

### Post by andylinux on 2006-09-13
Pleae note my machine kept sycning with the local instead of the servers.  I was getting this message in my log file,

synchronized to LOCAL(0), stratum 10

I had to add "burt iburst" to the end of the my server lines to get my machine to not use the local,  So I edited my 
/etc/ntp.conf file and made my server lines look like this.  

server 0.north-america.pool.ntp.org burst iburst
server 1.north-america.pool.ntp.org burst iburst
server 2.north-america.pool.ntp.org burst iburst

After a few hours of work I came across this solution on this page.

[http://www.novell.com/coolsolutions/feature/15345.html](http://www.novell.com/coolsolutions/feature/15345.html)

Thanks,
Andy

---

