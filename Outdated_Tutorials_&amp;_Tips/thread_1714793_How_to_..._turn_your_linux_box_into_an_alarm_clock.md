---
title: "How to ... turn your linux box into an alarm clock by writing your own init script"
date: 2011-03-25
forum: Outdated Tutorials &amp; Tips
---

### Post by JohnFH on 2011-03-25
[CENTER]**[SIZE="4"][COLOR="Blue"]How to ... turn your linux box into an alarm clock by writing your own init script[/COLOR][/SIZE]**[/CENTER]

**[SIZE="3"][COLOR="Blue"]Problem[/COLOR][/SIZE]**
You would like to implement an alarm clock that wakes you up by playing your favourite music or radio station.  Furthermore, the alarm clock should meet the following criteria:
[LIST]
[*]The alarm clock should not rely on the system being on all the time, ie. the system should turn on at the right time from either standby or switched off.
[*]The alarm should repeat so there's no need to remember to set the alarm every day.
[*]It should be easy to configure things like volume, radio station, music playlist, how often it is played, etc.
[*]It should not interfere with your day-to-day usage of the system, eg. you should at least be able to turn on the system, work on it, and turn if off without having to remember to reset the alarm.
[/LIST]

This alarm clock idea is not particularly new or ground-breaking but after quite a bit of searching I couldn't find anything that met all the requirements above, and I also wanted an excuse to do some more bash scripting and in particular learn how to write my own init script.  Even if you don't want an alarm clock you may still find this tutorial of some use if you want to learn more about writing your own init script.  If you are not interested in how the alarm clock works then you can ignore any of the implementation details (ie. skip most of this post) and go straight to the "Installing the alarm clock" section.

I've attached the files needed to configure and run the alarm clock, but for the purpose of this tutorial I'll pick out some potentially interesting implementation details. 

[SIZE="4"][COLOR="blue"]**Implementation: How the system is woken up**[/COLOR][/SIZE]
This tutorial uses the ACPI real time clock (RTC) alarm BIOS feature that is present on most motherboards.  For more details on ACPI Wakeup, see [[COLOR="RoyalBlue"]http://www.mythtv.org/wiki/ACPI_Wakeup[/COLOR]]("http://www.mythtv.org/wiki/ACPI_Wakeup").
The installation I am using is the LTS version, Ubuntu 10.04 and that allows the RTC time to be set by writing to /sys/class/rtc/rtc0/wakealarm.  The difficulty is that the file expects the date-time format to be the number of seconds since 1970 - not very user friendly!  The way around this is to use the date command in the example below.

To set the precise wake up time of 8:37am tomorrow morning:
```

wakeuptime=`date -d "8:37am tomorrow" +%s`
sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sudo sh -c "echo $wakeuptime > /sys/class/rtc/rtc0/wakealarm"

```

To check that the correct date/time is set in the BIOS:
```
grep alrm_[td] /proc/driver/rtc
```

[COLOR="Blue"][SIZE="4"]**Implementation: How to use a bash configuration file**[/SIZE][/COLOR]
I don't particularly want to delve into my init script to change things like the alarm volume, music playlist, or days on which the alarm is to run, so I've used a bash configuration file to keep options that are often changed separate from the main code that I want to protect.  There's no need to write your own parser for your configuration file if your configuration file is already a valid bash script.  Use '.' to load it ....

The following code sample will check that you have either a system configuration file (under /etc/) or one in your home directory.  Also any values specified in the config file in your home directory will take precedence over any values in the system config file.  To load your configuration file into your main script file:
```

SYSTEM_CONFIG_FILE=/etc/alarmclock/alarmrc
HOME_CONFIG_FILE=/home/john/.alarmrc

if [ ! -r $SYSTEM_CONFIG_FILE -a ! -r $HOME_CONFIG_FILE ]; then
    echo "Error.  No config file found.  Cannot continue." >&2
    exit 1
fi

[ -r $SYSTEM_CONFIG_FILE ] && . $SYSTEM_CONFIG_FILE
[ -r $HOME_CONFIG_FILE ] && . $HOME_CONFIG_FILE

```

[COLOR="Blue"][SIZE="4"]**Implementation: How to set the initial volume level**[/SIZE][/COLOR]
The volume level specified in the config file is dependent on your hardware.  To find out the volume integer range for your system:
```
amixer get Master | grep Limits
```
Then change the volume config value (ALRM_VOLUME) to be a value in this range.

Before the alarm is played, the volume is set by the following code in the init script:
```
[ "$ALRM_VOLUME" != "" ] && amixer -q set Master $ALRM_VOLUME
```

[SIZE="4"][COLOR="Blue"]**Setting the alarm**[/COLOR][/SIZE]
The alarm is set for the first time by:
```
sudo service alarmclock set
```
Confirmation of the alarm time is then displayed but you can check this at any time by:
```
service alarmclock status
```
which will also display the relevant cronjob entry.  Note that this does not need to run with root privileges.

The implementation details of setting the alarm involve writing the alarm time to the system wakealarm file, setting up a cronjob to play the alarm and writing to the status file to indicate that the alarm is active.  There is an in-built delay of 90 seconds to allow the system to wakeup before the alarm is played.  The alarm time specified in the config file is the time the alarm is played and the system is woken up 90 seconds earlier.  Writing to the status file to indicate the alarm is active, is useful when setting once-off alarms.  Every time the alarm is played the status is cleared to being Inactive and then the alarm is reset.  The alarm time is only reset if the alarm is not once-off or the alarm status is active, ie. the alarm time will not be cleared if the alarm hasn't been played yet or if the alarm is not just a once-off one.

For an alarm that repeats each day you can set the specific days in the config file by a comma separated list of integers where 1=Monday up to 7=Sunday.  For example, to play your alarm only on Saturdays and Sundays (why you would want to do this, I don't know!), change the value in the config file to:
```
ALRM_DAYS=6,7
```

[COLOR="Blue"][SIZE="4"]**Playing the alarm**[/SIZE][/COLOR]
Playing the alarm at the right time is controlled by a cronjob entry.  The actual command to play the alarm is:
```
sudo /etc/init.d/alarmclock play
```
The command needs root privileges to be able to set a new alarm for the next day.  Note the old-fashioned invocation of the init script here instead of 'sudo service alarmclock play' because we cannot allow the 'service' command to be run without a password (far too insecure), but we can easily specify /etc/init.d/alarmclock to run without a password in the sudoers file.

The alarm action is specified in the config file as a playlist that is passed to gmplayer.  gmplayer is preferred over mplayer so that it can receive keystrokes to control the playback.

[COLOR="Blue"][SIZE="4"]**Further Improvements**[/SIZE][/COLOR]
Hopefully from this tutorial you have learned enough to get your alarm clock working, but there may be other things you want your alarm clock to be able to do.  I've listed a few things below that should be relatively easy to incorporate into the main script to improve your alarm clock.
[LIST]
[*]Start the volume low and gradually increase it.  Do this by creating new config values to control the min and max volume levels and an option to turn off this feature.  In the main script, use fork a separate sub-script and use 'sleep' command in between incrementing the volume to the max level.
[*]The code in this tutorial was written to be run under Ubuntu 10.04 (Lucid Lynx).  If you notice that some things are different for later releases (eg. the location of the wakealarm file is different) then it might help to point that out in this thread so others are aware of the difference.
[/LIST]

**[COLOR="Blue"][SIZE="4"]Installing the alarm clock[/SIZE][/COLOR]**
[LIST=1]
[*]Put the "alarmclock" file (attached to this post) into /etc/init.d/ and edit the ALARM_USER value in it to be the user account in which the alarm is to be run.
[*]The alarmclock script needs to update /sys/class/rtc/rtc0/wakealarm (or similar depending on your system setup) and so requires root privileges.  For this to work without needing a password, make the following changes to your sudoers file.  Be careful when editing your sudoers file and only do so using the 'visudo' command.

Specify a Cmnd_Alias entry for the wakealarm file:
```

Cmnd_Alias	ALARMCLOCK = /etc/init.d/alarmclock

```
Assuming your user is in the admin group, allow your user to make changes to the wakealarm system file without a password, by adding the following line at the bottom of your sudoers file:
```
%admin ALL=NOPASSWD: ALARMCLOCK 
```
[*]Create the /etc/alarmclcock directory to hold the status file.  There's no need to create the status file as it will be created automatically.
[*]Install your init script so that it starts and stops as the system starts and stops:
```
sudo update-rc.d alarmclock defaults
```
[*]Copy the configuration file either as a system configuration file to /etc/alarmclock/alarmrc or as a personal configuration file to ~/.alarmrc
[*]A major limitation of the alarm clock is that it needs the user under which the alarm clock is run to be logged in at the time.  That means the system should be setup to automatically login to that user account.  For how to do that, click here:  [[COLOR="RoyalBlue"]http://www.ubuntugeek.com/how-to-enable-automatic-login-in-ubutnu.html[/COLOR]]("http://www.ubuntugeek.com/how-to-enable-automatic-login-in-ubutnu.html")
If you are concerned about the security implications of automatic login, then create a new user with very limited privileges and use that account to run the alarm.
[*]Finally, to get it to work, edit the config file to match your alarm clock tastes and first play the alarm to hear how it sounds:
```
sudo service alarmclock play
```
then set the alarm clock with:
```
sudo service alarmclock set
```
Check that the alarm is set correctly with:
```
service alarmclock status
```
[/LIST]
Your alarm clock is ready - sleep well!

[SIZE="3"][COLOR="Blue"]**References**[/COLOR][/SIZE]
[SIZE="1"][1] [http://www.mythtv.org/wiki/ACPI_Wakeup]("http://www.mythtv.org/wiki/ACPI_Wakeup")[/SIZE]
[SIZE="1"][2] [http://www.ubuntugeek.com/how-to-enable-automatic-login-in-ubutnu.html]("http://www.ubuntugeek.com/how-to-enable-automatic-login-in-ubutnu.html")[/SIZE]

---

### Post by JohnFH on 2011-04-02
Any comments from anyone?  Do you find any of this useful?

---

### Post by rampageoberon on 2011-05-08
Very handy and easy to follow How-To! Thank you very much.

---

### Post by Blonddeeni on 2011-06-27
Gidday there.
This looks to be the ideal beast for my use, unfortunately it will not work for me because whenever "/sys/clas/rtc/rtc0/wakealarm" is written to, it refuses to set the actual alarm-date, as shown by "cat /proc/driver/rtc".
alarm time yes: alarm date no.
If I write to rtc using "/usr/bin/rtcwake" then the alarm time & date are written and the machine works fine.

(I am using this "/usr/bin/rtcwake" along with "shutdown -h now" to shutdown and wakeup the mythbuntu machine, but would very much like to use your alarmclock script for my laptop).

But the same problem occurs on the laptop, IE: Cannot set the date using "/sys/clas/rtc/rtc0/wakealarm."
I've tried fiddling with your "/etc/init.d/alarmclock" script to use "rtcwake" but am always failing. (Not much of a linux guru I'm afraid.:( )

I'll enclose a copy of my results so far using your script.
I'm hoping you can give me a few pointers.

In my /etc/sudoers file:

# Cmnd alias specification
Cmnd_Alias ALARMCLOCK = /etc/init.d/alarmclock

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%admin ALL=NOPASSWD: ALARMCLOCK
%sudo ALL=(ALL) ALL

Results from the command line:

```
:~$ sudo update-rc.d alarmclock defaults
update-rc.d: warning: alarmclock stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (1)
 System start/stop links for /etc/init.d/alarmclock already exist.

:~$ sudo service alarmclock play
Invalid or unrecognised date specified.  Alarm not set.

:~$ sudo service alarmclock set
Invalid or unrecognised date specified.  Alarm not set.

:~$ service alarmclock status
Alarm cron entry:

System wakeup time:
alrm_time	: 21:44:03
alrm_date	: ****-**-27

$ cat /proc/driver/rtc
rtc_time	: 21:39:34
rtc_date	: 2011-06-27
alrm_time	: 21:44:03
alrm_date	: ****-**-27
alarm_IRQ	: no
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay
```


Next I will set the alarm manually using "/usr/bin/rtcwake" by setting a string to insert the new wakeup time for "rtcwake"

```
:~$ t1=$(date -d '+5 minutes' '+%s')

:~$ sudo rtcwake -lt$t1 -m no
rtcwake: wakeup from "no" using /dev/rtc0 at Mon Jun 27 21:45:55 2011

:~$ cat /proc/driver/rtc
rtc_time	: 21:41:17
rtc_date	: 2011-06-27
alrm_time	: 21:45:55
alrm_date	: 2011-06-27
alarm_IRQ	: yes
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay
```

Which as you can see sets the date which "/sys/class/rtc/rtc0/wakealarm" does not.

Below are the modifications I did to .alramrc
```
#!/bin/bash

# Configuration file for user alarm

#  Include option to query current alarm state
#  Accept keystroke for a snooze action

# valid options are: Tone, TV, Radio, Playlist, AlbumDir
# Tone, Radio and Playlist are the only options currently supported
#ACTION_TYPE="Radio"
ACTION_TYPE="Playlist"

# If the alarm action is set to Tone (PC Speaker), specify the tone duration
# in seconds.
TONE_DURATION=300

# further information about the alarm action (depends on AlarmACTION_TYPE)
# For playlist type, specify full path to music playlist file
# For radio type, specify the http path to the internet radio station
#ACTION_DETAIL="http://www.bbc.co.uk/radio/listen/live/r2.asx"
ACTION_DETAIL="/home/steve/Music/Playlists/Smplayer.TV_Music"

# Alarm time specified in a format that is accepted by the date command
ALRM_TIME="7am"

# Indicates whether it's a once-off alarm.  If set to 1, the alarm is cancelled
# after it is first activated.
ALRM_ONCE=0

# Indicates on which days of the week should the alarm be activated.
# Specified as a comma separated list of digits 1-7 where 1=Monday
ALRM_DAYS=1,2,3,4,5,6,7

# Set the master volume, 0-64 (the mplayer volume is set to 100%)
# This is ignored if the alarm type is set to Tone.
ALRM_VOLUME=20

```

And next is the only modification I did to /etc/init.d/alarmclock
ALARM_USER=steve
DISPLAY=:0.0 smplayer -playlist Music/Playlists/Smplayer.TV_Music $ACTION_DETAIL

Any ideas on how I could incorporate "rtcwake" into the "/etc/init.d/alarmclock" file?
I've tried but am overwhelmed by all the code and get easily turned around.:???:

Cheers.
Blonddeeni.

---

### Post by geazzy on 2011-06-27
thakns for sharing :)

---

### Post by Blonddeeni on 2011-06-29
Wheeeee, managed to get it working with "rtcwake".

Changed the following lines:

```
    # Set the system to wake up at the specified time
#    echo 0 > $RTC_FILE
#    echo $wakeuptime > $RTC_FILE
     echo "next line is to use rtcwake for the first time."
     sudo sh -c "rtcwake -lt$wakeuptime -m no"
```

```
        # Preserve the alarm wakeup time between reboots.
        #  $currentwakeup value is taken from the status file.
        [ -r $STATUS_FILE ] && . $STATUS_FILE
#        echo 0 > $RTC_FILE
#        echo $currentwakeup > $RTC_FILE
       echo "Trying to use rtcwake for cron now."
       sudo sh -c "rtcwake -lt$wakeuptime -m no"
```

And it works perfectly.

Now to try and get it to automatically shutdown after a preset time.
The reason for this shutdown: because although the alarm goes off to wake you up, when it stops playing then you know you should be out the door, or if you have it set to 10 minutes before you have to leave, then you know you've got ten minutes left so stop reading that Calvin & Hobbes book and get a move on. ;-)

However I'm having a bit of trouble here as the alarmclock script resets the cron entry, and so wipes anything I put in there to start my timer script. [sudo sh -c "shutdown -h +30"]

Guess I'll have to mess around with the 'cron' part of the script now.
Or get some other part of the system to trigger the shutdown_timer.

Shiney.

Blonddeeni.

---

### Post by Blonddeeni on 2011-07-01
Later: 
Well I got the cron job working, turns out that it is a bad idea to name your auto-login user "alarmclock" D'OH! #-o The /etc/init.d/alarmclock script also uses that exact phrase to wipe anything in "cron" called alarmclock.
So make sure any script that cron references is not in the /home/alarmclck... area. (Made an  "/Alarm_Timer" folder and "chown" it to alarmclock:alarmclock. This holds my attempts to make a shutdown timer).

Now the big one, how to get a user the permissions to use /sbin/shutdown **without** having to supply a password.
Must have something to do with "/etc/sudoers", but what? Not the easiest file to understand.

Having fun so far. :)
Blonddeeni.

Hmmmm... I wonder how Mythbuntu does it?

---

