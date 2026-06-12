---
title: "nvidia-settings is not detecting my external display (but the display works)"
date: 2018-03-26
forum: New to Ubuntu
---

### Post by desaroger on 2018-03-26
Hi! This is my first post here so if I made something wrong (like posting on a bad forum or something) please let me know!

I have a Lenovo laptop with 16.04 and two graphics cards (as far as I know): Nvidia 1050 and an integrated intel.
I installed the proprietary nvidia drivers and everything works fine. My external display, connected through hdmi, works perfect.

The problem comes when I wanted to use the nvidia-settings to customize some settings. It only detects my integrated laptop screen, and it needs to show the hdmi display too [like this photo I found on a tutorial]("http://karuppuswamy.com/wordpress/wp-content/uploads/2012/04/Screenshot-from-2012-04-28-222451.png").

Also, extremely noob question:
When I have two graphic cards, what does each one do? My fear is that my integrated screen works with the nvidia card but the hdmi port works with the integrated intel card, I don't know if this is even possible :confused:


Please ask me any info you need, thanks! Also thanks to these forums as It solved a lot of issues I had with ubuntu through years!


[SIZE=6][B]Info:
[/B][/SIZE](every screenshot is made with the hdmi port connected to my external display)

Here we can see I have two graphic cards. Also we see I am using the nvidia proprietary drivers:
```
desaroger@lenovo:~$ sudo lshw -numeric -C display
  *-display               
       description: 3D controller
       product: NVIDIA Corporation [10DE:1C8D]
       vendor: NVIDIA Corporation [10DE]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: irq:324 memory:a3000000-a3ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:5000(size=128)
  *-display
       description: VGA compatible controller
       product: Intel Corporation [8086:591B]
       vendor: Intel Corporation [8086]
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:321 memory:a2000000-a2ffffff memory:b0000000-bfffffff ioport:6000(size=64) memory:c0000-dffff
```


The ubuntu Displays settings shows my two screens:
[https://ibin.co/3wFMQTRMLpqR.png](https://ibin.co/3wFMQTRMLpqR.png)


Nvidia only shows my integrated screen:
[https://ibin.co/3wFNoKl3T8Aa.png](https://ibin.co/3wFNoKl3T8Aa.png)

Xrandr shows my two displays. Also shows another HDMI-1-2 that I have no idea what is, as my laptop only have 1 hdmi (also no vga port):
```
desaroger@lenovo:~$ xrandr
Screen 0: minimum 8 x 8, current 3840 x 1080, maximum 32767 x 32767
eDP-1-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080     60.02*+  59.93  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   960x600       60.00  
   960x540       59.99  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   800x512       60.17  
   700x525       59.98  
   640x512       60.02  
   720x450       59.89  
   640x480       60.00    59.94  
   680x384       59.80    59.96  
   576x432       60.06  
   512x384       60.00  
   400x300       60.32    56.34  
   320x240       60.05  
HDMI-1-1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080     60.00*+  50.00    59.94  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     59.88  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    60.00  
   832x624       74.55  
   800x600       75.00    60.32  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  
DP-1-1 disconnected (normal left inverted right x axis y axis)
HDMI-1-2 disconnected (normal left inverted right x axis y axis)



```

---

### Post by wildmanne39 on 2018-03-26
Hello and welcome to the forum!

Please use the attachment facility by clicking on the paperclip or use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

When posting code, instead of posting code as an image please post the text using code tags - if you are using New Reply button - highlight text and use the # button in the text box header. If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Thanks

---

### Post by desaroger on 2018-03-27
Thank you wildmanne39 for your advice! And also for editing my post :D

I changed the two terminal screenshots with the [code] tag.

---

