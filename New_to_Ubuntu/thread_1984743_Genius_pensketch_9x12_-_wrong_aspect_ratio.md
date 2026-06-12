---
title: "Genius pensketch 9x12 - wrong aspect ratio"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by krakonos on 2012-05-22
Hi, 
I have a problem with my graphic tablet - it works fine (pen pressure is ok) even with native ubuntu ([COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C] 11.04 - the *Natty Narwhal* )[/COLOR][/FONT][/COLOR] drivers. But it draw ellipses instead of circles (or rectangle  instead of square) - so I assume that it is caused due to different aspect ratio - monitor is 1,6 (1920x1200) and tablet 4:3 (Pensketch 9x12). 
So because I don't know how to affect original drivers I installed wizardpen and after configuration I had exactly the same result as with the original drivers - ellipses again but now with a lot of frustration with configuration. 
here is 70-wizardpen.conf file


> Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchProduct "Tablet|PF1209"
   Driver "wizardpen"
#[CALIBRATION] This data was taken from wizard-calibrate tool.
   Option          "KeepShape"     "on"
   Option          "TopX"          "81"
   Option          "TopY"          "0"
   Option          "BottomX"       "23970"
   Option          "BottomY"       "17999"
#[END CALIBRATION]
EndSectionI even recalculated the bottomX value as was suggested somewhere like this 
23970*(1200/1920)*(4/3)=19975

but still doesn't work and the tablet is useless for me  
Thanks in advance

---

### Post by Favux on 2012-05-22
Hi krakonos,

Welcome to Ubuntu forums!

Which release of Ubuntu are you currently using?

I'd like to do some diagnostics and establish what tablet you have.  Can you post the output of the following terminal commands?
```
xinput list

lsusb
```

---

### Post by krakonos on 2012-05-22
Thank you for response - as I mention I have Ubuntu [COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C] 11.04 - the *Natty Narwhal - core Linux 2.6.38-15-generic, GNOME 2.32.1* [/COLOR][/FONT][/COLOR]
xinput list
> &#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627;                 9x12 Tablet                 id=9    [slave  pointer  (2)]
&#9116;   &#8627;                 9x12 Tablet                 id=10    [slave  pointer  (2)]
&#9116;   &#8627;                 9x12 Tablet                 id=11    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=12    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Logitech Logitech USB Keyboard              id=8    [slave  keyboard (3)]
lsusb
> Bus 007 Device 002: ID 046d:c521 Logitech, Inc. Cordless Mouse Receiver
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 5543:0042 UC-Logic Technology Corp. Genius PenSketch 12x9 Tablet
Bus 003 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


---

### Post by Favux on 2012-05-22
Alright, your model:
> Bus 003 Device 003: ID 5543:0042 UC-Logic Technology Corp. Genius PenSketch 12x9 Tablet
is supported by Natty's 2.6.38 kernel according to:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

What version of evdev does Natty have?  I forget.  Check in Software Center or Synaptic Package Manager.  If it is >= 2.5.99 you should probably be using evdev rather than the WizardPen driver.

For Calibration with evdev see:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_xf86-input-evdev#Calibration](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_xf86-input-evdev#Calibration)

---

### Post by krakonos on 2012-05-22
Ok, I unistalled wizardpen and I have this and absolutely no clue what to do to change aspect ratio:
> xinput list-props "                                9x12 Tablet"
Warning: There are multiple devices matching '                9x12 Tablet'.
To ensure the correct one is selected, please use the device ID, or prefix the
device name with 'pointer:' or 'keyboard:' as appropriate.

unable to find device                 9x12 Tablet
There are 16 spaces which was cropped/trimmed previous to the each text* 9x12 Tablet*

---

### Post by Favux on 2012-05-22
You want to find the device ID for the stylus or pen device.  That would be the one with evdev "tablet catchall" snippet identifier match in /var/Xorg.0.log.

Since from your ***xinput list*** (check it again) they were numbered 9, 10, and 11 just run them in **list-props** one at a time.
```
xinput list-props ID#
```
Anyway in /usr/share/X11/xorg.conf.d/10-evdev.conf it should be this snippet matching the pen:
```
Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection
```
You want to duplicate the MatchIsTablet match in your custom .conf in /etc/X11/xorg.conf.d/52-tablet.conf.  So something like:
```
Section "InputClass"
        Identifier "Genius PenSketch pen"
        MatchProduct "Tablet"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.
        Option "Calibration" "min-x max-x min-y max-y"
EndSection
```
Or you could use "9x12" as the keyword in MatchProduct instead of "Tablet".

Then from your post above:
```
Option "TopX" "81"
Option "TopY" "0"
Option "BottomX" "23970"
Option "BottomY" "17999"
```
Change:
```
Option "Calibration" "min-x max-x min-y max-y"
```
to:
```
Option "Calibration" "81 23970 0 17999"
```
Or whatever it is you've determined.  Or you should be able to use run time commands like:
```
xinput set-prop "device name" "Evdev Axis Calibration" min-x max-x min-y max-y
```
But the problem is the ID#'s can change with hot plugs unlike the <device names>.  And you have 3 identical device names.

The calibration tool xinput-list is handy and is in the repo.s.

---

### Post by krakonos on 2012-05-23
I feel pretty frustrated and confused now. 

> xinput list-props id10
unable to find device id10
xinput list-props ID11
unable to find device ID11I tried for every id (or ID if it is case sensitive) but with the same result

Everything looks fine in /usr/share/X11/xorg.conf.d/10-evdev.conf

> #
# Catch-all evdev loader for udev-based systems
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection
But I cannot open or even edit 
> sudo gedit /etc/X11/xorg.conf.d/52-tablet-on-evdev.conf
and in gedit I have something like "Cannot find file /etc/X11/xorg.conf.d/52-tablet-on-evdev.conf" on red background.

I use Ubuntu for more than half a year and I never have to configure anything in conf file - this is my first experience so have patience with me please

---

### Post by Favux on 2012-05-23
No worries.  :)

I should have been clearer on the command.  You use just the ID #, so:
```
xinput list-props 10
```
and so on.

Yep, your /usr/share/X11/xorg.conf.d/10-evdev.conf looks normal.

You may need to create the directory xorg.conf.d in /etc/X11.  Check if it is already there in Nautilus or whatever.  Else:
```
sudo mkdir /etc/X11/xorg.conf.d
```

The gksudo gedit command will create the 52-tablet-on-evdev.conf file in /etc/X11/xorg.conf.d.  Use gksudo instead of sudo for graphical app.s.

---

### Post by krakonos on 2012-05-25
I finally found the time to try it and here is the result

> sudo mkdir /etc/X11/xorg.conf.d

mkdir:cannot create directory „/etc/X11/xorg.conf.d“ File already existsand with 
> gksudo gedit /etc/X11/xorg.conf.d/52-tablet-on-evdev.confI have exactly the same result as if I use only sudo - "Cannot find file /etc/X11/xorg.conf.d/52-tablet-on-evdev.conf" on red background.

and in console
> (gedit:4236): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Cannot create "/root/.local/share/recently-used.xbel.USCJEW": Directory or file doesnt exist.

(gedit:4236): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed:  Directory or file doesnt exist.I tried to translate some localized texts in those reports

---

### Post by Favux on 2012-05-25
Something funny is going on.  This:
> I have exactly the same result as if I use only sudo - "Cannot find file /etc/X11/xorg.conf.d/52-tablet-on-evdev.conf" on red background.
led me to believe the directory xorg.conf.d wasn't there because it should either open the file if it is there or create the file if it isn't.  But:
> sudo mkdir /etc/X11/xorg.conf.d

mkdir:cannot create directory &#8222;/etc/X11/xorg.conf.d&#8220; File already exists 
tells us xorg.conf.d is already there.  If so you should be able to navigate to it with Nautilus and look at any files in it.

You have regular Natty correct?  Anyway let's make the file on the Desktop.  Right click on the Desktop and Create New Document and title it "52-tablet-on-evdev.conf".  Open it in gedit and copy and paste the contents into it.  Then copy it into place.  Open a terminal and:
```
cd Desktop

sudo cp 52-tablet-on-evdev.conf /etc/X11/xorg.conf.d/52-tablet-on-evdev.conf 
```
That should work.

---

### Post by krakonos on 2012-05-25
Yes I have regular Natty . But now:
> cd Desktop  sudo cp 52-tablet-on-evdev.conf /etc/X11/xorg.conf.d/52-tablet-on-evdev.conf
cp: accessing to„/etc/X11/xorg.conf.d/52-tablet-on-evdev.conf“: is not a directorySorry if i don't translated the messages correctly

Here is image of the directory content

 [[IMG]http://img137.imagevenue.com/loc573/th_30526_dir_122_573lo.jpeg[/IMG]]("http://img137.imagevenue.com/img.php?image=30526_dir_122_573lo.jpeg")

---

### Post by Favux on 2012-05-25
Glad you showed me that screen shot of the directory.

It looks like we have some clean up to do.

What should be the xorg.conf.d folder is called the 52-tablet-on-evdev.conf folder.  52-tablet-on-evdev.conf should be a text file, not a directory/folder.  So let's remove it.  I'm assuming it is empty.
```
sudo rmdir /etc/X11/52-tablet-on-evdev.conf
```
Also you have a text file called xorg.conf.d in the /etc/X11 directory.  Let's check if there is anything in it first:
```
cd /etc

cd/X11

cat xorg.conf.d
```
If it is empty go back to your /home/username start directory (where the terminal opens to by default), use:
```
cd ~/
```
The ~/ is a short cut for /home/username.  Then to remove the file:
```
sudo rm /etc/X11/xorg.conf.d
```
If you had stayed in /etc/X11 you would have used:
```
sudo rm xorg.conf.d
```
If you get lost, and everyone does, enter:
```
pwd
```
and that will tell you where you are.  And to move back up to the previous directory:
```
cd ..
```

mkdir = make directory
rmdir = remove directory
cd = change directory
cp = copy
rm = remove
cat = catalog
cd .. = cd back up to previous directory
pwd = print working directory

Once you get it cleaned up we can start again.  Meanwhile I'll check the commands I gave you.  Maybe I made a typo.

---

### Post by krakonos on 2012-05-29
Ok, it's clean - what should I do now?

---

### Post by Favux on 2012-05-29
Good.

Now you want to make the missing xorg.conf.d directory/folder with:
```
sudo mkdir /etc/X11/xorg.conf.d
```
Check for it in Nautilus and make sure it is there now.

Then back to what we were talking about earlier.  Create the file 52-tablet.conf in the new xorg.con.d directory and then copy and paste the snippet/contents in it with:
```
gksudo gedit /etc/X11/xorg.conf.d/52-tablet.conf
```
So the snippet you'd place in the new file 53-tablet.conf would be:
```
Section "InputClass"
        Identifier "Genius PenSketch pen"
        MatchProduct "Tablet"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.
        Option "Calibration" "81 23970 0 17999"
EndSection
```
Then Save, Close and restart.  I'm using the coordinates you gave.

---

### Post by krakonos on 2012-05-30
Ug- ok now I'm exactly where I was with wizdpen - aspect ratio of my tablet(4:3) and my monitor(16:10  or 1920:1200) doesn't match. If I recalculate  x coordinate this way:
23970*(1200/1920)*(4/3)=19975
my tablets active working area is smaller (right side is cropped as expected) but the aspect ratio doesn't change - when I draw exact square on tablet I have rectangle on the screen. 
I'm not sure but I think it will be necessary to somehow recalculate transformation matrix :(

---

### Post by Favux on 2012-05-30
Great!  You've got the custom .conf working sounds like.  :)

Alright the coordinates you started with were:
```
Option "TopX" "81"
Option "TopY" "0"
Option "BottomX" "23970"
Option "BottomY" "17999"
```
I'm assuming those are the calibration values without you doing anything to them in a configuration file.  If the list-props showed the coordinates they should be about the same.  Or you might see them in Xorg.0.log at /var/log.

Genius on their site says it is a 12x9 inch active area, i.e. 4:3 aspect ratio.  And has a resolution of 4000 LPI.  Let's check:
23970 / 12 = 19997.5
17999 / 9 = 1999.88
That actually fits because I believe the driver currently only handles 2000 LPI.  Apparently there is a proprietary mode that gets the tablet to communicate some extra features, like the higher resolution.  That's being worked on.

Now the monitor is 1920 x 1200 or a 16:10.  To scale the tablet's active area to that you would need to decrease the tablet's active area height, i.e. 12 x 7.5.  That would give you the 16:10 aspect ration you want (12 / 7.5 = 1.6)  So it is the y axis you want scaled.  Then to determine the scaling:
7.5 x 1999.88 = 14,999.1

Which means the Option you want to use is:
```
        Option "Calibration" "81 23970 0 14999"
```
And the dead area on the tablet should be a strip along the bottom, I guess.

I think I've got that correct.

---

### Post by krakonos on 2012-05-30
Wow, I can't believe it - IT WORKS - THANK YOU, THANK YOU, THANK YOU  \\:D/
You had infinite patience with me - it needed some tweaking ( Option "Calibration" "81 23970 1080 14999"), but  it is precise enough for my needs. Now I only  have to wait for Gimp 2.8 pressure support to replace 2.6 - and it will be great:) Thanks one more time

---

### Post by ricardo roy on 2012-07-20
Dear [Favux]("http://ubuntuforums.org/member.php?u=699990"):

I am also trying to make work a Tablet Genius Penscketch 12x9 in Ubuntu 12.04 LTS but we don't even get any response of the tablet. We have followed the steps indicated before in this topic. Also, we tried with Wizardpen 0.8.0  and we didn't get any response either.

Maybe we don't have installed the drivers needed but we don't what are this drivers we must install. Do you know any documentation and where to look for the drivers?

Any Suggestion will be welcome.

Thank you for your help.

---

### Post by Favux on 2012-07-20
Hi ricardo roy,

Welcome to Ubuntu forums!


Let's confirm your model.  I think it is suppose to be supported.  Enter in a terminal this command:
```
lusb
```
and post the output.  The line that has the tablet, which will say UC-Logic or something close, should have 5543:0042 if it is the tablet I think it is.

Also in a terminal run this command:
```
xinput list
```
and post the output.

---

### Post by ricardo roy on 2012-07-20
> **Favux said:**
> Hi ricardo roy,

Welcome to Ubuntu forums!


Let's confirm your model.  I think it is suppose to be supported.  Enter in a terminal this command:
```
lusb
```and post the output.  The line that has the tablet, which will say UC-Logic or something close, should have 5543:0042 if it is the tablet I think it is.

Also in a terminal run this command:
```
xinput list
```and post the output.

Thank you. Here it is the output

lsusb
mori@Lapmori:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 5543:0042 UC-Logic Technology Corp. Tablet PF1209

xinput list

mori@Lapmori:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627;     Tablet PF1209                           id=8    [slave  pointer  (2)]
&#9116;   &#8627;     Tablet PF1209                           id=9    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]

---

### Post by Favux on 2012-07-20
Hmm.  That should be working.  See:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

I think yours is the second model I've seen that should be working out of the box in Precise that isn't.

The kernel driver should set your tablet up to be run by the evdev X driver and that should not require you to do anything else.

Do you still have the WizardPen driver installed in Precise?  And how did you install it by the way?  Did you also add a WizardPen .conf file to configure the tablet?

Let's see if we can find out what driver it is on.  Enter this command in a terminal and post the output:
```
xinput list-props 8
```
The ID number 8 should be for the pen and 9 for the mouse.  Did the mouse come with your tablet?  Also the ID number can change when you restart or hot plug so you have to run **xinput list** again to check what the ID numbers are if you do that.

---

### Post by ricardo roy on 2012-07-20
> **Favux said:**
> Hmm.  That should be working.  See:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

I think yours is the second model I've seen that should be working out of the box in Precise that isn't.

The kernel driver should set your tablet up to be run by the evdev X driver and that should not require you to do anything else.

Do you still have the WizardPen driver installed in Precise?  And how did you install it by the way?  Did you also add a WizardPen .conf file to configure the tablet?

Let's see if we can find out what driver it is on.  Enter this command in a terminal and post the output:
```
xinput list-props 8
```The ID number 8 should be for the pen and 9 for the mouse.  Did the mouse come with your tablet?  Also the ID number can change when you restart or hot plug so you have to run **xinput list** again to check what the ID numbers are if you do that.

Sure, we notice that the name of the last Tablet is not exactly the same and we checked also the page [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status) for the support of the tablet . 

First, we hot plugged the tablet without the driver "wizardpen 0.8.1" and had no response from the tablet and the pen. Then we followed the steps you just described in this topic and still didn't get any response. Then, we installed the driver "wizardpen 0.8.1"  that we downloaded from the page 
[https://launchpad.net/wizardpen](https://launchpad.net/wizardpen)
 So we gunziped and applied the tar to the file xorg-input-wizardpen-0.8.1.tar. Once inside the directory we runned the commands './configure', then 'make' and finally 'sudo make install' and tried to see if there was any response but nothing yet. 

In response to the "wizardpen.conf", we haven't configured any file with that name.

It seems that the ID's are the same even after plugged and unplugged the tablet. So, here it is the output of the commands:

xinput list-props 8

mori@Lapmori:~/Downloads$ xinput list-props 8
Device '    Tablet PF1209':
    Device Enabled (121):    1
    Coordinate Transformation Matrix (123):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (247):    0
    Device Accel Constant Deceleration (248):    1.000000
    Device Accel Adaptive Deceleration (249):    1.000000
    Device Accel Velocity Scaling (250):    10.000000
    Device Product ID (240):    21827, 66
    Device Node (241):    "/dev/input/event10"
    Evdev Axis Inversion (251):    0, 0
    Evdev Axis Calibration (252):    0, 32767, 0, 32767
    Evdev Axes Swap (253):    0
    Axis Labels (254):    "Abs X" (244), "Abs Y" (245), "Abs Pressure" (246)
    Button Labels (255):    "Button Unknown" (243), "Button Unknown" (243), "Button Unknown" (243), "Button Wheel Up" (127), "Button Wheel Down" (128), "Button Horiz Wheel Left" (129), "Button Horiz Wheel Right" (130)
    Evdev Middle Button Emulation (256):    0
    Evdev Middle Button Timeout (257):    50
    Evdev Third Button Emulation (258):    0
    Evdev Third Button Emulation Timeout (259):    1000
    Evdev Third Button Emulation Button (260):    3
    Evdev Third Button Emulation Threshold (261):    20
    Evdev Wheel Emulation (262):    0
    Evdev Wheel Emulation Axes (263):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (264):    10
    Evdev Wheel Emulation Timeout (265):    200
    Evdev Wheel Emulation Button (266):    4
    Evdev Drag Lock Buttons (267):    0

and 

xinput list-props 9

mori@Lapmori:~/Downloads$ xinput list-props 9
Device '    Tablet PF1209':
    Device Enabled (121):    1
    Coordinate Transformation Matrix (123):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (247):    0
    Device Accel Constant Deceleration (248):    1.000000
    Device Accel Adaptive Deceleration (249):    1.000000
    Device Accel Velocity Scaling (250):    10.000000
    Device Product ID (240):    21827, 66
    Device Node (241):    "/dev/input/event11"
    Evdev Axis Inversion (251):    0, 0
    Evdev Axis Calibration (252):    0, 32767, 0, 32767
    Evdev Axes Swap (253):    0
    Axis Labels (254):    "Rel X" (131), "Rel Y" (132), "Rel Vert Wheel" (268)
    Button Labels (255):    "Button Left" (124), "Button Middle" (125), "Button Right" (126), "Button Wheel Up" (127), "Button Wheel Down" (128), "Button Horiz Wheel Left" (129), "Button Horiz Wheel Right" (130)
    Evdev Middle Button Emulation (256):    0
    Evdev Middle Button Timeout (257):    50
    Evdev Third Button Emulation (258):    0
    Evdev Third Button Emulation Timeout (259):    1000
    Evdev Third Button Emulation Button (260):    3
    Evdev Third Button Emulation Threshold (261):    20
    Evdev Wheel Emulation (262):    0
    Evdev Wheel Emulation Axes (263):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (264):    10
    Evdev Wheel Emulation Timeout (265):    200
    Evdev Wheel Emulation Button (266):    4
    Evdev Drag Lock Buttons (267):    0

we want to add that the tablet comes with a mouse.

---

### Post by Favux on 2012-07-20
Well it is on the evdev driver which is correct.  But the two sections shouldn't be identical.  And the calibration is wrong:
```
Evdev Axis Calibration (252): 0, 32767, 0, 32767
```
max X and max Y shouldn't be the same.  The tablet isn't square.

Let's look at the Xorg.0.log in /var/log and see if that tells us anything.  It is big so you'll want to right click on it and compress it and send it as an attachment to your next post.

We could assume the WizardPen driver is ready to go and just needs a .conf file to get the tablet to match to it.  But I compilied it in Precise also, although I didn't do **sudo make install**.  I didn't seem to see any show stopper errors but I noticed after **make** I didn't get a wizardpen_drv.so which I would have expected.  Haven't looked into it any further yet.

---

### Post by ricardo roy on 2012-07-20
> **Favux said:**
> Well it is on the evdev driver which is correct.  But the two sections shouldn't be identical.  And the calibration is wrong:
```
Evdev Axis Calibration (252): 0, 32767, 0, 32767
```max X and max Y shouldn't be the same.  The tablet isn't square.

Let's look at the Xorg.0.log in /var/log and see if that tells us anything.  It is big so you'll want to right click on it and compress it and send it as an attachment to your next post.

We could assume the WizardPen driver is ready to go and just needs a .conf file to get the tablet to match to it.  But I compilied it in Precise also, although I didn't do **sudo make install**.  I didn't seem to see any show stopper errors but I noticed after **make** I didn't get a wizardpen_drv.so which I would have expected.  Haven't looked into it any further yet.

Ok, we understand, obviously it's not a square.
So, we attached the output of cat /var/log/Xorg.0.log. It is the same file in .txt and in .ascii. 
We haven't tried the Precise and apparently there were no error when we runned the 'sudo make install'.

---

### Post by Favux on 2012-07-20
Now that was interesting.  Looks like it is setting up OK but then it unloads the evdev module and goes through setup again.  In both cases the Xorg.0.log is showing two unknown identifiers.

So for the tablet pen:
```
[  8340.823] (II) config/udev: Adding input device     Tablet PF1209 (/dev/input/event10)
[  8340.823] (**)     Tablet PF1209: Applying InputClass "evdev tablet catchall"
[  8340.823] (**)     Tablet PF1209: Applying InputClass "wizardpen"
[  8340.823] (**)     Tablet PF1209: Applying InputClass "Genius PenSketch pen"
[  8340.823] (II) Using input driver 'evdev' for '    Tablet PF1209'
[  8340.823] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
```
and the tablet mouse:
```
[  8340.840] (II) config/udev: Adding input device     Tablet PF1209 (/dev/input/event11)
[  8340.840] (**)     Tablet PF1209: Applying InputClass "evdev pointer catchall"
[  8340.840] (**)     Tablet PF1209: Applying InputClass "evdev tablet catchall"
[  8340.840] (**)     Tablet PF1209: Applying InputClass "wizardpen"
[  8340.840] (**)     Tablet PF1209: Applying InputClass "Genius PenSketch pen"
[  8340.840] (II) Using input driver 'evdev' for '    Tablet PF1209'
```
I think "evdev pointer catchall" is correct for the mouse and I am not sure why then we're seeing "evdev tablet catchall".

But can you post the .conf files that have "wizardpen" and "Genius PenSketch pen"?  I assume "wizardpen" was installed by the WizardPen driver when you did **sudo make install**.  And that may be located at /usr/share/X11/xorg.conf.d/70-wizardpen.conf.  Although I might have the number wrong.  And the "Genius PenSketch pen" is likely a custom .conf you installed in /etc/X11/xorg.conf.d. And I don't know what you named it.  Likely we'll want to comment both of them out so they have no effect.

If it would work on the WizardPen driver it is possible you would just need to change the match.  That I've already figured out with another person with your model tablet because the generic WizardPen match wasn't picking it up.  But I would kind of like to know why the thing isn't working on evev in Precise (12.04).

---

### Post by ricardo roy on 2012-07-20
> **Favux said:**
> Now that was interesting.  Looks like it is setting up OK but then it unloads the evdev module and goes through setup again.  In both cases the Xorg.0.log is showing two unknown identifiers.

So for the tablet pen:
```
[  8340.823] (II) config/udev: Adding input device     Tablet PF1209 (/dev/input/event10)
[  8340.823] (**)     Tablet PF1209: Applying InputClass "evdev tablet catchall"
[  8340.823] (**)     Tablet PF1209: Applying InputClass "wizardpen"
[  8340.823] (**)     Tablet PF1209: Applying InputClass "Genius PenSketch pen"
[  8340.823] (II) Using input driver 'evdev' for '    Tablet PF1209'
[  8340.823] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
```and the tablet mouse:
```
[  8340.840] (II) config/udev: Adding input device     Tablet PF1209 (/dev/input/event11)
[  8340.840] (**)     Tablet PF1209: Applying InputClass "evdev pointer catchall"
[  8340.840] (**)     Tablet PF1209: Applying InputClass "evdev tablet catchall"
[  8340.840] (**)     Tablet PF1209: Applying InputClass "wizardpen"
[  8340.840] (**)     Tablet PF1209: Applying InputClass "Genius PenSketch pen"
[  8340.840] (II) Using input driver 'evdev' for '    Tablet PF1209'
```I think "evdev pointer catchall" is correct for the mouse and I am not sure why then we're seeing "evdev tablet catchall".

But can you post the .conf files that have "wizardpen" and "Genius PenSketch pen"?  I assume "wizardpen" was installed by the WizardPen driver when you did **sudo make install**.  And that may be located at /usr/share/X11/xorg.conf.d/70-wizardpen.conf.  Although I might have the number wrong.  And the "Genius PenSketch pen" is likely a custom .conf you installed in /etc/X11/xorg.conf.d. And I don't know what you named it.  Likely we'll want to comment both of them out so they have no effect.

If it would work on the WizardPen driver it is possible you would just need to change the match.  That I've already figured out with another person with your model tablet because the generic WizardPen match wasn't picking it up.  But I would kind of like to know why the thing isn't working on evev in Precise (12.04).

Here are the outputs of the .conf

mori@Lapmori:less 70-wizardpen.conf
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchTag "wizardpen"
   Driver "wizardpen"
   Option               "TopX"          "1506"
   Option               "TopY"          "2705"
   Option               "BottomX"       "31225"
   Option               "BottomY"       "30892"
EndSection
 
[email]mori@Lapmori:/etc/X11/xorg.conf[/email].d$ less 52-tablet.conf
Section "InputClass"
        Identifier "Genius PenSketch pen"
        MatchProduct "Tablet|PF1209"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.
        Option "Calibration" "0 32767 0 32767"
EndSection

---

### Post by Favux on 2012-07-20
You should be able to get an idea of the coordinates by looking at the tablet info. page on the DIGI*mend* site:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=UC-Logic_Tablet_PF1209](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=UC-Logic_Tablet_PF1209)  and then calculating it like so.
12"x9", 4000 LPI

max X = 12" x 4000 LPI = 48000
max Y = 9" x 4000 LPI = 36000

The origin or 0,0 is the top left corner.  And that's assuming the physical maximum potential 4000 LPI was what was used.

But I do see in the HID report descriptor:
```
0x05, 0x01,         /*          Usage Page (Desktop),       ; Generic desktop controls (01h)            */
0x09, 0x30,         /*          Usage (X),                  ; X (30h, dynamic value)                    */
0x09, 0x31,         /*          Usage (Y),                  ; Y (31h, dynamic value)                    */
0x15, 0x00,         /*          Logical Minimum (0),                                                    */
0x26, 0xFF, 0x7F,   /*          Logical Maximum (32767),                                                */
0x35, 0x00,         /*          Physical Minimum (0),                                                   */
0x46, 0xFF, 0x7F,   /*          Physical Maximum (32767),
```
If I do 32767 / 4000 = 8.19 that would make sense if the Y is actually 8.19 inches instead of 9 inches.  Is it?

Another way to get coordinates is to use xinput_calibrator.  It is also called 'Calibrate Touchscreen' in Software Center.

But let's forget about coordinates for now and see what happens if we just let the evdev snippets pick up the tablet like they are suppose to.  So comment out (#) the two .conf files you added, e.g.:
```
#Section "InputClass"
#Identifier "wizardpen"
#MatchIsTablet "on"
#MatchDevicePath "/dev/input/event*"
#MatchTag "wizardpen"
#Driver "wizardpen"
#Option "TopX" "1506"
#Option "TopY" "2705"
#Option "BottomX" "31225"
#Option "BottomY" "30892"
#EndSection
```
At least we know from the wizardpen.conf that **MatchIsTablet "on"** is matching.  Also that version appears to be one where the WizardPen udev rules were added because apparently **MatchTag "wizardpen"** is also matching.

Although on the 52-tablet.conf I would use **MatchProduct "PF1209"** because it is more unique.  Or **MatchProduct "Tablet PF1209"**.

With those two commented out does the tablet respond at all just on evdev?

---

### Post by krakonos on 2012-07-22
Hi I am unfortunately back, recently I switched to 12.04 due to gimp 2.8 - after installation everything was OK - pressure worked in gimp - but I try to change the aspect ratio as I did before 
-I've created /etc/X11/xorg.conf.d/   folder and 52-tablet.conf  file inside with this content
```

Section "InputClass"
        Identifier "Genius PenSketch pen"
        MatchProduct "Tablet"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.
        Option "Calibration" "81 23970 1080 14999"
EndSection

```On one side resolution changed but  on the other now I cannot draw any more. So I deleted the file and directory but the problem remain

I noticed that on comman xinput list-props 10 there is probably problem with Edev Axis calibration:
Evdev Axis Calibration (252):    <no items>

Here are all commands you requested last time
```

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 13fe:3100 Kingston Technology Company Inc. 2/4 GB stick
Bus 003 Device 002: ID 040b:2000 Weltrend Semiconductor 
Bus 003 Device 003: ID 5543:0042 UC-Logic Technology Corp. Tablet PF1209
Bus 007 Device 002: ID 046d:c521 Logitech, Inc. Cordless Mouse Receiver

``````

 xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Generic USB Keyboard                        id=9    [slave  pointer  (2)]
&#9116;   &#8627;                 9x12 Tablet                 id=10    [slave  pointer  (2)]
&#9116;   &#8627;                 9x12 Tablet                 id=11    [slave  pointer  (2)]
&#9116;   &#8627;                 9x12 Tablet                 id=12    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=13    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Generic USB Keyboard                        id=8    [slave  keyboard (3)]


``````

 list-props 10
Device '                9x12 Tablet':
    Device Enabled (122):    1
    Coordinate Transformation Matrix (124):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (247):    0
    Device Accel Constant Deceleration (248):    1.000000
    Device Accel Adaptive Deceleration (249):    1.000000
    Device Accel Velocity Scaling (250):    10.000000
    Device Product ID (242):    21827, 66
    Device Node (243):    "/dev/input/event6"
    Evdev Axis Inversion (251):    0, 0
    Evdev Axis Calibration (252):    <no items>
    Evdev Axes Swap (253):    0
    Axis Labels (254):    "Abs X" (269), "Abs Y" (270), "Abs Pressure" (271)
    Button Labels (255):    "Button 0" (268), "Button Unknown" (245), "Button Unknown" (245), "Button Wheel Up" (128), "Button Wheel Down" (129)
    Evdev Middle Button Emulation (256):    0
    Evdev Middle Button Timeout (257):    50
    Evdev Third Button Emulation (258):    0
    Evdev Third Button Emulation Timeout (259):    1000
    Evdev Third Button Emulation Button (260):    3
    Evdev Third Button Emulation Threshold (261):    20
    Evdev Wheel Emulation (262):    0
    Evdev Wheel Emulation Axes (263):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (264):    10
    Evdev Wheel Emulation Timeout (265):    200
    Evdev Wheel Emulation Button (266):    4
    Evdev Drag Lock Buttons (267):    0



``````

list-props 11
Device '                9x12 Tablet':
    Device Enabled (122):    1
    Coordinate Transformation Matrix (124):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (247):    0
    Device Accel Constant Deceleration (248):    1.000000
    Device Accel Adaptive Deceleration (249):    1.000000
    Device Accel Velocity Scaling (250):    10.000000
    Device Product ID (242):    21827, 66
    Device Node (243):    "/dev/input/event7"
    Evdev Axis Inversion (251):    0, 0
    Evdev Axes Swap (253):    0
    Axis Labels (254):    "Rel X" (132), "Rel Y" (133), "Rel Vert Wheel" (246), "Rel Misc" (272)
    Button Labels (255):    "Button Left" (125), "Button Middle" (126), "Button Right" (127), "Button Wheel Up" (128), "Button Wheel Down" (129), "Button Horiz Wheel Left" (130), "Button Horiz Wheel Right" (131)
    Evdev Middle Button Emulation (256):    0
    Evdev Middle Button Timeout (257):    50
    Evdev Third Button Emulation (258):    0
    Evdev Third Button Emulation Timeout (259):    1000
    Evdev Third Button Emulation Button (260):    3
    Evdev Third Button Emulation Threshold (261):    20
    Evdev Wheel Emulation (262):    0
    Evdev Wheel Emulation Axes (263):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (264):    10
    Evdev Wheel Emulation Timeout (265):    200
    Evdev Wheel Emulation Button (266):    4
    Evdev Drag Lock Buttons (267):    0



```

---

### Post by Favux on 2012-07-22
Hi krakonos,

This is discouraging.  Isn't the default Precise Gimp still a 2.6?  Did you install 2.8?

Do you happen to remember an update coming through about the time the tablet stopped drawing?  If so any chance you remember what was in the update?

Also when you changed proportions was it drawing lines or anything that stopped or just pressure?

I'm having a hard time understanding why applying the Coordinate option would knock the tablet off the correct evdev snippet "permanently".  Were you seeing Evdev Axis Calibration with some coordinate values before you tried the Coordinate option?

---

### Post by krakonos on 2012-07-22
Yes, I installed gimp 2.8 from here [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) - everything  worked fine
Unfortunately it was among first things I've installed ( gimp 2.8 was the reason for upgrade because it cannot be installed under 11.04 or 11.10 as I know.) and almost all other software and updates was done after it and it was hundereds of MB I installed many  dependencies for blender, not sure if I installed nvidia-current driver before or after it.
Here is a video where you can see wahat happened. I use only pen during this video
[http://www.youtube.com/watch?v=a1L5IyaX6As](http://www.youtube.com/watch?v=a1L5IyaX6As)

> Were you seeing Evdev Axis Calibration with some coordinate values before you tried the Coordinate option?I didn't check it because it's worked

---

### Post by Favux on 2012-07-22
Thank you.  The video was very helpful.  Alright on the video the cursor/pointer is tracking the pen tip and it can select.  Just no line is drawn.  That sound right?
> I didn't check it because it's worked 
I figured, but the chance of maybe finding out if there were correct looking coordinates compelled me to ask.

Alright find your Xorg.0.log in /var/log and right click on it and choose Compress.  Attach it to your next post please.  Let's see if that tells us anything.

So we are seeing tracking and a left click (Button 1 press and release).  But no line being drawn implies no pressure coordinates being transmitted.

We've seen stuff like this before with tablets in Ubuntu from some of their modifications of the touch stack for multitouch.  Bugs were introduced.

So I'm wondering if this is a Ubuntu specific problem/bug.

I'm thinking we may need to run evtest:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Evtest](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Evtest)  and see if the pressure coordinates are being transmitted correctly or at all.

---

### Post by krakonos on 2012-07-22
I'm not absolutly sure but I think that everything worked before I've created 52-tablet.conf file - anyway here is the log

I instlled also [B]evtest
[/B]```

 sudo evtest /dev/input/event6
Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0x5543 product 0x42 version 0x110
Input device name: "                9x12 Tablet"
Supported events:
  Event type 0 (EV_SYN)
  Event type 1 (EV_KEY)
    Event code 256 (BTN_0)
    Event code 320 (BTN_TOOL_PEN)
    Event code 330 (BTN_TOUCH)
    Event code 331 (BTN_STYLUS)
  Event type 3 (EV_ABS)
    Event code 0 (ABS_X)
      Value      0
      Min        0
      Max    24000
    Event code 1 (ABS_Y)
      Value      0
      Min        0
      Max    18000
    Event code 24 (ABS_PRESSURE)
      Value      0
      Min        0
      Max     1023
  Event type 4 (EV_MSC)
    Event code 4 (MSC_SCAN)
Testing ... (interrupt to exit)


```

but I don't know where can I see the event stream

---

### Post by Favux on 2012-07-22
Right, I understand you timed it to right then.  It's just that I discounted that because if using .conf files in /etc/X11/xorg.conf.d broke things that would imply something profoundly wrong with the X Server.  And you would think they would have caught somthing like that before they released it.  But maybe I'm making too big of an assumption?

---

### Post by krakonos on 2012-07-22
I'm not sure what are you asking - you know, my English isn't the best :)

---

### Post by Favux on 2012-07-22
Don't worry, talking out loud again.  :)

Hmm.  In the Xorg.0.log.old the evdev module gets dropped for the tablet right near the end.  But it seems OK with the Xorg.0.log.  In both you see two "evdev tablet catchall" identifiers with the only difference between them, other than the event number, being:
```
[    12.682] (--) evdev:                 9x12 Tablet: Found 1 mouse buttons
```
in the first one and:
```
[    12.985] (--) evdev:                 9x12 Tablet: Found 3 mouse buttons
```
I'm pretty sure that isn't right.  There should only be one pen or "evdev tablet catchall" identifier.

Which leads to this harebrained idea.  Let's hope the event numbers are stable and let's try to block the second one, the one on event8 and see what happens.

If you deleted the xorg.conf.d directory add it back.
```
sudo mkdir /etc/X11/xorg.conf.d
```
Then create the file 52-tablet.conf in the new xorg.con.d directory and then copy and paste the snippet/contents in it with:
```
gksudo gedit /etc/X11/xorg.conf.d/52-tablet.conf
```
So the snippet you'd place in the new file 52-tablet.conf would be:
```
Section "InputClass"
        Identifier "Ignore second Genius PenSketch pen"
        MatchIsTablet "on"
        MatchProduct "Tablet"
        MatchDevicePath "/dev/input/event8"
        Driver "evdev"
	Option "Ignore" "on"
EndSection
```
And restart with fingers crossed.

---

### Post by krakonos on 2012-07-22
It wasn't right way - now my tablet is "dead"

---

### Post by Favux on 2012-07-22
What happens if you change it to **event6**?

---

### Post by krakonos on 2012-07-22
It's moving now but doesn't draw again

---

### Post by Favux on 2012-07-22
Hmm.  So the pen is on the third event not the first?  I didn't expect that.

This is sounding more and more like a driver problem.  Unless a udev rule can mess things up.  I don't think so.

Do you get drawing in anything else like MyPaint or Inkscape?

If not are you up for running evtest on event8?  So we can see what pressure is doing?

I'll try to think about this a bit.  I suspect we'll need to ask Nick for help to sort this out.

---

### Post by krakonos on 2012-07-22
I didn't expect it but it draw nicely in mypaint (attachment)

I found that if I set up Input devices Virtual core XTEST pointer and 9x12 Tablet on Disabled (instead of Screen) than it can draw in gimp but without pressure

---

### Post by Favux on 2012-07-22
Wow!

So the bug is in Gimp?  Amazing.

Qt currently has a bug where it doesn't have pressure but at least it draws I think.  It can't handle pressure from the evdev driver.  So any Qt app. is affected.  See the Krita page:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_in_Krita](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_in_Krita)

It looks like Gimp 2.8 has done them one better and can't handle a tablet pen on the evdev driver at all.

Instead of deleting 2.8 and reinstalling Gimp 2.6 how about checking Inkscape?  Does it draw with pressure there too?

If so this is definitely a bug we want to report.

Oh wait a minute.  You said it did draw in Gimp 2.8 when you first installed it I think, didn't you?

---

### Post by krakonos on 2012-07-22
Definitely - I had pressure in gimp 2.8 after installation
In 2.6 I had to change in preferencies - Window management - hint for docks and toolbox to Normal window   to have pressure but in 2.8 it has no effect

---

### Post by Favux on 2012-07-22
We might be on to something.  So in Gimp 2.8 you still have to configure Extended Input Devices by setting the pen to Screen, correct?

How many input devices do you see in Configure Extended Input Devices.  3?  are they all called "9x12 Tablet"?  Did the number go to 2 after we added the Ignore snippet?

---

### Post by krakonos on 2012-07-22
You can see it in the video I posted before it still look the same
[http://www.youtube.com/watch?v=a1L5IyaX6As](http://www.youtube.com/watch?v=a1L5IyaX6As)

---

### Post by Favux on 2012-07-22
Alright, I had to go to full screen to see it.  There is only one "9x12 Tablet".

Now Vicktori.S said that was a bug in set up.  I forget which app., it may have been Gimp.  The reason it was a bug is that the device names were all the same and the app. couldn't distinguish between them.  She said it was luck that the first event was the pen.  So the app. worked.

We had a discussion with Nick about modifying the kernel driver to fix that.  Maybe we could do that through udev rules instead.  I'll have to ask Nick.

But it looks like your pen is the third event.  Maybe that is why it isn't working.

If we assume the Ignore snippet got rid of the first tablet identifier Gimp is now seeing the mouse snippet.  What if we set up an Ignore on it also?  Will that finally leave just the pen?

So duplicate the Ignore snippet this time use **event7**.  And hope your event numbers don't change.

You don't have a tablet mouse do you?

---

### Post by krakonos on 2012-07-23
The same as before - cursor is moving but not drawing utill I check disabled in Input Devices - but events's probaly changed and there are only two 9x12 Tablet instead of 3 in xinput list

And yes I have a mouse for the tablet but I don't use it

```

 xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Generic USB Keyboard                        id=9    [slave  pointer  (2)]
&#9116;   &#8627;                 9x12 Tablet                 id=10    [slave  pointer  (2)]
&#9116;   &#8627;                 9x12 Tablet                 id=11    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=12    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Generic USB Keyboard                        id=8    [slave  keyboard (3)]


$ xinput list-props 10
Device '                9x12 Tablet':
    Device Enabled (122):    1
    Coordinate Transformation Matrix (124):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (247):    0
    Device Accel Constant Deceleration (248):    1.000000
    Device Accel Adaptive Deceleration (249):    1.000000
    Device Accel Velocity Scaling (250):    10.000000
    Device Product ID (242):    21827, 66
    Device Node (243):    "/dev/input/event7"
    Evdev Axis Inversion (251):    0, 0
    Evdev Axes Swap (253):    0
    Axis Labels (254):    "Rel X" (132), "Rel Y" (133), "Rel Vert Wheel" (246), "Rel Misc" (268)
    Button Labels (255):    "Button Left" (125), "Button Middle" (126), "Button Right" (127), "Button Wheel Up" (128), "Button Wheel Down" (129), "Button Horiz Wheel Left" (130), "Button Horiz Wheel Right" (131)
    Evdev Middle Button Emulation (256):    0
    Evdev Middle Button Timeout (257):    50
    Evdev Third Button Emulation (258):    0
    Evdev Third Button Emulation Timeout (259):    1000
    Evdev Third Button Emulation Button (260):    3
    Evdev Third Button Emulation Threshold (261):    20
    Evdev Wheel Emulation (262):    0
    Evdev Wheel Emulation Axes (263):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (264):    10
    Evdev Wheel Emulation Timeout (265):    200
    Evdev Wheel Emulation Button (266):    4
    Evdev Drag Lock Buttons (267):    0


$ xinput list-props 11
Device '                9x12 Tablet':
    Device Enabled (122):    1
    Coordinate Transformation Matrix (124):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (247):    0
    Device Accel Constant Deceleration (248):    1.000000
    Device Accel Adaptive Deceleration (249):    1.000000
    Device Accel Velocity Scaling (250):    10.000000
    Device Product ID (242):    21827, 66
    Device Node (243):    "/dev/input/event8"
    Evdev Axis Inversion (251):    0, 0
    Evdev Axis Calibration (252):    <no items>
    Evdev Axes Swap (253):    0
    Axis Labels (254):    "Abs X" (269), "Abs Y" (270), "Abs Pressure" (271)
    Button Labels (255):    "Button Left" (125), "Button Middle" (126), "Button Right" (127), "Button Wheel Up" (128), "Button Wheel Down" (129)
    Evdev Middle Button Emulation (256):    0
    Evdev Middle Button Timeout (257):    50
    Evdev Third Button Emulation (258):    0
    Evdev Third Button Emulation Timeout (259):    1000
    Evdev Third Button Emulation Button (260):    3
    Evdev Third Button Emulation Threshold (261):    20
    Evdev Wheel Emulation (262):    0
    Evdev Wheel Emulation Axes (263):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (264):    10
    Evdev Wheel Emulation Timeout (265):    200
    Evdev Wheel Emulation Button (266):    4
    Evdev Drag Lock Buttons (267):    0



```

---

### Post by Favux on 2012-07-23
Alright, you do have a tablet mouse.  At any point did you check if the mouse drew?

Since the Ignore snippet does block one of them from appearing in **xinput list** let me be sure.  You added a second Ignore snippet to the custom .conf file correct?  There should be a total of two Ignore snippets now.

If so maybe the event numbers changed.

> The same as before - cursor is moving but not drawing utill I check disabled in Input Devices 
So disabled gets it drawing?  What exactly happens when you do that?

---

### Post by krakonos on 2012-07-23
Yes, the mouse can draw (it is first time I try it since I bought the tablet).
Here is conf file
```

Section "InputClass"
        Identifier "Ignore second Genius PenSketch pen"
        MatchIsTablet "on"
        MatchProduct "Tablet"
        MatchDevicePath "/dev/input/event6"
        Driver "evdev"
    Option "Ignore" "on"
EndSection

Section "InputClass"
        Identifier "Ignore second Genius PenSketch pen"
        MatchIsTablet "on"
        MatchProduct "Tablet"
        MatchDevicePath "/dev/input/event7"
        Driver "evdev"
    Option "Ignore" "on"
EndSection

```And yes if I set it to disabled the pen can draw without pressure.
BTW do you  sleep at least from time to time? :)

---

### Post by ricardo roy on 2012-07-23
> **Favux said:**
> You should be able to get an idea of the coordinates by looking at the tablet info. page on the DIGI*mend* site:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=UC-Logic_Tablet_PF1209](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=UC-Logic_Tablet_PF1209)  and then calculating it like so.
12"x9", 4000 LPI

max X = 12" x 4000 LPI = 48000
max Y = 9" x 4000 LPI = 36000

The origin or 0,0 is the top left corner.  And that's assuming the physical maximum potential 4000 LPI was what was used.

But I do see in the HID report descriptor:
```
0x05, 0x01,         /*          Usage Page (Desktop),       ; Generic desktop controls (01h)            */
0x09, 0x30,         /*          Usage (X),                  ; X (30h, dynamic value)                    */
0x09, 0x31,         /*          Usage (Y),                  ; Y (31h, dynamic value)                    */
0x15, 0x00,         /*          Logical Minimum (0),                                                    */
0x26, 0xFF, 0x7F,   /*          Logical Maximum (32767),                                                */
0x35, 0x00,         /*          Physical Minimum (0),                                                   */
0x46, 0xFF, 0x7F,   /*          Physical Maximum (32767),
```If I do 32767 / 4000 = 8.19 that would make sense if the Y is actually 8.19 inches instead of 9 inches.  Is it?

Another way to get coordinates is to use xinput_calibrator.  It is also called 'Calibrate Touchscreen' in Software Center.

But let's forget about coordinates for now and see what happens if we just let the evdev snippets pick up the tablet like they are suppose to.  So comment out (#) the two .conf files you added, e.g.:
```
#Section "InputClass"
#Identifier "wizardpen"
#MatchIsTablet "on"
#MatchDevicePath "/dev/input/event*"
#MatchTag "wizardpen"
#Driver "wizardpen"
#Option "TopX" "1506"
#Option "TopY" "2705"
#Option "BottomX" "31225"
#Option "BottomY" "30892"
#EndSection
```At least we know from the wizardpen.conf that **MatchIsTablet "on"** is matching.  Also that version appears to be one where the WizardPen udev rules were added because apparently **MatchTag "wizardpen"** is also matching.

Although on the 52-tablet.conf I would use **MatchProduct "PF1209"** because it is more unique.  Or **MatchProduct "Tablet PF1209"**.

With those two commented out does the tablet respond at all just on evdev?

Thanks a lot for your patience it was not possible for me to comment you back until now. 
Well, indeed I made some of the steps you just described to the other user and that's why I created the file '52-tablet.conf'. I had no clue of how i could get the coordinates right but then I downloaded the program 'Calibrate Touchscreen' and that program gave me the coordinates in printed in the terminal. This numbers are those that I put on my file '52-tablet.conf':

xmin= 0                              xmax = 32767 
ymin= 0                              ymax=  32767

About the file '70-wizardpen.conf' I haven't configurated it.
So, you suggested me to check if **MatchProduct "Tablet PF1209"** works better with my tablet? I mean, to configure the file ' 52-tablet.conf'? I ask this because i configurated it just as the steps described some pages before.
I will check ;)

---

### Post by krakonos on 2012-07-23
After another restart now the pen doesn't react at all - I've tried the tablet mouse and it behave exactly like the pen before - when I set in gimp settings Mode to Screen - mouse doesn't react but when I set it to disable it draws.

```

xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627;                 9x12 Tablet                 id=9    [slave  pointer  (2)]
&#9116;   &#8627;                 9x12 Tablet                 id=10    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Logitech Logitech USB Keyboard              id=8    [slave  keyboard (3)]



 xinput list-props 9
Device '                9x12 Tablet':
    Device Enabled (122):    1
    Coordinate Transformation Matrix (124):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (250):    0
    Device Accel Constant Deceleration (251):    1.000000
    Device Accel Adaptive Deceleration (252):    1.000000
    Device Accel Velocity Scaling (253):    10.000000
    Device Product ID (242):    21827, 66
    Device Node (243):    "/dev/input/event5"
    Evdev Axis Inversion (254):    0, 0
    Evdev Axis Calibration (255):    <no items>
    Evdev Axes Swap (256):    0
    Axis Labels (257):    "Abs X" (247), "Abs Y" (248), "Abs Pressure" (249)
    Button Labels (258):    "Button 0" (246), "Button Unknown" (245), "Button Unknown" (245), "Button Wheel Up" (128), "Button Wheel Down" (129)
    Evdev Middle Button Emulation (259):    0
    Evdev Middle Button Timeout (260):    50
    Evdev Third Button Emulation (261):    0
    Evdev Third Button Emulation Timeout (262):    1000
    Evdev Third Button Emulation Button (263):    3
    Evdev Third Button Emulation Threshold (264):    20
    Evdev Wheel Emulation (265):    0
    Evdev Wheel Emulation Axes (266):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (267):    10
    Evdev Wheel Emulation Timeout (268):    200
    Evdev Wheel Emulation Button (269):    4
    Evdev Drag Lock Buttons (270):    0




$ xinput list-props 10
Device '                9x12 Tablet':
    Device Enabled (122):    1
    Coordinate Transformation Matrix (124):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (250):    0
    Device Accel Constant Deceleration (251):    1.000000
    Device Accel Adaptive Deceleration (252):    1.000000
    Device Accel Velocity Scaling (253):    10.000000
    Device Product ID (242):    21827, 66
    Device Node (243):    "/dev/input/event6"
    Evdev Axis Inversion (254):    0, 0
    Evdev Axes Swap (256):    0
    Axis Labels (257):    "Rel X" (132), "Rel Y" (133), "Rel Vert Wheel" (271), "Rel Misc" (272)
    Button Labels (258):    "Button Left" (125), "Button Middle" (126), "Button Right" (127), "Button Wheel Up" (128), "Button Wheel Down" (129), "Button Horiz Wheel Left" (130), "Button Horiz Wheel Right" (131)
    Evdev Middle Button Emulation (259):    0
    Evdev Middle Button Timeout (260):    50
    Evdev Third Button Emulation (261):    0
    Evdev Third Button Emulation Timeout (262):    1000
    Evdev Third Button Emulation Button (263):    3
    Evdev Third Button Emulation Threshold (264):    20
    Evdev Wheel Emulation (265):    0
    Evdev Wheel Emulation Axes (266):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (267):    10
    Evdev Wheel Emulation Timeout (268):    200
    Evdev Wheel Emulation Button (269):    4
    Evdev Drag Lock Buttons (270):    0



```

---

### Post by Favux on 2012-07-23
```

```Hi krakonos & ricardo roy,

Something has me puzzled.  You both are in Precise (12.04) and apparently both have Genius PenSketch 12x9's.  Your **lsusb**'s are the same:
> Bus 003 Device 003: ID 5543:0042 UC-Logic Technology Corp. Tablet PF1209
But your xinput list's are different.  Krakonos' is:
> &#9116;   &#8627;                 9x12 Tablet                 id=10    [slave  pointer  (2)]
&#9116;   &#8627;                 9x12 Tablet                 id=11    [slave  pointer  (2)]
&#9116;   &#8627;                 9x12 Tablet                 id=12    [slave  pointer  (2)]
But ricardo roy's is:
> &#9116; &#8627; Tablet PF1209 id=8 [slave pointer (2)]
&#9116; &#8627; Tablet PF1209 id=9 [slave pointer (2)]
And I don't know why.  I know krakonos has let Update Manager update his Precise.  Is there a chance your Precise hasn't been updated ricardo roy?  **If it hasn't please don't update it!**  If you run Update Manager the list of proposed updates may contain the one(s) that broke krakonos' tablet.  It would be very useful to know what that update(s) is.


@ krakonos
So the Ignore snippets in the .conf file look good.  And we can only get it down to two events.  Interesting since that is what ricardo roy sees without doing any ignores.  So I guess get rid of at least the mouse ignore snippet.  I mean comment (#) it out.
> Yes, the mouse can draw (it is first time I try it since I bought the tablet).  And yes if I set it to disabled the pen can draw without pressure.

Now that is interesting.  I recall you said you wanted Gimp 2.8 for its (new) pressure feature.  I haven't seen Gimp 2.8 but I gathered there was a new dialog to configure pressure.  This makes me wonder.  Is there a new setting for pressure in Gimp 2.8 that you need to set in order to get the pen to draw with pressure, and maybe draw at all, when set to screen and not disabled?  Obviously that wouldn't apply to the mouse since it can't give pressure and you always use it with Mode disabled.
> BTW do you sleep at least from time to time?
Yes.  :)

I did go ahead and asked Nick a couple of basic questions that may help us, when he answeres, if it isn't a Gimp setting that turns out to be the problem.


@ ricardo roy,
> I downloaded the program 'Calibrate Touchscreen' and that program gave me the coordinates in printed in the terminal. This numbers are those that I put on my file '52-tablet.conf':

xmin= 0 xmax = 32767
ymin= 0 ymax= 32767
The limit is apparently 2000 LPI so calibration should be:
max X = 12" x 2000 LPI = 24000
max Y = 9" x 2000 LPI = 18000
```
	Option "Calibration" "0 24000 0 18000"
```
Since that shouldn't be different between the two tablets.  Krankonos used:
```
	Option "Calibration" "81 23970 0 17999"
```
My guess is that the coordinates you put in the 52-tablet.conf are why xinput_calibrator is coming up with the incorrect values.
> Well, indeed I made some of the steps you just described to the other user and that's why I created the file '52-tablet.conf'.

About the file '70-wizardpen.conf' I haven't configurated it.

No the point I was making is that the two .conf files you added are matching.  We know that because in the Xorg.0.log we see:
> [    19.627] (**)     Tablet PF1209: Applying InputClass "wizardpen"
[    19.627] (**)     Tablet PF1209: Applying InputClass "Genius PenSketch pen"
Which are the identifiers from the snippets in those two .conf files.  I was asking you to comment them out so they don't affect things.  I wanted to see where you are at just using the 10-evdev.conf.
> So, you suggested me to check if MatchProduct "Tablet PF1209" works better with my tablet? I mean, to configure the file ' 52-tablet.conf'? I ask this because i configurated it just as the steps described some pages before.
Yes when you use:
```
MatchProduct "Tablet|PF1209"
```
You are saying match to either Tablet or PF1209.  It will run into Tablet first and so use that.  PF1209 is a lot more specific than Tablet.  So that's why I suggested the alternate matches for the MatchProduct in your 52-tablet.conf.

---

### Post by krakonos on 2012-07-24
> Now that is interesting.  I recall you said you wanted Gimp 2.8 for its  (new) pressure feature.  I haven't seen Gimp 2.8 but I gathered there  was a new dialog to configure pressure.  This makes me wonder.  Is there  a new setting for pressure in Gimp 2.8 that you need to set in order to  get the pen to draw with pressure, and maybe draw at all, when set to  screen and not disabled?  Obviously that wouldn't apply to the mouse  since it can't give pressure and you always use it with Mode disabled.It's not fully truth - I don't want gimp 2.8 for its new pressure feature but in that time it didn't support pressure for some tablets (I think it was something in GTK (but I'm not absolutely sure) - which should be solved now  - I had some problems with 2.6 like unwanted lines almost every other stroke ([https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/971521](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/971521) and [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154)) and latest versions of gimp 2.8 cannot be installed because can destroy 11.04 or 11.10. 
I think there is not new setting for pressure in  2.8.

> 
     Code:
         Option "Calibration" "0 24000 0 18000" 
Since that shouldn't be different between the two tablets.  Krankonos used:
     Code:
         Option "Calibration" "81 23970 0 17999" 
My guess is that the coordinates you put in the 52-tablet.conf are why xinput_calibrator is coming up with the incorrect values.

I did the measurement manually with the pen in left top and right bottom corner of tablet so it's not so precise

---

### Post by Favux on 2012-07-24
Well darn, that shoots down that theory.

So the PPA for Gimp you used was this one?:  [https://launchpad.net/~otto-kesselgulasch/+archive/gimp](https://launchpad.net/~otto-kesselgulasch/+archive/gimp)

Viktoria S. had some thoughts.
> Well. I could not figured this out (I mean the device list.). I have got a "specially" compiled gimp 2.8 and on that the pen is the 2nd mousepen on the list, but if I start gimp 2.6 or mypaint the pen is the 1st mousepen on the device list (I am using 12.04 64bit digimended kernel). (Actually the pen got device id 17, and the mouse got 18......)

I can suggest couple of things:
1. Install mypaint from the repositories. Configure the pen in mypaint and see if he can draw with the pen there. (At least in this way we can check if there is everything ok with the pen or not.)
2. Compile gimp 2.8 on the way I have suggested and on the device list enable only the pen.
3. Maybe he can try to use the wacom driver. As far as I know the wacom driver ads the word stylus to the name of the pen so in this way everything or almost everything gets a unique name. So there could not be a problem with gimp 2.8. (I am thinking about trying to use the wacom driver on 12.10 too, but only after the kernel has been update to 3.5 stable and I can configure the Oracle VM perfectly with that kernel. Later I can give feedback if I was successfull with it or not.)

Good luck guys!
We already tried MyPaint and it worked.

With Gimp she's talking about:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_in_GIMP#Configuring_multiple_input_devices](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_in_GIMP#Configuring_multiple_input_devices)  Where she links to her Gimp bug report where she shows the code changes (patch) needed to fix the bug:  [https://bugzilla.gnome.org/show_bug.cgi?id=674253](https://bugzilla.gnome.org/show_bug.cgi?id=674253)  And the Gimp code to patch and compile is here:  [http://www.gimp.org/downloads/](http://www.gimp.org/downloads/)

I guess trying the Wacom X driver is worth a shot.  What do you think?  I believe I vaguely remember how we used to go about it with the Waltop tablets.

---

### Post by ricardo roy on 2012-07-24
> **Favux said:**
> Hi krakonos & ricardo roy,

Something has me puzzled.  You both are in Precise (12.04) and apparently both have Genius PenSketch 12x9's.  Your **lsusb**'s are the sam...

Favux:

About the update of Precise, I want to tell you that I just installed Ubuntu 12.04 LTS (with the cd iso) in a computer that hadn't had Ubuntu before and inmediately I started in Ubuntu I made the update, it was about 200 updates that the manager install.

When I tried with the driver 'wizardpen', as a followed a tutorial, I installed some packages from the Ubuntu software center,  ' xutils, libx11-dev, libxext-dev, build-essential,             xautomation, xinput, xserver-xorg-dev, xutils-dev, libtool,              autoconf'.  I hope i didn't break so configuration of my evdev.

And this is the output of the file '10-evdev.conf':

[email]mori@Lapmori:/usr/share/X11/xorg.conf[/email].d$ less 10-evdev.conf
#
# Catch-all evdev loader for udev-based systems
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

---

### Post by Favux on 2012-07-24
Alright, so you are up to date through Update Manager also.  That doesn't explain the difference in **xinput list**.  I wonder what it could be?  Firmware?

No, adding libraries to your system won't break anything unless they have a weird dependency chain that causes a removal of needed stuff.  That happens occasionally and is almost always a packaging mistake.

So have you now commented out (#) the wizardpen.conf and the 52-tablet.conf to "deactivate" them?  Or removed them?

Does your tablet now do anything with only the default 10-evdev.conf you show?

---

### Post by ricardo roy on 2012-07-25
> **Favux said:**
> 
So have you now commented out (#) the wizardpen.conf and the 52-tablet.conf to "deactivate" them?  Or removed them?

Oh! I was confused about it. Well I put the simbol (#) in both files, I comment it and then rebooted the computer and nothing happened, no response. 

> **Favux said:**
> 
Does your tablet now do anything with only the default 10-evdev.conf you show?

Something happens with this deafault configuration of '10-evdev.conf'. It seems like the pen do a click but only in the corners of the work area, if I touch the tablet with the pen it's like if I were doing click with the left button of the mouse and I want to repeat that it only occurs in the corners. What do you think??

Thanks alot for your help one again

---

### Post by Favux on 2012-07-26
> I put the symbol (#) in both files, I comment it and then rebooted the computer and nothing happened, no response.

the pen do a click but only in the corners of the work area, if I touch the tablet with the pen it's like if I were doing click with the left button of the mouse and I want to repeat that it only occurs in the corners.

So it does respond with the default 10-evdev .conf.  Just not the way we want.  :(

The pen tip is suppose to cause a Button 1 event (left click).  So that seems on the right track.  But why only in the corners?

I can't think of a coordinate problem that would cause this.  Please repeat **xinput list** and using the ID numbers repeat the list-props commands.  Example:
```
xinput list-props 8
```
Please also post your Xorg.0.log from /var/log.  Go ahead and Compress and attach it.

Does your tablet work in Windows or another OS?

---

### Post by ricardo roy on 2012-07-26
> **Favux said:**
> 
The pen tip is suppose to cause a Button 1 event (left click).  So that seems on the right track.  But why only in the corners?


I'm wonder why.

> **Favux said:**
> 
Please repeat **xinput list** and using the ID numbers repeat the list-props commands. 

Here they are:

mori@Lapmori:~$ xinput list-props 8
Device '    Tablet PF1209':
    Device Enabled (121):    1
    Coordinate Transformation Matrix (123):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (247):    0
    Device Accel Constant Deceleration (248):    1.000000
    Device Accel Adaptive Deceleration (249):    1.000000
    Device Accel Velocity Scaling (250):    10.000000
    Device Product ID (240):    21827, 66
    Device Node (241):    "/dev/input/event3"
    Evdev Axis Inversion (251):    0, 0
    Evdev Axis Calibration (252):    <no items>
    Evdev Axes Swap (253):    0
    Axis Labels (254):    "Abs X" (244), "Abs Y" (245), "Abs Pressure" (246)
    Button Labels (255):    "Button Unknown" (243), "Button Unknown" (243), "Button Unknown" (243), "Button Wheel Up" (127), "Button Wheel Down" (128), "Button Horiz Wheel Left" (129), "Button Horiz Wheel Right" (130)
    Evdev Middle Button Emulation (256):    0
    Evdev Middle Button Timeout (257):    50
    Evdev Third Button Emulation (258):    0
    Evdev Third Button Emulation Timeout (259):    1000
    Evdev Third Button Emulation Button (260):    3
    Evdev Third Button Emulation Threshold (261):    20
    Evdev Wheel Emulation (262):    0
    Evdev Wheel Emulation Axes (263):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (264):    10
    Evdev Wheel Emulation Timeout (265):    200
    Evdev Wheel Emulation Button (266):    4
    Evdev Drag Lock Buttons (267):    0

mori@Lapmori:~$ xinput list-props 9
Device '    Tablet PF1209':
    Device Enabled (121):    1
    Coordinate Transformation Matrix (123):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (247):    0
    Device Accel Constant Deceleration (248):    1.000000
    Device Accel Adaptive Deceleration (249):    1.000000
    Device Accel Velocity Scaling (250):    10.000000
    Device Product ID (240):    21827, 66
    Device Node (241):    "/dev/input/event4"
    Evdev Axis Inversion (251):    0, 0
    Evdev Axes Swap (253):    0
    Axis Labels (254):    "Rel X" (131), "Rel Y" (132), "Rel Vert Wheel" (268)
    Button Labels (255):    "Button Left" (124), "Button Middle" (125), "Button Right" (126), "Button Wheel Up" (127), "Button Wheel Down" (128), "Button Horiz Wheel Left" (129), "Button Horiz Wheel Right" (130)
    Evdev Middle Button Emulation (256):    0
    Evdev Middle Button Timeout (257):    50
    Evdev Third Button Emulation (258):    0
    Evdev Third Button Emulation Timeout (259):    1000
    Evdev Third Button Emulation Button (260):    3
    Evdev Third Button Emulation Threshold (261):    20
    Evdev Wheel Emulation (262):    0
    Evdev Wheel Emulation Axes (263):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (264):    10
    Evdev Wheel Emulation Timeout (265):    200
    Evdev Wheel Emulation Button (266):    4
    Evdev Drag Lock Buttons (267):    0

> **Favux said:**
>  Xorg.0.log from /var/log. 
Ok, it's attached

> **Favux said:**
> Does your tablet work in Windows or another OS?

At least I know that it works perfectly on Windows but I don't know if It works on a Mac. For windows it was necessary to install the driver (CD) that is included with the Tablet, so no problem on windows.

:/

---

### Post by ricardo roy on 2012-07-26
> **Favux said:**
> 
Does your tablet work in Windows or another OS?
 Well, now I'm more puzzeled than before. Related to this question, I just try to see what happened with the tablet in another computer so I plugged the tablet in one friend's computer with ubuntu 11.10 and it worked instantly! I just can't believe it. It is a desktop computer and he have used that version of ubuntu for a long time. I looked into his Xorg.0.log and the driver used for this tablet seems to be set by default by evdev.

:confused:

---

### Post by Favux on 2012-07-26
Hi ricardo roy,

> At least I know that it works perfectly on Windows

Well, now I'm more puzzeled than before. Related to this question, I just try to see what happened with the tablet in another computer so I plugged the tablet in one friend's computer with ubuntu 11.10 and it worked instantly! I just can't believe it. It is a desktop computer and he have used that version of ubuntu for a long time. I looked into his Xorg.0.log and the driver used for this tablet seems to be set by default by evdev.
That is important information.  We now know for sure it is not your hardware or firmware.  As you know I think krakonos' problem may be his firmware or  a scrambled kernel.

In your case something has changed between 11.10 and 12.04.  What?

1)  The kernel driver.  Maybe, but I tend to doubt it.

2)  The evdev driver.  More likely, but I still doubt it.

3)  Something Ubuntu has done in 12.04.  I think this is the most likely scenario.  But that means our chances of finding and fixing it are not good.

Your Xorg.0.log attachment did not upload.  It is not attached.

---

### Post by ricardo roy on 2012-07-26
Interesting. I'm also puzzuled.


> **Favux said:**
> 
Your Xorg.0.log attachment did not upload.  It is not attached.

Oh! Sorry I didn't notice it. So here it is.

---

### Post by Favux on 2012-07-26
Alright.  Again the setup of the tablet appears OK but then the evdev driver is unloaded.  And the tablet is apparently succesfully reloaded.

The tablet looks OK:
> [   502.361] (II) config/udev: Adding input device     Tablet PF1209 (/dev/input/event3)
[   502.361] (**)     Tablet PF1209: Applying InputClass "evdev tablet catchall"
[   502.361] (II) Using input driver 'evdev' for '    Tablet PF1209'
finishing with:
> [   502.361] (II) XINPUT: Adding extended input device "    Tablet PF1209" (type: TABLET, id 8 )
I am a little bothered by:
> [   502.379] (II) config/udev: Adding input device     Tablet PF1209 (/dev/input/event4)
[   502.379] (**)     Tablet PF1209: Applying InputClass "evdev pointer catchall"
[   502.379] (**)     Tablet PF1209: Applying InputClass "evdev tablet catchall"
[   502.379] (II) Using input driver 'evdev' for '    Tablet PF1209'
Why is the identifier from the tablet snippet there?  But it seems to setup correctly anyway:
> [   502.379] (II) XINPUT: Adding extended input device "    Tablet PF1209" (type: MOUSE, id 9)
Three things happen before the evdev module/driver unloads.  Keyboard on evdev, mouse on evdev, and a NVidia resolutions setting.

Could you try booting without your PS/2 mouse connected?
> [    19.443] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE, id 11)
How does the tablet behave then?

---

### Post by krakonos on 2012-07-27
Ok - I've compilled custom gimp -still the same 
Then I tried gimp in virtualbox but it has its own drivers that probably doesn't support pressure 
Now I downloaded and installed wacom drivers but don't know how to disable current driver
But I still believe that it is something in config files for gimp or tablet driver - is there a way how to replace all the config files with defaults?


BTW I use gnome-classic (no effect) and 3.2.0-27-generic kernel

---

### Post by Favux on 2012-07-27
> is there a way how to replace all the config files with defaults?
I don't know.  I do know Gimp places some config files around that are apparently hard to find so you can get rid of them.  Recompiling may not do it.  I've seen several threads/tutorials on finding them and removing them.  So mysterious Gimp problems finally get fixed.  I thought I had bookmarked a couple of them but if so I can't find them now.

---

### Post by krakonos on 2012-07-27
Do you know how to activate the wacom driver I would like to give it a try

---

### Post by Favux on 2012-07-27
Sure, I describe it here:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_xf86-input-wacom#52-waltop.conf](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_xf86-input-wacom#52-waltop.conf)  You'd use a different name for the custom .conf file and your keyword for MatchProduct of course.  Probably ought to try adding MatchIsTablet before MatchProduct also.  And of course you need to use your two snippets.  But it gives you the basic idea.

---

### Post by ricardo roy on 2012-07-27
That's very interesting and I'm also puzzuled about the evdev driver.

> **Favux said:**
> 
Could you try booting without your PS/2 mouse connected?
How does the tablet behave then?

Ok. I just did that and is still doing the same thing, I mean, the pointer does not move while I move the pen and it does a click in the corners. :-|

---

### Post by Favux on 2012-07-27
> Ok. I just did that and is still doing the same thing, I mean, the pointer does not move while I move the pen and it does a click in the corners. 
So it is not some strange conflict with the mouse.  Have seen that kind of thing before.

Are you plugging the tablet directly into a usb port on the computer and not a hub?  Don't use a hub when troubleshooting.  Also have you tried other usb ports on the computer?

---

### Post by ricardo roy on 2012-07-27
> **Favux said:**
> 
Are you plugging the tablet directly into a usb port on the computer and not a hub?  Don't use a hub when troubleshooting.  Also have you tried other usb ports on the computer?

Yes, I plug my tablet into the usb directly. I used the usb ports of the back of my computer. Also I did that, I plugged the tablet into different usb ports while the mouse was unplugged and also with the mouse plugged. And I keep trying just to see if there is a different response but it keeps doing the same.

you just tell me not to update my Precise, right now I have some updates related to the kernel 3.2 ready to install on my update manager, Should I install them? It would change something?
I still have commented the instructions of my '52-tablet.conf', I don't know if you want me to do the same thing with the mouse unppluged? Does it would response different?

---

### Post by Favux on 2012-07-30
Hi ricardo roy,

No go ahead and update if you want to.  I wanted you to hold off when I wasn't sure if you had been updating.  I was hoping that might explain the differences krakonos and you were seeing.  But since you had been updating that doesn't matter now.

Alright it doesn't appear to be a usb port problem.  Always good to rule those out.

I think we've ruled out a mouse conflict.  But it doesn't hurt to check that when you think of it.

Actually at this point we should hope an update fixes things.  So pay attention to what the updates are.  You might spot the important one.

---

### Post by ricardo roy on 2012-07-30
Hi Favux

> **Favux said:**
> 
Actually at this point we should hope an update fixes things.  So pay attention to what the updates are.  You might spot the important one.


Well, I just updated and still not working. I think that the most important of all of this updates was the Kernel, it upgrade my Kernel to the 3.2. I have now no idea what to do. The tablet is still working only in the corners zone. Any other suggestion you could give me?

Thanks a lot.

---

### Post by Favux on 2012-07-31
I figured since I am involved with the DIGI*mend* project I should get one of these tablets.  I have a UC-Logic tablet coming in a couple of days and I think it is the same model that you both have.

So I'll take a look see at it.  One thing to look at is the Windows drivers version and the firmware version according to Windows.  If you know how to get that you should post that.  Maybe one or the other might explain the differences.

When I get it I'll look the thread over again and try to see if I'm missing something obvious.  If it is the same model that should help.  Otherwise I think it is becoming time to post on DIGImend-users and ask Nick for help.

---

### Post by krakonos on 2012-07-31
I think I'll give it up, but one more try before it - perhaps this video can help with some solution :

[http://www.youtube.com/watch?v=sju1N_wvVzA](http://www.youtube.com/watch?v=sju1N_wvVzA)

In the end you can see the pressure is recognized but it still doesn't use it in the working area. But why it works in mypaint - is it GTK+ problem, or could it be caused by java sun - now I dont think that it is driver problem but I can be wrong

---

### Post by krakonos on 2012-09-22
Still no solution? 
I've tried to build gimp 2.8.2 and I have this error in console.

```
(gimp:4337): Gimp-Widgets-CRITICAL **: gimp_device_info_set_device: assertion `(info->device == NULL && GDK_IS_DEVICE (device)) || (GDK_IS_DEVICE (info->device) && device == NULL)' failed

(gimp:4337): Gimp-Widgets-CRITICAL **: gimp_device_info_set_device: assertion `(info->device == NULL && GDK_IS_DEVICE (device)) || (GDK_IS_DEVICE (info->device) && device == NULL)' failed

(gimp:4337): Gimp-Widgets-CRITICAL **: gimp_device_info_set_device: assertion `(info->device == NULL && GDK_IS_DEVICE (device)) || (GDK_IS_DEVICE (info->device) && device == NULL)' failed
```
Than I've tried to edit 10-evdev.conf like this

```

Section "InputClass"
        Identifier "stylus"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

```
This gives me new options in Gimp's Input devices
-9x12 Tablet
-9x12 Tablet Pad
-9x12 Tablet Stylus
but any setup doesn't solve the problem. 

I'm afraid that I'll have to switch back to commercial solutions  almost exactly after one year with Ubuntu :sad:

---

### Post by Favux on 2012-09-22
Hi krakonos,

What I would try is Quantal Beta 2.  It is due out on 9-27-12.  It turns out Precise has a hybrid X Server.  It is a combination of 1.11 and 1.12.  I'm now wondering if that is causing the problem we are seeing in Precise.  I've discovered the Wacom driver needs to be patched to work correctly with it and I am thinking evdev hasn't been properly patched to work with the hybrid X Server when it is running a tablet.  If my guess is correct Quantal, which uses X Server 1.13, should work for you.  And I think it also has Gimp 2.8.  With luck it will take care of both of your issues.

I know for sure the hybrid X Server causes a bug with evdev and the use of a CTM (coordinate transformation matrix) for use with dual monitors and so on.  So maybe this bug too?

I have had luck with Beta 2 releases.  They have been stable enough for me to use and when I do use one I haven't needed to upgrade to the final release.  Update Manager has taken care of updating the Beta 2 to the final release so that hasn't been a problem.

---

### Post by krakonos on 2012-09-23
Is it possible to use the gnome classic there? I'm one of those who really don't like unity

---

### Post by Favux on 2012-09-23
Don't know if Ubuntu will have a classic available.  Don't think so.  In that case you might want to try Mint 14.  The wait will be longer though because it will probably be out a few weeks after Quantal is released.

Mint 14 will basically be Quantal with either MATE or Cinnamon replacing Unity as the Desktop.  And either is basically meant to replicate the feel of Gnome classic.

What I've done is place Cairo Dock on the right side, opposite of the Unity Launcher bar, instead of across the bottom.  Tweaked it a little to look like the Unity Launcher bar.  And by selecting what Cairo Dock displays I have the Gnome Main Menu, my Weather applet, and Gimp, Inkscape, MyPaint icons.  And so on.  So it supplements Unity.  Works for me anyway.

---

### Post by krakonos on 2012-09-23
Ok, I can give it a try on my second system. Still waiting for gnomebuntu but its homepage is still void [http://gnomebuntu.org/](http://gnomebuntu.org/)

---

### Post by krakonos on 2012-09-28
So glad that I did it on my second system - not only I haven't pressure but it make unwanted lines again like in 2.6 what was the reason I switched to 2.8 - I know it's beta (very very buggy) but I don't believe they resolve it in regular release .
I don't know why but I think that every newer version of ubuntu is worse then the previous - I was happy only with 11.04 - this isn't way to go (ubuntu and gimp) - at least in my opinion.

---

### Post by viktoria.s on 2012-10-02
Hi krakonos,

I would like to help with gimp. But I don't know which system you are using right now, so here are all of my thoughts about gimp.

In Ubuntu 11.10, I was experiencing the ghost line issue described here: [http://ubuntuforums.org/showthread.php?t=1899225&page=4](http://ubuntuforums.org/showthread.php?t=1899225&page=4) in the #32 post. For me installing gimp from the mentioned ppa ([https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline](https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline)) helped.

The Ubuntu 12.04 is shipped with gimp 2.6.12 and in this version I did not experienced the ghost line problem at all and I am able to use my multi input tablet without any issue.:p

The Ubuntu 12.10 is going to be shipped with gimp 2.8 where I have problems with my multi input device. I did a quick test with Xubuntu 12.10 beta 2 64 bit on a VM about how can I make my tablet work. So here are the steps I did:
I have installed synaptic and in the repositories I have enabled the source repositories.
I have given everyone read/write access to the /opt directory.
I opened the terminal I have executed the following commands:
```

sudo apt-get build-dep gimp

```(to get the dependencies for building gimp)
```

mkdir sources
cd sources

```(this directory will contain the source of gimp)
```

apt-get source gimp

```(getting the source for gimp)
In the soruces/gimp-2.8/app/widgets directory there is a gimpdevicemanager.c file and in that file in line 312 starts the gimp_device_manager_device_added function. I have modified it in gedit to look like this:
```

static void
gimp_device_manager_device_added (GdkDisplay        *gdk_display,
                                  GdkDevice         *device,
                                  GimpDeviceManager *manager)
{
  GimpDeviceManagerPrivate *private = GET_PRIVATE (manager);
  GimpDeviceInfo           *device_info;

  device_info =
    GIMP_DEVICE_INFO (gimp_container_get_child_by_name (GIMP_CONTAINER (manager),
                                                        device->name));

  /*if (device_info)
    {
      gimp_device_info_set_device (device_info, device, gdk_display);
    }
  else
    {*/
      device_info = gimp_device_info_new (private->gimp, device, gdk_display);

      gimp_container_add (GIMP_CONTAINER (manager), GIMP_OBJECT (device_info));
      g_object_unref (device_info);
    //}
}

```(This hack is needed to make sure the configure input device dialog displays all of the devices. Without this you get those Gimp-Widgets-CRITICAL **: gimp_device_info_set_device: assertion... errors.)
```

export PATH=/opt/gimp-2.8/bin:$PATH
export PKG_CONFIG_PATH=/opt/gimp-2.8/lib/pkgconfig
export LD_LIBRARY_PATH=/opt/gimp-2.8/lib
./configure --prefix=/opt/gimp-2.8

```(for configuring gimp for to be installed into the /opt directory. I guess it is better not to overwrite the shipped version.)
```

make
make install

```(compile then install)
```

/opt/gimp-2.8/bin/gimp

```(run gimp)

In this way I was able to configure my tablet because the configure input device dialog displayed all of my devices.
One important thing to note: on that dialog I never click on the save button. This can confuse gimp next time I start. I just click the close button, and each time I start gimp I start with configuring my device.

If you want to use gimp 2.8 in Ubuntu 12.04 there is a great article how to build it here: [http://www.gimpusers.com/tutorials/compiling-gimp-for-ubuntu](http://www.gimpusers.com/tutorials/compiling-gimp-for-ubuntu). But you have to modify the gimpdevicemanager.c otherwise gimp will now work (at least according to my best knowledge).

I hope you have find something useful here.

---

### Post by krakonos on 2012-10-12
Thank you  and viktoria.s and Favux for your help. I've installed gimp 2.6.12-1ubuntu1and everything seems to work right.
But this has a really bitter taste that it has taken only 3 years to work as expected on my system (ok maybe longer - it could be more than five years ago when I've tried it for first time). And I still don't get it - in ubuntu 11.04 and 11.10  gimp 2.6 has that ugly lines and 2.8 cannot be installed (well it can be installed but it can damage your system and it does - personal experience) - due to the lines you have to install 2.8 so I had to install ubuntu 11.10 to install 12.04 (what was way throght hell - due to low space on disk and another thing that I don't get is why it cannot instll fully from cd when it is claimed - you HAVE TO BE CONNECTED and a lot of data is downloaded during OFFLINE installation - and after downloading hunderds of megabytes it tells you that installation cannot be finished and that happend for several times even thought that the installer claimed that I have enought space) 
Ok than I've installed gimp 2.8 in 12.04 and pressure didn't work again - I've builded gimp for few times without success and spent A LOT OF TIME searching for solution - no success again (here I have to confirm that I didn't try gimp 2.6 due to expectation of those lines) it was time I could spend working on something useful - you know I'm not teenager anymore to have a lot of time and passion to play with operating system - we live in 21st century and I expect that I can work not to tweak system everyday for a few hours. 
I don't know if anybody will read this - honestly I wouldn't - but I had to say it and I feel a little bit better because I'm so angry on ubuntu (there is MUCH LONGER list of problems I had to solve and some of those haven't solution at all) and particularly gimp  - yes its for free but it seems to be too expensive for me (so many hours if I would spend it in work instead of searching I would have adobe creative suit for sure:mad:). 
And in the end all problems merged in ubuntu 12.10 where gimp 2.8 is default and hasn't pressure support for my tablet but has the ugly lines  - GRRRRRRRRRR.
Moreover I've tried to install  another distro of linux (I think it was fedora) in to the virtual box to try if it works there - but the installation process on virtual disk mysteriously install on my physicall disk and demaged a lot of data - some of which was unique - fortunately I back up  regullary :)

It was a long and tiring journey and I need to rest now. It was my first question on forums and I promise it was the last one - I DON'T UNDERSTAND HOW THIS SYSTEM CAN BE AIMED ON BFU - I studied in IT and can say that I know a little about it (not much about unix I have to admit) and it was enervating process for me

---

