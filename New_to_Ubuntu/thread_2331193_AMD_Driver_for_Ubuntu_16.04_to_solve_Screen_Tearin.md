---
title: "AMD Driver for Ubuntu 16.04 to solve Screen Tearing"
date: 2016-07-19
forum: New to Ubuntu
---

### Post by yash047 on 2016-07-19
Hello All,

Can I install the [AMD Graphic Drivers]("http://support.amd.com/en-us/download/desktop?os=Ubuntu%20x86%2064") for Ubuntu 14.04 on Ubuntu 16.04? I have the R7 260X, 8GB memory and Core i3 2120. If not which driver should I install? I wish to enable vsync as there are screen tearing when I watch movies on VLC.

---

### Post by grahammechanical on 2016-07-19
I doubt very much that you can do that. AMD is not providing a proprietary video driver for Ubuntu 16.04 because Ubuntu 16.04 uses X Server version 1.18 and the AMD proprietary video drivers do not support X Server 1.18. If AMD did not want to do the work of upgrading the proprietary video driver to work with X Server 1.18, then I do not see how an older version of the proprietary video driver would work with X Server 1.18.

[https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/](https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/)

> The fglrx driver is now deprecated in 16.04, and we recommend its open  source alternatives (radeon and amdgpu). AMD put a lot of work into the  drivers, and we backported kernel code from Linux 4.5 to provide a  better experience.

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

Regards.

---

### Post by yash047 on 2016-07-19
Can you tell me how I can enable vsync?

---

### Post by Mark Phelps on 2016-07-19
I'm using an R7 240x, whi\ch can't be very different from your 260x, and VLC works fine without tearing.

My vide settings are: 
Display:
 - Accelerated video output (overlay)
- Windows decorations (checked)
Video:
Deinterlacing - off

Advanced Video settings:
General video settings ---------------
Enable video
Embedded video
Drop late frames
Skip frames
Key press events
Mouse events
Overlay video output
Disable screensaver
Show media title on video
Show video title for 5000 milliseconds
Position of video title: Bottom
Hide cursor and fullscreen controller after 1000 milliseconds
Window properties --------------------
Video auto scaling
Fix HDTV height
Window decorations
Deinterlace: off
Deinterlace mode: Blend

---

### Post by yash047 on 2016-07-21
My settings on VLC were exactly the same, I restarted my computer and there was no screen tearing.

---

