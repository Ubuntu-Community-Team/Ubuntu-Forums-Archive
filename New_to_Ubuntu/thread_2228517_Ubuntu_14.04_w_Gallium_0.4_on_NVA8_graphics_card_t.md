---
title: "Ubuntu 14.04 w/ Gallium 0.4 on NVA8 graphics card thinks my 47&quot; tv is a 50&quot;"
date: 2014-06-07
forum: New to Ubuntu
---

### Post by Paper Pusher on 2014-06-07
I have plugged in my TV to use as another monitor for playing movies, but when I go to display settings it says it is a 50" TV when in reality it is only a 47" Vizio TV. Because of this I cannot see the menu bar on the side and the screen doesn't fit properly. The Ubuntu settings doesn't allow me to personalize the screen enough to make it fit. I have installed NVIDIA X Server settings and it only gives me two choices: Application Profiles and nvidia-setting Configuration. I know there are more options but it just doesn't diplay them. This used to work great in 12.04 but doesn't seem to like 14.04. Is there another program I can run in order to make the TV screen fit? or am I just out of luck with Ubuntu 14.04?

---

### Post by papibe on 2014-06-07
Hi Paper Pusher.

It looks like your are suffering from [overscan]("http://en.wikipedia.org/wiki/Overscan").

Usually it is the TV's fault, and you solve it using your remote.  For example, in the case of my Sony Bravia you can fix it by setting 'Full Pixel' to Screen -> Display Area. In my brother's Samsung you would set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).

Nevertheless, if you can't adjust the resolution using your TV remote, then you can compensate the resolution using the 'nvidia-settings' command on the terminal

Hope it helps. Let us know how it goes, and if you need more help with 'nvidia-settings'
Regards.

---

### Post by Paper Pusher on 2014-06-08
HI papibe,

         I appreciate your advice, but I did some research and found that the way to fix overscan on a Vizio TV was to set it to "wide" but after doing this it still did not fix my issue. Is there some way of setting screen size on the Nvidia utility? Can you give me some more info the 'nvidia-settings' command on the terminal? I would greatly appreciate it!

---

### Post by papibe on 2014-06-08
Sure.

I imagine it is a full HDTV so the resolution is 1920x1080. If that is not the native resolution change accordingly.

We need to start querying the current settings:
```
nvidia-settings -q CurrentMetaMode
```
From this you will get the current metamode, and the name the nvidia driver uses for the display. It would be DFP-0, DPY-1, or similar. Let's say it is DFP-0 for the next examples.

Then let's assume that the overscan is 'eating' 16 pixels from every side, and 20 from top and bottom. Then, the useful area to display the desktop should be:
```
(1920-16-16)x(1080-20-20) =  1888x1040
```
Finally this would create an 1888x1040 area inside the 1920x1080 resolution but shifted 16 pixel on the horizontal and 20 on the vertical side.
```
nvidia-settings --assign CurrentMetaMode="DFP-0: 1920x1080 { ViewPortOut=1888x1040+16+20 }"
```
It may be possible that 16x20 won't do it, so try 20x20, or other values to get the both perfect viewing area, and the shift position.

Hope it helps. Let us know how it goes.
Regards.

P.S.: This should revert you back to the default you are right now:
```
nvidia-settings --assign CurrentMetaMode="DFP-0: 1920x1080 { ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0 }"

```

---

### Post by Paper Pusher on 2014-06-08
Hi papibe,

         I appreciate your help a ton! I started with typing in "nvidia-setting -q CurrentMetaMode" but recieved: 

                         ERROR: Error resolving target specification '' (No targets match target
                           specification), specified in query 'CurrentMetaMode'.

       Thanks again! and I look forword to hearing your input on this.

---

### Post by papibe on 2014-06-08
Do you have multiple monitors?

Could you run these commands and post backs the results?
```
nvidia-settings -q screens

nvidia-settings -q gpus
```
Regards.

---

### Post by Paper Pusher on 2014-06-09
Hi papibe,

       I tried those commands in the terminal and this is what I got axel@axel-NC890AA-ABA-a6803w:~$ nvidia-settings -q screens

1 X Screen on axel-NC890AA-ABA-a6803w:0

    [0] Not NVIDIA (Unknown)

axel@axel-NC890AA-ABA-a6803w:~$ nvidia-settings -q gpus

axel@axel-NC890AA-ABA-a6803w:~$ 


Thanks!

---

### Post by papibe on 2014-06-09
It looks like the nvidia driver is either not recognizing the monitor, or not running properly.

Could you open a terminal, run this, and paste back the results?
```
lspci -nnk | grep -iA2 vga

xrandr -q

xrandr -q --q1
```
Regards.

---

### Post by Paper Pusher on 2014-06-10
Hi papibe, I put in the code that you gave me and this is what I got:

axel@axel-NC890AA-ABA-a6803w:~$ lspci -nnk | grep -iA2 vga
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218 [GeForce 210] [10de:0a65] (rev a2)
	Subsystem: eVga.com. Corp. Device [3842:1213]
	Kernel driver in use: nouveau
02:00.1 Audio device [0403]: NVIDIA Corporation High Definition Audio Controller [10de:0be3] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:1213]
	Kernel driver in use: snd_hda_intel
04:00.0 USB controller [0c03]: VIA Technologies, Inc. VL80x xHCI USB 3.0 Controller [1106:3432] (rev 03)
axel@axel-NC890AA-ABA-a6803w:~$ 
axel@axel-NC890AA-ABA-a6803w:~$ xrandr -q
Screen 0: minimum 320 x 200, current 3840 x 1105, maximum 8192 x 8192
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 920mm x 520mm
   1280x720       60.0 +   59.9  
   1920x1080      60.0*    59.9     59.9  
   1920x1080i     60.1     50.0     60.0  
   1440x576i      50.1  
   720x576        50.0  
   720x480        60.0     59.9  
   640x480        60.0     59.9  
VGA-1 connected 1920x1080+1920+25 (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080      60.0*+
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
axel@axel-NC890AA-ABA-a6803w:~$ 
axel@axel-NC890AA-ABA-a6803w:~$ xrandr -q --q1
 SZ:    Pixels          Physical       Refresh
 0   1280 x 720    ( 920mm x 520mm )   60  
*1   1920 x 1080   ( 920mm x 520mm )  *60   30   25  
 2   1440 x 576    ( 920mm x 520mm )   25  
 3    720 x 576    ( 920mm x 520mm )   50  
 4    720 x 480    ( 920mm x 520mm )   60  
 5    640 x 480    ( 920mm x 520mm )   60  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - X Axis Y Axis
axel@axel-NC890AA-ABA-a6803w:~$ 


-Thanks again!

---

### Post by papibe on 2014-06-11
Thanks.

You are not running the proprietary Nvidia driver, but the open source driver:
```
Kernel driver in use: **[COLOR="#FF0000"]nouveau[/COLOR]**
```
I imagine you installed it since nvidia-settings is available. However it did not loaded.

Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste it here: [pastebin.ubuntu.com]("http://pastebin.ubuntu.com/"), and then post back the link.

Regards.

---

### Post by Paper Pusher on 2014-06-13
Hi papibe, here is the link: 
           
                           [http://pastebin.ubuntu.com/7641835/](http://pastebin.ubuntu.com/7641835/)

I also didn't know that we were not using the proprietary driver and we would like to know how to use it.

---

### Post by papibe on 2014-06-14
Thanks. Try this:

Save your current X config file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
If that gives you an error, it means you don't have one so it doesn't matter.

Then create a custom one that explicitly uses the Nvidia driver:
```
sudo nvidia-xconfig
```
Then reboot. 

Now test if the Nvidia driver is running:
```
lspci -nnk | grep -iA2 vga
```
check if now it says the driver in use is nvidia.

If that is the case, try again the direction on post #4 to see if you can get rid of the overscan.

Let us know how that works.
Regards.

P.S.: If you still see the nouveau driver in use please paste again the file /var/log/Xorg.0.log

---

### Post by Paper Pusher on 2014-06-14
Hi pipabe,

         I put in the command: 'sudo nvidia-xconfig' and it told me that the command wasn't found. I am unsure on where to go from here.

---

### Post by papibe on 2014-06-15
Let remove any Nvidia package that was installed, and make a clean install:

[LIST]
[*]Get the list of Nvidia packages currently installed:```
dpkg -l  | grep nvidia
```
[*]Star purging the nvidia-* packages using commands like this:```
sudo apt-get purge nvidia-something
```
(replace 'something' with the actual packages names obtain in the command before).

[*]Remove all packages separately except for this one:```
nvidia-common
```
[*]Then reconfigure nvidia common:```
sudo dpkg-reconfigure nvidia-common
```
[*]At this point you can reboot, and you'll be using by default the Open Source driver (nouveau).
[*]Make sure you have your headers installed:```
sudo apt-get install linux-headers-generic
```
[*]Install the nvidia driver:```
sudo apt-get install nvidia-current
```
[*]Create a new X conf file:```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo nvidia-xconfig
```
[/LIST]
Now restart so that the Nvidia driver can take effect.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Paper Pusher on 2014-06-16
What you told me to do worked great! Now I have all the available options on the Nvidia X Server Settings, Thank you! 


But now when I go to the Nvidia X server settings and adjust the screens, when I click apply after setting my desired specs the screens do nothing and when I open Nvidia again, all of the settings are back to the default. For example I set both screens to 1920x1080 and click apply, nothing happens and when I open to project back up the TV resolution is back to 1280x720. Do you know why it would be doing this?

---

### Post by papibe on 2014-06-17
'Nvidia X Server Settings' (or nvidia-settings) saves its setting on the file
```
~/.nvidia-settings-rc
```
make sure you can rewrite that file. Sometimes if you have run nvidia-settings as root the file may have change owners. If so, run this:
```
sudo chown youruser:youruser ~/.nvidia-settings-rc
```
(replace youruser for your actual username).

Another approach is to save the current settings directly to the X config file:

Open nvidia settings as root:
```
gksudo nvidia-settings
```
Then, adjust all settings as you need, and then select 'X Server Display Configuration' from the left, and press 'Save to X Configuration File' from the right.

That should save the current settings on /etc/X11/xorg.conf, thus re enable them every time you boot.

Hope it helps. Let us know how it goes.
Regards.

P.S.: if gksudo is not installed, install it like this:
```
sudo apt-get install gksu 
```
Remember to not run GUI apps with sudo, use gksudo instead.

---

### Post by Paper Pusher on 2014-06-17
Hi papibe,

         I installed gksudo and rewrote the file in my name but I am still having no luck with the settings being changed. I listed the file name in the Terminal and this is what I got:

 axel@axel-NC890AA-ABA-a6803w:~$ ls -l ~/.nvidia-settings-rc
-rw-rw-r-- 1 axel axel 2678 Jun 17 18:25 /home/axel/.nvidia-settings-rc

Does this look right to you? Or did rewriting the filename not work correctly. My username is "axel" by the way.

---

### Post by papibe on 2014-06-17
Open 'Startup Applications' and make sure there's a script that reloads the nvidia settings every time you log in.

The script should have this as a command:
```
sh -c '/usr/bin/nvidia-settings --load-config-only'
```
Let us know if that makes a difference.

Regards.

---

### Post by Paper Pusher on 2014-06-17
Hi papibe, 

         I opened up 'Startup Application and made a script with the command you gave me and I still have no luck.

---

### Post by Paper Pusher on 2014-07-12
Hey everyone! I just changed the monitor that I was using for this issue to a bigger Samsung monitor and after plugging in the different monitor the desktop now fits great on the TV screen. I am not exactly sure if this fixed the issue, or if just over time it fixed itself, but I appreciate everyone and their help!

---

