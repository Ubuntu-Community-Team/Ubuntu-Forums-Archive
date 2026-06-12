---
title: "HOWTO: Watch videos with TV-Out from Xrandr"
date: 2007-11-28
forum: Outdated Tutorials &amp; Tips
---

### Post by CarpKing on 2007-11-28
**Updated 10/22/2009**

**Warning:** I've had X freeze on me a couple times with this (and Xrandr in general).  Use at your own risk, and make sure you don't have important unsaved files open while using it.  I've never had it freeze with Compiz turned off, but that doesn't mean it never will.  

**Edit:** It seems that I was making this harder than it had to be by using VLC.  MPlayer and SMPlayer behave almost perfectly in this setup.  Instructions altered to encourage simplicity.  

This will allow you to watch videos on a TV connected through an S-video cable. It requires that your video drivers be Xrandr-capable.  At the moment this includes (AFAIK) the open-source ATI and Intel drivers included with Ubuntu (and maybe the open-source nVidia ones as well).  If you figure out ways for this to work with additional players, post it in this thread and I'll add it to this post.   Special thanks to this post:  [http://ubuntuforums.org/showthread.php?p=3467287#post3467287](http://ubuntuforums.org/showthread.php?p=3467287#post3467287)

**Step 1**

First, make sure the TV is connected.  

Then, install xvattr by entering the following in a terminal:

```
sudo apt-get install xvattr
```

A similar command would install VLC, MPlayer, or SMPlayer if they are not installed already.  

**Step 2a: For MPlayer/SMPlayer**

Mplayer should require no configuration.  

In SMPlayer, go to Options -> Preferences -> Advanced and check the "Run MPlayer in its own window" option.  Then click "Apply" and "OK."

Next, use Xrandr to enable the TV:

```
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600 --crtc 1
```

This will display an 800x600 area of your desktop with its top left corner aligned with the top left corner of your screen.  When you play a video, the fullscreen should fill up this area but not the rest of your monitor.  Continue to step three.  

**Step 2b: For VLC**

Open up VLC and go to Settings->Preferences.  Click on the check box at the bottom to show "Advanced options."  Click the item on the left labeled "Video."  Enter 800 in "Video Width," 600 in "Video Height," and 200 in both "Video X coordinate" and "Video y coordinate."  Uncheck "Window decoration."  Now click on the left to Interfaces-> Main Interfaces-> wxWidgets and uncheck "Embed video in interface."  This will make the video appear in a separate window without decoration occupying the space that is displayed on the TV.  Save your settings.  You may have to restart the program for this to take effect.  

Next, use Xrandr to enable the TV:

```
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600 --pos 200x200 --crtc 1
```

This will display an 800x600 area of your desktop with its top left corner 200 pixels to the right and 200 pixels down from the top left corner of your screen.  If you don't have a top panel, you can omit the parts about the video coordinates and the --pos 200x200.  In either case, do not set the video to fullscreen.  

**Step 3**

Now set the Xv overlay to appear on the TV:  

```
xvattr -a XV_CRTC -v 1
```

If some white areas get full of noise (a known problem which should be fixed in the drivers soon), try:

```
xvattr -a XV_BRIGHTNESS -v -30
```

And you should be good to go!  

When you want to return to normal, simply enter the following: 

```
xvattr -a XV_CRTC -v 0
xrandr --output S-video --off
```

For a script to switch between the two states, see [this post](http://ubuntuforums.org/showpost.php?p=8144703&postcount=35).

---

### Post by frodon on 2007-11-28
What you don't like with **displayconfig-gtk** ?
[https://wiki.ubuntu.com/DisplayConfigGTK](https://wiki.ubuntu.com/DisplayConfigGTK)

---

### Post by CarpKing on 2007-11-28
> **frodon said:**
> What you don't like with **displayconfig-gtk** ?
[https://wiki.ubuntu.com/DisplayConfigGTK](https://wiki.ubuntu.com/DisplayConfigGTK)

It won't let me set the TV as a secondary screen.  The only options availiable are "default screen" and "disabled."  Also my video card's max texture size is 2048x2048, so if I wanted the screens to display side by side, I'd have to disable Compiz.

---

### Post by Sith_cz on 2007-12-01
I have same problem as CarpKing. I can't change values in displayconfig-gtk to others than "default screen" and "disabled". Even if I try connect sencondary monitor.
Is there any way to solve this problem?

---

### Post by sciurus on 2007-12-03
> **frodon said:**
> What you don't like with **displayconfig-gtk** ?
[https://wiki.ubuntu.com/DisplayConfigGTK](https://wiki.ubuntu.com/DisplayConfigGTK)

DisplayConfigGTK doesn't support xrandr. It's a very poor tool to use for multiple monitors with the intel or radeon driver.

[https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/144641](https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/144641)

---

### Post by CarpKing on 2008-01-27
First post updated with a simpler method and (hopefully) better organization.

---

### Post by Dacarlson on 2008-03-17
If i were wanting to use my RCA out on my card how would i change the code?

---

### Post by piercleo on 2008-03-19
Hello,

Thank you for this thread, I am now able to have a desktop on two screens and it's very useful.

I have almost reached the result i am looking for :

I have a Dell laptop which i put on a work station linked to a dell screen or which i directly connect to a TV. I don't want to have one big desktop on my two screens. I'd rather have two separate desktops, one on each screen. Is this possible with xrandr ?  If not, what would be the best solution ?

Thank you in advance

PC

---

### Post by zuzoa on 2008-03-20
When I entered 

```
xrandr --addmode S-video 800x600
```

I got:

```
xrandr: cannot find output "S-video"
```

I'm using xrandr 1.2.2, with an ATI Radeon Xpress 200M using the open-source "ati" driver, on Gutsy. Display on the TV through the S-video cable works okay, except I am not able to watch video on the TV, only the monitor. Additonally, entering

```
xvattr -a XV_CRTC -v 1
```

returns this:

```
Found Xv 2.2
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  13 ()
  Serial number of failed request:  11
  Current serial number in output stream:  12
```

xrandr by itself returns:

```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       60.0* 
   1024x768       60.0  
   1024x480       60.0  
   848x480        60.0  
   800x600        60.0  
   720x576        60.0  
   720x480        60.0  
   640x480        60.0  
   640x400        60.0  
   640x350        60.0  
   512x384        60.0  
   400x300        60.0  
   320x240        60.0  
   320x200        60.0  
```

---

### Post by Furiattl on 2008-03-20
Hey yeah, that's cool
The problem is I want to watch a movie on the TV AND still be able to work on the monitor. When I do full screen in the VLC or SMPlayer the first screen goes black... hmm.
In XP I can start a movie and it goes full screen on the TV, the monitor is all mine.

---

### Post by Jonte_J on 2008-05-03
Hello
Great tutorial, finally my TV out is working the way I want it to in Ubuntu, or at least almost, there is only one small problem left:

When I watch a movie on my TV, the movie window doesn't use the entire TV width. There is an about 2 cm black area to the left of the movie. Does anybode else have this problem, and how is it solved?

Thank you

Jonas

---

### Post by chronographer on 2008-05-26
Hi all.

i just thought i'd add this script I made, which you can right click on a movie, and play it on the TV. The only thing left to work out (we can do it folks!) is to play a movie on the tv while leaving the monitor free to do other things, this way I can put finding nemo on for the kids, and work hard at the desk!

Anywho here's the script, put it in ~/.gnome2/nautilus-scripts/ and then it should appear in a right click menu 'Scripts' oh. you have to name it, 'movie.sh' and then make it executable, by right clicking it, go to permissions and checking 'Allow execution file as a program' enjoy!

> 
#!/bin/sh
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600 --set tv_standard pal
xvattr -a XV_CRTC -v 1
/usr/bin/mplayer -fs "$*"
xvattr -a XV_CRTC -v 0
xrandr --output S-video --off


---

### Post by jocko on 2008-05-26
I think I may help with getting movies to play only on the tv.
I have set up dual head in my xorg.conf, with the second screen running as a separate session on the tv (i.e not cloned mode or xinerama/big desktop or whatever).
Unfortunately I have no idea how to use xrandr to set that up (but in the manual (man xrandr) there are commands for where to place the second output relative to the primary screen, so it should not be that hard to figure out).
Then to set mplayer to show videos fullscreen on the tv, add these two options to ~/.mplayer/config (hidden folder in your home directory):
```
DISPLAY=:0.1
fs=1

```

---

### Post by chronographer on 2008-05-28
Can you do a dual head set up with an ati card? I used to have this setup with my nvidia, separate screens and had a script which had something like 'DISPLAY=:0.1 /usr/bin/vlc -f $*' but you can use mplayer -fs $* and it puts the video fullscreen on the other monitor. But I am now using the above script which works real nice! Just doesn't let me use the monitor at the same time...

---

### Post by jocko on 2008-05-28
> **chronographer said:**
> Can you do a dual head set up with an ati card?

Yes. I don't think amdcccle can set it up, but aticonfig can:
```
sudo aticonfig --initial=dual-head
```(first backup your xorg.conf if you have made any manual changes in it)
And: compiz does not work with a dual head setup unless you inactivate aiglx and install xgl.

---

### Post by chronographer on 2008-06-05
hey I got dual head working with the fglrx drivers, but the problem then is that compiz wont run. I checked compiz IRC and they said nobody has got 2 separate x-screens with prop-ati drivers working with compiz. So I am gonna leave it as it is, using xrandr script above to turn the tv on and play a movie!

---

### Post by Placenta Juan on 2008-07-30
Well, I've gotten my TV to display an 800x600 portion of my desktop, and thanks to xvattr I can get video to display on the TV rather than the monitor, the problem is when I fullscreen the video, it fullscreens to the desktop's resolution, so I only see the upper left portion of the video on my TV. Additionally, the video is dim and white areas show static/flickering.
I've been trying to get video to play on my TV for nearly two years, and this is the closest I've come (in Linux, anyway). It's frustrating to get so close and yet not quite have it...:sad:

I'm using a Radeon 9600XT with the latest xorg ati drivers (6.9.0) on Kubuntu 8.04, by the way.

---

### Post by CarpKing on 2008-08-28
> **Placenta Juan said:**
> when I fullscreen the video, it fullscreens to the desktop's resolution, so I only see the upper left portion of the video on my TV. Additionally, the video is dim and white areas show static/flickering.

What player are you using?  I had the fullscreen problem with Totem and VLC, but Mplayer and SMplayer work fine.  

As for the static problem, I've gotten around it by adjusting the brightness down in gxvattr.  The problem is that I have to do it each time a video starts; it doesn't seem to "stick."  

I should probably update the first post.

---

### Post by Crafty Kisses on 2008-08-29
Nice tutorial, smoothly written.

---

### Post by stevan2002 on 2008-09-07
Good tips, here is a bigger tutorial on using XranR to dualscreen with different types of outputs. 

[http://navetz.com/v/132/Simple-dual-monitor-setup-with-XrandR-in-Ubuntu-Linux]("http://navetz.com/v/132/Simple-dual-monitor-setup-with-XrandR-in-Ubuntu-Linux")

---

### Post by eumetaxas on 2008-12-20
Hi and thanks for the tutorial.
I am in Europe and tried

```

xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600 --set tv_standard pal
xvattr -a XV_CRTC -v 1
Found Xv 2.2
XV_CRTC set to 1

```

It did not return any errors. Using it i was able to see something like waves on my tv . It seems like the tv is not synchronising or something like that (excuse me for my non tech terms). It a Phiips CRT 29inch.

i have a nx9010 compaq laptop with a Radeon IGP 345M, using hardy 8.04 LTS
Tried atitvout but did not work either.

```
 dmesg | grep agp
[ 41.114541] Linux agpgart interface v0.102
[ 41.328190] agpgart: Detected Ati IGP345M chipset
[ 41.338886] agpgart: AGP aperture is 64M @ 0xd4000000 

lspci
VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

XORG.CONF
Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection 
```

Thank you for your help!

---

### Post by anderssl on 2009-03-24
> **zuzoa said:**
> When I entered 

```
xrandr --addmode S-video 800x600
```

I got:

```
xrandr: cannot find output "S-video"
```



I have exactly the same problem as zuzoa. I see this thread is getting old, but I`m still a clueless noob and can`t fix this myself... Anyone know why my xrandr can`t find the S-video output?

I`m using 8.10 on an Acer Travelmate 4501 with an ATI 9700 radeon graphics card. I`m not getting anything on my tv screen, nada... I`m using a simple adapter from s-video to basic video, if that matters to anyone. Any help would be greatly appreciated!

Cheers,
Anders

---

### Post by jocko on 2009-03-24
> **anderssl said:**
> I have exactly the same problem as zuzoa. I see this thread is getting old, but I`m still a clueless noob and can`t fix this myself... Anyone know why my xrandr can`t find the S-video output?

I`m using 8.10 on an Acer Travelmate 4501 with an ATI 9700 radeon graphics card. I`m not getting anything on my tv screen, nada... I`m using a simple adapter from s-video to basic video, if that matters to anyone. Any help would be greatly appreciated!

Cheers,
Anders
Which driver do you use?
With ati's proprietary driver you need to use the catalyst control center to change tv-out settings.
randr should work fine with the open source driver.
Which outputs are detected by randr? Run:
```
randr -q
```

---

### Post by anderssl on 2009-03-31
Thanks for replying! I`d been playing around with both the open source drivers and the proprietary ones, not getting stuff to work. In the end something went seriously wrong, I wasn`t even able to boot. so I ended up reinstalling the whole system. Now, at a fresh install, I`ve followed this howto once more, and get the following output from xrandr -q:

```

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1200
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right x axis y axis)
   800x600        60.3  

```

Running just randr -q gives "Command not found"...

Any idea what the problem can be?

---

### Post by fermulator on 2009-05-10
> **anderssl said:**
> Thanks for replying! I`d been playing around with both the open source drivers and the proprietary ones, not getting stuff to work. In the end something went seriously wrong, I wasn`t even able to boot. so I ended up reinstalling the whole system. Now, at a fresh install, I`ve followed this howto once more, and get the following output from xrandr -q:

```

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1200
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right x axis y axis)
   800x600        60.3  

```

Running just randr -q gives "Command not found"...

Any idea what the problem can be?

What about
```
xrandr -q
```
?

I'm having the same problem, my xrandr -q returns:
> Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 3360 x 1050
DVI-1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      59.9*+
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)

It doesn't show S-video as a device ....

---

### Post by anderssl on 2009-05-11
It seems that the open source drivers don't support TV-Out on ATI graphics cards. I messed around for a long time in the documentation before I finally found that piece of info buried somewhere in a footnote (can't find it right now, will post link if I find it later). As for the propietary drivers, they are too unstable for my machine (I tried twice, and had to reinstall my system both times). So for now, no TV-Out on ATI...

---

### Post by fermulator on 2009-05-11
Apparently it's "soon to be fixed" -- see my post here: [http://phoronix.com/forums/showpost.php?p=73693&postcount=13](http://phoronix.com/forums/showpost.php?p=73693&postcount=13)

---

### Post by anderssl on 2009-05-11
> **fermulator said:**
> Apparently it's "soon to be fixed" -- see my post here: [http://phoronix.com/forums/showpost.php?p=73693&postcount=13](http://phoronix.com/forums/showpost.php?p=73693&postcount=13)

Hey, thanks a lot for the link! My card is r300, so looks like I should already be covered. Geronimo!

---

### Post by diablostereo on 2009-05-15
the first method works also with vlc if you use x11 or opengl as the video output

---

### Post by hissyfut on 2009-07-31
Having some problems understanding xrandr syntax. Trying to get the tv out to match clone the monitor. The output need to be shifted left or right and up or down. And the output needs to be resized. Tried --pos which does fair but it does not seem to shift the screen 'x' way, and trying --scale 1.xx1.x with 'x' being anything over 1 does correct output but changing the monitor. If anyone can post some examples of xrandr moving an output screen around and also resizing examples it would be greatly appreciated.

---

### Post by eumetaxas on 2009-08-08
After recently updating to 9.04 and despite the other problems of the update thankfully my s-video out finally worked. One less reason to boot into legacy system:)
Some minor problems like the ones listed above, are  present, but at least s-video works!
Thank you

---

### Post by ricsi-pontaz on 2009-08-16
Hello!

Thanks for the tutorial, but it doesn't work for me.

When I type this command:

```
xvattr -a XV_CRTC -v 1
```

I've got this message:

> Found Xv 2.2
XV_CRTC set to 1

Is this okay?

So when I connect my notebook (Ubuntu 9.04, ATI Xpress 1100, Open ATI Driver) with the TV, I only see a blank screen with white vibration. (Is different from the basic screen, so something is turn on, but not in the right way, I think).

What is the problem?

---

### Post by ricsi-pontaz on 2009-08-27
> **CarpKing said:**
> What player are you using?  I had the fullscreen problem with Totem and VLC, but Mplayer and SMplayer work fine.  

As for the static problem, I've gotten around it by adjusting the brightness down in gxvattr.  The problem is that I have to do it each time a video starts; it doesn't seem to "stick."  

I should probably update the first post.

I solved my previous problem, but now I've got the same problem as you. How can I adjust down the brightness in gxvattr?

---

### Post by CarpKing on 2009-10-22
> **ricsi-pontaz said:**
> I solved my previous problem, but now I've got the same problem as you. How can I adjust down the brightness in gxvattr?

In my script I have:
```
xvattr -a XV_BRIGHTNESS -v -30
```

Since upgrading to Jaunty this seems to actually stay in effect.  If you want to use the graphical tool (gxvattr), XV_BRIGHTNESS is about halfway down.  Keep in mind that this only affects Xv outputs, so if you're watching flash video or your player is set to use OpenGL or something else, this command will not affect it.  

On a brighter note, I think I saw a post on the Phoronix forums implying that the underlying problem with the white areas had been fixed in the driver.  Hopefully the driver in Karmic is new enough to contain this fix.  Then we wouldn't have to worry about this at all.


> **Jonte_J said:**
> When I watch a movie on my TV, the movie window doesn't use the entire TV width. There is an about 2 cm black area to the left of the movie. Does anybode else have this problem, and how is it solved?

That's the result of a lack of overscan.  I'm not sure what cards support overscan, but I know some at least have controls for it in their Windows configuration programs.  I also have this issue in Windows, but the black area is split between both sides of the output instead of on one side like in Linux.  

I don't know if it can be solved currently, but "overscan" is the term for it, if that helps you find out more.

---

### Post by CarpKing on 2009-10-22
Here's the script I use to start and stop my TV output.  I'm not sure where I got the first line from, otherwise I'd cite the post.  You'll have to set it to executable.  I put a launcher for it on my panel.  

```
#!/bin/sh

#checks to see if TV display is already on
if xrandr --prop | grep -q '800x600+0+0'
	then
	#sets Xv overlay to computer
	xvattr -a XV_CRTC -v 0

	#shuts off TV output
	xrandr --output S-video --off
else
	#enables TV output
	xrandr --addmode S-video 800x600

	#if using VLC with an upper panel, add --pos 200x200
	xrandr --output S-video --mode 800x600 --crtc 1
	#if enough virtual output space is available, make displays side by side instead:
	#xrandr --output S-video --right-of VGA-1 --mode 800x600 --crtc 1

	#sets Xv overlay to TV and adjusts brightness
	xvattr -a XV_CRTC -v 1
	xvattr -a XV_BRIGHTNESS -v -30
fi
```

---

### Post by kmedioman on 2010-01-30
Thanks, it works great with my ATI IGP340m on HP nx9010. :p

I just found easier to set a new user in 800x600 mode and send tvout directly without modifying VLC window size and position. 
Surprisingly in 800x600 laptop screen the script doesn't work as it is but I have to do this sequence of operations:

0. Set the laptop screen in 1024x768
1. Execute the script and send signal on TV screen, works correctly
2. Set the laptop in 800x600, TV screen blanks
3. Execute not the complete script but only the command ```
 xrandr --output S-video --mode 800x600 --crtc 1 
```and it works great! Any idea on how to have the script working in 800x600 directly? Thanks

---

