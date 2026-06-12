---
title: "The brightness setting"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by acimi66 on 2012-05-17
I have not found any info on this. I am using 12.04.
I have to adjust my brightness setting every time I start my computer. 
Why won't it stay where I set the slide bar? Is it a bug? or is is it tired into power management somehow?

I would love to solve this!

---

### Post by black veils on 2012-05-18
the way i have always dealt with it is to:

1.  set the required brightness

2.  restart


it remembers if i do that.

---

### Post by acimi66 on 2012-05-18
Hey thanks for the response BV
But that still did not work.

I also tried this:
[http://ubuntuguide.net/how-to-save-screen-brightness-settings-in-ubuntu-12-04-laptop](http://ubuntuguide.net/how-to-save-screen-brightness-settings-in-ubuntu-12-04-laptop)

which did not work either...:confused:

I will keep on looking I guess

Cheers

---

### Post by Toz on 2012-05-18
That link you reference should work, but you have to have the proper information (his command may not work on your computer). What backlight interfaces do you have? Run this command and post back the results:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/actual_brightness; cat $interface/max_brightness; done
```

EDIT: make sure you run that command when the brightness is at the setting you want on restart.

---

### Post by acimi66 on 2012-05-19
[FONT=monospace]Thanks for the response
Here it is:

/sys/class/backlight/acpi_video0
5
7
/sys/class/backlight/intel_backlight
2871
4882
/sys/class/backlight/toshiba
5
7

Is this a fix or just a systems check?

[/FONT]

---

### Post by Toz on 2012-05-19
Just a system check. Which of the following commands change the brightness:
```
echo 7 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

...or

```
echo 7 | sudo tee /sys/class/backlight/toshiba/brightness
```

---

### Post by acimi66 on 2012-05-19
Yes, The first one:
echo 7 | sudo tee /sys/class/backlight/acpi_video0/brightness

I tried adding this :  echo 7 > /sys/class/backlight/acpi_video0/brightness 

to 
/etc/rc.local and then restart but it did not work...

What am I missing

Thanks again for the help.

---

### Post by Toz on 2012-05-19
> echo 7 > /sys/class/backlight/acpi_video0/brightness 
would set the brightness to full. If you want it less bright, try echoing 5 instead. Make sure your command is above the *exit 0* command. Maybe post back the contents of /etc/rc.local to ensure its correct.

---

### Post by codingman on 2012-05-19
Would be a good idea to report this as a bug, although there should be some patches, it's always helpful to the developers to have a bug record of it.

---

### Post by acimi66 on 2012-05-19
Ok, so here is the file:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo 6 >  /sys/class/backlight/acpi_video0/brightness

exit 0

I went with 6, but it still does not save it after a restart. bummer.
I will report it as a bug.

Bug Report sent to launchpad

---

### Post by Toz on 2012-05-19
I'm surprised that this doesn't work (actually, this doesn't save the previous brightness, it only sets one certain value on boot). With this command in /etc/rc.local and after a boot, what is the value of /sys/class/backlight/acpi_video0/actual_brightness? Does the value even get changed?

Is there anything in /var/log/syslog about this command not working?

---

### Post by acimi66 on 2012-05-19
Yes it's working. The only thing I changed in the file ( /etc/rc.local ) was, there was a space between the echo 6 > and here  /sys/class/backlight/acpi_video0/brightness

When I started my computer just now the brightness setting were correct!:guitar:

Thanks again, nice work!

---

### Post by acimi66 on 2012-05-23
I can't quite believe it!?!
It reverted back to 0 (zero) after working for quite a few days.

Very strange. The etc/rc.local file is still the same.

Any ideas?

---

### Post by Toz on 2012-05-23
Change the command to read:
```
ls /sys/class/backlight/* > /tmp/blight.log
echo 6 > /sys/class/backlight/acpi_video0/brightness
```
...and after you're logged in, post back the contents of /tmp/blight.log

Also, have a look at /var/log/syslog to see if any error messages are popping up when running this command. Lets see if the interface is there when the value is being echoed.

---

### Post by acimi66 on 2012-05-23
Hey Toz,
here it is

/sys/class/backlight/acpi_video0:
actual_brightness  bl_power  brightness  device  max_brightness  power  subsystem  type  uevent

/sys/class/backlight/intel_backlight:
actual_brightness  bl_power  brightness  device  max_brightness  power  subsystem  type  uevent

/sys/class/backlight/toshiba:
actual_brightness  bl_power  brightness  device  max_brightness  power  subsystem  type  uevent


I am not sure what to be looking for in the var/log/syslog but there were no warnings/failure that I could.

---

### Post by Toz on 2012-05-23
Can you post back the contents of your /var/log/syslog file so I can have a look? Or:
```
pastebinit /var/log/syslog
```
...and post back the link.

When it doesn't work, can you then manually change it from the command line? Does that still work?

---

### Post by acimi66 on 2012-05-23
[http://paste.ubuntu.com/1003942/](http://paste.ubuntu.com/1003942/)

---

### Post by acimi66 on 2012-05-23
re-cap:
the rc.local file has this;
echo 5 >/sys/class/backlight/acpi_video0/brightness

I manually change the slider to reflect this in sys settings > restarted > dim at 0 (zero) again.

---

### Post by Toz on 2012-05-23
> **acimi66 said:**
> Hey Toz,
here it is

/sys/class/backlight/acpi_video0:
actual_brightness  bl_power  brightness  device  max_brightness  power  subsystem  type  uevent

/sys/class/backlight/intel_backlight:
actual_brightness  bl_power  brightness  device  max_brightness  power  subsystem  type  uevent

/sys/class/backlight/toshiba:
actual_brightness  bl_power  brightness  device  max_brightness  power  subsystem  type  uevent


I am not sure what to be looking for in the var/log/syslog but there were no warnings/failure that I could.

Was there anything in /tmp/blight.log?

---

### Post by Toz on 2012-05-23
> **acimi66 said:**
> [http://paste.ubuntu.com/1003942/](http://paste.ubuntu.com/1003942/)

Yeah, nothing there.

---

### Post by Toz on 2012-05-23
> **acimi66 said:**
> re-cap:
the rc.local file has this;
echo 5 >/sys/class/backlight/acpi_video0/brightness

I manually change the slider to reflect this in sys settings > restarted > dim at 0 (zero) again.

As a test, try delaying the execution of the command. Use:
```
(sleep 5) && (echo 5 >/sys/class/backlight/acpi_video0/brightness)
```
...feel free to play with the sleep 5 command and increase the value of 5 seconds to 10 to see if that works.

---

### Post by acimi66 on 2012-05-23
YES!
I added that code >restart and it worked...so far.

thanks for your help Toz. Nice one

---

