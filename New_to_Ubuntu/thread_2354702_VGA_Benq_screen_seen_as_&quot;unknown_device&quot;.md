---
title: "VGA Benq screen seen as &quot;unknown device&quot;"
date: 2017-03-05
forum: New to Ubuntu
---

### Post by paologs on 2017-03-05
hi,

 I am running Ubuntu 16.04 in Dual boot with Windows 7 and it works fine except the screen size/resolution
in Ubuntu, unlike Windows, my screen does not get recognized.
Before going on, better i give some specs:

-my hardware is a Hp compact pc small format with VGA or USB ports to connect a screen (no HDMI or other newer)
- i got an INTEL Core duo and a built in INTEL graphic card 
 (at the bottom i listed some useful specs also given by the command "Lpci" in Ubuntu: );)

My screen is a Benq "Senseye" 21.5 inches . it has a DVI/VGA input

Unfortunately i do not get this recognized in screen display:
it appears a "unknown device" and in the drop down menu resolution i have only 1024x768 (4:3) or 800x600.

in both, it is stretched out and the characters are not appropriate (too big, so actually not good readable).

I tried to follow the procedure using the XANDR command line and get the properties of my screen

then i added the native resolution taken from the right one in windows 7 like this

```
sudo cvt 1920 1080 60

```

then i follow the procedure got the result, used a "newmode" command, then "addmode" and suddenly my native screen resolution was set like i wanted (same of windows) and it appeared in the drop down menu of screen display in system settings.

The only thing , it still remains set as "unknown device".
So,  i thought i had solved but once rebooted, it comes back to the same situation and i entered in a "loop". i have to do that workaround every time and this is quite annoying. 
I have followed a workaround on the Internet that says to delete "monitors.xml" but the situation did not changed.

So, also, now i miss likely a file that could be useful to set some parameters? 

is there a workaround to fix this bug with Ubuntu?  
any ideas to solve this is very welcomed. thanks ):P

(from LPCI Command some of  my graphic devices details)

```
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
 
00:1a.0 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02)
 
00:1c.1 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 2 (rev 02)
 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2)
00:1f.0 ISA bridge: Intel Corporation 82801JDO (ICH10DO) LPC Interface Controller (rev 02)
 
00:1f.5 IDE interface: Intel Corporation 82801JD/DO (ICH10 Family) 2-port SATA IDE Controller (rev 02)
```

---

### Post by DuckHook on 2017-03-07
You are already 90% of the way there, and you did that without help and on your own which is really excellent.

[LIST=1]
[*]What's left is to put your commands into a script: say, *resolution.sh*.
[*]Make it executable.
[*]Run it at login by adding the script to Ubuntu's Startup Applications that you can find using the Dash.
[/LIST]

---

### Post by dahlberg84 on 2017-03-10
Hello there ;)

have you seen this post ? [http://askubuntu.com/questions/746125/screen-resolution-is-not-saved-after-reboot](http://askubuntu.com/questions/746125/screen-resolution-is-not-saved-after-reboot)
even though its for 14.04 it should also work the same in 16.04 . 

for more info in xrandr command see [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

regards
Alex

---

### Post by paologs on 2017-03-11
Hi Thanks to both for help.
Quite struggling but with a  bit of problems:
The situation, indeed,  is the following one:

1. Regarding the first help, thanks for letting me know how the .sh files execution works, i was unaware of this kind of things. At least i know the way to create a script.
But this file that i created with help taken from the Internet does not work at the reboot. I made sure to set it as executable file in "right click and properties"/permissions.
the file i set: 

```
#!/bin/bash


sudo cvt 1920 1080 60

xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

sudo xrandr --addmode VGA1  1920x1080_60.00

xrandr --output VGA1 --mode 1920x1080_60.00

```

As said it works when run in my terminal (at least i don't have to retype all the commands)

there is an error also during when i run at the terminal, though:
  
```
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  32
  Current serial number in output stream:  32
```


but anyway i got my real screen size so it is good: the resolution of my Benq screen is added in the ddm of the screen display section. I can switch from one display size to another. Anyway once reboot i got the wrong screen size again and i have to re-run the file from the terminal.
This is the turning point. I really do not get why it does not work once reboot, as it seems it does not find the the resolution "1920x1080"
in the beginning, it appeared an error (not now, anymore, no effect, just got the wrong "stretched out" display resolution.
this was the error at the reboot

 
```
none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 63
CRTC 63: trying mode 1024x768@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 63: trying mode 800x600@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 63: trying mode 800x600@56Hz with output at 1920x1080@60Hz (pass 0)
CRTC 63: trying mode 848x480@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 63: trying mode 640x480@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 63: trying mode 1024x768@60Hz with output at 1920x1080@60Hz (pass 1)
CRTC 63: trying mode 800x600@60Hz with output at 1920x1080@60Hz (pass 1)
CRTC 63: trying mode 800x600@56Hz with output at 1920x1080@60Hz (pass 1)
CRTC 63: trying mode 848x480@60Hz with output at 1920x1080@60Hz (pass 1)
CRTC 63: trying mode 640x480@60Hz with output at 1920x1080@60Hz (pass 1)
Trying modes for CRTC 64
CRTC 64: trying mode 1024x768@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 64: trying mode 800x600@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 64: trying mode 800x600@56Hz with output at 1920x1080@60Hz (pass 0)
CRTC 64: trying mode 848x480@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 64: trying mode 640x480@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 64: trying mode 1024x768@60Hz with output at 1920x1080@60Hz (pass 1)
CRTC 64: trying mode 800x600@60Hz with output at 1920x1080@60Hz (pass 1)
CRTC 64: trying mode 800x600@56Hz with output at 1920x1080@60Hz (pass 1)
CRTC 64: trying mode 848x480@60Hz with output at 1920x1080@60Hz (pass 1)
CRTC 64: trying mode 640x480@60Hz with output at 1920x1080@60Hz (pass 1)
Trying modes for CRTC 65
CRTC 65: trying mode 1024x768@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 65: trying mode 800x600@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 65: trying mode 800x600@56Hz with output at 1920x1080@60Hz (pass 0)
CRTC 65: trying mode 848x480@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 65: trying mode 640x480@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 65: trying mode 1024x768@60Hz with output at 1920x1080@60Hz (pass 1)
CRTC 65: trying mode 800x600@60Hz with output at 1920x1080@60Hz (pass 1)
CRTC 65: trying mode 800x600@56Hz with output at 1920x1080@60Hz (pass 1)
CRTC 65: trying mode 848x480@60Hz with output at 1920x1080@60Hz (pass 1)
CRTC 65: trying mode 640x480@60Hz with output at 1920x1080@60Hz (pass 1)


```
I just have one question just to understand the basic of Linux (as you understand this is my first approach): why if it runs as executable file from the terminal, it does not run at the reboot? I added in the startup application window and the path is correct. thanks

Regarding the second help, unfortunately again it does not work. nothing happens.
Also, following the tutorial, i got an error when I run in the terminal  the following command: 
xrandr -s 1920x1080Size 1920x1080 not found in available modes

But if i execute the resolution file" suggested before, prior, then also this command  works and it recognize the screen size without any issues.
Thanks Dahlberg, anyway, at least i am aware of how to add and run a startup command! all learning;)

if anyone has some suggestions again, please let me know.):P
thank you!

---

### Post by DuckHook on 2017-03-11
> **paologs said:**
> Hi Thanks to both for help.
Quite struggling but with a  bit of problems:
The situation, indeed,  is the following one:

1. Regarding the first help, thanks for letting me know how the .sh files execution works, i was unaware of this kind of things. At least i know the way to create a script.
But this file that i created with help taken from the Internet does not work at the reboot. I made sure to set it as executable file in "right click and properties"/permissions.
the file i set: 

```
#!/bin/bash


sudo cvt 1920 1080 60

xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

sudo xrandr --addmode VGA1  1920x1080_60.00

xrandr --output VGA1 --mode 1920x1080_60.00

```

As said it works when run in my terminal (at least i don't have to retype all the commands)Again, you almost had it:

[LIST=1]
[*]*sudo* is neither needed nor desirable when running these commands interactively, and
[*]*sudo* simply won't work in a user script. Consider: *sudo* requires your active intervention by way of entering your password. Therefore, it cannot be automated (and automating is what a script does);
[*]The CVT command is not necessary every time. Once you get the modeline, it is good forever so long as you don't change your mobo/graphics card.
[*]Be sure the script is owned by you and not root. In other words, don't create the script using sudo nano. Just nano (or gedit).
[/LIST]
My apologies for lack of detail, but you had figured out so much on your own that I did not think it necessary to fill in anything further. Your script should read like this:```

#!/bin/bash
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode VGA1  1920x1080_60.00
xrandr --output VGA1 --mode 1920x1080_60.00
```As you can see, you had all the components right and were just a little off on structure. For a self-professed "first approacher", this is impressive. If this still doesn't work it is sometimes necessary to make the script wait a few seconds before activating so that X actually has a chance to first load. You can do this with the *sleep* command, as follows:```

#!/bin/bash
sleep 3
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode VGA1  1920x1080_60.00
xrandr --output VGA1 --mode 1920x1080_60.00
```The number following *sleep* is in seconds.> &#8230;there is an error also during when i run at the terminal&#8230;Don't use *sudo*. Also, if the new script works, let's ignore that output for now.> &#8230;once reboot i got the wrong screen size again and i have to re-run the file from the terminal&#8230;I really do not get why it does not work once reboot,Yes. xrandr is interactive and will not survive logout or reboot. That's why you must add it to auto startup applications, because this service automatically runs the script at each login.> &#8230;why if it runs as executable file from the terminal, it does not run at the reboot? I added in the startup application window and the path is correct.Likely because you used *sudo* in your original script (see above).

Let us know how it goes!

---

### Post by paologs on 2017-03-23
Hi 
Thanks again, DuckHook, i have resolved with your workaround . Much appreciated the help :)

just a point: now even if the screen is set at his desired size, luckily, i have still the same error mentioned above
but this is not bothering me at all, as it works, great stuff, again,. i am fine now
just the curiosity to know the reason of this below error that reappears even if issue is solved.
 ```
CRTC 63: trying mode 1024x768@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 63: trying mode 800x600@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 63: trying mode 800x600@56Hz with output at 1920x1080@60Hz (pass 0)
CRTC 63: trying mode 848x480@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 63: trying mode 640x480@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 63: trying mode 1024x768@60Hz with output at 1920x1080@60Hz (pass 1)
CRTC 63: trying mode 800x600@60Hz with output at 1920x1080@60Hz (pass 1)
CRTC 63: trying mode 800x600@56Hz with output at 1920x1080@60Hz (pass 1)
CRTC 63: trying mode 848x480@60Hz with output at 1920x1080@60Hz (pass 1)
CRTC 63: trying mode 640x480@60Hz with output at 1920x1080@60Hz (pass 1)
```

---

### Post by DuckHook on 2017-03-23
The error is a result of your system initially querying your monitor and not getting any response that it can understand. That is why it defaults to 1024x768 as the lowest common resolution that any monitor can display. All of your steps above were required because of this error. Solving this error would make the *xrandr* workaround unnecessary, but it would involve a lot of detective work and trial & error.

I am away from home right now and do not have access to my usual resources, but it would be educational to try chasing this down. On the other hand, your system now displays properly and the workaround is straightforward and not at all intrusive, so you may just want to leave it alone.

If you are still curious or want a better solution, other forum members may be able to help.

---

