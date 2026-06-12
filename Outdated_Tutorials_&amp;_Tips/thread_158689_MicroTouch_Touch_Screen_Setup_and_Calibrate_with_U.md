---
title: "MicroTouch Touch Screen Setup and Calibrate with Ubuntu"
date: 2006-04-11
forum: Outdated Tutorials &amp; Tips
---

### Post by fattmox on 2006-04-11
I have spent many late nights ](*,)  trying to figure
out how to get my touch screen working. Below is a
step by step process from ground up of what I
followed. No other poor sucker need suffer. I setup a
MicroTouch Touch Screen Controller with the Excalibre
Chipset. Ubuntu 5.10 comes ready to go with a the
driver 'mutouch' that works with Xorg

**INSTALLATION**
1. Install Ubuntu
2. Figure out where your touch screen is plugged in.
-- For my case I had a serial interface so I plugged
it into the serial port on the tower. To test, at the
command prompt I typed:
[INDENT][FONT="Courier New"]cat
/dev/ttyS0[/FONT][/INDENT]
I then touched the touch screen. If a bunch of garbage
is displayed then you have found the right device. You
may also want to try [FONT="Courier New"]cat
/dev/ttyS1[/FONT]
-- If you have a USB interface then a nice litle trick
I learned is
[INDENT][FONT="Courier New"]tail -f
/var/log/dmesg[/FONT][/INDENT]
now unplug the connector from the tower and plug it
back in. The tail program should display new entires
in the log and display which device was unplugged and
plugged. For example [FONT="Courier
New"]/dev/ttyUSB0[/FONT]
-- If none of this works, it is possible you havea a
hardware problem and need to change setting at bootup
to enable USB and Serial ports or maybe you need a new
computer!
3. Once you figure out how the screen is connected we
need to edit the [FONT="Courier
New"]/etc/X11/xorg.conf[/FONT] file so the that the
touch screen driver is loaded when you load GDM
(Windows Manger). You need to have root privelages to
edit and save this file.
[INDENT][FONT="Courier New"]sudo pico
/etc/X11/xorg.conf[/FONT][/INDENT]
You need to make two entries. One for the settings and
one so the setting will be executed.
Below is a configuration that works for me taken and
slighty modified from a famous touchscreen how-to. If
you have the same setup as I this should work fine but
if not look at the FAQ for setting for your specific
device.
([http://www.faqs.org/docs/Linux-HOWTO/XFree86-Touch-Screen-HOWTO.html]("http://www.faqs.org/docs/Linux-HOWTO/XFree86-Touch-Screen-HOWTO.html"))

I added this under the similar block of settings for
the mouse InputDevice block.
[FONT="Courier New"]Section "InputDevice"
[INDENT]        Identifier  "TouchScreen"
        Driver      "mutouch"
        Option      "Type" "finger"
        Option      "Device" "/dev/ttyS0"
        Option      "ScreenNo" "0"
        Option      "MinX" "0"
        Option      "MaxX" "16383"
        Option      "MinY" "0"
        Option      "MaxY" "16383"
        Option      "SendCoreEvents" "yes"[/INDENT]
EndSection[/FONT]

I then added one line to the Server Layout block (in
bold)
[FONT="Courier New"]Section "ServerLayout"
[INDENT]        Identifier      "Default Layout"
        Screen  "Default Screen"
        InputDevice "Generic Keyboard"
...
        **InputDevice "TouchScreen"**[/INDENT]
EndSection[/FONT]

Now reboot GDM. This can be achieved by
Ctrl+Alt+Backspace. If GDM does not come back up then
you may need to recheck the xorg.conf or restart GDM.

--To check to see if there is a configuration issue
Alt+Left Arrow one or more times to find a warning in
a different console
--To edit the xorg.conf - [FONT="Courier New"]sudo
pico /etc/X11/xorg.conf[/FONT]
--To restart GDM
[INDENT][FONT="Courier New"]sudo killall gdm
sudo gdm[/FONT][/INDENT]

Once GDM is running again try out the touch screen. It
will most likely not be very accurate but it should
work. If not do a little ](*,)  and double check
everything. The next step is calibration.

**CALIBRATION**
1. Download the calibration tool. I used touchcal-0.23
which I found here:
[http://www.sgoc.de/touchcal.html]("http://www.sgoc.de/touchcal.html")
Unpack the file to your /tmp folder.
2. Prepare your system to compile the calibration
tool. Ubuntu comes with all the tools you need to
unpackage this file but not to compile the program.
If you installed Ubuntu off a CD-ROM then you need to
update the /etc/apt/sources.list file to look for
packages from the internet.
[INDENT][FONT="Courier New"]sudo pico
/etc/apt/sources.list[/FONT][/INDENT]
Uncomment the lines that collect packages from the
network. Save the file and exit.
To get the packages you need to compile touchcal run
the following lines
[INDENT][FONT="Courier New"]sudo apt-get update
sudo apt-get install gcc make
libncurses5-dev[/FONT][/INDENT]
3. Compile touchcal
Now run the configure script
[INDENT][FONT="Courier New"]cd /tmp/touchcal-0.23
./configure[/FONT][/INDENT]
Then run make
[INDENT][FONT="Courier New"]make[/FONT][/INDENT]
If either of these steps fail it is most likely
because you are still missing some required packages.
I may have missed some so do a little ](*,)  and try
and figure out which packages are missing.
4. Run touchcal
--touchcal comes with a good README file. I highly
recommend reading it. [INDENT][FONT="Courier New"]pico
/tmp/touchcal-0.23/README[/FONT][/INDENT]
--Go to console Ctrl+Alt+F1
--shutdown gdm (Xserver)
[INDENT][FONT="Courier New"]sudo killall
gdm[/FONT][/INDENT]
--run touchcal program
[INDENT][FONT="Courier New"]cd /tmp/touchcal-0.23
./touchcal m /dev/ttyS0[/FONT] ([FONT="Courier
New"]m[/FONT] stands for mutouch, [FONT="Courier
New"]/dev/ttyS0[/FONT] is where the touch screen is
connected to. (see above)[/INDENT]
--follow the onscreen instructions
When finished running, touchcal should output your new
calibration coordinates (MinX, MaxY etc). Copy these
values and use them to replace the preset values in
the [FONT="Courier New"]/etc/X11/xorg.conf[/FONT] for
the touchscreen device.
IE
[INDENT][FONT="Courier New"]Option      "MinX"  
"0"[/FONT]
Changes to
[FONT="Courier New"]Option      "MinX"  
"2254"[/FONT][/INDENT]
5.  Restart GDM
[INDENT][FONT="Courier New"]sudo gdm[/FONT][/INDENT]
Once GDM has loaded try it out! If you are still
unhappy try going through step 4. again.

Hopefully this has helped at least one person save a
few hours. I would have loved a How-To like this when
I was ](*,) . Thankfully I have a good friend that
helped me along the way. Thanks Mike!

DISCLAIMER: These instructions are by no means 100%
complete or correct. Please let me know if I have any
errors. Good luck!

---

