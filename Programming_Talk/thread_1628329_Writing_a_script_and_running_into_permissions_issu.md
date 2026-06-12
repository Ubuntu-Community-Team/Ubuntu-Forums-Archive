---
title: "Writing a script and running into permissions issues."
date: 2010-11-22
forum: Programming Talk
---

### Post by brennydoogles on 2010-11-22
So I recently wrote a script that toggles my laptop's touchpad on or off using xinput, and it works beautifully when run from terminal. I was attempting to set this script to auto-run whenever my mouse is plugged in, but it seems to be running the script (echo statements I put in the script for debugging are working) without actually disabling the touchpad. I am using halevt to detect the device and launch the command, so I assume I am doing something wrong with halevt and permissions. Any ideas?

The Script:
```

# toggleTouchpad by Brendon Dugan
# Toggles a touchpad on or off depending on it's current state or CLI argument
#
# To configure, run the command 'xinput list' in terminal and identify your touch pad.
# Using the output of the above command, change the touchpadString variable to a substring
# of your touchpad's description that is unique to that device.
#
# To run, simply type 'toggleTouchpad' to toggle your touchpad on or off, or
# 'toggleTouchpad on' to explicitly turn your touchpad on, or
# 'toggleTouchpad off' to explicitly turn it off.
#
# Enjoy!
touchpadString="TouchPad"
touchpadID=$(xinput list | grep $touchpadString | awk -F " " '{print $6}' | awk -F "=" '{print $2}')
touchpadEnabled=$(xinput list-props $touchpadID | grep "Device Enabled" | awk -F ":" '{print $2}')

# Check for arguments on the command line
if test $# -eq 1
then
	# Change the argument to lowercase
	arg1=$(echo $1 | tr [:upper:] [:lower:])
	cliArg=1
else
	# There is no argument.
	cliArg=0
fi

if [ $cliArg -eq 1 ]
then
	# If there's an argument, check to see whether it is on, off, or junk
	if [ $arg1 = 'on' ]
	then
		# The argument was 'on', so turn the touchpad on 
		xinput --set-prop $touchpadID "Device Enabled" 1
		echo "ON"
	elif [ $arg1 = 'off' ]
	then
		# The argument was 'off', so turn the touchpad off 
		xinput --set-prop $touchpadID "Device Enabled" 0
		echo "OFF"
	else
		# The argument was junk, so do nothing 
		sleep 1
	fi
else
	# There was no argument, so just toggle the touchpad to the opposite
	# of the state it has now.
	if [ $touchpadEnabled -eq 1 ]
	then
		xinput --set-prop $touchpadID "Device Enabled" 0
	else
		xinput --set-prop $touchpadID "Device Enabled" 1
	fi
fi

```

The command to launch halevt:
```

sudo halevt -u brendon -g brendon -c /home/brendon/.halevt.xml

```

The halevt config file:
```

<?xml version="1.0" encoding="UTF-8"?>
<halevt:Configuration version="0.1" xmlns:halevt="http://www.environnement.ens.fr/perso/dumas/halevt.html">
	<halevt:Device match="hal.info.udi = /org/freedesktop/Hal/devices/usb_device_46d_c70e_00076142E023">
		<halevt:Insertion exec="/home/brendon/bin/toggleTouchpad off"/>
		<halevt:Removal exec="/home/brendon/bin/toggleTouchpad on"/>
	</halevt:Device>
</halevt:Configuration>

```

---

### Post by ziekfiguur on 2010-11-22
I have my own script, which switches the touchpad on when it's off and off when it's on. with the touchpad device name hardcoded in the script. I used System>Preferences>Keyboard Shortcuts to run the script whenever i press the windows key and F2.
That's not really what you're trying to do, but it works for me and it might work for you as well :P

---

### Post by spjackson on 2010-11-22
Some things I'd check.

1. In the environment where there script runs automatically and doesn't work, is the DISPLAY environment variable set?
2. Under which user account does it run? 
3. Does stderr go anywhere?

---

### Post by brennydoogles on 2010-11-22
> **ziekfiguur said:**
> I have my own script, which switches the touchpad on when it's off and off when it's on. with the touchpad device name hardcoded in the script. I used System>Preferences>Keyboard Shortcuts to run the script whenever i press the windows key and F2.
That's not really what you're trying to do, but it works for me and it might work for you as well :P

I actually have mine set to a keyboard shortcut as well, but would like to automate it even more.

---

### Post by brennydoogles on 2010-11-22
> **spjackson said:**
> Some things I'd check.

1. In the environment where there script runs automatically and doesn't work, is the DISPLAY environment variable set?
2. Under which user account does it run? 
3. Does stderr go anywhere?

Those are great questions... unfortunately I have no idea. Any suggestions on how to find out the answers?

---

### Post by ziekfiguur on 2010-11-23
1:
```

if [ -n "$DISPLAY ]
then
    #Display is set
fi

```
2:
```

echo "$USER" > /tmp/somefile

```
and check the contents of somefile after the script has been run.

don't know about 3 though, sorry.

---

### Post by Arndt on 2010-11-23
I don't know if this helps, but I added a line to report the new setting after disabling the touchpad:

```
		xinput --set-prop $touchpadID "Device Enabled" 0
		xinput list-props $touchpadID| grep "Enabled"

```

and it reports 1 when run from halevt, even though we set it to 0 on the line before.

---

### Post by spjackson on 2010-11-23
> **ziekfiguur said:**
> 1:
```

if [ -n "$DISPLAY ]
then
    #Display is set
fi

```2:
```

echo "$USER" > /tmp/somefile

```and check the contents of somefile after the script has been run.

don't know about 3 though, sorry.
Agreed. brennydoogles, you said that you had put echo statements in to show that it was being called, so I'd just do:
```

echo "DISPLAY is $DISPLAY" >> /tmp/somefile
id >> /tmp/somefile

```I don't know where stderr is going to. I'd need to investigate the documentation for halevt, but I would also put something in to force an error and see if I can find where it goes. e.g. 
```

ls no/such/file

```

---

### Post by Arndt on 2010-11-23
> **Arndt said:**
> I don't know if this helps, but I added a line to report the new setting after disabling the touchpad:

```
		xinput --set-prop $touchpadID "Device Enabled" 0
		xinput list-props $touchpadID| grep "Enabled"

```

and it reports 1 when run from halevt, even though we set it to 0 on the line before.

I think something else is enabling the touchpad. If I do this:

```
		xinput --set-prop $touchpadID "Device Enabled" 0
		xinput list-props $touchpadID| grep "Enabled"
		xinput --set-prop $touchpadID "Device Enabled" 0
		xinput list-props $touchpadID| grep "Enabled"
		xinput --set-prop $touchpadID "Device Enabled" 0
		xinput list-props $touchpadID| grep "Enabled"
		sleep 5
		xinput list-props $touchpadID| grep "Enabled"
		xinput --set-prop $touchpadID "Device Enabled" 0
		xinput list-props $touchpadID| grep "Enabled"
		xinput --set-prop $touchpadID "Device Enabled" 0
		xinput list-props $touchpadID| grep "Enabled"
		sleep 5
		xinput list-props $touchpadID| grep "Enabled"
		xinput --set-prop $touchpadID "Device Enabled" 0
		xinput list-props $touchpadID| grep "Enabled"
		xinput --set-prop $touchpadID "Device Enabled" 0
		xinput list-props $touchpadID| grep "Enabled"
```

the output (captured in a file) is this:

	Device Enabled (125):	0
	Device Enabled (125):	0
	Device Enabled (125):	1
	Device Enabled (125):	1
	Device Enabled (125):	0
	Device Enabled (125):	0
	Device Enabled (125):	0
	Device Enabled (125):	0
	Device Enabled (125):	0

---

### Post by brennydoogles on 2010-11-23
> **Arndt said:**
> I think something else is enabling the touchpad. If I do this:

```
		xinput --set-prop $touchpadID "Device Enabled" 0
		xinput list-props $touchpadID| grep "Enabled"
		xinput --set-prop $touchpadID "Device Enabled" 0
		xinput list-props $touchpadID| grep "Enabled"
		xinput --set-prop $touchpadID "Device Enabled" 0
		xinput list-props $touchpadID| grep "Enabled"
		sleep 5
		xinput list-props $touchpadID| grep "Enabled"
		xinput --set-prop $touchpadID "Device Enabled" 0
		xinput list-props $touchpadID| grep "Enabled"
		xinput --set-prop $touchpadID "Device Enabled" 0
		xinput list-props $touchpadID| grep "Enabled"
		sleep 5
		xinput list-props $touchpadID| grep "Enabled"
		xinput --set-prop $touchpadID "Device Enabled" 0
		xinput list-props $touchpadID| grep "Enabled"
		xinput --set-prop $touchpadID "Device Enabled" 0
		xinput list-props $touchpadID| grep "Enabled"
```

the output (captured in a file) is this:

	Device Enabled (125):	0
	Device Enabled (125):	0
	Device Enabled (125):	1
	Device Enabled (125):	1
	Device Enabled (125):	0
	Device Enabled (125):	0
	Device Enabled (125):	0
	Device Enabled (125):	0
	Device Enabled (125):	0


On my machine this results in the following output:
```

Device Enabled (125):	0
Device Enabled (125):	0
Device Enabled (125):	0
Device Enabled (125):	0
Device Enabled (125):	0
Device Enabled (125):	0
Device Enabled (125):	0
Device Enabled (125):	0
Device Enabled (125):	0

```

Which also successfully disabled the touchpad. If you have Ubuntu set to automatically disable your touchpad while you type, it could be creating the output you received by re-enabling the touchpad after the specified period of time from when you typed the command. I have that feature disabled, so it appears to be a possible candidate.

---

### Post by Arndt on 2010-11-23
> **brennydoogles said:**
> On my machine this results in the following output:
```

Device Enabled (125):	0
Device Enabled (125):	0
Device Enabled (125):	0
Device Enabled (125):	0
Device Enabled (125):	0
Device Enabled (125):	0
Device Enabled (125):	0
Device Enabled (125):	0
Device Enabled (125):	0

```

Which also successfully disabled the touchpad. If you have Ubuntu set to automatically disable your touchpad while you type, it could be creating the output you received by re-enabling the touchpad after the specified period of time from when you typed the command. I have that feature disabled, so it appears to be a possible candidate.

I seem to get the 1's in both cases. But are you saying that your script works now, or that the touchpad gets enabled later anyway?

---

### Post by brennydoogles on 2010-11-23
> **spjackson said:**
> Agreed. brennydoogles, you said that you had put echo statements in to show that it was being called, so I'd just do:
```

echo "DISPLAY is $DISPLAY" >> /tmp/somefile
id >> /tmp/somefile

```I don't know where stderr is going to. I'd need to investigate the documentation for halevt, but I would also put something in to force an error and see if I can find where it goes. e.g. 
```

ls no/such/file

```

Ok, so it seems that stderr is missing. Here is the output with the above changes:

```

DISPLAY is :0.0
uid=1000(brendon) gid=1000(brendon) groups=1000(brendon),4(adm),20(dialout),24(cdrom),46(plugdev),110(netdev),111(lpadmin),119(admin),122(sambashare)
brendon

```

Even redirecting stderr to a file in the halevt config produces a blank log. Here's how I did that btw:
```

<halevt:Device match="hal.info.udi = /org/freedesktop/Hal/devices/usb_device_46d_c70e_00076142E023">
		<halevt:Insertion exec="/home/brendon/bin/toggleTouchpad off2>>/home/brendon/log"/>
		<halevt:Removal exec="/home/brendon/bin/toggleTouchpad on2>>/home/brendon/log"/>
	</halevt:Device>

```

---

### Post by Arndt on 2010-11-23
> **brennydoogles said:**
> On my machine this results in the following output:
```

Device Enabled (125):	0
Device Enabled (125):	0
Device Enabled (125):	0
Device Enabled (125):	0
Device Enabled (125):	0
Device Enabled (125):	0
Device Enabled (125):	0
Device Enabled (125):	0
Device Enabled (125):	0

```

Which also successfully disabled the touchpad. If you have Ubuntu set to automatically disable your touchpad while you type, it could be creating the output you received by re-enabling the touchpad after the specified period of time from when you typed the command. I have that feature disabled, so it appears to be a possible candidate.

I realize now you may have misunderstood me. My experiment was not done by running from the command line, but from halevt. I let it call a script, which in turn redirected all output to a file. I got nothing on stderr, by the way.

When running from the command line, I get only 0's whether the disable-while-you-type setting is true or not.

---

### Post by brennydoogles on 2010-11-23
> **Arndt said:**
> I seem to get the 1's in both cases. But are you saying that your script works now, or that the touchpad gets enabled later anyway?

Lol. My script has always worked when run from terminal. Running the commands you posted from terminal (in a script) works as well. The only time it is not working is when halevt runs it, which is strange because halevt appears to be running it with my permissions.

---

### Post by spjackson on 2010-11-23
> **brennydoogles said:**
> Ok, so it seems that stderr is missing.

Even redirecting stderr to a file in the halevt config produces a blank log. Here's how I did that btw:
```

<halevt:Device match="hal.info.udi = /org/freedesktop/Hal/devices/usb_device_46d_c70e_00076142E023">
        <halevt:Insertion exec="/home/brendon/bin/toggleTouchpad off2>>/home/brendon/log"/>
        <halevt:Removal exec="/home/brendon/bin/toggleTouchpad on2>>/home/brendon/log"/>
    </halevt:Device>

```
If it just accepts normal shell syntax in the exec, then you would need a space between off and 2, and on and 2. Otherwise the 2 is part of the parameter.

---

### Post by Arndt on 2010-11-23
> **brennydoogles said:**
> Lol. My script has always worked when run from terminal. Running the commands you posted from terminal (in a script) works as well. The only time it is not working is when halevt runs it, which is strange because halevt appears to be running it with my permissions.

Try this:

1) Disable the touchpad
2) Insert the USB mouse (remove it first if it was present)

I think you will find that the touchpad is now enabled.

---

### Post by brennydoogles on 2010-11-23
> **Arndt said:**
> Try this:

1) Disable the touchpad
2) Insert the USB mouse (remove it first if it was present)

I think you will find that the touchpad is now enabled.

Hmmm... you are correct. Do you have any idea why this is true?

---

### Post by Arndt on 2010-11-23
> **brennydoogles said:**
> Hmmm... you are correct. Do you have any idea why this is true?

Well, as I wrote before, my theory is that something else enables the touchpad when the USB mouse is added - maybe even when anything USB device at all is added, I haven't tried that. Some daemon which is awakened on USB events. I've looked a little at 'hald' and 'usb' things but this is not something I'm familiar with at all. Maybe it's a good idea to ask in a more device-oriented forum here. In the system logs, I can see that USB things happen, but not any indication of what particular program is run.

---

### Post by brennydoogles on 2010-11-23
> **Arndt said:**
> Well, as I wrote before, my theory is that something else enables the touchpad when the USB mouse is added - maybe even when anything USB device at all is added, I haven't tried that. Some daemon which is awakened on USB events. I've looked a little at 'hald' and 'usb' things but this is not something I'm familiar with at all. Maybe it's a good idea to ask in a more device-oriented forum here. In the system logs, I can see that USB things happen, but not any indication of what particular program is run.

Good to know. Thanks for the help!

---

### Post by brennydoogles on 2010-11-23
> **Arndt said:**
> ... my theory is that something else enables the touchpad when the USB mouse is added - 

Genius! This got me to thinking, what if I simply wait a couple seconds or so after the mouse is detected to change the touchpad state? I seem to be having success now, and I'm just playing with it to see exactly how long I need to wait. I will be marking the thread solved in a moment after I post a fixed script!

---

### Post by brennydoogles on 2010-11-23
Working script and config file below, as well as the command I used to launch it successfully!

Command:
```
halevt -c /home/brendon/.halevt.xml
```

Config file (.halevt.xml):
```

<?xml version="1.0" encoding="UTF-8"?>
<halevt:Configuration version="0.1" xmlns:halevt="http://www.environnement.ens.fr/perso/dumas/halevt.html">
	<halevt:Device match="hal.info.udi = /org/freedesktop/Hal/devices/usb_device_46d_c70e_00076142E023">
		<halevt:Insertion exec="/home/brendon/bin/toggleTouchpad off"/>
		<halevt:Removal exec="/home/brendon/bin/toggleTouchpad on"/>
	</halevt:Device>
</halevt:Configuration>

```

toggleTouchpad:
```

# toggleTouchpad by Brendon Dugan
# Toggles a touchpad on or off depending on it's current state or CLI argument
#
# To configure, run the command 'xinput list' in terminal and identify your touch pad.
# Using the output of the above command, change the touchpadString variable to a substring
# of your touchpad's description that is unique to that device.
#
# To run, simply type 'toggleTouchpad' to toggle your touchpad on or off, or
# 'toggleTouchpad on' to explicitly turn your touchpad on, or
# 'toggleTouchpad off' to explicitly turn it off.
#
# Enjoy!
touchpadString="TouchPad"
touchpadID=$(xinput list | grep $touchpadString | awk -F " " '{print $6}' | awk -F "=" '{print $2}')
touchpadEnabled=$(xinput list-props $touchpadID | grep "Device Enabled" | awk -F ":" '{print $2}')
sleeptime=1


# Check for arguments on the command line
if test $# -eq 1
then
	# Change the argument to lowercase
	arg1=$(echo $1 | tr [:upper:] [:lower:])
	cliArg=1
else
	# There is no argument.
	cliArg=0
fi

if [ $cliArg -eq 1 ]
then
	# If there's an argument, check to see whether it is on, off, or junk
	if [ $arg1 = 'on' ]
	then
		# The argument was 'on', so turn the touchpad on 
		sleep $sleeptime
		xinput --set-prop $touchpadID "Device Enabled" 1
	elif [ $arg1 = 'off' ]
	then
		# The argument was 'off', so turn the touchpad off 
		sleep $sleeptime
		xinput --set-prop $touchpadID "Device Enabled" 0
	else
		# The argument was junk, so do nothing 
		echo $arg1
		sleep 1
	fi
else
	# There was no argument, so just toggle the touchpad to the opposite
	# of the state it has now.
	if [ $touchpadEnabled -eq 1 ]
	then
		xinput --set-prop $touchpadID "Device Enabled" 0
	else
		xinput --set-prop $touchpadID "Device Enabled" 1
	fi
fi

```

Thanks for the help!

---

### Post by SnappyU on 2011-02-02
Thanks for sharing your script.

I'm compelled to do a similar script to do something when I plugin my mobile phone.

1. On mobile phone plugged in, trigger script.
2. Script to synchronise certain files.

This would make it much easier to keep my mobile phone and my notebook/netbook synced up.

Ah, Palm ... why did you collapse?

Thanks again!

---

