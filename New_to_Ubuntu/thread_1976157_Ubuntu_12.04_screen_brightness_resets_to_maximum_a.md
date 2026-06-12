---
title: "Ubuntu 12.04 screen brightness resets to maximum after reboot"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by plant on 2012-05-08
:confused:I have Toshiba Satellite Pro laptop with ATI graphics card.
Recently installed Ubuntu 12.04 (64-bit)
I can adjust the screen brightness but after restarting the screen brightness resets to maximum.

Earlier I edited the /etc/rc.local file and added echo 2 > /usr/class....../brightnes
to set the brightness

but now since I installed the fglrx driver(graphics driver), the issue is back.
Now, no matter what brightness I set, after restart, it's always the maxmium value.

Please help!!!

---

### Post by plant on 2012-05-08
bump

---

### Post by plant on 2012-05-08
someone. Please reply

---

### Post by brainwash on 2012-05-08
Shouldn't it be /**sys**/class....../brightness instead of /usr/class....../brightness?

---

### Post by cmcanulty on 2012-05-08
Mine always reset to dim and this fixed it. Might work in reverse also
[http://ubuntuforums.org/showthread.php?t=1972303&highlight=screen+Brightness+ste+0%25]("http://ubuntuforums.org/showthread.php?t=1972303&highlight=screen+Brightness+ste+0%25")

---

### Post by plant on 2012-05-09
> **brainwash said:**
> Shouldn't it be /**sys**/class....../brightness instead of /usr/class....../brightness?
Yes, it is.

---

### Post by plant on 2012-05-09
> **cmcanulty said:**
> Mine always reset to dim and this fixed it. Might work in reverse also
[http://ubuntuforums.org/showthread.php?t=1972303&highlight=screen+Brightness+ste+0%25](http://ubuntuforums.org/showthread.php?t=1972303&highlight=screen+Brightness+ste+0%25)
Thank you for the reply, I will check this as I get home. Hope this sovles the issue.

---

### Post by plant on 2012-05-10
> **cmcanulty said:**
> Mine always reset to dim and this fixed it. Might work in reverse also
[http://ubuntuforums.org/showthread.php?t=1972303&highlight=screen+Brightness+ste+0%25](http://ubuntuforums.org/showthread.php?t=1972303&highlight=screen+Brightness+ste+0%25)

It did not help. 
Now the screen brightness control bar itself is missing.
The brightness remains maximum on every boot.

---

### Post by plant on 2012-05-10
[cmcanulty]("http://ubuntuforums.org/member.php?u=36066"),

I was able to undo that step that you showed in the other forum.

sudo sed "s/\(GRUB_CMDLINE_LINUX=\)\"\"/\1\"acpi_osi=Linux acpi_backlight=vendor\"/" /etc/default/grub -i 

what I did is,
I went to the file: /etc/default/grub
and commented the line that showed

    GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
Thereby, i got back my brightness control bar.

However the issue still persists, brightness resets to max after reboot.
It seems that the /etc/rc.local file is not being executed after I installed the fglrx file.

but 
    echo 1 > /sys/class/backlight/acpi_video0/brightness
executes fine in terminal

Is there anyway to include rc.local in the boot seqence?

I know it's already included ,however this file is clearly being ignored while startup.
Will it work if I created my own script to include the /etc/rc.local file?


From what I observe is that,
I can set my brightness to low using the brightness control bar, 
Now on restart, the brightness is still low, or what I set before restart.
However after the ubuntu logo that shows loading, the screen flickers and sets the brightness to max.
This is the step that makes everything wrong.
Something or some loading sequence is resetting the brightness to 7 (max in my lap). discarding the previous value.

Is there any solution for this?

---

### Post by brainwash on 2012-05-10
You could try to delay the execution of the command on startup:
```
(sleep 10 && echo 1 > /sys/class/backlight/acpi_video0/brightness) &
```

---

### Post by fleamour on 2012-05-10
Does this help?:

[http://ubuntuguide.net/how-to-save-screen-brightness-settings-in-ubuntu-12-04-laptop](http://ubuntuguide.net/how-to-save-screen-brightness-settings-in-ubuntu-12-04-laptop)

EDIT:  Oooops sorry!

---

### Post by plant on 2012-05-11
> **brainwash said:**
> You could try to delay the execution of the command on startup:
```
(sleep 10 && echo 1 > /sys/class/backlight/acpi_video0/brightness) &
```

The question is where do I need to apply that.
If I save the line in rc.local file will not work, as I already told that, rc.local isn't being executed.

---

### Post by plant on 2012-05-11
> **fleamour said:**
> Does this help?:

[http://ubuntuguide.net/how-to-save-screen-brightness-settings-in-ubuntu-12-04-laptop](http://ubuntuguide.net/how-to-save-screen-brightness-settings-in-ubuntu-12-04-laptop)

EDIT:  Oooops sorry!

Yeah, I tried, but it isn't working. 
I had the line added to the rc.local file, but rc.local itself isn't being called at startup.
Some startup acton is reseting the brightness value.

---

### Post by brainwash on 2012-05-11
> **plant said:**
> The question is where do I need to apply that.
If I save the line in rc.local file will not work, as I already told that, rc.local isn't being executed.
Did you somehow test, if rc.local gets executed or not?

Lets expand the command I posted before:
```
(sleep 10 && echo 1 > /sys/class/backlight/acpi_video0/brightness > /tmp/logfile 2>&1) &
```

Now it will log the output into a file (/tmp/logfile). After login it should contain the brightness value or an error message or the file won't exist at all.

Furthermore, please attach the content of your rc.local file.

---

### Post by cmcanulty on 2012-05-11
did you try adding it to startup applications?

---

### Post by plant on 2012-05-12
My /etc/init.d/rc,local file has

> #! /bin/sh
PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

do_start() {
    if [ -x /etc/rc.local ]; then
            [ "$VERBOSE" != no ] && log_begin_msg "Running local boot scripts (/etc/rc.local)"
        /etc/rc.local
        ES=$?
        [ "$VERBOSE" != no ] && log_end_msg $ES
        return $ES
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
esacand my /etc/rc.local file has

> #!/bin/sh -e

echo 1 > /sys/class/backlight/acpi_video0/brightness
exit 0


Now even if I add the rc.local to my startup application.
But the thing is, 
My computer will be booting with the previous brightness set  and  some other startup sequence (that works wrong inside ubuntu )
will reset my brightness to max, and then, my startup script will be resetting the screen brightness to 1 or whatever value I set.

Isn't that bad for the screen, as on every booting the screen brightness is set twice.

---

### Post by plant on 2012-05-15
> **cmcanulty said:**
> did you try adding it to startup applications?

Ok, as a last resort, I added a startup application to reset my brightness as low.
Thank you.

---

### Post by Deo Pal on 2012-08-25
mine is a similar problem, but the thing is that when i boot it in recovery mode it works fine, but when i normally boot it doesnot display anything there's just the blank screen. When i close my lid and then open, I could see the white login screen barely on my screen.

I am using ubuntu 12.04 LTS... please help me also please.....

---

### Post by nsznaj on 2012-12-01
> **plant said:**
> Ok, as a last resort, I added a startup application to reset my brightness as low.
Thank you.

Would you help me do that too?

I can't stop the screen going too bright all the time (when AC is plugged on only!)

---

### Post by grushanka on 2013-04-03
Thanks, plant, this really helped. The delay really work for me on my Asus Zenbook.

---

### Post by Seinfeld on 2013-05-27
Thanks brainwash and plant

Like grushanka, it worked with me "only" with a delay. 
Also, editing the /etc/default/grub file method might work, check the acpi section in the following very useful link
[https://wiki.archlinux.org/index.php/Backlight](https://wiki.archlinux.org/index.php/Backlight) 


Just for curiosity, why it only works when the execution is delayed by sleep X ??

Also, why the brigtness meter/indicator using the function keys is always set to max ?? I know it might not be so important, but if solved will be great :) 

Finally, it works only with reboot, not logout. Can that be fixed too ??


Thanks in advance

---

### Post by vacaloca on 2013-06-27
Thanks for the suggestion of putting the sleep before the command, just a simple 1 second delay worked for me (SSD and recent laptop)

---

### Post by aquanauta on 2014-02-08
I have an Asus 1015E-DS03 with Ubuntu 12.04 lts (factory pre-installed) and have the same problem. Is there a solution for this? Is there a fix in the new kernels?
I am also unable to use Fn+F2 for Wifi activation/deactivation nor FN+F8 for switching screens. The funny thing is that Asus sells this machine with ubuntu pre-installed from factory. (Anyway I made a fresh LTS instalation beacuse the HDD was partitioned for Windows 8. Thanks for any help.

---

