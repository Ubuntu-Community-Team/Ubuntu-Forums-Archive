---
title: "HOWTO: enable circular scrolling on synaptics touchpads"
date: 2008-03-07
forum: Outdated Tutorials &amp; Tips
---

### Post by MONODA on 2008-03-07
This tutorial will show you how to give your touchpad on your laptop the ability to  scroll up and down using a circular motion on the touchpad. this is similar to vertical and horizontal scrolling. You will have to edit your xorg.conf file so if you do not feel comfortable doing this then do not continue this tutorial.
ok so let's start:

first you need to make sure that the driver for your touchpad on your laptop is synaptics (it should be). To find out whether it is or not, do the following:
```

sudo nano /etc/X11/xorg.conf

```
and search for :
> Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"


if you find this section (the Identifier may be bamed something else but as long as the driver is synaptics, you are good) then continue if not, do not.

at the end of this section, add:
>         Option          "CircularScrolling"     "on"
        Option          "CircScrollTrigger"     "2"

so that it looks like:
> Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
        Option          "CircularScrolling"     "on"
        Option          "CircScrollTrigger"     "2"
EndSection

Option          "CircularScrolling"     "on" turns circular scrolling on, and  Option          "CircScrollTrigger"     "2"  selects the edge which should be the trigger. Meaning that if I set it to 2 then circular scrolling will be activated when I put my finger at edge 2. This is the translation from numbers to edges:
> 
0          any edge
1          top edge
2           top right corner
3           right edge
4           bottom right corner
5            bottom edge
6            bottom left corner
7          left edge
8          top left corner
the way you use it is similar to an ipod, clockwise motions on the touchpad will scroll downwards while counterclockwise will scroll upwards. 

once you have done this, restart X with ctrl+alt+backspace. be sure to save all your work and exit all apps first. hope it works for you.

---

### Post by MONODA on 2008-03-15
so does this work for everyone?

---

### Post by graingert on 2008-04-12
Briliant!

---

### Post by MONODA on 2008-04-13
thanks :D i thought that no one would try it.

---

### Post by DynamicStu on 2008-04-14
This is really excellent!  Thanks.

My wife hates the vertical scrolling that defaults with the touchpad.  I'm going to show her this, and hopefully she'll find out the convenience of not having to click on the scrollbar!

---

### Post by chmac on 2008-11-12
Any idea what to do on Intrepid (Ubuntu 8.10) where the xorg.conf is empty by default?

---

### Post by sharon.gmc on 2008-11-12
wow!  thank you. . . this is a mine. . . .

---

### Post by beilwei123 on 2008-11-12
I fully support you, this is my task. I hope you better[**Shanghai massage**|**Shanghai escort**](http://www.lovemassage.com.cn)|[**massage Shanghai**|**massage in Shanghai**](http://www.lovemassage.com.cn)|[**Shanghai massage**|**Shanghai escort**](http://www.lovemassage.cn)|[**massage Shanghai**|**massage in Shanghai**](http://www.lovemassage.cn)|[**Shanghai massage**|**Shanghai escort**|**massage Shanghai**|**massage in Shanghai**](http://www.okmassage.net)

---

### Post by gogreenpower on 2008-11-12
didnt work for me using 8.10, vertical and horizontal work fine but no circular

---

### Post by chmac on 2008-11-12
> **gogreenpower said:**
> didnt work for me using 8.10, vertical and horizontal work fine but no circular

Did you create an xorg.conf? Or did you upgrade from 8.04 and so it was already there for you?

I think the default in 8.10 is an empty xorg.conf.

---

### Post by gogreenpower on 2008-11-12
i upgraded from 8.04 but i set the scroll trigger to 6 and it wasn't working but when i put it back to 2 it worked? not to annoying just wanted it to start at the bottom left

---

### Post by waitn2drive on 2010-05-04
I know my reply is a little late, about 2 yrs late, but I have 10.04, and tried this tut. and it didn't work, the doc. to edit didn't pop up, you think anyone could show me how to do it in 10.04?

---

### Post by Björn on 2010-05-04
Hi, don't know anything about cirular scrolling but nano is a terminal text editor and it should stay in the terminal. Try to exchange nano for gedit and make sure you spelled everything right because i can open the file both in gedit and nano.

Björn

---

### Post by chmac on 2010-05-04
I forgot to post back to this thread. There's no need to edit xorg.conf any more, it's blank by default in recent versions of Ubuntu. Instead, I followed the instructions [here]("https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig") to create a file /etc/hal/fdi/policy/shmconfig.fdi with the contents:
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">on</merge>
    </match>
  </device>
</deviceinfo>
```

You can create this file with the command:
```
gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi
```

Then copy / paste in the contents and save. After that, install gsynaptics and use System > Preferences > Touchpad to enable circular scrolling.

That worked for me under 9.04, I'm about to upgrade to 10.04 and so I'm hoping it'll work there also. If not, I'll be back here looking for more info. waitn2drive, if you test this on 10.04 would be you kind enough to post back your results? Here's hoping it works... :-)

---

### Post by skorange on 2010-05-05
chmac, it worked great for me in Lucid.  Thanks for the tip!

---

### Post by chmac on 2010-05-06
Just installed 10.04. I installed gsynaptics, enabled circular scrolling, and it's game on. I didn't change anything else. On Lucid I don't have a /etc/hal/fdi/policy/shmconfig.fdi file. Just works. :-)

---

