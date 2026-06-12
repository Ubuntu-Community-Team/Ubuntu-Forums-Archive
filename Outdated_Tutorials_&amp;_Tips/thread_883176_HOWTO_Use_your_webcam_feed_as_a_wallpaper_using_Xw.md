---
title: "HOWTO: Use your webcam feed as a wallpaper using Xwinwrap."
date: 2008-08-07
forum: Outdated Tutorials &amp; Tips
---

### Post by easybake on 2008-08-07
This tutorial will show you how you can use your webcam feed as your wallpaper (For people who constantly need to look at themselves). 
*This will NOT make you lose the functionality of icons, conkys, screenlets, or docks. *

**From this**[[IMG]http://img359.imageshack.us/img359/7707/screenshotia1.th.png[/IMG]](http://img359.imageshack.us/img359/7707/screenshotia1.png)_[[IMG]http://img210.imageshack.us/img210/5060/screenshotir7.th.png[/IMG]](http://img210.imageshack.us/img210/5060/screenshotir7.png)**To This!**
**If you are clever enough and have time to do some tinkering, [jdong]("http://ubuntuforums.org/member.php?u=780") pointed out that you could use this same idea to create a transparent display effect**

[COLOR="Red"]**[SIZE="3"]1. Check Requirements:[/SIZE]**[/COLOR]
> 
[SIZE="2"][COLOR="Red"]**This will only work with Compiz-Fusion enabled as your Window Manager.**[/COLOR][/SIZE] [_Click Here_]("http://ubuntuforums.org/showpost.php?p=5056867&postcount=1") for installation instructions.
*NOTE: This won't require any special settings in CompizConfig Settings Manager.*

[COLOR="Red"][SIZE="2"]**This will also require Mplayer being installed.** [/SIZE][/COLOR][_Click Here_]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html") for installation instructions.


[SIZE="2"]**[COLOR="Red"]This also requires an already working webcam.[/COLOR]**[/SIZE]


[SIZE="3"]**2. Download Xwinwrap**[/SIZE].

**[SIZE="3"]_Installation Option 1[/SIZE]_** 
> **Open Accessories>Terminal**
*Enter the following codes*:```
sudo apt-get install build-essential libx11-dev x11proto-xext-dev libxrender-dev libxext-dev cvs
```
```
cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xapps co xwinwrap
```
```
cd xwinwrap
```
```
make
```
```
sudo cp xwinwrap /usr/bin
```


**[SIZE="3"]_Installation Option 2[/SIZE]_**
> Go to this URL. _[http://www.getdeb.net/app/xwinwrap]("http://www.getdeb.net/app/xwinwrap")_

Select the option that fits your system.

Click Download Xwinwrap

A download popup should appear.

Select the option **Open with GDebi Package Installer (default)**

**Click OK**

The rest of the installation is automated.[/quote]

*You have now successfully installed Xwinwrap*.

[SIZE="3"]**3. Test it out.**
[/SIZE]
**In Terminal** 
```
cd
```
```
xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- mplayer -wid  WID -quiet -fps 15 tv://
```
*If you want a Mirror effect add this to the end of the line above*```
 -vf mirror
```
*NOTICE: When you close the terminal window it will stop Xwinwrap.*
[SIZE="3"]


**4. Create an easy way to start/stop this effect**[/SIZE].

**[SIZE="2"]In Teminal[/SIZE]** ```
gedit toggle
```
**Paste this in your text editor**```
#!/bin/sh

# click to start, click to stop
if pidof xwinwrap ; then
 killall xwinwrap
 else
 exec xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- mplayer -wid  WID -quiet -fps 15 tv:// 
fi
```
*NOTE: If you want the Mirror effect, after "tv://" , _on the same line_ add:*```
 -vf mirror
```

**Save and close.**

You now need to make the script executable.

**In Terminal**
```
sudo chmod a+x toggle
```

**[SIZE="3"]5. Create A Launcher[/SIZE]**:

Right Click on either the desktop or on your panel.  
***For Desktop*** select (create Launcher)
***For Panel*** select (click Add To Panel)+(Custom Application Launcher)

For _Name_ input anything.
For _Command_ input ```
./toggle
```
You can leave the comment section blank.
**Click Ok**. 

**[SIZE="3"]You're done![/SIZE]**
-----------------------------------------------------

[COLOR="Navy"]_**Dissecting the Xwinwrap code.**_
```
xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- mplayer -wid  WID -quiet -fps 15 tv://
```
**-ni** means No Input
**-o 0.20** is the Opacity setting from 0 to 1
**-fs** means FullScreen
**-s** means Sticky(its on all workspaces)
**-sp** means Skip Pager (window won't appear in pager)
**-st** means Skip Taskbar (window won't appear in taskbar)
**-b** means Below
**-nf** means No Focus
**-wid** creates a window id
**--mplayer** means mplayer 
**-fps 15** means 15 Frames Per Second
**tv://** tells mplayer to use the default video input device.
**-vf mirror** means video filter Mirror.

Feel free to change any of these if you want it to act differently.
More filters and effects can be found by opening Terminal and typing ```
man mplayer
```[/COLOR]
-----------------------------------------------------

[COLOR="DarkRed"]**_[SIZE="2"]Problems you may run into.[/SIZE]_ **

_If you have another video input device hooked up to your computer you have to tell mplayer which one to use._ The tv:// command alone selects the default device. [Ace214]("http://ubuntuforums.org/member.php?u=347356") pointed out that you would have to use ```
-tv device=/dev/video1
```**change the path to where the webcam device is located if not /dev/video1**

_Other programs can't use the webcam simultaneously._ I suggest turning Off the program before you use other programs.

_Suspend-To-Ram won't work while your webcam is on._ I suggest turning Off the program when you don't want it in use. You could also add the line **killall xwinwrap** to **/etc/acpi/sleep.sh** Which would kill the process before suspending to ram. You can also add the line **killall xwinwrap** to **/etc/acip/hibernate.sh** if you have problems suspending to the hard drive.

_This apparently only works using the X11 driver in Mplayer._ Other drivers tend to not be capable for handling due to the lack of indirect rendering on some Intel cards.

*Got to give credit to* [***The Warlock***]("http://ubuntuforums.org/member.php?u=18829"), [***gaminggeek***]("http://ubuntuforums.org/member.php?u=105709"), ***[Valdi]("http://ubuntuforums.org/member.php?u=311216")***, and ***[cammin]("http://ubuntuforums.org/member.php?u=384472")*** for pointing out problems [/COLOR]

-----------------------------------------------------

(For more info on Xwinwrap click [_Here_]("http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/") or [_Here_]("http://swik.net/xwinwrap"))

Credit for the original idea [_Here_]("http://ubuntuforums.org/showthread.php?t=879897") and [_Here_]("http://ubuntuforums.org/showthread.php?t=846743")

---

### Post by easybake on 2008-08-13
Let me know if you have any ideas on what to add/change.

---

### Post by melchiorre on 2008-08-13
Wonderful howto, thank you

---

### Post by easybake on 2008-08-17
> **melchiorre said:**
> Wonderful howto, thank you

thanks

---

### Post by Eastisle on 2008-08-17
Great How-To, what exactly is that running on the top right of your desktop?

---

### Post by easybake on 2008-08-17
> **Eastisle said:**
> Great How-To, what exactly is that running on the top right of your desktop?

Thanks. Thats just Pidgin with a [Screenlet]("http://www.gnome-look.org/content/show.php/PidginScreenlet?content=72611") with a [Transparent Theme]("http://www.gnome-look.org/content/show.php/Pidgin+Screenlet+Transparent+Theme?content=82352").

---

### Post by Prometheum on 2008-08-18
First off, thanks for the awesome howto! 

However, I've found a slight problem: When the song changes in Rhythmbox, the popup that comes up is invisible under the webcam feed. It'll be visible if I use gnome-do to show the notification before I start the feed (using the toggle script), but if I start it afterwards, it doesn't show anything.

Any ideas as to what this might be, fixes, etc.?

---

### Post by easybake on 2008-08-19
> **Prometheum said:**
> First off, thanks for the awesome howto! 

However, I've found a slight problem: When the song changes in Rhythmbox, the popup that comes up is invisible under the webcam feed. It'll be visible if I use gnome-do to show the notification before I start the feed (using the toggle script), but if I start it afterwards, it doesn't show anything.

Any ideas as to what this might be, fixes, etc.?

Thanks. I believe that problem is because Rhythmbox won't show that little popup window if you have any window set to fullscreen. 

(It's actually a good feature because it would be kind of annoying if that popup showed up while watching a full screen video or playing a game)


Here's a fix for it. You have to edit the line in the Toggle Script.

In Terminal ```
gedit toggle
```
remove the entry ```
 -fs
```
and replace it with ```
-g 1280x1024
```
(edit that line to fit your screen resolution)

*You end up having a title bar to deal with.*

Save and Close.

**If you close Xwinwrap with the title bar you have to click the toggle button again to retain use of your webcam.**

---

### Post by ace214 on 2008-09-05
I can't get this to work correctly. I can only get it to work when the opacity is set to 1. Otherwise, it just darkens my background picture. I haven't tested it with a webcam- I've been using movie files in mplayer with the same settings, but it should still work...

Any ideas?

UPDATE: If I install xserver-xgl, it works but it completely takes over my CPU. I was using the mesa driver before... I tried using the X11 driver in mplayer, but there are multiple ones, and some freeze my session.
Also some screensavers, like glmatrix, only work properly with xgl installed on my box. So perhaps this is a bug of the mesa driver or xwinwrap not working properly with each other??

---

### Post by easybake on 2008-09-06
> **ace214 said:**
> I can't get this to work correctly. I can only get it to work when the opacity is set to 1. Otherwise, it just darkens my background picture. I haven't tested it with a webcam- I've been using movie files in mplayer with the same settings, but it should still work...

Any ideas?

UPDATE: If I install xserver-xgl, it works but it completely takes over my CPU. I was using the mesa driver before... I tried using the X11 driver in mplayer, but there are multiple ones, and some freeze my session.
Also some screensavers, like glmatrix, only work properly with xgl installed on my box. So perhaps this is a bug of the mesa driver or xwinwrap not working properly with each other??

Definitely sounds like a driver problem. I've heard of people having problems on some intel based cards where indirect rendering isn't supported. So you might be out of luck. [gaminggeek]("http://ubuntuforums.org/member.php?u=105709") pointed out that you still might be able to use the opengl mplayer plugin. But I'm not sure if that will help your situation.

SideNote: if you wanted to test out your webcam just with mplayer you can use this in terminal```
mplayer -fps 15 tv://
```

---

### Post by jdong on 2008-09-06
BONUS: If your webcam can be oriented the opposite way (facing away from you), and you have enough boredom to do the scaling right, you can create a pretty startling "transparent display" effect by making it seem like you can look through your laptop display.


(*cough* I got really bored in Calculus lecture one day...)

---

### Post by easybake on 2008-09-06
> **jdong said:**
> BONUS: If your webcam can be oriented the opposite way (facing away from you), and you have enough boredom to do the scaling right, you can create a pretty startling "transparent display" effect by making it seem like you can look through your laptop display.


(*cough* I got really bored in Calculus lecture one day...)

Nicely done. I actually thought about that but never followed through. If you have any pics of it or the details on what you used I would be glad to add it to the instructions.

---

### Post by Rian46 on 2008-09-06
> **ace214 said:**
> I can't get this to work correctly. I can only get it to work when the opacity is set to 1. Otherwise, it just darkens my background picture. I haven't tested it with a webcam- I've been using movie files in mplayer with the same settings, but it should still work...

Any ideas?

UPDATE: If I install xserver-xgl, it works but it completely takes over my CPU. I was using the mesa driver before... I tried using the X11 driver in mplayer, but there are multiple ones, and some freeze my session.
Also some screensavers, like glmatrix, only work properly with xgl installed on my box. So perhaps this is a bug of the mesa driver or xwinwrap not working properly with each other??

I'm the same, works only with xserver-xgl with cpu issues :(

Really really cool find though! Any updates or further help would be appreciated with regards to the problems some of us are having too if you find anything out!

---

### Post by Rian46 on 2008-09-06
actually, i've just found a mild fix when using xgl myself from here:

[http://chromakode.blogsome.com/2006/02/16/howto-compiz-xgl-on-ubuntu-for-the-morbidly-lazy-2](http://chromakode.blogsome.com/2006/02/16/howto-compiz-xgl-on-ubuntu-for-the-morbidly-lazy-2)

it mentions adding "-zoom -vo x11" to the command like so:

```
xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- mplayer -wid  WID -quiet -zoom -vo x11 -fps 15 tv://
```

and whilst i'm not sure exactly what that does, being a n00blet, it sure did help!

---

### Post by easybake on 2008-09-07
> **Rian46 said:**
> actually, i've just found a mild fix when using xgl myself from here:

[http://chromakode.blogsome.com/2006/02/16/howto-compiz-xgl-on-ubuntu-for-the-morbidly-lazy-2](http://chromakode.blogsome.com/2006/02/16/howto-compiz-xgl-on-ubuntu-for-the-morbidly-lazy-2)

it mentions adding "-zoom -vo x11" to the command like so:

```
xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- mplayer -wid  WID -quiet -zoom -vo x11 -fps 15 tv://
```

and whilst i'm not sure exactly what that does, being a n00blet, it sure did help!
What you're doing by adding -zoom is just changing the aspect ratio.

The -vo x11 is just telling mplayer to use the x11 video output driver.

x11 is definitely the best to use with this effect.

---

### Post by Rian46 on 2008-09-07
> **easybake said:**
> What you're doing by adding -zoom is just changing the aspect ratio.

The -vo x11 is just telling mplayer to use the x11 video output driver.

x11 is definitely the best to use with this effect.

oh right! was thinking along those lines anyway!
but is x11 not what is used as defualt unless you install xgl? before i installed xgl i had the problems ace and i mentioned earlier, but now it works with xgl installed but x11 specified as the video output driver... clearly i am wrong here and x11 is not default :(
once again, this is a really cool (if only for the sake of cool) HOWTO, thanks!

---

### Post by ace214 on 2008-09-07
Thanks a lot! That works for me! 
Now if only xwinwrap could draw under the icons so they didn't darken...

I thought the same thing about the X11 driver. Couldn't figure it out (although, I admit I didn't do enough tinkering).

Apparently it uses the xv driver by default. This shows up in the terminal output:
> VO: [xv]

I was trying to set it to the Ximage driver in the gui and apparently that didn't carry over into the CLI...

---

### Post by ace214 on 2008-09-07
By the way, just figured out that mplayer has a setting to specify the TV device if there's more than one.

Add -tv device=/dev/video1 or wherever the device is and it will work. You can also set this up automatically in the mplayer.conf file. Found this on the mplayer man page.

Unfortunately, mplayer doesn't seem to like *my* webcam...

> ~$ mplayer -tv device=/dev/video1:input=0 tv:///
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3500+ (Family: 15, Model: 7, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv:///.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Microdia USB Video Camera
 Capabilites:  video capture  read/write  streaming
 supported norms:
 inputs: 0 = Webcam;v4l2: ioctl get input failed: Invalid argument

 Current input: 1
 Current format: YUV420
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
FPS not specified in the header or invalid, use the -fps option.
No stream found.

v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.

Exiting... (End of file)

---

### Post by easybake on 2008-09-08
> **Rian46 said:**
> oh right! was thinking along those lines anyway!
but is x11 not what is used as defualt unless you install xgl? before i installed xgl i had the problems ace and i mentioned earlier, but now it works with xgl installed but x11 specified as the video output driver... clearly i am wrong here and x11 is not default :(
once again, this is a really cool (if only for the sake of cool) HOWTO, thanks!

I want to say that x11/xv was the default, or at least on my system, but I'm not 100% sure. Glad you liked it though.

> **ace214 said:**
> Thanks a lot! That works for me! 
Now if only xwinwrap could draw under the icons so they didn't darken...

It does place the root window in a weird place. You have to trade off between a dark effect with bright icons, or a bright effect with dark icons. You can change the opacity value ```
-o 0.20
``` to anything between 0 and 1 to fit your needs.

> Add -tv device=/dev/video1 or wherever the device is and it will work. You can also set this up automatically in the mplayer.conf file. Found this on the mplayer man page. Thanks I'll add this to the problems section.

---

### Post by Prometheum on 2008-09-13
> **easybake said:**
> Thanks. I believe that problem is because Rhythmbox won't show that little popup window if you have any window set to fullscreen. 

(It's actually a good feature because it would be kind of annoying if that popup showed up while watching a full screen video or playing a game)


Here's a fix for it. You have to edit the line in the Toggle Script.

In Terminal ```
gedit toggle
```
remove the entry ```
 -fs
```
and replace it with ```
-g 1280x1024
```
(edit that line to fit your screen resolution)

*You end up having a title bar to deal with.*

Save and Close.

**If you close Xwinwrap with the title bar you have to click the toggle button again to retain use of your webcam.**

Thank you so much! Everything works perfectly now.

The title bar is somewhat annoying, but totally invisible unless you're looking for it, so no problems there (I didn't notice it until I read your post again).

Thanks again! Happy hacking!

---

### Post by earthpigg on 2008-09-20
great how-to, i'd love it if it worked, but...

not working for me... ubuntu 64 bit, yes i installed the 64 bit deb, im using two monitors (probably the problem).

i did the 2nd install method, from the website.

edit: tried re-installing mplayer.

edit 2: yes, my webcam works... i use it in kopete (which is not currently running)

> mason@mason-laptop:~$ xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- mplayer -wid  WID -quiet -fps 15 tv://
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl query capabilities failed: Invalid argument
v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.


Exiting... (End of file)
mplayer died, exit status 0


=)

---

### Post by easybake on 2008-09-20
> **earthpigg said:**
> great how-to, i'd love it if it worked, but...

not working for me... ubuntu 64 bit, yes i installed the 64 bit deb, im using two monitors (probably the problem).

i did the 2nd install method, from the website.

edit: tried re-installing mplayer.

edit 2: yes, my webcam works... i use it in kopete (which is not currently running)
=)

What happens when you just run ```
mplayer -quiet -vo x11 -fps 15 tv://
``` in terminal?

---

### Post by earthpigg on 2008-09-21
> **easybake said:**
> What happens when you just run ```
mplayer -quiet -vo x11 -fps 15 tv://
``` in terminal?

> mason@mason-laptop:~$ mplayer -quiet -vo x11 -fps 15 tv://
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: unable to open '/dev/video0': No such file or directory
v4l2: ioctl set mute failed: Bad file descriptor
v4l2: 0 frames successfully processed, 0 frames dropped.


Exiting... (End of file)
mason@mason-laptop:~$ 


thanks in advance for the help

---

### Post by easybake on 2008-09-22
> **earthpigg said:**
> thanks in advance for the help

It looks like your webcam probably isn't at the default video device location. 

Run this first in terminal to get some options
```
ls /dev/video*
```

You will get a list of all the video device locations in my case I only get this```
easybake@easybake-desktop:~$ ls /dev/video*
**/dev/video0**
```

Take whatever outputs you get from that and plug them into this code until you get one that works. Just change the "0" at the end.```
mplayer -fps 15 device=***/dev/video0*** tv://
```

If that worked and you figured out which device location just take that device code and plug it into the original xwinwrap command ```
xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- mplayer -wid  WID -quiet -fps 15 ***device:/dev/video0*** tv://
```.

---

### Post by earthpigg on 2008-09-22
> mason@mason-laptop:~$ ls /dev/video*
/dev/video0
mason@mason-laptop:~$ 


that's all i get, too :\

and

> mason@mason-laptop:~$ mplayer -fps 15 device=/dev/video0 tv://
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing device=/dev/video0.
File not found: 'device=/dev/video0'
Failed to open device=/dev/video0.


Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl query capabilities failed: Invalid argument
v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.


Exiting... (End of file)
mason@mason-laptop:~$ 


---

### Post by fghi899 on 2008-09-22
Good article!!!Good article!!!!!!!!!!!!Runescape news:Great! Buy cheap **[runescape GP](http://www.rs2-gold.com)** in [www.rs2-gold.com------------------------------------------](www.rs2-gold.com------------------------------------------)**[runescape money](http://www.runescape2money.com)[buy runescape GP](http://www.runescape4money.cn) | [runescape gold](http://www.rs2-gold.com) | [RS money](http://www.rs2-money.com)**

---

### Post by earthpigg on 2008-09-22
i dont get it.

how do i go from:

> mason@mason-laptop:~$ ls /dev/video*
/dev/video0
mason@mason-laptop:~$ 

and then in the VERY NEXT command get:

> Playing device=/dev/video0.
File not found: 'device=/dev/video0'

---

### Post by easybake on 2008-09-22
> **earthpigg said:**
> i dont get it.

I actually thought I messed up my set up trying to figure this out, but in the process ran into the problem that you are having right now. But I was able to fix it. It could just be a permissions problem. Try running ```
sudo chmod 777 /dev/video0
``` enter your password and then reboot just for fun.

Now try out ```
mplayer -quiet -fps 15 device:/dev/video0 tv://

```

---

### Post by earthpigg on 2008-09-22
> **easybake said:**
> I actually thought I messed up my set up trying to figure this out, but in the process ran into the problem that you are having right now. But I was able to fix it. It could just be a permissions problem. Try running ```
sudo chmod 777 /dev/video0
``` enter your password and then reboot just for fun.

Now try out ```
mplayer -quiet -fps 15 device:/dev/video0 tv://

```

k, ran 1st command, restarted the whole computer. returned...

> 
mason@mason-laptop:~$ mplayer -quiet -fps 15 device:/dev/video0 tv://
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing device:/dev/video0.
File not found: 'device:/dev/video0'
Failed to open device:/dev/video0.


Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl query capabilities failed: Invalid argument
v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.


Exiting... (End of file)
mason@mason-laptop:~$

EDIT~~ my laptop has a built in webcam that i've never even bothered with in any way whatsoever. the above "ls" command that returns everything in /dev/video* did not show it.

---

### Post by easybake on 2008-09-22
> **earthpigg said:**
> k, ran 1st command, restarted the whole computer. returned...



EDIT~~ my laptop has a built in webcam that i've never even bothered with in any way whatsoever. the above "ls" command that returns everything in /dev/video* did not show it.

You could try this instead but I'm starting to doubt it will work. ```
mplayer -fps 15 -tv device=/dev/video0:input=0 tv://
```**you could try and change the input number to 1**

What is the model of your laptop and webcam? It could be buggy.

---

### Post by earthpigg on 2008-09-23
> **easybake said:**
> What is the model of your laptop and webcam? It could be buggy.

laptop is from ibuypower.com, bout 10 months old. they change the names of their different lines of laptops like every 3 months so... at the time it was called "Battalion 101".

webcam is this - or a version from 5 years ago that looks exactly the same as the one they are selling now:
[http://www.target.com/GE-EasyCam-PC-Camera-H098063/dp/B00006HMGD](http://www.target.com/GE-EasyCam-PC-Camera-H098063/dp/B00006HMGD)

---

### Post by mindoms on 2008-09-27
Hi earthpigg.

I am no pro, but maybe i can help...
first you can try this:

```
mplayer tv:// -tv driver=v4l:device=/dev/video0
```
please post the output.

if that didn't work, we`ll try to get some info about the cam:
please run these commands and post the output

```

lsusb
ls -l /dev/video*
lsof -b | grep "/dev/video"
v4l-info
```

after unplug/plug the cam:
```
dmesg | tail
```

---

### Post by joss24 on 2008-10-15
Thats a nice howto. Thanks.
But still wondering what to use to get same result in xp?

Low quality version is maybe:
Try to stream ur cam to web and use that webpage as backgroud or get VLC to show the stream in back.

Otherwise .Net maybe but im not so pro to make it happen:
[http://www.thaiio.com/prog-cgi/vbnetwebcam.html](http://www.thaiio.com/prog-cgi/vbnetwebcam.html)
[http://www.codeproject.com/KB/audio-video/WebcamUsingDirectShowNET.aspx](http://www.codeproject.com/KB/audio-video/WebcamUsingDirectShowNET.aspx)

---

### Post by ace214 on 2008-10-15
> **joss24 said:**
> But still wondering what to use to get same result in xp?
must..... resist.......... :x

ADD: Actually, I think VLC can paint to the wallpaper in Windows. So if you have it running capturing your webcam, you could do it.
ADD2: Oh, you said that already... That seems to be the easiest option to me.

---

### Post by easybake on 2008-10-15
> **joss24 said:**
> Thats a nice howto. Thanks.
But still wondering what to use to get same result in xp?

Glad you liked it.

For your question, I have no idea. I dropped XP at the launch of Hardy and haven't looked back.

---

### Post by easybake on 2008-12-06
Sidenote: If anyone was wondering this should work perfectly fine under Intrepid.

---

### Post by Shasmo on 2008-12-08
Thanks heaps!
I'm so going to give this a try when I get home. I took ages to get a picture of the walls behind my monitor so I could have a 'transparent' background, but to have a 'live' one ...

What's the name of the calendar at the bottom of your screen in your screenshots?

---

### Post by easybake on 2008-12-08
> **Shasmo said:**
> Thanks heaps!

What's the name of the calendar at the bottom of your screen in your screenshots?

No problem. The calendar is [Rainlendar]("http://www.rainlendar.net/cms/index.php?option=com_rny_download&Itemid=32") with this [Skin]("http://customize.org/rainlendar/skins/57943"). (it's not really in spanish)

---

### Post by easybake on 2008-12-10
> **Shasmo said:**
> I'm so going to give this a try when I get home. I took ages to get a picture of the walls behind my monitor so I could have a 'transparent' background, but to have a 'live' one ...

Feel free to post pics of the set up you make.

---

### Post by easybake on 2009-02-10
Note: This tutorial should work in Jaunty.

---

