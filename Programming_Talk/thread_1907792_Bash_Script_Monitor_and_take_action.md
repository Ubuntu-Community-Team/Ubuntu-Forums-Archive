---
title: "Bash Script Monitor and take action"
date: 2012-01-12
forum: Programming Talk
---

### Post by Jose Catre-Vandis on 2012-01-12
Hi

I am in the process of writing a bash script (which will run on a netbook) to monitor the status of ac power and take action if the power changes to battery power, namely to suspend the netbook. When the netbook is resumes the script should start again, happy until the ac power changes.

The part that troubles me is how to get the script to keep running after it has told the netbook to suspend. The only way I have found so far is to write a second "inverse" script that watches for a change to ac power from battery power, which then calls the first script again, but this seems over the top. How can I combine the two scripts in to one?(I know about on_ac_power so it's not about how to make the script "work", but scripting and syntax)

**Script (in English)**
```
script 1
Is there ac power?
Yes then loop.
No then run script 2 and suspend.
Exit

script 2
Is there battery power?
Yes then loop. (we only want to suspend after loss of ac power)
No then run script 1.
Exit
```

Also, should I have the script running all the time (so whilst ac power is on it just keeps looping at a timed inteval) or is it "better" to run a cronjob?

---

### Post by ofnuts on 2012-01-13
> **Jose Catre-Vandis said:**
> Hi

I am in the process of writing a bash script (which will run on a netbook) to monitor the status of ac power and take action if the power changes to battery power, namely to suspend the netbook. When the netbook is resumes the script should start again, happy until the ac power changes.

The part that troubles me is how to get the script to keep running after it has told the netbook to suspend. The only way I have found so far is to write a second "inverse" script that watches for a change to ac power from battery power, which then calls the first script again, but this seems over the top. How can I combine the two scripts in to one?(I know about on_ac_power so it's not about how to make the script "work", but scripting and syntax)

**Script (in English)**
```
script 1
Is there ac power?
Yes then loop.
No then run script 2 and suspend.
Exit

script 2
Is there battery power?
Yes then loop. (we only want to suspend after loss of ac power)
No then run script 1.
Exit
```Also, should I have the script running all the time (so whilst ac power is on it just keeps looping at a timed inteval) or is it "better" to run a cronjob?

No need to exit... run your script all the time...

```

if No power suspend.
// you get suspended here, or not
loop // your script resumes there when the computer itself resumes.

```

---

### Post by Toz on 2012-01-13
Why not just use the built-in functionality of pm-utils? Whenever your system goes from power to battery or battery to power, scripts in /usr/lib/pm-utils/power.d and /etc/pm/power.d are run automatically. Local user scripts should be put in **/etc/pm/power.d**.

The script should be in the format of:
```
#!/bin/bash

case $1 in
    true) ### laptop enters battery mode
        # enter your commands here
    ;;
    false) ### laptop enters ac mode
        # enter your commands here
    ;;
    *) exit ;;
esac

```

Make sure you make the file executable (you will need root privleges to create this file). 

If you are looking to simply suspend the computer when it goes to battery mode (kind of curious as to why are trying to do this), I would suggest a script like this:
```
#!/bin/bash

case $1 in
    true) ### laptop enters battery mode
        pm-suspend
    ;;
    false) ### laptop enters ac mode
        # do nothing
    ;;
    *) exit ;;
esac

```

---

### Post by Jose Catre-Vandis on 2012-01-13
Ah Toz, your knowledge of the inner workings once again brings forth rejoicing :)

I'll give this a try and see how it goes.

Why suspend when going to battery? Well this is for a carpc, so when the ac power is off, the ignition is off, I don't need (can't use) the carpc, so it needs to suspend, ready for the ignition to come on. I have a magic button to wake the netbook from sleep!

Many thanks

While I am at it, can I do a similar script in this area to open and close a serial port? I have to connect to a serial port for what I need to do. On boot the serial port is on ttyUSB0, if the laptop goes to sleep and then resumes the serial port then moves to ttyUSB1. After another sleep/wake round it moves back to ttyUSB0. Would be good if I could make it so it was always on ttyUSB0?

---

### Post by Toz on 2012-01-13
> **Jose Catre-Vandis said:**
> Ah Toz, your knowledge of the inner workings once again brings forth rejoicing :)

I'll give this a try and see how it goes.

Why suspend when going to battery? Well this is for a carpc, so when the ac power is off, the ignition is off, I don't need (can't use) the carpc, so it needs to suspend, ready for the ignition to come on. I have a magic button to wake the netbook from sleep!

Many thanks
Cool.

> While I am at it, can I do a similar script in this area to open and close a serial port? I have to connect to a serial port for what I need to do. On boot the serial port is on ttyUSB0, if the laptop goes to sleep and then resumes the serial port then moves to ttyUSB1. After another sleep/wake round it moves back to ttyUSB0. Would be good if I could make it so it was always on ttyUSB0?
What command are you using now to open/close the serial port? Off the top of my head, run the open port command on startup, and then create another script in /etc/pm/power.d to close the port when laptop goes to battery and the same command to open when it then comes back to ac mode. This might actually ensure the same port is being used.

---

### Post by Jose Catre-Vandis on 2012-01-13
I don't have to do anything for the port to be "open" or recognised, the kernel takes care of that (reported in dmesg). So on boot in dmesg it reports ttyUSB0 then after sleep USB1 and then back to USB0 and so on. How would I programmatically unplug the usb serial converter and plug it back in? (The usb location does not change).

---

### Post by Jose Catre-Vandis on 2012-01-13
> **Toz said:**
> Why not just use the built-in functionality of pm-utils? Whenever your system goes from power to battery or battery to power, scripts in /usr/lib/pm-utils/power.d and /etc/pm/power.d are run automatically. Local user scripts should be put in **/etc/pm/power.d**.

The script should be in the format of:
```
#!/bin/bash

case $1 in
    true) ### laptop enters battery mode
        # enter your commands here
    ;;
    false) ### laptop enters ac mode
        # enter your commands here
    ;;
    *) exit ;;
esac

```

Make sure you make the file executable (you will need root privleges to create this file). 

If you are looking to simply suspend the computer when it goes to battery mode (kind of curious as to why are trying to do this), I would suggest a script like this:
```
#!/bin/bash

case $1 in
    true) ### laptop enters battery mode
        pm-suspend
    ;;
    false) ### laptop enters ac mode
        # do nothing
    ;;
    *) exit ;;
esac

```

This is excellent, just tested, works a treat, and just what I was after. And even better it works when xbmc is in full screen, which was a problem I was also having. Two for the price of one!! :) Many thanks.

---

### Post by Jose Catre-Vandis on 2012-01-13
> **ofnuts said:**
> No need to exit... run your script all the time...

```

if No power suspend.
// you get suspended here, or not
loop // your script resumes there when the computer itself resumes.

```

Thanks **ofnuts**, I'll give this a try too, as it can give me the option of running the netbook on battery when I need to. Can't see a way to stop a suspend in the way you can with "shutdown -c".

---

### Post by Toz on 2012-01-13
> **Jose Catre-Vandis said:**
> I don't have to do anything for the port to be "open" or recognised, the kernel takes care of that (reported in dmesg). So on boot in dmesg it reports ttyUSB0 then after sleep USB1 and then back to USB0 and so on. How would I programmatically unplug the usb serial converter and plug it back in? (The usb location does not change).

Can you post back the results of:
```
lsmod
```
and the contents of dmesg where its reporting the port changes?

---

### Post by Jose Catre-Vandis on 2012-01-14
I took the usb connector out of the car so it wasn't connected up, and ttyUSB0 seems to persist across sleep/awakes. I was getting a different result when connected to the car so will have to go off and test again. ( A bit cold outside!)

Here is dmesg output on the bench

```
[  578.184135] usb 2-1: new full speed USB device number 3 using uhci_hcd
[  578.508398] usbcore: registered new interface driver usbserial
[  578.508460] USB Serial support registered for generic
[  578.508552] usbcore: registered new interface driver usbserial_generic
[  578.508560] usbserial: USB Serial Driver core
[  578.525007] USB Serial support registered for cp210x
[  578.526692] cp210x 2-1:1.0: cp210x converter detected
[  578.636160] usb 2-1: reset full speed USB device number 3 using uhci_hcd
[  578.791676] usb 2-1: cp210x converter now attached to ttyUSB0
[  578.791744] usbcore: registered new interface driver cp210x
[  578.791752] cp210x: v0.09:Silicon Labs CP210x RS232 serial adaptor driver


[  775.810453] cp210x 2-1:1.0: cp210x converter detected
[  775.920147] usb 2-1: reset full speed USB device number 3 using uhci_hcd
[  776.066788] usb 2-1: cp210x converter now attached to ttyUSB0
[  776.104515] PM: resume devices took 2.116 seconds
[  776.104601] PM: Finishing wakeup.
```

And here is dmesg output in the car

```
[  989.008200] usb 2-1: new full speed USB device number 4 using uhci_hcd
[  989.181516] cp210x 2-1:1.0: cp210x converter detected
[  989.292197] usb 2-1: reset full speed USB device number 4 using uhci_hcd
[  989.443709] usb 2-1: cp210x converter now attached to ttyUSB0
[  997.376221] usb 2-1: USB disconnect, device number 4
[  997.376737] cp210x ttyUSB0: cp210x converter now disconnected from ttyUSB0
[  997.376834] cp210x 2-1:1.0: device disconnected

[ 1701.070254] cp210x 2-1:1.0: cp210x converter detected
[ 1701.180098] usb 2-1: reset full speed USB device number 6 using uhci_hcd
[ 1701.327288] usb 2-1: cp210x converter now attached to ttyUSB1
[ 1701.396426] PM: resume devices took 2.088 seconds
[ 1701.396512] PM: Finishing wakeup.


```

I have a simple script that can test for the tty and start my communication program, openbm-gateway, but this means I have to close it (openbm-gateway) on sleep and restart. Openbm-gateway survives sleep/wakes OK. So would be better to ensure that the tty stays the same.


However another problem has arisen, using the script in power.d, the PC won't always sleep the first time I go to battery. I have to connect the ac power and disconnect again to get it to sleep? This is fun in the car because if you turn of the iginition the PC stays awake then as you go to start the car you have power then lose it then have it again, so PC goes to sleep once car is started again :)

---

### Post by Toz on 2012-01-14
> **Jose Catre-Vandis said:**
> I took the usb connector out of the car so it wasn't connected up, and ttyUSB0 seems to persist across sleep/awakes. I was getting a different result when connected to the car so will have to go off and test again. ( A bit cold outside!)

Here is dmesg output on the bench

```
[  578.184135] usb 2-1: new full speed USB device number 3 using uhci_hcd
[  578.508398] usbcore: registered new interface driver usbserial
[  578.508460] USB Serial support registered for generic
[  578.508552] usbcore: registered new interface driver usbserial_generic
[  578.508560] usbserial: USB Serial Driver core
[  578.525007] USB Serial support registered for cp210x
[  578.526692] cp210x 2-1:1.0: cp210x converter detected
[  578.636160] usb 2-1: reset full speed USB device number 3 using uhci_hcd
[  578.791676] usb 2-1: cp210x converter now attached to ttyUSB0
[  578.791744] usbcore: registered new interface driver cp210x
[  578.791752] cp210x: v0.09:Silicon Labs CP210x RS232 serial adaptor driver


[  775.810453] cp210x 2-1:1.0: cp210x converter detected
[  775.920147] usb 2-1: reset full speed USB device number 3 using uhci_hcd
[  776.066788] usb 2-1: cp210x converter now attached to ttyUSB0
[  776.104515] PM: resume devices took 2.116 seconds
[  776.104601] PM: Finishing wakeup.
```

And here is dmesg output in the car

```
[  989.008200] usb 2-1: new full speed USB device number 4 using uhci_hcd
[  989.181516] cp210x 2-1:1.0: cp210x converter detected
[  989.292197] usb 2-1: reset full speed USB device number 4 using uhci_hcd
[  989.443709] usb 2-1: cp210x converter now attached to ttyUSB0
[  997.376221] usb 2-1: USB disconnect, device number 4
[  997.376737] cp210x ttyUSB0: cp210x converter now disconnected from ttyUSB0
[  997.376834] cp210x 2-1:1.0: device disconnected

[ 1701.070254] cp210x 2-1:1.0: cp210x converter detected
[ 1701.180098] usb 2-1: reset full speed USB device number 6 using uhci_hcd
[ 1701.327288] usb 2-1: cp210x converter now attached to ttyUSB1
[ 1701.396426] PM: resume devices took 2.088 seconds
[ 1701.396512] PM: Finishing wakeup.


```

I have a simple script that can test for the tty and start my communication program, openbm-gateway, but this means I have to close it (openbm-gateway) on sleep and restart. Openbm-gateway survives sleep/wakes OK. So would be better to ensure that the tty stays the same.
Interesting. I'm not sure how to help solve this issue.


> However another problem has arisen, using the script in power.d, the PC won't always sleep the first time I go to battery. I have to connect the ac power and disconnect again to get it to sleep? This is fun in the car because if you turn of the iginition the PC stays awake then as you go to start the car you have power then lose it then have it again, so PC goes to sleep once car is started again :)
When you try it in the car, what does /var/log/powersave.log say? And can you post back the contents of the script you are using?

---

### Post by Jose Catre-Vandis on 2012-01-14
Ah, looks like its the wireless interface causing the problems (seems to be backed up by what is in pm-suspend.log too). I only have a pm-powersave.log but guess this is the same one. Log from when I started using the script in power.d (see attached), as the problem occured both in and out of the car.

[ATTACH]210855[/ATTACH]

Regarding the script, I am only using an exact copy of the script you indicated to get suspend when going to battery at present for testing:

```
#!/bin/bash

case $1 in
    true) ### laptop enters battery mode
        pm-suspend
    ;;
    false) ### laptop enters ac mode
        # do nothing
    ;;
    *) exit ;;
esac
```

I'll try things with the wireless off, don't need it for the car, at present, unless there is a fix? I can always script wireless to go off?

Sorry, I forgot to do an lsmod when I had the usb serial device connected. I guess if there is a module, rmmod might do the trick. I'll venture out into the cold once again :)

Yep I get the following difference between an lsmod before and after pluggin ing the usb serial interface:

```

$ diff lsmod1.txt lsmod2.txt
1a2,3
> cp210x         17464   0
> usbserial      37203   1  cp210x
```

Thanks for your help and pointer to the log, Toz.

---

### Post by Jose Catre-Vandis on 2012-01-15
Taken a slightly different approach in trying to resolve all my variables. For now will be satisfied with complete shutdown on laptop when ignition goes off. So here is the script I'll put in start up. Yet to test it fully:

```

#!/bin/bash

### powerwatch.sh
### created by Jose Catre-Vandis
### for carpc
### run this script on start up of laptop
### will start all required programs
### shuts down laptop if ignition switched off
### should keep working after a sleep or hibernate too?

while :

do
	if on_ac_power; then
		sleep 2
		### starts xbmc
		if [ -z  $(pgrep xbmc.bin) ]; then
		xbmc &
		fi
		### starts openbm-gateway
		if [ -z  $(pgrep openbm-gateway) ]; then
		openbm-gateway &
		fi
		### blanks laptop screen (its in the boot!)
		if [[ $(xrandr -q | grep "current 1024 x 600") ]]; then
		xrandr --output LVDS1 --off
		fi
	else
		### turn laptop screen on
                xrandr --output LVDS1 --auto
                ### dialog popup to allow user to cancel shutdown
		### for whatever reason. Defaults to YES after timeout!
		zenity --question --text='Do you want to Shutdown (Yes) \
		or continue working on battery power? (No)' --title='Shutdown ?' \
		--width=400 --height=100 --timeout=5
		if [ $? = 5 ]; then
		### shuts down xbmc gracefully (?)
		wmctrl -c "XBMC Media Center"
		### shuts down openbm-gateway
		killall openbm-gateway
		### shuts down laptop, assumes script not run as root 
		### resolves ttyUSB0 assignment, only takes 30 seconds to boot
		echo "xxxx" | sudo -S shutdown -h now
		else
                xrandr --output LVDS1 --auto
		exit
		fi 
	fi
done

```

---

