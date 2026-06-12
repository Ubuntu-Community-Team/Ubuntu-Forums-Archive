---
title: "HOWTO: Fancontrol"
date: 2006-09-03
forum: Outdated Tutorials &amp; Tips
---

### Post by remmelt on 2006-09-03
(Original thread is [here]("http://www.ubuntuforums.org/showthread.php?p=219205"), but it got snowed under. This is the updated, new and improved version!)

Controlling the speed (and sound!) of your CPU fan is easy!
*[COLOR=Red]Disclaimer: this can ruin your hardware. A CPU fan is needed to cool your CPU and in this howto it will be turned off for a couple of seconds. If you are not comfortable with doing this, don't![/COLOR]*

**Setup lm-sensors**
First, you need to set up lm-sensors. This is explained [here](http://ubuntuforums.org/showthread.php?t=2780). That's for Warty, but still works under Dapper (and Hoary).

Once you have lm-sensors installed, you should have a readout with 'sensors'
```
$ sensors
w83627thf-isa-0290
Adapter: ISA adapter
VCore:     +1.54 V  (min =  +1.69 V, max =  +1.86 V)              
+12V:     +11.67 V  (min = +10.82 V, max = +13.19 V)              
+3.3V:     +3.42 V  (min =  +3.14 V, max =  +3.47 V)              
+5V:       +5.15 V  (min =  +4.75 V, max =  +5.25 V)              
-12V:     -14.91 V  (min = -10.80 V, max = -13.18 V)              
V5SB:      +5.05 V  (min =  +4.76 V, max =  +5.24 V)              
VBat:      +0.06 V  (min =  +2.40 V, max =  +3.60 V)              
fan1:        0 RPM  (min = 18750 RPM, div = 8)                     
CPU Fan:  1188 RPM  (min = 18750 RPM, div = 8)                     
fan3:        0 RPM  (min = 19285 RPM, div = 1)                     
M/B Temp:    +31Â°C  (high =   -73Â°C, hyst =   +21Â°C)   sensor = thermistor           
CPU Temp:  +50.0Â°C  (high =   +80Â°C, hyst =   +75Â°C)   sensor = thermistor           
temp3:     +15.0Â°C  (high =   +80Â°C, hyst =   +75Â°C)   sensor = thermistor           
vid:      +1.775 V  (VRM Version 9.0)
alarms:   
beep_enable:
          Sound alarm enabled

eeprom-i2c-0-51
Adapter: SMBus Via Pro adapter at 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

eeprom-i2c-0-50
Adapter: SMBus Via Pro adapter at 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

```

Notice that my CPU fan is running really slowly, only 1100 RPM. The CPU temp is a little high, so I need to do some tweaking of the config there. The fan can run so slowly and quietly, because it's a large 12 cm fan made by Zalman (it's the 7000B AlCu). If your output does not display an RPM for your CPU fan, and you are positive it is running, you need to increase the fan divisor. If your fan speed is shown and higher than 0, skip the next step.

**Increasing fan_div**
The first line of the sensors output is the chipset your motherboard uses to read the speeds/temps/voltages. Make a backup first:
```
$ sudo cp /etc/sensors.conf /etc/sensors.conf_original
```
Edit the /etc/sensors.conf file as root
```
$ sudo gedit /etc/sensors.conf
```
and look up your exact chipset. The names all look alike, so make sure the one you are editing is yours. Add the line fanX_div 4 near the start of your chipset config. Replace the X with the number of your CPU fan's, for me that was 2. You have to figure out for yourself which one it is, but it's probably 1, 2 or 3.

Save, and run 
```
$ sudo sensors -s
```
which will reload the sensors.conf's set variables.
Run sensors again and check if there is an RPM readout. If not, increase the divisor to 8, 16 or 32. YMMV!

Here is a sample from my sensors.conf
```
chip "w83627thf-*" "w83637hf-*"

    label in0 "VCore"
    label in1 "+12V"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "-12V"
    label in7 "V5SB"
    label in8 "VBat"

    compute in1 ((28/10)+1)*@, @/((28/10)+1)
    compute in3 ((34/51)+1)*@, @/((34/51)+1)
    compute in4 (5.14*@)-14.91, (@+14.91)/5.14
    compute in7 ((6.8/10)+1)*@ ,  @/((6.8/10)+1)

    set fan2_div 8

    <snip>

```
You can safely ignore anything that's not fanX_div. I would advise you to leave the other default settings as they are.

**Run pwmconfig**
```
$ sudo pwmconfig
```
One by one, all fans will be tested for 'speedcontrol' (Pulse Width Modulation, actually). Follow the onscreen help. Pwmconfig will write a config file in /etc. I set the interval to 5 seconds, just to be safe, but 10 should be fine too. Let the script run until you see "Select fan output to configure, or other action:" (all default options are fine, you can basically enter you way through the script).

Now press 5 to look at the configuration file. Press 1 to edit settings. Select a temperature that matches your CPU temp (usually the same number as the fan number, but check and double check!). Go with the defaults until you see: "Enter the minimum PWM value (0-255)
at which the fan STARTS spinning (press t to test) (150):"
Here, press t.
Keep pressing enter until you hear (or better: see) the fan spinning up. Then, press y and enter.
Same for the next step, but the other way around. If you see the fan stops spinning, press y and enter.

Press 5 again to display the config file one more time, then press 4 to save and quit. Almost there!

My /etc/fancontrol config looks like this:
```
INTERVAL=5
FCTEMPS= 1-0290/pwm2=1-0290/temp2_input
FCFANS= 1-0290/pwm2=1-0290/fan2_input
MINTEMP= 1-0290/pwm2=43
MAXTEMP= 1-0290/pwm2=53
MINSTART= 1-0290/pwm2=120
MINSTOP= 1-0290/pwm2=105

```
this is an example!

**Starting fancontrol** 
The last step is to start up fancontrol. Enter this:
```
$ sudo fancontrol &
``` 
Now you can see and hear that your CPU fan is running slower, unless your CPU heats up. Good stuff!

**Starting fancontrol automatically on boot**
Create a file called "fancontrol" in /etc/init.d:
```
sudo gedit /etc/init.d/fancontrol
```

And paste this in there:
```
#!/bin/sh
#
# Fancontrol start script.
#

set -e

# Defaults
DAEMON=/usr/sbin/fancontrol
PIDFILE=/var/run/fancontrol.pid
PATH=/sbin:/bin:/usr/sbin:/usr/bin

test -f $DAEMON || exit 0

. /lib/lsb/init-functions


case "$1" in
        start)
                log_begin_msg "Starting fancontrol daemon..."
                start-stop-daemon --start -o -q -m -b -p $PIDFILE -x $DAEMON
                log_end_msg $?
                ;;
        stop)
                log_begin_msg "Stopping fancontrol daemon..."
                start-stop-daemon --stop -o -q -p $PIDFILE
                log_end_msg $?
                ;;
        force-reload|restart)
                sh $0 stop
                sh $0 start
                ;;
        *)
                log_success_msg "Usage: /etc/init.d/fancontrol {start|stop|restart|force-reload}"
                log_success_msg "  start - starts system-wide fancontrol service"
                log_success_msg "  stop  - stops system-wide fancontrol service"
                log_success_msg "  restart, force-reload - starts a new system-wide fancontrol service"
                exit 1
                ;;
esac

exit 0

```

Save and close, then run ```
sudo chmod 0755 /etc/init.d/fancontrol
sudo update-rc.d fancontrol defaults 99 01
``` and you should be set.

(Thanks, Mr Wonka and jotape99!)


I would advise you to have some sort of fan/temp monitoring software installed. There is a nice one in gkrellm, or you can use xsensors.

Most of this howto is from here:
[http://www.fedoraforum.org/forum/showpost.php?p=161610&postcount=5](http://www.fedoraforum.org/forum/showpost.php?p=161610&postcount=5)
Check if your hardware is supported here:
[http://www.almico.com/forumindex.php](http://www.almico.com/forumindex.php)

---

### Post by kitt on 2006-09-04
Hey, Great How-to... but i have a problem:
"sudo sensors" returns this:
No sensors found!
--
What am i supposed to do now?

---

### Post by voltronguy on 2006-09-04
First of all, Remmelt, thank you for creating this.  I was finally able to silence my fans with this!

The problem I am having is trying to mimic the fan behavior in Windows.  I can run fancontrol, but I just don't trust the setpoints I came up with using the pwnconfig method above.  It's fine if I'm sitting right there keeping an eye on temp, but I'd like to just be able to leave it running like in Windows.

Are you aware of a config file in Windows that would have the temp/RPM setpoints?

Thanks again.

---

### Post by remmelt on 2006-09-06
> **kitt said:**
> Hey, Great How-to... but i have a problem:
"sudo sensors" returns this:
No sensors found!
--
What am i supposed to do now?

You forgot step one: 

Setup lm-sensors
First, you need to set up lm-sensors. This is explained here. That's for Warty, but still works under Dapper (and Hoary).
[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

---

### Post by remmelt on 2006-09-06
> **voltronguy said:**
> First of all, Remmelt, thank you for creating this.  I was finally able to silence my fans with this!

The problem I am having is trying to mimic the fan behavior in Windows.  I can run fancontrol, but I just don't trust the setpoints I came up with using the pwnconfig method above.  It's fine if I'm sitting right there keeping an eye on temp, but I'd like to just be able to leave it running like in Windows.

Are you aware of a config file in Windows that would have the temp/RPM setpoints?

Thanks again.

I tweaked a bit and have it running like this all the time. What exactly do you mean with "leave it running like in windows?" When the CPU heats up, the fan starts turning faster, so in that respect it's the same as win the windows Speedfan program. Speedfan has lots of configuration stuff, some of it hidden out of view (it's cool like that.) It also has all the fan_div and everything. I don't know if it saves its config in a .cfg or in the registry or somewhere else, so you'll have to look around!

Good luck.

---

### Post by voltronguy on 2006-09-09
> **remmelt said:**
> I tweaked a bit and have it running like this all the time.

I guess that's what I'm looking for, how to "tweak" it.  When the fans run in windows they are very consistent, and only come rev up for a few minutes here and there.  In Linux they are reving up and down constantly, like it's on the edge of the trip point.  They aren't running at full speed, but I'm worried that the constant speed changes are worse for it.

What is best to mess with?  I have cracked open the case and know the exact pwm values for the fans to turn on and off, but when I use them with pwmconfig it generates the settings that are causing the revs to constantly change.

What tweaking strategy worked best for you?

---

### Post by remmelt on 2006-09-11
> **voltronguy said:**
> What tweaking strategy worked best for you?

Ha! For me it was exactly the other way around, the Windows Speedfan would have it constantly revving up and then down, like it was on a treshold value. Very annoying!

/etc/fancontrol is the file you should edit. Mine looks like this: 
```
INTERVAL=5
FCTEMPS= 1-0290/pwm2=1-0290/temp2_input
FCFANS= 1-0290/pwm2=1-0290/fan2_input
MINTEMP= 1-0290/pwm2=43
MAXTEMP= 1-0290/pwm2=53
MINSTART= 1-0290/pwm2=120
MINSTOP= 1-0290/pwm2=105
```

man fancontrol is your friend, too. The first line sets the polling interval, 5 seconds is fine. FCTEMPS and FCFANS are mapping entries, they map a pwm to a fan and a temp. If your script works, don't mess with these :)
Now we come to the interesting stuff. MINTEMP is the temperature at which your fan will switch off entirely. When the temperature reaches MAXTEMP, the fan will be set to 100%.
You could try raising or lowering the temperature values (last value on the line, after the = sign.) That should move the treshold, hopefully, to a different value, which would help in your case.
My fan came with a manual physical knob to lower the fan speed. I keep it at 100% all the time and let the software vary the speed (much, MUCH safer) but if you have one of these you could try lowering the max speed a little bit and see if that moves the treshold.


Good luck and let me know how it went!

---

### Post by voltronguy on 2006-09-11
> **remmelt said:**
> Ha! For me it was exactly the other way around, the Windows Speedfan would have it constantly revving up and then down, like it was on a treshold value. Very annoying!

I should mention that I was only using SpeedFan to monitor and chart my temp and RPMs.  I didn't use the autocontrol feature.  I'll try some more messing with the high/low temp cutoffs.  My machine is very quiet but I'm still worried about the stress of the constant speed changes.

---

### Post by remmelt on 2006-09-11
> **voltronguy said:**
> I should mention that I was only using SpeedFan to monitor and chart my temp and RPMs.  I didn't use the autocontrol feature.  I'll try some more messing with the high/low temp cutoffs.  My machine is very quiet but I'm still worried about the stress of the constant speed changes.

I guess the fan would last longer if it's at a constant speed. Then again, a fan is 30 € or something, even with regular changing of the speed it will last for a long time, and the computer is MUCH more quiet. I guess that's the tradeoff. YMMV, etc.

---

### Post by therobbot on 2006-12-06
Hi,

I just tried this out and I have a problem with it. I have an Asus A7V8X-X MOBO (for which fan speed regulation works fine with Speedfan in Windows) and it seems that for some strange reason the fan gets regulated by pwm2 only for values between 0 and 10. For 10 it is already full speed. So I can manually regulate it just fine (by e.g. echo 3 > pwm2) but it seems that fancontrol can't cope with such a case. Is there anything I can reconfigure to get regulation between 0 and 255 or can I change the way fancontrol works to make this work correctly.

Thanks so much in advance!

Tobias

---

### Post by remmelt on 2006-12-07
Did you do
```
sudo pwmconfig
```

That should set the relative values...

---

### Post by mooter on 2007-02-08
Thanks for the great tutorial.


I have a problem writing the pwmconfig though.
I get a lot of permission denied entries for enabling all of the pwm's
Example:

Found the following PWM controls:
   0-002e/pwm1
/usr/sbin/pwmconfig: line 102: 0-002e/pwm1_enable: Permission denied
   0-002e/pwm2
/usr/sbin/pwmconfig: line 102: 0-002e/pwm2_enable: Permission denied
   0-002e/pwm3
/usr/sbin/pwmconfig: line 102: 0-002e/pwm3_enable: Permission denied

Do you think this has to do with my motherboard (Intel D955xbk) not being supported yet?

It still wrote the config file but the only entry that can be changed is the interval, the rest of the entries are empty.  I did sudo...

---

### Post by remmelt on 2007-02-09
Did you do "sudo pwmconfig"?

---

### Post by mooter on 2007-02-09
> I did sudo...      
Yes.

---

### Post by ob2 on 2009-07-12
Awesome tutorial/explanation!  Old fan crashed had to put in a fan I found at work designed as a HP replacement cpu fan.  Darn thing did not like the bios SMART control.  Configured it terminal and all is well.

---

### Post by Nerevar144 on 2009-11-10
This is a good howto, just it's out-dated.  Just install lm-sensors then reboot and run pwmconfig.  DO NOT CHANGE YOUR fancontrol FILE!  Reboot and it will be automagically loaded.  Presto!

---

