---
title: "Refresh rate/ no xorg.conf file ?"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by siriusbg on 2011-12-08
Hello! I am running Ubuntu 11.10 and have a Nvidia 9500 GT video card and installed the proper drivers. But I can't adjust the refresh rate to my wish. The options are spanning from 56 to 100 hz, but the exact refresh rate I normally use - 80hz isn't available. I read somewhere that I have to edit the xorg.conf file and there is an option to edit it with the desired refresh rate ... but my xorg.conf file is completely empty! And the refresh rate is simply killing me - I can't get used to it. I have an old CRT 14' monitor - could it be that it is in some way incompatible?
Could someone give me a hint how to handle this situation?

---

### Post by lechien73 on 2011-12-08
I think you can use the xrandr tool to set the resolution and refresh rate.

First, we need to figure out what your monitor is called, so just open a terminal window and run:

```
xrandr
```

The first few lines will tell you the name of your monitor, so for my laptop it returns:

```
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 8192 x 8192
LVDS1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 367mm x 23000mm
```

So my screen is called LVDS1. By way of the example, I'm presuming yours might be VGA0. I'm also going to use 800x600 as the example resolution, so change any references to 800x600 to your actual screen resolution.

Now you need to generate the modeline for xrandr. If you want to use 80Hz refresh rate, then try:

```
cvt HORIZONTAL_RESOLUTION VERTICAL_RESOLUTION 80
```

Replace HORIZONTAL_RESOLUTION and VERTICAL_RESOLUTION with the screen resolution you want - for example 1024 768, or 800 600. This will return a modeline. Copy the modeline to the clipboard (but don't include the word "Modeline"). On my system it looks like this:

```
"1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
```

To set it, then use xrandr as follows:

```
xrandr --newmode MODELINE_FROM_cvt
```

Replace MODELINE_FROM_cvt with the modeline you copied to the clipboard.

Add and activate the new mode:

```
xrandr --verbose --addmode VGA0 "800x600_80.00"
xrandr --output VGA0 --mode "800x600_80.00"
```

I know it seems like a long way to do it, but if it works, then this link might help you with details on how to make the changes persistent: [https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_changes_persistently](https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_changes_persistently)

---

### Post by siriusbg on 2011-12-08
Hello! Thank you for the thorough analysis. Everything goes well, until I try activating the new mode. This is what appears 
```
xrandr: Failed to get size of gamma for output default
xrandr: cannot find output "VGA0"

```

The problem is - the above mentioned VGA0 appears nowhere in the xrandr command. This is what appeared after using it :
```
 xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0*    51.0     52.0     53.0     54.0  
   960x540        55.0  
   840x525        56.0     57.0  
   832x624        58.0  
   800x600        59.0     60.0     61.0     62.0     63.0     64.0     65.0  
   720x450        66.0  
   720x400        67.0  
   700x525        68.0  
   680x384        69.0     70.0  
   640x480        71.0     72.0     73.0     74.0     75.0     76.0     77.0     78.0  
   640x400        79.0  
   640x350        80.0     81.0  
   512x384        82.0     83.0     84.0  
   400x300        85.0  
   320x240        86.0     87.0  
   320x175        88.0  


```

---

### Post by lechien73 on 2011-12-08
Hi,

It looks like your screen is simply called "default", so try replacing VGA0 with that instead.

---

### Post by siriusbg on 2011-12-10
No, it didn't work. I used the "default" screen name, but I keep receiving the ```
xrandr: Failed to get size of gamma for output default
```Somehow I get the feeling the modeline can't be recognized by the xandr. Anyway, I follow closely every step and it just doesn't work.. Please, help.

---

### Post by lechien73 on 2011-12-10
I was reading too quickly and didn't notice the error message was in your original xrandr output.

The problem is that your monitor isn't providing the EDID (Enhanced Display Identification Data) that xrandr needs to try and intelligently figure out certain settings.

These will need to be provided manually, and you'll need to create an xorg.conf.

This link: [https://wiki.ubuntu.com/X/Config/Resolution#Setting_resolution_changes_in_xorg.conf](https://wiki.ubuntu.com/X/Config/Resolution#Setting_resolution_changes_in_xorg.conf) might help you with regard to xorg.conf

While this wiki: [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2) gives some useful help with how to use xrandr.

I'd like to help you get it sorted, though, and I know that there's a lot of reading there. One thing I'd like to do is have a look at your monitors.xml file. Please open a terminal window and type:

```
gedit ~/.config/monitors.xml
```

Please paste the contents of the file here between [CODE] tags. Maybe we can force it that way without having to create an xorg.conf file.

---

### Post by lolpenguin on 2011-12-10
AFAIK Ubuntu no longer uses Xorg.conf

---

### Post by siriusbg on 2011-12-11
Hi, this is what showed up.

```
<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="DVI-I-1">
      </output>
      <output name="DVI-I-2">
          <vendor>CTX</vendor>
          <product>0x5696</product>
          <serial>0x00000000</serial>
          <width>1024</width>
          <height>768</height>
          <rate>75</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>yes</primary>
      </output>
  </configuration>
  <configuration>
      <clone>no</clone>
      <output name="default">
          <vendor>???</vendor>
          <product>0x0000</product>
          <serial>0x00000000</serial>
          <width>800</width>
          <height>600</height>
          <rate>50</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>yes</primary>
      </output>
  </configuration>
</monitors>
```

---

### Post by lechien73 on 2011-12-12
I'm presuming that the monitor we want to use is not the CTX monitor connected to the DVI port?

Also, I should have asked earlier, but are you trying to set the old 14" monitor up as your primary monitor, or as a secondary?

---

### Post by siriusbg on 2011-12-12
On the contrary, the old CTX monitor is the one I want to use, since I have no other monitor available .. at least for some time to come. 
So, I really need to get this old 14" CTX monitor working (yes, I should have mentioned it earlier, my bad)under ubuntu. Thank you :)

---

### Post by lechien73 on 2011-12-12
I could be wrong here, but I believe that the UI processes the contents of monitors.xml after initialising X.

If you go to the command prompt and try the following:

```
cd .config
gksu gedit monitors.xml
```

Change the <rate> to 80, save, exit, reboot and cross everything you've got :D

---

### Post by siriusbg on 2011-12-13
Hi. After numerous attempts, all of them effortless, I discovered the CompizConig Manager and installed it. It was actually a major success - I changed the refresh rate to 80 Hz without any trouble. Thank you for your patience and guidance, but it seems I got the problem solved ... at least for now :)

---

### Post by bobalazs on 2011-12-13
Hey ya.

Let me post my question-request here, since i just started using ubuntu, and freshly registered to forum, I can not start a new thread.
Im using an[SIZE=1] VIA S3 unichrome Pro IGP integrated graphics on a laptop.
I connected a 1920x1080 capable led monitor - and now got dual display -by default- but with same 1280x800 resolution. 
I have read up on the subject, and there are some people who actually did configure the 1920 resolution on linux (using x perhaps) -but details were not given. 
on linux-drivers.com the driver is accessible and without installation, after reading the readme file i checked if driver is present, and it is, so installing is not necessary (im using  ubuntu 10.4. and its installed by default) 

Let me quote one of the posts on viaarena forums: "[/SIZE]That's because Windows drivers depend on the VGA BIOS for mode-setting  support, which is embedded in the motherboard BIOS, while current Linux  drivers can bypass VGA BIOS dependency."


BTw this is what i'm getting for modes: 
Screen 0: minimum 640 x 400, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       60.0* 
   1280x768       60.0  
   1280x720       60.0     59.0  
   1024x768       75.0     60.0     70.0  
   1024x600       60.0  
   1024x576       60.0  
   1024x512       60.0  
   832x624        75.0  
   800x600        75.0     60.0     72.0     56.0  
   720x576        60.0  
   856x480        60.0  
   848x480        60.0  
   800x480        60.0  
   720x480        60.0  
   640x480        75.0     60.0     73.0  
   720x400        70.0

Now, this is why i specifically switched to ubuntu on my laptop, since it is possible to change the resolution to 1920x1080?  As i said i'm a complete newb when it comes to linux, however, this ubuntu 10.4 is not using X? Is there a guru that could help me with this problem, or perhaps refer me to an appropriate Pro user that could solve this? (maybe connect to my computer and give me help)
Thanks

---

### Post by lechien73 on 2011-12-14
> **bobalazs said:**
> Hey ya.

Let me post my question-request here, since i just started using ubuntu, and freshly registered to forum, I can not start a new thread.

Hi & welcome to Ubuntu,

I'd strongly suggest that you go back to the [forum index]("http://ubuntuforums.org/forumdisplay.php?f=326") and create a new thread. If you can reply to this thread, then you should be able to create a new one. I've attached a screenshot showing you where the button is.

Adding your request to the end of a different thread means it's likely to be missed - especially since the OP now has solved his problem.

Send me a private message if you have problems creating a new thread, and I'll help you :)

---

### Post by lechien73 on 2011-12-14
> **siriusbg said:**
> Thank you for your patience and guidance, but it seems I got the problem solved ... at least for now :)

Great - you're welcome - I'm glad it seems to be working at last.

If you get chance, could you use the **Thread Tools** menu at the top of the page, and mark this issue as [SOLVED]?

Many thanks

---

