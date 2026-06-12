---
title: "Can't get correct resolution 1600x900"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by andrewcole50 on 2012-06-28
Hello,

I'm totally new to Ubuntu and love it except I can't get my screen's resolution correct which is a problem since I do graphic design! I have a month old Alienware M14X. I've tried looking at all the help on here and google but nothing seems to help. I've gone into xrandr and this is what it tells me:

cole@cole:~$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 174mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
  1600x900_60.00 (0xa9)  118.2MHz
        h: width  1600 start 1696 end 1856 total 2112 skew    0 clock   56.0KHz
        v: height  900 start  903 end  908 total  934           clock   59.9Hz
  1600x60_60.00 (0xba)    7.8MHz
        h: width  1600 start 1648 end 1800 total 2000 skew    0 clock    3.9KHz
        v: height   60 start   63 end   73 total   76           clock   51.0Hz
cole@cole:~$ 



Here is the error code i usually get when trying to add a resolution:
cole@cole:~$ xrandr --addmode LVDS1 1600x900_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  29
  Current serial number in output stream:  30
cole@cole:~$ 


Thanks!

---

### Post by andrewcole50 on 2012-06-29
Bump

---

### Post by andrewcole50 on 2012-07-02
Anybody? If this isn't in the right section could a mod please move it please so I have a better chance of getting help?

---

### Post by sudodus on 2012-07-02
Welcome to the Ubuntu Forums andrewcole50 :-)

Have you tried the following command
```
xrandr -s 1600x900
```

---

### Post by andrewcole50 on 2012-07-02
Ah, thank you! I just tried it and this is what I got:

cole@cole:~$ xrandr -s 1600x900
Size 1600x900 not found in available modes

---

### Post by sudodus on 2012-07-02
What graphics card are you using?

What graphics driver are you using?
 - nouveau (the default built in driver), or
 - a built-in proprietary driver (via jockey-gtk) or
 - a proprietary driver downloaded from the manufacturer's web page?
 
You might need to test more than one of those from the manufacturer's web page.

[I]Edit: Is this what you are using: Graphics Processor 3.0GB DDR3 nVidia GeForce GT 555M using nVidia Optimus technology? You can find threads in the Ubuntu Forums discussing the Optimus technology.
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=2014681_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2014681")
[[COLOR="red"]_http://ubuntuforums.org/showthread.php?t=2011675&highlight=optimus_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2011675&highlight=optimus")
[/I]

---

### Post by andrewcole50 on 2012-07-02
I would assume nouveau. I tried to go to Nvidia's page and download their drivers but it all got kind of confusing. I'm brand new to Ubuntu and Linux in general so it's all a little confusing right now. If it helps, I have a Nvidia GEforce GT 555M video card. I've went to the additional drivers GUI and it doesn't detect a thing. Thank you for the replies btw.

---

### Post by sudodus on 2012-07-02
What about Optimus? See the edit in my previous post.

---

### Post by sudodus on 2012-07-02
And what version of Ubuntu? 10.04 LTS, 11.10 or 12.04 LTS? I think your chances are best with new hardware and new software (12.04 LTS). If you dare test the alpha-testing-stage 12.10, you get a newer kernel with better support for new hardware, and it is important particularly if you cannot get the proprietary drivers running.

---

### Post by andrewcole50 on 2012-07-04
Alright so here's what's happened:

My friend installed the nvidia drivers for me and then  I was stuck with 640x480 resolution. I couldn't work the windows because  I couldn't get to the buttons on the bottom of the windows. However, before we installed the drivers (and after for that matter) we hooker an external display (VGA) to the laptop. Everything worked perfectly for the other display, we even added and used 1600x900 on it! It seemed like Ubuntu doesn't like my laptop display or something.

So I uninstalled and reinstalled Ubuntu 12.04 and the first thing I did was get bumblebee through <a href='http://ubuntuforums.org/showthread.php?t=1987670'>instructions here</a>

That's all well and great but my graphics card is still unknown to Ubuntu and I don't think bumblebee helped at all. The only plus side to reinstalling 12.04 was that I got my drag maximize commands back. Somehow I didn't get  those the last time I had 12.04. 

<i>Edit: I forgot, you were correct in the video card I'm using. It does indeed have Optimus technology.</i>

I also will not be trying 12.10 alpha because...well...I'm still learning linux haha.

---

### Post by westcoast01 on 2012-07-04
To move the page up so you can access the bottom of the page try moving your mouse toward the bottom of the page ... press and hold alt ... left click and hold the mouse while moving in an upward direction. This will raise the page up so you can access the bottom. Best of luck.

---

### Post by andrewcole50 on 2012-07-06
westcoast - thank you! That is a pretty useful bit of info regardless if my screen is screwed up or not :)

---

