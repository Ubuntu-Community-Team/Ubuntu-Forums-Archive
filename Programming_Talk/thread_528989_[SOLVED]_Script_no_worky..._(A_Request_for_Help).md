---
title: "[SOLVED] Script no worky... (A Request for Help)"
date: 2007-08-18
forum: Programming Talk
---

### Post by dustigroove on 2007-08-18
Hey all,

I have a script that I am working on and am having some difficulty with. Listed below is the improperly functioning portion of the script. It is meant to determine if a process is running or not and do something accordingly. Currently if I directly assign the values to the variable "checkup", the script works fine. This indicates to me that A) there is something wrong with the syntax of my script or B) the method of determining if the process is running is faulty. ```
ps ax | grep 'nm-applet' | grep -v grep | wc -l
``` I'm leaning towards option A as when I input the above into a terminal, I get the expected returned value, but when plugged into the full thing I'm not getting the expected outcome.

Any and all help is much appreciated, thanks.

Cheers!

The full code:
```
#!/bin/bash

#checkup="0"
#checkup="1"
#checkup="2"
checkup="`ps ax | grep 'nm-applet' | grep -v grep | wc -l`"

function start_check() {
    if [[ "$checkup" = "0" ]]; then
            echo "First"
    elif [[ "$checkup" = "1" ]]; then
            echo "Second"
    else
            echo "Third"; echo -e "\a"
    fi
}

start_check
```

---

### Post by Nekiruhs on 2007-08-18
You need to surround it with $(). Other wise checkup is a string of the command, not the value:
```
checkup = $(ps ax | grep 'nm-applet' | grep -v grep | wc -l)
```

---

### Post by dustigroove on 2007-08-18
> **Nekiruhs said:**
> You need to surround it with $(). Other wise checkup is a string of the command, not the value:
```
checkup = $(ps ax | grep 'nm-applet' | grep -v grep | wc -l)
```


Thanks for your help Nekiruhs, however I'm still returning an incorrect result. With nm-applet running or not running, I keep getting the else ("Third") portion of the function as my result.

Please let me know if I misinterpreted your help, or missed something in corrected script:

```
#!/bin/bash

checkup=$(ps ax | grep 'nm-applet' | grep -v grep | wc -l)

function start_check() {
    if [[ "$checkup" = 0 ]]; then
            echo "First"
    elif [[ "$checkup" = 1 ]]; then
            echo "Second"
    else
            echo "Third"; echo -e "\a"
    fi
}

start_check
```

---

### Post by walkerk on 2007-08-18
> **dustigroove said:**
> Thanks for your help Nekiruhs, however I'm still returning an incorrect result. With nm-applet running or not running, I keep getting the else ("Third") portion of the function as my result.

Please let me know if I misinterpreted your help, or missed something in corrected script:

```
#!/bin/bash

checkup=$(ps ax | grep 'nm-applet' | grep -v grep | wc -l)

function start_check() {
    if [[ "$checkup" = 0 ]]; then
            echo "First"
    elif [[ "$checkup" = 1 ]]; then
            echo "Second"
    else
            echo "Third"; echo -e "\a"
    fi
}

start_check
```

Made a couple changes. There was a syntax error with "[[" and after the errors it outputs the else statement.. Also I removed the quotations from $checkup in the if statements. "$checkup" = 0 is like asking if the string "$checkup" = 0 instead of the variable $checkup = 0.

```
#!/bin/bash

checkup=$(ps ax | grep 'nm-applet' | grep -v grep | wc -l)

start_check() {
    if [ $checkup = 0 ]; then
            echo "First"
    elif [ $checkup = 1 ]; then
            echo "Second"
    else
            echo "Third"; echo -e "\a"
    fi
}

start_check
```

---

### Post by Chaotic Thought on 2007-08-18
I noticed you're using **ps ax**, but you can also give **ps** the name of a process and then use the return code to determine if it is running. Look at this example:

```

#!/bin/bash

PROCESS="nm-applet"

# Check for PROCESS
ps_output="$(ps --no-headers -C "$PROCESS")"
ret=$?

# Report result
[ "$ret" = "0" ] && echo "$PROCESS is running."
[ "$ret" != "0" ] && echo "$PROCESS is not running, or there was an error."

# Count the number of lines in the collected output from ps
if [ "$ps_output" = "" ]
then
   wc_output=0    # Assume 0 lines if there was no output from ps
else
   wc_output=$(echo "$ps_output" | wc -l)
fi
echo "wc reports $wc_output lines of output:"
echo "$ps_output"

```


**Sample output:**
```

nm-applet is running.
wc reports 1 lines of output:
 5265 ?        00:00:03 nm-applet

```


[b]

**Tip:** read the manpage for ps(1) and look for the -o option. You can use this in scripts to find out specific information about processes. For example, I recently used this to find out if a process was sleeping or not:

**ps --no-headers -o state -C firefox-bin**

The output is a single letter, so you can check for this in your script.

---

### Post by dustigroove on 2007-08-19
Thank you both for your replies. I will take a look at your suggestions tomorrow and will rework what I have.

Appreciate the help!

---

### Post by dustigroove on 2007-08-19
> **Chaotic Thought said:**
> I noticed you're using **ps ax**, but you can also give **ps** the name of a process and then use the return code to determine if it is running. Look at this example:

**Tip:** read the manpage for ps(1) and look for the -o option. You can use this in scripts to find out specific information about processes. For example, I recently used this to find out if a process was sleeping or not:

**ps --no-headers -o state -C firefox-bin**

The output is a single letter, so you can check for this in your script.

Thanks Chaotic, this information and example was quite helpful, I was able to utilize your tip regarding the -o option for ps in a number of scripts as it was a much more direct way to achieve a desired result in many cases.

Thanks to you as well walkerk for the syntax corrections (although I determined something was still amiss as the results would keep giving me different values... I have changed the method so this is no longer an issue).

In case anyone is interested, below is the main script that I had been tinkering with. It's fairly rough and simple, and I still need to add a piece to let firestarter launch and continue the rest of the script if the IP address is not assigned after a specified duration (basically allowing time for me to enter my keyring pw and let nm-applet do its thing, but not have the script continue to loop indefinitely if I don't for some reason).

Code:
```
#!/bin/bash
#
# INFO: This login script was written to check for selected applications
# after login and launch them if needed.
#
# It accounts for firestarter being fussy and throwing up an error dialog
# when nm-applet does not yet show an active wireless connection. It also
# staggers the timing of when some apps are run so that their icons appear
# in the notification area, ordered to my preference.
#
# Last updated on Aug 27, 2007.

noip=0

function while_noip() {
    while [ $noip = 0 ]; do
        if [ "`ifconfig ath0 | grep 'inet addr'`" = "" ]; then
            noip=0
        else
            sudo firestarter --start-hidden &
            noip=1
        fi
        sleep 0.5
    done
}

function start_compiz() {
    if [ "`ps ax | grep compiz| grep -v grep | wc -l`" != 0 ]; then
        echo "Compiz is already running."
    else
        echo "Starting Compiz..."; compiz --indirect-rendering --replace -c emerald &
    fi
}

function start_awn() {
    if [ "`ps --no-headers -o state -C 'avant-window-navigator' | wc -l`" != "0" ]; then
        echo "Avant Window Navigator is already running."
    else
        echo "Starting Avant Window Navigator..."; avant-window-navigator &
    fi
}

function start_tilda() {
    if [ "`ps --no-headers -o state -C 'tilda' | wc -l`" != "0" ]; then
        echo "Tilda is already running."
    else
        echo "Starting Tilda..."; tilda &
    fi
}

function start_nmapplet() {
    if [ "`ps --no-headers -o state -C 'nm-applet' | wc -l`" != "0" ]; then
        echo "NetworkManager is already running."
    else
        echo "Starting NetworkManager..."; nm-applet --sm-disable &
    fi
}

function start_firestarter() {
    if [ "`ps --no-headers -o state -C 'firestarter' | wc -l`" != "0" ]; then
        echo "Firestarter is already running."
    else
        echo "Starting Firestarter..."; while_noip
    fi
}

function start_bluetooth() {
    if [ "`ps --no-headers -o state -C 'bluetooth-applet' | wc -l`" != "0" ]; then
        echo "Bluetooth Applet is already running."
    else
        echo "Starting Bluetooth Applet..."; bluetooth-applet &
    fi
}

function start_glipper() {
    if [ "`ps --no-headers -o state -C 'glipper' | wc -l`" != "0" ]; then
        echo "Glipper is already running."
    else
        echo "Starting Glipper..."; glipper &
    fi
}

function start_google() {
    if [ "`ps --no-headers -o state -C 'gdl_service' | wc -l`" != "0" ]; then
        echo "Google Desktop is already running."
    else
        echo "Starting Google Desktop..."; /opt/google/desktop/bin/gdlinux start &
    fi
}

function start_gaim() {
    if [ "`ps --no-headers -o state -C 'gaim' | wc -l`" != "0" ]; then
        echo "Gaim is already running."
    else
        echo "Starting Gaim..."; gaim &
    fi
}

function start_tomboy() {
    if [ "`ps --no-headers -o state -C 'tomboy' | wc -l`" != "0" ]; then
        echo "Tomboy is already running."
    else
        echo "Starting Tomboy..."; tomboy &
    fi
}

start_compiz
sleep 4; start_awn
sleep 1; start_tilda
sleep 1; start_nmapplet
sleep 1; start_firestarter
sleep 2; start_bluetooth
sleep 1; start_glipper
sleep 1; start_google
sleep 4; start_gaim
sleep 1; start_tomboy

echo ""; echo "Done!"
```

---

### Post by Chaotic Thought on 2007-08-27
> **dustigroove said:**
> ```

function while_noip() {
    while [ $noip = 0 ]; do
        if [ "`ifconfig ath0 | grep 'inet addr'`" = "" ]; then
            noip=0
        else
            sudo firestarter --start-hidden &
            noip=1
        fi
    done
}

```

This will work get the job done, but you may notice that this is a tight loop and the CPU will be near 100% while it is executing--also in some cases, continuously polling like this can cause problems... To make your script nicer, add a short sleep statement before the "done" keyword. This version will wait 500 ms between each poll:

```

function while_noip() {
    while [ $noip = 0 ]; do
        if [ "`ifconfig ath0 | grep 'inet addr'`" = "" ]; then
            noip=0
        else
            sudo firestarter --start-hidden &
            noip=1
        fi
        sleep 0.5
    done
}

```

NOTE: If you need your script to be backwards-compatible, you need to use an integer argument to sleep (i.e. "sleep 1" is the minimum). But the newer versions included with the current Ubuntu accept fractions like 0.5 which is useful for brief polling like this.

---

### Post by dustigroove on 2007-08-27
> **Chaotic Thought said:**
> ...This will work get the job done, but you may notice that this is a tight loop and the CPU will be near 100% while it is executing...

Ah, I had indeed wondered about that.

> **Chaotic Thought said:**
>  ...also in some cases, continuously polling like this can cause problems... To make your script nicer, add a short sleep statement before the "done" keyword. This version will wait 500 ms between each poll...

Thanks for pointing this out and for the recommended refinement.

Now if things could just settle down with other areas of my life so I can revisit scripting a bit more. It's a little frustrating to try and learn when I get to play only in these little sporadic chunks!

---

