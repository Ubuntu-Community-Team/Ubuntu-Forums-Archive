---
title: "Help Modifying Script"
date: 2006-11-15
forum: Programming Talk
---

### Post by davebed on 2006-11-15
I am hoping someone can help me modify my **power.sh** script. I am very new to Linux, and even newer to scripts! From what I understand, this script is called when I switch to battery *and* when I plug the AC back in. (This way, when I run Beryl, I'll still have my display turn off automatically)

I would like to add the following command when it's running on battery (ie. when Laptop-mode engages:
```
DISPLAY=:0 xset dpms 60
```

And then add the following for when it's back on AC (ie. when laptop-mode disengages):
```
DISPLAY=:0 xset dpms 180
```  

Here is my Power.sh script. Could someone show me **where** and **how** to add this command?  Thanks

```
#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

function laptop_mode_enable {
    $LAPTOP_MODE start
    
    for x in /sys/bus/ide/devices/*/block; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 100 /dev/$drive 2>/dev/null
	$HDPARM -B 128 /dev/$drive 2>/dev/null
    done
    
    for x in /sys/bus/scsi/devices/*/block; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 100 /dev/$drive 2>/dev/null
	$HDPARM -B 128 /dev/$drive 2>/dev/null
    done
}

function laptop_mode_disable {
    for x in /sys/bus/ide/devices/*/block; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 800 /dev/$drive 2>/dev/null
	$HDPARM -B 255 /dev/$drive 2>/dev/null
    done
    for x in /sys/bus/scsi/devices/*/block; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 800 /dev/$drive 2>/dev/null
	$HDPARM -B 255 /dev/$drive 2>/dev/null
    done
    $LAPTOP_MODE stop
}

getState;

checkStateChanged;

shopt -s nullglob

for x in /proc/acpi/ac_adapter/*; do
    grep -q off-line $x/state

    if [ $? = 0 ] && [ x$1 != xstop ]; then	
	for SCRIPT in /etc/acpi/battery.d/*.sh; do
	    . $SCRIPT
	done
	if [ x$ENABLE_LAPTOP_MODE = xtrue ]; then
	    (sleep 5 && laptop_mode_enable)&
	fi
    else
	for SCRIPT in /etc/acpi/ac.d/*.sh; do
	    . $SCRIPT
	done
	if [ x$ENABLE_LAPTOP_MODE = xtrue ]; then
	    (sleep 5 && laptop_mode_disable)&
	fi
    fi
done

```

---

### Post by araz on 2006-11-15
I would put the code like this:



> (...)
if [ $? = 0 ] && [ x$1 != xstop ]; then	
	for SCRIPT in /etc/acpi/battery.d/*.sh; do
	    . $SCRIPT
	done
[QUOTE]DISPLAY=:0 xset dpms 60
	if [ x$ENABLE_LAPTOP_MODE = xtrue ]; then
	    (sleep 5 && laptop_mode_enable)&
	fi
    else
	for SCRIPT in /etc/acpi/ac.d/*.sh; do
	    . $SCRIPT
	done
> DISPLAY=:0 xset dpms 180
	if [ x$ENABLE_LAPTOP_MODE = xtrue ]; then
	    (sleep 5 && laptop_mode_disable)&
	fi
    fi
(...)[/QUOTE]

---

### Post by davebed on 2006-11-15
Thank you araz,

It's not working :(   Could you have a look at the code and see if i made an error?
I know typing the command
```
DISPLAY=:0 xset dpms X
``` works for any value of X when i run it in a terminal

```
#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

function laptop_mode_enable {
    $LAPTOP_MODE start
    
    for x in /sys/bus/ide/devices/*/block; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 100 /dev/$drive 2>/dev/null
	$HDPARM -B 128 /dev/$drive 2>/dev/null
    done
    
    for x in /sys/bus/scsi/devices/*/block; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 100 /dev/$drive 2>/dev/null
	$HDPARM -B 128 /dev/$drive 2>/dev/null
    done
}

function laptop_mode_disable {
    for x in /sys/bus/ide/devices/*/block; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 800 /dev/$drive 2>/dev/null
	$HDPARM -B 255 /dev/$drive 2>/dev/null
    done
    for x in /sys/bus/scsi/devices/*/block; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 800 /dev/$drive 2>/dev/null
	$HDPARM -B 255 /dev/$drive 2>/dev/null
    done
    $LAPTOP_MODE stop
}

getState;

checkStateChanged;

shopt -s nullglob

for x in /proc/acpi/ac_adapter/*; do
    grep -q off-line $x/state

    if [ $? = 0 ] && [ x$1 != xstop ]; then	
	for SCRIPT in /etc/acpi/battery.d/*.sh; do
	    . $SCRIPT
	done
	DISPLAY=:0 xset dpms 60
	if [ x$ENABLE_LAPTOP_MODE = xtrue ]; then
	    (sleep 5 && laptop_mode_enable)&
	fi
    else
	for SCRIPT in /etc/acpi/ac.d/*.sh; do
	    . $SCRIPT
	done
	DISPLAY=:0 xset dpms 180
	if [ x$ENABLE_LAPTOP_MODE = xtrue ]; then
	    (sleep 5 && laptop_mode_disable)&
	fi
    fi
done
```

fglrx-powermode.sh is another script that gets called when i unplug and replug AC
```
#!/bin/bash 

. /etc/default/fglrx
if [ x$FGLRX_ACPI_SWITCH_POWERSTATES != xtrue ]; then
  exit;
fi

getXuser() {
        user=`finger| grep -m1 ":$displaynum " | awk '{print $1}'`
        if [ x"$user" = x"" ]; then
                user=`finger| grep -m1 ":$displaynum" | awk '{print $1}'`
        fi
        if [ x"$user" != x"" ]; then
                userhome=`getent passwd $user | cut -d: -f6`
                export XAUTHORITY=$userhome/.Xauthority
        else
                export XAUTHORITY=""
        fi
}

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]; then
 lid_closed=1
else
 lid_closed=0
fi

grep -q off-line /proc/acpi/ac_adapter/*/state 
if [ $? = 0 ]; then
   on_dc=1
else
   on_dc=0
fi



if [ ${lid_closed} -eq 1 -o ${on_dc} -eq 1 ]; then
    echo "fglrx: setting low power"
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"	    
	    powermode=`/usr/bin/aticonfig --lsp | grep -m1 low | cut -b 3-3`
	    if [ x"$powermode" != x"" ]; then
	        su $user -c "/usr/bin/aticonfig --set-powerstate=$powermode --effective=now" &>/dev/null
	    fi
	fi
    done
else
    echo "fglrx: setting default powermode"
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"
	    powermode=`/usr/bin/aticonfig --lsp | grep -m1 default | cut -b 3-3`
	    if [ x"$powermode" != x"" ]; then
	        su $user -c "/usr/bin/aticonfig --set-powerstate=$powermode --effective=now" &>/dev/null
	    fi
	fi
    done
fi

```

Would it be better placed there?

Any other ideas? Thanks.

---

### Post by shining on 2006-11-15
Maybe you could add an entry in a log file to check that this part is executed.
For example, just before this line:
DISPLAY=:0 xset dpms 60
Add:
echo "xset dpms 60" >> /tmp/power.log

And same for the other line.

Then plug and unplug, and check the /tmp/power.log file.

---

### Post by davebed on 2006-11-15
Thank you Shining,

I see the log entries and they are as expected:
```
xset dpms 60
```
and ```
xset dpms 180
```
Which would indicate that the command has run right?

Why does the command work in a terminal and not like this?

Thanks.

---

### Post by davebed on 2006-11-16
anyone have any ideas?
Thanks

---

### Post by araz on 2006-11-16
> **davebed said:**
> anyone have any ideas?
Thanks

I have no ideia

---

### Post by shining on 2006-11-16
> **davebed said:**
> Thank you Shining,

I see the log entries and they are as expected:
```
xset dpms 60
```
and ```
xset dpms 180
```
Which would indicate that the command has run right?

Why does the command work in a terminal and not like this?

Thanks.

Is this script run as root?
And does it work in a terminal as root?

---

### Post by davebed on 2006-11-17
> **shining said:**
> Is this script run as root?
And does it work in a terminal as root?

I assum that the power.sh scripts is run as root, but I'm not sure. Aren't all system initiated / ACPI scripts run as root?

In any case, in the terminal```
DISPLAY=:0 xset dpms 1

```
turns off the screen in 1 second, for example, whiel:
```
sudo DISPLAY=:0 xset dpms 1

```
returns:
```
sudo: DISPLAY=:0: command not found

```

and if I run ```
xset dpms 1
``` or ```
sudo xset dpms 1
```nothing happens...

Thanks.

---

### Post by shining on 2006-11-17
Anyway, never mind, running it as root makes now difference to me.
Both "xset dpms 1" , and "sudo xset dpms 1" works just fine.
I don't know why you need to set the DISPLAY , the default one should be the correct one. Or maybe you aren't running locally, or aren't using a single X session?

---

