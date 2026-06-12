---
title: "boot-up: Cannot display this video mode"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by burnsmicro on 2011-11-29
I installed Ubuntu-11.10 about a week ago on a new bare-bones PC as my attempt to wean myself from Windows.

Today, after updating to get Thunderbird 8 (TB-7 was buggy with Ubuntu-11.10), I shut down my PC. On restarting, my screen turned purple to black and I got the following message on my screen as Ubuntu failed to launch:[INDENT]Cannot display this video mode
Optimum resolution 1280x1024 60 Hz
[/INDENT]The screen in question is an old Dell 1280x1024 60 Hz LCD screen which works fine until Ubuntu tries to take final control of the screen.

After pulling my hair out, I replaced the old screen with a newer LG wide screen monitor ..and it and Ubuntu-11 work fine. The problem is it is not mine to use and I have to figure out how to get Ubuntu-11 to work on my old 1280x1024 screen.

---

### Post by fantab on 2011-11-29
> **burnsmicro said:**
> I installed Ubuntu-11.10 about a week ago on a new bare-bones PC as my attempt to wean myself from Windows.

Today, after updating to get Thunderbird 8 (TB-7 was buggy with Ubuntu-11.10), I shut down my PC. On restarting, my screen turned purple to black and I got the following message on my screen as Ubuntu failed to launch:[INDENT]Cannot display this video mode
Optimum resolution 1280x1024 60 Hz
[/INDENT]The screen in question is an old Dell 1280x1024 60 Hz LCD screen which works fine until Ubuntu tries to take final control of the screen.

After pulling my hair out, I replaced the old screen with a newer LG wide screen monitor ..and it and Ubuntu-11 work fine. The problem is it is not mine to use and I have to figure out how to get Ubuntu-11 to work on my old 1280x1024 screen.

There seems to be some bug with Ubuntu recognizing 1280x1024 resolution. There have been numerous threads reporting this and not just on Ubuntu... I had this issue with Mint and PinguyOS too, they are based on Ubuntu. 

Have you tried to set the resolution to 1280x1024 from System Settings- Displays?
Are you able to pass the Grub process when using your Old Monitor?
Do you use any proprietary drivers? If you do then try reinstalling them.

If still can't get it then there is workaround we could try. Let us know.

---

### Post by burnsmicro on 2011-11-30
> **fantab said:**
> Have you tried to set the resolution to 1280x1024 from System Settings- Displays?
Are you able to pass the Grub process when using your Old Monitor?
Do you use any proprietary drivers? If you do then try reinstalling them.

If still can't get it then there is workaround we could try. Let us know.

Yes, I set the display to 1280x1024 from System Settings-> Displays, to no avail.

Not sure how to tell if the Grub process was completed. What I do see:

[LIST]
[*]motherboard screen: Press F8..
[*]Purple screen
[*]Black screen
[*]Purple screen with UBUNTU-11.10 in what appears to be 1280x1024 resolution with some while text underneath, the last of which is "Checking disk drive for errors" followed by a number of messages that flash by too quickly before the screen goes black.
[*]Black Screen "Cannot Display This Video Mode". This remains until reset
[/LIST]
I would appreciate the workaround as it is not easy for me to get my hands on the wide screen which works fine.

Thanks.

---

### Post by fantab on 2011-12-01
What is your Graphics Card? Does it have Proprietary Drivers? If yes, then have you tried installing or reinstalling those Drivers? 
Have you tried un-installing Thunderbird? (I doubt that Thunderbird could cause this) Try it first.

(I use this workaround on one of my monitor where, Ubuntu does not use the recommended optimal resolution. In your case it does not boot at all saying "cannot display this video mode"... So I really don't know how this will help you. It would be a good idea to Back up Data and be prepared to reinstall Ubuntu).

Lets try this:

We first need to find out if your system recognizes 1280x1024 resolution. If it does then perhaps we can force it.

Run the following commands in the terminal.

```
sudo apt-get install xresprobe

sudo ddcprobe
```This should reveal the supported resolutions.

Then find out the name of your interface, like VGA1 or HDMI1 or HDMI2  etc. as an example I am using HDMI2.
 Also make note of the Resolution and refresh rate. (I assume you  know these already).

```
xrandr
```Now replace the resolution and refresh rate in the command below with your own.

```
gtf 1920 1080 59.9
```From the output copy every thing after the word "Modeline"
What you copy will be something like this: [COLOR=DarkRed]"1920x1080_59.90"  172.51  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync[/COLOR]

Having done that run this one after another in Terminal using your outputs.

```
xrandr --newmode "1920x1080_59.90"  172.51  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync

xrandr --addmode HDMI2 "1920x1080_59.90"

xrandr --output HDMI2 --mode "1920x1080_59.90"
```This should give  you your desired monitor resolution. This is only temporary. 

To make this permanent you will have to write a script and save it as follows:

```
mkdir ~/Scripts
gedit ~/Scripts/fixresolution.sh
```This will open a blank document with gedit. Add following to the document and save it:

```
#! /usr/bin/env sh
xrandr --newmode "1920x1080_59.90"  172.51  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
xrandr --addmode HDMI2 "1920x1080_59.90"
xrandr --output HDMI2 --mode "1920x1080_59.90"
```Now to load this file at each start-up run following in terminal:

```
chmod +x ~/Scripts/fixresolution.sh
sudo ln -s ~/Scripts/fixresolution.sh /etc/X11/Xsession.d/45fixresolution
```Try restarting with your wide-screen and see with xrandr if it is using 1280x1024. 
If it is then use your old dell monitor and see if it works. 
If it doesn't then I am afraid you either have to wait for a solution or re-install.

Good Luck.

---

### Post by burnsmicro on 2011-12-01
Thanks for the detailed instructions. I was only able to follow them so far because I am do not know the label for my PC's VGA output.

Here is the blow-by-blow description, using the wide screen, which is the only screen that will boot:

```
~$ sudo ddcprobe
vbe: VESA 3.0 detected.
oem: ATI ATOMBIOS
vendor: (C) 1988-2005, ATI Technologies Inc.
product: RS880 01.00
memory: 16384kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x256
mode: 1024x768x256
mode: 1280x1024x256
mode: 640x480x64k
mode: 800x600x64k
mode: 1024x768x64k
mode: 1280x1024x64k
mode: 320x200x64k
mode: 1600x1200x256
mode: 1600x1200x32k
mode: 1600x1200x64k
edid: 
edid: 1 3
id: 5700
eisa: GSM5700
serial: 0007bcd5
manufacture: 8 2011
input: separate sync, sync on green, analog signal.
screensize: 51 29
gamma: 2.200000
dpms: RGB, active off, suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 640x480@60 Hz (VGA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@75 Hz (VESA)
ctiming: 1680x1680@60
ctiming: 1280x1024@60
ctiming: 1280x1024@75
ctiming: 1152x864@75
dtiming: 1920x1080@67
dtiming: 1680x1050@77
monitorrange: 30-83, 56-75
monitorname: W2343
~$
``````
~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 1920 x 1920
DFP1 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 290mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       75.0     60.0  
   1366x768       59.9  
   1360x768       60.0  
   1280x800       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       74.9     59.9  
   1280x720       60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   720x480        60.0  
   640x480        75.0     60.0  
~$
``````
~$ gtf 1280 1024 60.0

  # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync

~$
``````
~$ xrandr --newmode "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
~$
```Regrettably I ran into a wall by not knowing how to label my PC's DB15 video output:

```
~$ xrandr --addmode VGA "1280x1024_60.00"
xrandr: cannot find output "VGA"
~$ xrandr --addmode VGA1 "1280x1024_60.00"
xrandr: cannot find output "VGA1"
~$
```Would someone be able to suggest how I find the correct label for my PC's DB15 video output?

With luck, the rest of the recipe looks straightforward.

Thanks again,

RF

---

### Post by burnsmicro on 2011-12-01
Oh, yes, as to Video card and driver: 

On [mother] board video: Integrated ATI Radeon HD 4250 GPU
Supports D-Sub with maximum resolution of 2048 x 1536 @ 85Hz
Supports HDMI with maximum resolution of 1920 x 1080
Supports Dual-link DVI with maximum resolution of 2560 x1600 @ 60 Hz

I am not aware of loading any video drivers and I really do not know how to find out.

---

### Post by fantab on 2011-12-01
> **burnsmicro said:**
> Would someone be able to suggest how I find the correct label for my PC's DB15 video output?

With luck, the rest of the recipe looks straightforward.

Thanks again,
RF

Can you boot the Ubuntu LiveCD using your Dell monitor?
If yes, then use it to run **xrandr** from LiveCD and you will be able to find the video interface label as xrandr knows it.

Remember the video interface of your Dell monitor may not work with the other monitor, so just create the fixresolutioh.sh and chmod it using your borrowed monitor. Shut down the computer, plugin your old monitor and restart.

The script should start...

---

### Post by burnsmicro on 2011-12-02
Brilliant! Why didn't I think of booting up with the LiveCD to get the DB15 video output label?

```
ubuntu@ubuntu:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 8192 x 8192
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
ubuntu@ubuntu:~$
```From this I concluded the label would be VGA-0. Not so:

```
~# xrandr --addmode VGA-0 "1280x1024_60.00"
xrandr: cannot find output "VGA-0"
~#
```The unexpected good news is my UbuntuPC now boots with my old 1280 x 1024 monitor.

Was this a result of the latest "apt-get update"? Was it a spontaneous display of good will?

Despite this, I would like to carry this fix through to completion, should the "Cannot Display" issue raise its ugly head again ..for me or for others.

The issue remains: How to find the correct label for the corresponding video output?

Thanks again,

RF

---

### Post by fantab on 2011-12-02
It good news to learn that your old monitor is working again ... it could be the new updates.

Now to the above problem of detecting Video Interface:

Don't run above fix as root, otherwise you will have to login as root all the time to make it work. xrandr will tell you the video interface. just try it again.

and from the above I think your interface is VGA and not VGA - 0.

---

### Post by burnsmicro on 2011-12-05
Thanks Fantab,

Your instructions in post #4 below (post 11505651) did the job.

The label I needed for the VGA output had been staring me in the face all along:
```
~$ xrandr Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 1920 x 1920 
DFP1 disconnected (normal left inverted right x axis y axis) 
**[COLOR=Red]CRT1[/COLOR]** connected 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 290mm
   1920x1080      60.0*+
```However, when I tested the link, by executing it, I did get some bizarre errors; errors that appeared to be of little consequence.

```
~$ sudo /etc/X11/Xsession.d/45fixrandr
[sudo] password for robert: 
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  156 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  25
  Current serial number in output stream:  25
~$
```Thanks again,

RF

---

### Post by alzie on 2011-12-06
fantab thank you for some most excellent instructions!


I had about given up on the idea of running unity for the time being since I couldn't find any instructions to manually set the resolution on an old Daewoo monitor.  Oddly the ddcprobe did hit my monitor and model number :)

Cheers!

---

### Post by burnsmicro on 2012-01-03
Aaaaaaaargh!!!!

I just fired up my Ubuntu-11.10 PC after the holidays and I got the dreaded "Cannot display this video mode" instead of the sign-on screen I had expected. I thought I had licked this problem, thanks to Fantab's help (post 11505651).

On firing up the PC with the original Ubuntu-11.10 CD from Nov 26th, my screen displayed perfectly. With it, I found out that my link to my fixrandr.sh script, /media/b7.../etc/X11/Xsession.d/45fixrandr, had been wiped out, perhaps by a "smart" update.

I should mention, my original boot partition shows up as /media/b7..../, where the b7... is a mile long hex number. Similartly, my Home directory is on a different partition which shows up as /media/47.../, another mile long hex number. Entering these mile long hex numbers in a command line is not as bad as one would expect; one just enters the first 2 numbers and a tab will autocomplete.

I was able to find /media/47..../my_name/scripts/fixrandr.sh with the file/folder viewer on the UBUNTU-11.10 CD. The CD offers no terminal window, but I discovered one can open a terminal window by entering CtrlAltF1 (and CtrlAltF7 to return to the Ubuntu desktop).

So, the solution seemed simple enough: Recreate  the missing simlink in /media/b7.../etc/X11/Xsession.d/ and link to  /media/47..../my_name/scripts/fixrandr.sh.

It failed to execute on rebooting from the hard drive.

Back to booting from the CD: 

[LIST]
[*]I tried to execute the fixrand script from the link, /media/b7.../etc/X11/Xsession.d/45fixrandr
[LIST]
[*]-bash: 45fixrandr: no such file or directory
[/LIST]
 
[*]I tried to execute   /media/47..../my_name/scripts/fixrandr.sh.
[LIST]
[*]Can't open display
[/LIST]
 
[/LIST]
I then borrowed my wife's super wide-screen LCD monitor. But now my Ubuntu will not talk to it, either.

Help!!!

RF

---

### Post by burnsmicro on 2012-01-03
I just learned to open the more familiar terminal window with Ctrl-Alt-T. The beauty of this terminal is it has more capabilities than the Ctrl-Alt-F1 terminal.

With it, I was able to execute "xrandr" and find out that the fixrandr.sh script failed because the display label has been changed from "CRT1" to "VGA-0".

I ran the updated (VGA-0) version of fixranadr.sh and the display went black for a couple of seconds and then reappeared, leading me to believe I had cured the problem.

Not so. on rebooting from the hard drive, I still got "Cannot display this video mode".

Rebooting from the Ubuntu-11.10 CD and listing 45fixrandr, the link  to the fixrandr.sh, showed:

```
lrwxrwxrwx  1 root root   70 2012-01-03 22:07 45fixrandr -> /media/48e09e30-e4fd-4d10-920a-232c55527d66/robert/scripts/fixrandr.sh
```However, executing the link to the fixrandr.sh script failed:

```
ubuntu@ubuntu:/media/b7b55bff-998c-4d2c-8c0e-af22e922c099/etc/X11/Xsession.d$ sudo ./45fixrandr
sudo: ./45fixrandr: command not found
```..whereas executing the fixrandr.sh script appeared to work:

```
ubuntu@ubuntu:/media/b7b55bff-998c-4d2c-8c0e-af22e922c099/etc/X11/Xsession.d$ sudo /media/48e09e30-e4fd-4d10-920a-232c55527d66/robert/scripts/fixrandr.sh
```Help!!

Thanks,

RF

---

### Post by burnsmicro on 2012-01-04
I stand corrected. After booting from the Ubuntu-11.10 CD, I am able to execute the fix resolution script from the link in /etc/X11/Xsession.d/ in what would normally be the boot partition of my PC's hard drive.

```
sudo /media/b7b55bff-998c-4d2c-8c0e-af22e922c099/etc/X11/Xsession.d/45fixrandr 
```Moreover, on examining System Settings --> Display, it appears only 2 resolutions are supported by  the Ubuntu-11.10 CD: 1024x768 and 800x600.

As a consequence, I changed  the fix resolution script, fixrandr.sh, to support 1024x768_60.0 resolution/Hz. The script works as intended and so does the link to the script. But I still get "Cannot display this video mode" when I attempt to boot from the hard drive.

The evidence seems to be pointing at me barking up the wrong tree. I am really at a loss.

RF

---

### Post by Chrysopras on 2012-10-20
fantab's  instruction worked well to get 1280 x1024 for Intel D945GCL onbord graphics using Ubuntu 12.04
Thank you.

---

### Post by Gelevera on 2013-05-08
> **fantab said:**
> What is your Graphics Card? Does it have Proprietary Drivers? If yes, then have you tried installing or reinstalling those Drivers? 
Have you tried un-installing Thunderbird? (I doubt that Thunderbird could cause this) Try it first.

(I use this workaround on one of my monitor where, Ubuntu does not use the recommended optimal resolution. In your case it does not boot at all saying "cannot display this video mode"... So I really don't know how this will help you. It would be a good idea to Back up Data and be prepared to reinstall Ubuntu).

Lets try this:

We first need to find out if your system recognizes 1280x1024 resolution. If it does then perhaps we can force it.

Run the following commands in the terminal.

```
sudo apt-get install xresprobe

sudo ddcprobe
```This should reveal the supported resolutions.

Then find out the name of your interface, like VGA1 or HDMI1 or HDMI2  etc. as an example I am using HDMI2.
 Also make note of the Resolution and refresh rate. (I assume you  know these already).

```
xrandr
```Now replace the resolution and refresh rate in the command below with your own.

```
gtf 1920 1080 59.9
```From the output copy every thing after the word "Modeline"
What you copy will be something like this: [COLOR=DarkRed]"1920x1080_59.90"  172.51  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync[/COLOR]

Having done that run this one after another in Terminal using your outputs.

```
xrandr --newmode "1920x1080_59.90"  172.51  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync

xrandr --addmode HDMI2 "1920x1080_59.90"

xrandr --output HDMI2 --mode "1920x1080_59.90"
```This should give  you your desired monitor resolution. This is only temporary. 

To make this permanent you will have to write a script and save it as follows:

```
mkdir ~/Scripts
gedit ~/Scripts/fixresolution.sh
```This will open a blank document with gedit. Add following to the document and save it:

```
#! /usr/bin/env sh
xrandr --newmode "1920x1080_59.90"  172.51  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
xrandr --addmode HDMI2 "1920x1080_59.90"
xrandr --output HDMI2 --mode "1920x1080_59.90"
```Now to load this file at each start-up run following in terminal:

```
chmod +x ~/Scripts/fixresolution.sh
sudo ln -s ~/Scripts/fixresolution.sh /etc/X11/Xsession.d/45fixresolution
```Try restarting with your wide-screen and see with xrandr if it is using 1280x1024. 
If it is then use your old dell monitor and see if it works. 
If it doesn't then I am afraid you either have to wait for a solution or re-install.

Good Luck.

Woooooww
its alive!  hehe

thanks fantab.  i try it and work like a charm!
i wanted a higer resolution and ubuntu only permit 1024x768

for the record i have :

Notebook Lenovo ThinkPad R61i  with Ubuntu 12.04 64bit
Graphic card : Intel 965GM
and HP L1706 Monitor  in extended desktop mode.

this is the config i  used  (sorry, my english is..)
--------------------------------------
```

ThinkPad-R61:~$   sudo ddcprobe
vbe: VESA 3.0 detected.
oem: Intel(r)Crestline Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)Crestline Graphics Controller Hardware Version 0.0
memory: 7616kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edidfail
```

```
ThinkPad-R61:/usr/bin$ xrandr
Screen 0: minimum 320 x 200, current 2304 x 800, maximum 8192 x 8192
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 304mm x 190mm
   1280x800       60.0*+   50.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1024x768+1280+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DVI1 disconnected (normal left inverted right x axis y axis)

```

```

ThinkPad-R61:~$ gtf 1280 1024 59.9


  # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
```


```

xrandr --newmode "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
xrandr --addmode VGA1 "1280x1024_60.00"
xrandr --output VGA1 --mode "1280x1024_60.00"

```

after your sug..

```
ThinkPad-R61:~$ xrandr
Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 8192 x 8192
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 304mm x 190mm
   1280x800       60.0*+   50.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
  ** 1280x1024_60.00   60.0* **
DVI1 disconnected (normal left inverted right x axis y axis)


```

---

### Post by carib909 on 2014-03-27
> **fantab said:**
> Can you boot the Ubuntu LiveCD using your Dell monitor?
If yes, then use it to run **xrandr** from LiveCD and you will be able to find the video interface label as xrandr knows it.

Remember the video interface of your Dell monitor may not work with the other monitor, so just create the fixresolutioh.sh and chmod it using your borrowed monitor. Shut down the computer, plugin your old monitor and restart.

The script should start...

How do you do that?

---

### Post by fantab on 2014-03-27
*carib909* this is an old thread. Please start your own new thread and describe the problem you are facing as clearly as possible. 
Back in the day, some Intel Graphics had issues running on Linux, like GMA500. However this has been fixed some time back....

---

