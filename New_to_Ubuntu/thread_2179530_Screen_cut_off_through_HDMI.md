---
title: "Screen cut off through HDMI"
date: 2013-10-08
forum: New to Ubuntu
---

### Post by DLCmEy8 on 2013-10-08
So I connected my pc through HDMI.
All I got was all sides of my screen cutt off by about 20 or so pixels. I can barely even see the sidebar and I can't see my interface on the top of my screen with the time display.
I contacted my TV's manufacturer and they simply told me that it had nothing to do with their tv. I should contact my computer provider... (I smell lazy but okay)
Is there any way to fix this issue manually?
My TV: Magnavox 32MF301B/F7
My PC: Dell Inspiron 1525 (Specs: [http://www.cnet.com/laptops/dell-inspiron-1525/4507-3121_7-32814939.html](http://www.cnet.com/laptops/dell-inspiron-1525/4507-3121_7-32814939.html))

---

### Post by papibe on 2013-10-08
Hi DLCmEy8. Welcome to the forum ):P

Are you seeing the black bars on the side too? or that is on the screenshot?

Could you post the result of these commands?
```
lspci -nnk | grep -iA2 vga

xrandr

xrandr -q --q1

xvidtune -show
```
Regards.

---

### Post by DLCmEy8 on 2013-10-08
> **papibe said:**
> Hi DLCmEy8. Welcome to the forum ):P

Are you seeing the black bars on the side too? or that is on the screenshot?

Could you post the result of these commands?
```
lspci -nnk | grep -iA2 vga

xrandr

xrandr -q --q1

xvidtune -show
```
Regards.

The black bars were simply a visual representation. I'm an idiot for posting it anyways. The top and bottom of the screen are also cut off by about 10-20 pixels.
```
user@user-Inspiron-1525:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
    Subsystem: Dell Device [1028:022f]
    Kernel driver in use: i915
user@user-Inspiron-1525:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 32767 x 32767
LVDS1 connected (normal left inverted right x axis y axis)
   1280x800       60.0 +
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected (normal left inverted right x axis y axis)
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
   1600x900_60.00   59.9  
HDMI1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 16mm x 9mm
   1920x1080      60.0*+   30.0     24.0  
   1920x1080i     30.0  
   1280x720       60.0  
   1440x480i      30.0  
   720x480        59.9  
   640x480        59.9  
   1360x768_60.00   59.8  
TV1 disconnected (normal left inverted right x axis y axis)
user@user-Inspiron-1525:~$ xrandr -q --q1
 SZ:    Pixels          Physical       Refresh
*0   1920 x 1080   (  16mm x   9mm )  *60   30   24  
 1   1280 x 720    (  16mm x   9mm )   60  
 2   1440 x 480    (  16mm x   9mm )   30  
 3    720 x 480    (  16mm x   9mm )   60  
 4    640 x 480    (  16mm x   9mm )   60  
 5   1360 x 768    (  16mm x   9mm )   60  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - X Axis Y Axis
user@user-Inspiron-1525:~$ xvidtune -show
"1920x1080"   148.50   1920 2008 2052 2200   1080 1084 1089 1125 +hsync +vsync
```

---

### Post by DLCmEy8 on 2013-10-08
Anyone?

---

### Post by papibe on 2013-10-08
Thanks.

That looks awful like [overscan]("http://en.wikipedia.org/wiki/Overscan"). Very annoying and usually it is the TV's fault. 

For example, in the case of my Sony Bravia you can fix it by setting 'Full Pixel' to Screen -> Display Area. In my brother's Samsung you would set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).

Nevertheless, if you can't adjust the resolution using your TV remote, then you're left to solve the problem using xrandr commands on the terminal. Take a look at this example [here]("http://ubuntuforums.org/showthread.php?t=2141776&page=2&p=12643066#post12643066").

Let us know if that helped, and if you need more help with that.
Regards.

---

### Post by DuckHook on 2013-10-09
> **papibe said:**
> ...in the case of my Sony Bravia you can fix it by setting 'Full Pixel' to Screen -> Display Area. In my brother's Samsung you would set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly)....in the OP's Magnavox, it is fixed by setting Format>PC Input to "Unscaled" (it's in OP's TV Users Manual).

---

### Post by DLCmEy8 on 2013-10-09
> **papibe said:**
> Thanks.

That looks awful like [overscan]("http://en.wikipedia.org/wiki/Overscan"). Very annoying and usually it is the TV's fault. 

For example, in the case of my Sony Bravia you can fix it by setting 'Full Pixel' to Screen -> Display Area. In my brother's Samsung you would set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).

Nevertheless, if you can't adjust the resolution using your TV remote, then you're left to solve the problem using xrandr commands on the terminal. Take a look at this example [here]("http://ubuntuforums.org/showthread.php?t=2141776&page=2&p=12643066#post12643066").

Let us know if that helped, and if you need more help with that.
Regards.

```
user@user-Inspiron-1525:~$ xrandr --output HDMI1 --set underscan on
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  31
  Current serial number in output stream:  31
```
Wut?...

> **DuckHook said:**
> ...in the OP's Magnavox, it is fixed by setting  Format>PC Input to "Unscaled" (it's in OP's TV Users  Manual).
Works with VGA. Doesn't work with HDMI.
Since this TV manufacturer thought HDMI was law when this TV was made they expected it to be perfect hence they never added adjustment settings for it.

---

