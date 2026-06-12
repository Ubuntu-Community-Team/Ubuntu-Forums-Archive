---
title: "Monitor/Resolution problem"
date: 2012-12-19
forum: New to Ubuntu
---

### Post by Nick00 on 2012-12-19
Hi everybody,
I'm new to ubuntu (I installed yesterday 12.04 LTS  and upgraded it to 12.10) and I can't figure out why i can't set my resolution to 1440x900, which would be the right one for my monitor. i tried to follow some troubleshooting lines I found on the forum, since, as I came to understand, it's a pretty common problem, but no solution has worked for me yet.
On preferences > Monitor i have only three options: 800x600, 1024x768 and 1280x1024. 
The only thing I managed to do is to add the mode that should work for me (?) to xrandr output:
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1280 x 1024
default connected 1024x768+0+0 0mm x 0mm
   1280x1024       0.0  
   1024x768        0.0* 
   800x600         0.0  
   640x480         0.0  
  1440x900_60.00 (0x16d)  106.5MHz
        h: width  1440 start 1528 end 1672 total 1904 skew    0 clock   55.9KHz
        v: height  900 start  903 end  909 total  934           clock   59.9Hz 
```I post my lshw too (Display section):
```
 *-display UNCLAIMED
             description: VGA compatible controller
             product: G86 [GeForce 8500 GT]
             vendor: NVIDIA Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller cap_list
             configuration: latency=0
             resources: memory:fa000000-faffffff memory:e0000000-efffffff memory
```I also found out that there shouldn't be an xorg.conf file in /etc/X11/ but i have it, so i post it too, it's pretty short actually:
```
Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection
```what should i do?
Thanks,
Nick00

---

### Post by sandyd on 2012-12-19
Did you install the nvidia drivers from the "Hardware Drivers" utility? The nouveau drivers don't work well with some nvidia cards.

---

### Post by Nick00 on 2012-12-19
I've tried to, but when I rebooted ubuntu just wouldn't start and i was stuck at a black screen. I managed to resolve that by logging in safe mode and the line
```
sudo get-apt purge nvidia*
```

EDIT
now I can choose 1440x900 (16:10) from preferences>monitor, but when I click on apply an error message shows up:
```
GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._gnome_2drr_2derror_2dquark.Code3
```
saying i can't set res to 1440x900 'cause maximum possible resolution is 1280x1024..

---

### Post by sandyd on 2012-12-19
if your installing nvidia drivers, run
```

sudo apt-get install linux-headers-generic linux-headers-$(uname -r)
```
first.

its a known bug

---

### Post by Nick00 on 2012-12-19
> **sandyd said:**
> if your installing nvidia drivers, run
```

sudo apt-get install linux-headers-generic linux-headers-$(uname -r)
```first.

its a known bug

Output:
linux-headers-3.5.0-21-generic is at its most recent version yet
0 updated, 0 installed, 0 remove, 0 not updated

---

### Post by cwsnyder on 2012-12-19
You can try editing your /etc/X11/xorg.conf file to be the following:```
Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1440x900"
#    HorizSync       31.5 - 64.0  # Change these lines to match your
#    VertRefresh     56.0 - 65.0  # monitor and then remove the # at the
#                               # beginning of the line and these remarks
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1440x900@60" 106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync

EndSection

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

Section "Screen"
    Identifier      "Primary Screen"
    Device          "Default Device"
    DefaultDepth    24
    SubSection "Display"
        Virtual 3600 1200
        Depth           24
        Modes   "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
``` and see if that helps, per the Arch wiki.

---

### Post by lordievader on 2012-12-19
A better/easier route to install the nVidia driver would probably be the Jockey (a.k.a. Additional Driver). From a terminal run "jockey-gtk", or search in the system settings application for "Additional Drivers".

Another thing that might be worth a shot is forcing the correct resolutions, take a look at this guide: [http://www.linuxjournal.com/content/guerrilla-tactics-force-screen-mode-ubuntu](http://www.linuxjournal.com/content/guerrilla-tactics-force-screen-mode-ubuntu)

---

### Post by Nick00 on 2012-12-19
Thanks everybody for the answers, but the problem is still here.
I figured out it may be related to the fact that on System settings>Display it says i'm running on a laptop even if I am working on a desktop pc: even

```
sudo laptop-detect -v
```

gives output
```
We're not on a laptop (no relevant hint found)
```

I made a little research and found out this is a known bug too.
Looking for a solution to this one, if I find one myself i will let know in this thread

---

### Post by cwsnyder on 2012-12-29
I had the error on my Ubuntu 13.04 virtual machine install where my display was recognized as a laptop.  I was able to fix it by the following:```
xrandr --output default --gamma 1:1:1 --mode <newmodename>
```Where <newmodename> was the mode defined as in [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) for something different than that available before.  Not only did I get my new resolution, I could select from the Display settings menu from several other resolutions (some which would not work on my LCD monitor).

---

### Post by The Foz on 2013-02-04
Hi Nick00,

Did you ever find a solution to your resolution problem?

I have similar symptoms. I get the same error when trying xrandr to set my resolution: xrandr reports "Failed to change the screen configuration!", and the display settings applet says "The selected configuration for displays could not be applied. required virtual size does not fit available size: requested=(1680, 1050), minimum=(640, 400), maximum=(1280, 1024)." & "GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._gnome_2drr_2derror_2dquark.Code3: required virtual size does not fit available size: requested=(1680, 1050), minimum=(640, 400), maximum=(1280, 1024)". I find this odd, as xrandr reports that the maximum resulution is 1680 x 1050, which is what I am trying to set it to. The only progress that I have achieved is that my desired resolution (1680 x 1050) is now listed by the display settings applet and by xrandr.

I am using an ATI graphics card, which suggests that the root cause for us both is nothing to do with the NVIDIA drivers.

I also have the symptom of the display applet saying that the display is "Laptop". I tried 'sudo laptop-detect -v', with the expected result (We're not on a laptop (no relevant hint found)). The suggested fix for that didn't seem to work.

The output of ' xrandr --verbose' is:
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 400, current 1280 x 1024, maximum 1680 x 1050
default connected 1280x1024+0+0 (0x52) normal (normal) 0mm x 0mm
	Identifier: 0x51
	Timestamp:  18316024
	Subpixel:   no subpixels
	Clones:    
	CRTC:       0
	CRTCs:      0
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
  1280x1024 (0x52)    0.0MHz *current
        h: width  1280 start    0 end    0 total 1280 skew    0 clock    0.0KHz
        v: height 1024 start    0 end    0 total 1024           clock    0.0Hz
  1152x864 (0x53)    0.0MHz
        h: width  1152 start    0 end    0 total 1152 skew    0 clock    0.0KHz
        v: height  864 start    0 end    0 total  864           clock    0.0Hz
  1024x768 (0x54)    0.0MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock    0.0KHz
        v: height  768 start    0 end    0 total  768           clock    0.0Hz
  800x600 (0x55)    0.0MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock    0.0KHz
        v: height  600 start    0 end    0 total  600           clock    0.0Hz
  640x480 (0x56)    0.0MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock    0.0KHz
        v: height  480 start    0 end    0 total  480           clock    0.0Hz
  720x400 (0x57)    0.0MHz
        h: width   720 start    0 end    0 total  720 skew    0 clock    0.0KHz
        v: height  400 start    0 end    0 total  400           clock    0.0Hz
  1680x1050 (0x64)  147.1MHz -HSync +VSync
        h: width  1680 start 1784 end 1968 total 2256 skew    0 clock   65.2KHz
        v: height 1050 start 1051 end 1054 total 1087           clock   60.0Hz

```

---

### Post by aksrana8 on 2013-02-04
Thanks all of you for share your feedback.. This is very helpful information.

---

