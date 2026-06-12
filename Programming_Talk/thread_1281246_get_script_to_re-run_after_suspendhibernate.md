---
title: "get script to re-run after suspend/hibernate"
date: 2009-10-03
forum: Programming Talk
---

### Post by utnubuuser on 2009-10-03
hello--  I need some help with a script...

I have a script in my thinkpad's /etc/init.d folder which starts the cooling fan at boot, and keeps it running for duration of the session unless I stop it.  Problem is the script isn't re-run after resuming from suspend-to-ram.
the script in /etc/init.d is:> !#/bin/bash
echo level 2 /proc/acpi/ibm/fan
exit
The script I've put into /etc/acpi/resume.d is:> #!/bin/sh

# Get fan back after resume
if [ -x /etc/init.d/fanscript.sh ]; then
  /etc/init.d/fanscript.sh start
fi

exit
 


but the fan is not resuming after suspend.

Any help/suggestion is appreciated.
Thanks
PS. The fan script has to be run at root-level and really all I'm looking for is a way to run "echo level 2 > /proc/acpi/ibm/fan" at root level when the machine comes out of suspend mode.  thanks again

---

### Post by tatrefthekiller on 2009-10-03
Hi,

/etc/acpi/resume.d is not used anymore.
To know which method your're using :
```
cat /etc/default/acpi-support | grep  SUSPEND_METHODS
```
I think you have to use /etc/pm/sleep.d/
See man pm-suspend, section FILES.

I had the same problem for downclocking my graphics card !

---

### Post by utnubuuser on 2009-10-03
thanks, I'll check it out.

---

### Post by utnubuuser on 2009-10-03
Ya, it's not through /etc/pm/sleep.d.  That folder is empty, as are all the folder in /etc/pm.  

cat /etc/default/acpi-support | grep SUSPEND_METHODS  --ineffective.

Any other suggestions?

---

### Post by utnubuuser on 2009-10-03
This is what is recorded in pm-suspend.log> ===== Sat Oct  3 09:56:37 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Sat Oct  3 09:56:38 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Sat Oct  3 09:56:38 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Sat Oct  3 09:56:38 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/20video =====
kernel.acpi_video_flags = 0
===== Sat Oct  3 09:56:39 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Sat Oct  3 09:56:39 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Sat Oct  3 09:56:39 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Sat Oct  3 09:56:41 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Sat Oct  3 09:56:41 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/95anacron =====
===== Sat Oct  3 09:56:41 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/95hdparm-apm =====
===== Sat Oct  3 09:56:41 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Sat Oct  3 09:56:41 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/99video =====
Sat Oct  3 09:56:41 PDT 2009: done running suspend hooks.
Sat Oct  3 09:56:52 PDT 2009: running resume hooks.
===== Sat Oct  3 09:56:52 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/99video =====
===== Sat Oct  3 09:56:52 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Sat Oct  3 09:56:52 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/95hdparm-apm =====
/usr/lib/pm-utils/sleep.d/95hdparm-apm: 50: get_power_status: not found

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
===== Sat Oct  3 09:56:52 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/95anacron =====
===== Sat Oct  3 09:56:53 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Sat Oct  3 09:56:53 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Sat Oct  3 09:56:53 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
 * Reconfiguring network interfaces...
   ...done.
===== Sat Oct  3 09:56:53 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Sat Oct  3 09:56:53 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/20video =====
===== Sat Oct  3 09:56:53 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Sat Oct  3 09:56:53 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Sat Oct  3 09:56:53 PDT 2009: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
Sat Oct  3 09:56:53 PDT 2009: done running resume hooks.


Maybe I'll try adding the command to start the fan to one of the pm-sleep.d scripts.  Looking at them, it seems I might've found the right set.  Now I just need to figure out which script I can add it to.

---

### Post by utnubuuser on 2009-10-03
Hi -- Nevermind, --  I got it workin'.   Thanks tatrefthekiller - got me lookin' in the right direction.
Blessed /var/logs

---

### Post by cecilx22 on 2009-10-14
Hey!  What did you do to get it working?  I have a similar need and would love to know how to get a script to run.

Specifically, I need to switch from compiz to metacity on suspend, and from metacity back to compiz on resume.  (Compiz fouls up suspend on my setup).

I'm looking at using the /usr/lib/pm-utils/sleep.d/01PulseAudio as a skeleton script:

> #! /bin/sh

. "${PM_FUNCTIONS}"

get_pulse_users() {
    echo $(ps aux | awk '/\/usr\/bin\/pulseaudio --start/ {print $1}')
}

suspend_pulse() {
    for i in $(get_pulse_users); do
        sudo -H -u $i pactl suspend-sink 1 &> /dev/null
        sudo -H -u $i pactl suspend-source 1 &> /dev/null
    done
}

resume_pulse() {
    for i in $(get_pulse_users); do
        sudo -H -u $i pactl suspend-sink 0 &> /dev/null
        sudo -H -u $i pactl suspend-source 0 &> /dev/null
    done
}

case $1 in 
    hibernate|suspend)
        suspend_pulse
        ;;
    thaw|resume)
        resume_pulse
        ;;
    *) exit $NA
        ;;
esac
#! /bin/sh

. "${PM_FUNCTIONS}"

get_pulse_users() {
    echo $(ps aux | awk '/\/usr\/bin\/pulseaudio --start/ {print $1}')
}

suspend_pulse() {
    # do a metacity --replace here
    for i in $(get_pulse_users); do
        sudo -H -u $i pactl suspend-sink 1 &> /dev/null
        sudo -H -u $i pactl suspend-source 1 &> /dev/null
    done
}

resume_pulse() {
    # do a compiz --replace here
    for i in $(get_pulse_users); do
        sudo -H -u $i pactl suspend-sink 0 &> /dev/null
        sudo -H -u $i pactl suspend-source 0 &> /dev/null
    done
}

case $1 in 
    hibernate|suspend)
        suspend_pulse
        ;;
    thaw|resume)
        resume_pulse
        ;;
    *) exit $NA
        ;;
esac


Will modifying the suspend_pulse() and resume_pulse functions as commented do the trick do you think? (obviously sliming down the whole script and making more appropriate names for functions, etc, but that's all superficial anyhow...)

Thanks!!

---

