---
title: "How can I change the display resolution of my second monitor?"
date: 2016-08-08
forum: New to Ubuntu
---

### Post by usbpc on 2016-08-08
I have already looked into the system preferences and it dosen't list the native resolution of 1280x1024 that my second monitor has. I have already tried a lot of things, so let me just copy over what I did from [askubuntu]("http://askubuntu.com/q/809469/579074"):

[SIZE=6]Short explanation:[/SIZE]


The problem in short is that changing my display resolution to what I want it to be fails, but works in Windows. I tried using xrandr and that failed with a "[FONT=courier new]BadMatch"[/FONT] error. And after that I tried to create an xorg.conf file with "[FONT=courier new]X -configure[/FONT]" in root shell, but that failed with the error "[FONT=courier new]Number of created screens does not match number of detected devices. Configuration failed.[/FONT]" **How can I cange my screen resolution?**


[SIZE=6]Long explanation:[/SIZE]


[SIZE=5]My Setup[/SIZE]
I want to start with that I'm new to ubuntu and just installed the system and the nvidia driver following [these]("http://askubuntu.com/a/700613/579074") steps And now the system specs I think are relevant:


    ```
$ lsb_release -a
    No LSB modules are available.
    Distributor ID:    Ubuntu
    Description:    Ubuntu 16.04.1 LTS
    Release:    16.04
    Codename:    xenial
```


CPU: i5-4460  
GPU: GTX 970  
1. Monitor: acer M230HDL (works perfectly)  
2. Monitor: Philips 190S8 (works with wrong resolution) [Manual with a lot of information.]("http://linfotech.co.uk/schematics/Philips/Philips%20190s8_190v8.pdf")


[SIZE=5]First Try[/SIZE]


1.


    ```
$ cvt 1280 1024 60   
    # 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
    Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```
2.


    ```
$ xrandr --newmode "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
```
3.


    ```
$ xrandr
    Screen 0: minimum 8 x 8, current 3072 x 1080, maximum 16384 x 16384
    DVI-I-0 disconnected (normal left inverted right x axis y axis)
    DVI-I-1 connected 1152x864+1920+0 (normal left inverted right x axis y axis) 0mm x 0mm
       1024x768      60.00 +
       1360x768      59.96    59.80  
       1152x864      60.00* 
       800x600       72.19    60.32    56.25  
       680x384       59.96    59.80  
       640x480       59.94  
       512x384       60.00  
       400x300       72.19  
       320x240       60.05  
    HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 509mm x 286mm
       1920x1080     60.00*+  60.00    59.94    50.00    49.95    60.00    50.04  
       1680x1050     59.95  
       1280x1024     75.02    60.02  
       1280x720      60.00    59.94    50.00  
       1152x864      75.00  
       1024x768      75.03    70.07    60.00  
       800x600       75.00    60.32    56.25  
       720x576       50.00    50.08  
       720x480       59.94  
       640x480       75.00    72.81    59.94    59.93  
    DP-0 disconnected (normal left inverted right x axis y axis)
    DP-1 disconnected (normal left inverted right x axis y axis)
    DP-2 disconnected (normal left inverted right x axis y axis)
    DP-3 disconnected (normal left inverted right x axis y axis)
    DP-4 disconnected (normal left inverted right x axis y axis)
    DP-5 disconnected (normal left inverted right x axis y axis)
      1280x1024_60.00 (0x30f) 108.880MHz -HSync +VSync
            h: width  1280 start 1360 end 1496 total 1712 skew    0 clock  63.60KHz
            v: height 1024 start 1025 end 1028 total 1060           clock  60.00Hz
```


4.


    ```
$ xrandr --addmode DVI-I-1 1280x1024_60.00
    X Error of failed request:  BadMatch (invalid parameter attributes)
    Major opcode of failed request:  140 (RANDR)
    Minor opcode of failed request:  18 (RRAddOutputMode)
    Serial number of failed request:  47
    Current serial number in output stream:  48
```


[SIZE=5]Second try[/SIZE]


 1. Boot into root shell.
 2. Make / read-write `mount -o remount,rw /`  
 3. ```
$ X -configure
        some output (will add if asked)
        Number of created screens does not match number of detected devices. Configuration failed.
```


[SIZE=5]The Question[/SIZE]
[B]How the hell do I  
a) get a modeline that will work with my second monitor?  
b) get a xorg.conf that I can edit so that I can change the resolution in there?[/B]

---

