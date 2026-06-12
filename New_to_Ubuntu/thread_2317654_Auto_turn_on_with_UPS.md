---
title: "Auto turn on with UPS ?"
date: 2016-03-18
forum: New to Ubuntu
---

### Post by Greg Mueller on 2016-03-18
I have a computer that runs Kubuntu 14. I use it solely for transmitting my weather station info to Weather Underground. It takes in the info from the weather station (via RS232) and sends it on via the internet.
Lately we have had a number of power outages because of storms, some outages have lasted many hours or a day or longer. The problem is that I am not always there to start things back up and may be gone for days before I can get back. During that time the computer is off.
I have the computer set to power on when electricity is restored, but lately it seems to be confused when trying to power up and hangs on the grub display even though there is no other OS on the hard drive.

I just bought a UPS (1350) which will probably last several hours. It will safely power down the computer when the power goes out, but the problem is how to turn the computer back on when the power is restored without me having to physically push the on button.

I'm trying to get some ideas for how to resolve this. Currently I am away from home and the power has come back on but I'm not there to restart the computer.

Ideas?

---

### Post by DuckHook on 2016-03-18
Hi Greg,

I am confused about something: you mention that you have set the BIOS to power on automatically after a shutdown (a HW setting) but that it hangs at GRUB. But then you say that you have to "physically push the on button". If your computer boots and takes you to GRUB, why do you still have to push the on button? Are you saying that physically powering the machine on won't hang it vs auto-restart hangs? At any time in the past, and especially before all the power outtages, did it ever automatically recover with a proper auto-restart?

At any rate, I would start by reinstalling GRUB. Instructions [here]("https://help.ubuntu.com/community/Grub2/Installing"). Make sure to backup all your data first. Check to make sure the following line is in /etc/default/grub```
GRUB_DEFAULT=0
```After reinstalling GRUB, remember to run```
sudo update-grub
```If all else fails, try reinstalling the entire system. It doesn't sound like this would be too onerous, since it is a single-use box.

---

### Post by Greg Mueller on 2016-03-18
It used to power up after power loss fine. But something seems to have changed and I didn't do any of the changing. I was thinking maybe it got it's brains scrambled after one of the loss of power(s). 
I'm pretty sure I know what I will find when I get home and flip on the monitor. It will be stuck on the grub selection page. The past couple times all I have to do is hit return and it will boot, but that there are potential choices to make is confusing since there's only one OS.

Seems like it always does it the day after I leave for a couple weeks

Just to clarify....... if there is a power outage and it self starts when the power returns, it hangs at grub.
If I power down normally and start it by pushing the "On" button it boots fine.

I was hoping by using a UPS and having it power down normally I could figure a way (when the power comes back) to have it reboot via the bios.....but how will the computer know that the power has come back?
Still looking forward to experimenting with the UPS and what software is available.

Maybe a linear solenoid to push the on button...

---

### Post by DuckHook on 2016-03-18
Please post output of```
cat /etc/default/grub
```

---

### Post by Greg Mueller on 2016-03-18
It will be a week until I return home....but I will

---

### Post by DuckHook on 2016-03-18
I'll try to remember to refrain from deleting the subscription to this thread. I usually delete thread subscriptions that are stagnant more than three days.

---

### Post by him610 on 2016-03-19
> UPS (1350)
I assume that means  1350 VA. I wonder how long a Raspberry Pi running Raspbian would operate from a UPS with that capacity. The Rpi draws a maximum of 1 amp, not sure about Pi3. A knowledgeable EE could probably figure it out, but I am neither. My guess is that it would probably operate until the power came back on. 
Maybe  Greg Mueller should consider another computer, ie Rpi.;)

---

### Post by Greg Mueller on 2016-03-19
> **hgh9mrp said:**
> I assume that means  1350 VA. I wonder how long a Raspberry Pi running Raspbian would operate from a UPS with that capacity. The Rpi draws a maximum of 1 amp, not sure about Pi3. A knowledgeable EE could probably figure it out, but I am neither. My guess is that it would probably operate until the power came back on.
Maybe  Greg Mueller should consider another computer, ie Rpi.;)

The UPS is a [B]CyberPower CP1350AVRLCD Intelligent LCD Series UPS 1350VA 810W AVR Mini-Tower
[/B]
Currently (ha) I am using a **Dell OptiPlex 745** (Craigslist) that I put a solid state HD in because the one that was in it was dead. I paid $50 for the computer. I figured the SSD would use less juice.
If I could come up with an even simpler solution I wouldn't mind (as long as it was cheap) It only runs one program *The Weather Underground HeavyWeather Uploader (WUHU)* which I run under WINE.
As I said the weather data comes in via RS232 and out via LAN but that will probably change when I upgrade my weather station and then it will come in via USB.

I have heard there are single board single purpose "computers" out there but I doubt I am tech savvy enough to figure that out.
It would be an interesting pass-time though

---

### Post by grahammechanical on 2016-03-19
The loading of the OS should not hang at the Grub menu. The default setting is to load the first OS after waiting for 10 seconds. Unless a key is pressed then wait indefinitely. The file referred to by DuckHook is /usr/share/grub/default/grub. Look for the line that says GRUB_TIMEOUT=

If GRUB_TIMEOUT=10, then the menu will display for 10 seconds before loading the first OS. If GRUB_DEFAULT=0, then the menu will not display and Grub will load the OS immediately. If GRUB_TIMEOUT=-1, then Grub will wait indefinitely.

From the Grub manual

> GRUB_TIMEOUT&#8217;
Boot the default entry this many seconds after the menu is displayed, unless a key is pressed. The default is &#8216;5&#8217;. Set to &#8216;0&#8217; to boot immediately without displaying the menu, or to &#8216;-1&#8217; to wait indefinitely.

The default for Ubuntu is '10'. Does the machine hang at the Grub menu every time it is restarted? Does it ever automatically load the OS after the time out has expired? If it hangs at every restart and GRUB_TIMEOUT is not set to '-1' then look for a sticky key on the keyboard.

Theoretically, there should be no difference between a user controlled power off & restart and the motherboard restarting after electrical power is restored. Not as far as Grub is concerned. 

Regards.

---

### Post by Greg Mueller on 2016-03-19
Thanks for that interesting info.
I'll have to play with it when I get home.

---

### Post by grahammechanical on 2016-03-19
> but how will the computer know that the power has come back?

My understanding of an UPS system is that the mains power supply is connected to the UPS unit input socket and the PC power line is connected the UPS output socket. The PC gets its power from the mains power supply directly until the mains power drops out and then the UPS unit switches power from its battery to the UPS output socket powering the PC.

There is a diagram in this Wikipedia page.

Once, the mains power comes back on the UPS unit should switch back to allowing the mains power to go directly to the unit's output sockets and so to the PC. At the same time recharging its battery.

Quality of the mains supply after power is restored might be a factor in this. Powering a PC; recharging UPS batteries; powering other computer equipment connected to the UPS; powering other electrical equipment in the building and all the other buildings in town and at a time when the mains electrical supply has not reached optimum power levels. 

Regards.

---

### Post by Greg Mueller on 2016-03-19
Are you saying that the plugin that the computer is plugged in to will shut down after the computer shuts down (via USB ?) and then turns back on when the power comes back?
That would be the perfect answer.

---

### Post by Greg Mueller on 2016-03-24
Got home and as I expected it was stuck on the GRUB page. All I had to do is hit <RETURN> and it started right up. Here is what it said......

(The first line ***Ubuntu** was highlighted)


**GNU GRUB version 2.02~beta2-9ubuntu1.2**

*Ubuntu
advanced options for ubuntu
memory test (memtest86+)
memory test (memtest86+, serial console 115200)

---

### Post by Greg Mueller on 2016-03-24
> **DuckHook said:**
> Please post output of```
cat /etc/default/grub
```



**Here you go......**


greg@Kubuntu:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update 
# /boot/grub/grub.cfg. # For full documentation of the options in this file, see: 
#   info -f grub -n 'Simple configuration'  

GRUB_DEFAULT=0 
GRUB_HIDDEN_TIMEOUT=0 
GRUB_HIDDEN_TIMEOUT_QUIET=true 
GRUB_TIMEOUT=10 
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
GRUB_CMDLINE_LINUX=""  

# Uncomment to enable BadRAM filtering, modify to suit your needs 
# This works with Linux (no patch required) and with any kernel that obtains 
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...) 
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"  

# Uncomment to disable graphical terminal (grub-pc only) 
#GRUB_TERMINAL=console  

# The resolution used on graphical terminal 
# note that you can use only modes which your graphic card supports via VBE 
# you can see them in real GRUB with the command `vbeinfo' 
#GRUB_GFXMODE=640x480  

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux 
#GRUB_DISABLE_LINUX_UUID=true  

# Uncomment to disable generation of recovery mode menu entries 
#GRUB_DISABLE_RECOVERY="true"  

# Uncomment to get a beep at grub start 
#GRUB_INIT_TUNE="480 440 1" 
greg@Kubuntu:~$

---

### Post by Greg Mueller on 2016-03-24
Duplication......

---

