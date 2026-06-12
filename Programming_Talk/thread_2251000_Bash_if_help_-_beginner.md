---
title: "Bash if help - beginner"
date: 2014-11-01
forum: Programming Talk
---

### Post by Harpz on 2014-11-01
New to bash / linux scripts and am trying to get my head around multiple if statements but seem to be failing miserably :(

At the moment I have managed to write a few simple scripts that check to see if a process is running or a smart test is running and act accordingly, but I cant seem to get my head around how to combine them. :(

Process check:
```
name of SnapRAID process
PROCESS=$"[s]napraid"
          # Check if snapraid is running
                if ps aux | grep $PROCESS >/dev/null
                then
                   echo "SnapRAID Running"
                   else
                   echo "SnapRAID NOT Running"
                fi


```

SMART Check:
```

#! /bin/bash

for disk in {a..k}
do
        # Check if smartctl is currently running a self test
        if [ $(/usr/sbin/smartctl -a /dev/sd$disk | grep -c "Self-test routine in progress") = 0 ]; then
                   echo "SMART Tests NOT running"
                   else
                   echo "SMART Tests Running"
       fi
done

```

The idea for the final script is that if either snapraid or a smart test are working / underway an email is sent and the system isn't shut down, but If snapraid and smart arnt running then an email is sent and the system is shut down.

I know how to send the email using mutt but i can t get my head around multiple ifs, i have the following so far:

```

# Name of SnapRAID process
PROCESS=$"[s]napraid"

for disk in {a..k}
do
        # Check if smartctl is currently running a self test
        if [ $(/usr/sbin/smartctl -a /dev/sd$disk | grep -c "Self-test routine in progress") = 0 ]; then

                # Check if snapraid is running
                if ps aux | grep $PROCESS >/dev/null
                then
                   echo "SnapRAID or SMART Tests NOT running"
                   else
                   echo "SnapRAID or SMART Tests Running"
                fi
       fi
done

```

I know I'm missing something stupid and my knowledge is what's holding me back so any help is greatly appreciated.

---

### Post by Lars Noodén on 2014-11-01
When you make a numeric comparison, you'll want **-eq** instead of the equal sign, =, which is for strings.  

Check the manual page for [test](http://manpages.ubuntu.com/manpages/utopic/en/man1/test.1posix.html) for the full details on comparisons.

---

### Post by Harpz on 2014-11-01
> **Lars Noodén said:**
> When you make a numeric comparison, you'll want **-eq** instead of the equal sign, =, which is for strings.  

Check the manual page for [test](http://manpages.ubuntu.com/manpages/utopic/en/man1/test.1posix.html) for the full details on comparisons.

Thanks for the reply would you mind expanding upon what you said, the scripts work as expected on there own, just cant get my head around how to get them to work together?

---

### Post by Harpz on 2014-11-08
I solved it with the following, I run it via cron hourly between 1-7am. It checks to see if the SnapRAID process is running, then it will see if  any smartctl tests are running, and finally if will ping the media centre to see if its up.
If nothings running and the media centre's off it will shutdown the server.

```
#!/bin/bash
# Variables
PROCESS="[s]napraid"
PTMP=/"tmp/ptmp"
STMP="/tmp/stmp"
EMAIL="mymail@gmail.com"
SHUTDOWN_TEMP="/tmp/shutdown_tmp"
SERVERIP="192.168.1.165"
PINGTEST="/tmp/ping"
PINGTMP="/tmp/pingtmp"

# Check to see if SnapRAID process is running
echo "Checking for SnapRAID process" > $PTMP
ps aux | pgrep -c $PROCESS >> $PTMP

# Check if any smartctl tests are runnng
echo "Checking for running  SMART tests" > $STMP
# Disk range
for disk in {a..k}
do
/usr/sbin/smartctl -a /dev/sd$disk | grep -c "Self-test routine in progress" >> $STMP
done

# Ping media centre to see if its up
echo "Status of media centre" > $PINGTMP
/bin/ping -c 3 $SERVERIP > $PINGTEST
if [ $? -eq 0 ]
then
echo "1" >> $PINGTMP
else
echo "0" >> $PINGTMP
fi

# Compare the tmp files to see if the process, media centre or tests are running
if
grep '1' /tmp/ptmp || grep '1' /tmp/stmp || grep '1' /tmp/pingtmp
then
echo "Somethings running"
else
echo "NOTHING'S running"
echo "SnapRAID has completed it's work, no S.M.A.R.T tests are running and the media centre is down." >> $SHUTDOWN_TEMP
echo "" >> $SHUTDOWN_TEMP
echo "System Uptime..." >> $SHUTDOWN_TEMP
/usr/bin/uptime >> $SHUTDOWN_TEMP
echo "" >> $SHUTDOWN_TEMP
echo "Last 50 lines of syslog..." >> $SHUTDOWN_TEMP
echo "" >> $SHUTDOWN_TEMP
/usr/bin/tail -50 /var/log/syslog >> $SHUTDOWN_TEMP
/usr/bin/mutt -s "Altair - Sever shut down in 60 seconds." harpz1907@gmail.com < $SHUTDOWN_TEMP
rm $PTMP && rm $STMP && rm $SHUTDOWN_TEMP && rm $PINGTEST && rm $PINGTMP
/sbin/shutdown -h +1 "Server shuttung down in 60 seconds"
fi

exit

```

As I learn more I dare say I can clean up the code, but it works and I'm happy with my first attempt.

---

