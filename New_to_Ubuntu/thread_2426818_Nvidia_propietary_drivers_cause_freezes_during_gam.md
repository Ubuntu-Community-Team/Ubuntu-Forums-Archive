---
title: "Nvidia propietary drivers cause freezes during gaming sessions"
date: 2019-09-13
forum: New to Ubuntu
---

### Post by davidbond12 on 2019-09-13
When I play Team Fortress 2, and War Thunder and try to pick class/vehicle,  computer freezes and I can't alt+f2 to go command line or ctrl + alt + delete to log out. I have to hold down power button to restart computer

I think it's the proprietary NVIDIA driver I'm using. Open source drivers cause very low frame rates during gaming sessions.

I have NVIDIA gtx 750 ti GB sc

4GB Ram

Intel 3550

I know its not because of low ram, because I was able to play team fortress 2 on Intergrated graphics, with mastercomfig easy.

I went to ksystemlog and I think these errors were from the freeze.


 9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr: Connected output 449 to CRTC 442
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper: Detected XRandR 1.5
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper: Event Base:  89
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper: Event Error:  147
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr: XRandR::setConfig
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr: Requested screen size is QSize(1920, 1200)
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr: Needed CRTCs:  1
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr: Actions to perform:
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     Primary Output: true
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:         Old: 446
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:         New: 449
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     Change Screen Size: false
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     Disable outputs: false
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     Change outputs: false
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     Enable outputs: false
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr: RRSetOutputPrimary
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     New primary: 449
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr: XRandR::setConfig done!
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper: RRNotify_OutputChange
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Output:  446
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     CRTC:  0
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Mode:  0
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Rotation:  "Rotate_0"
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Connection:  "Disconnected"
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Subpixel Order:  0
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper: RRNotify_OutputChange
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Output:  449
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     CRTC:  442
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Mode:  450
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Rotation:  "Rotate_0"
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Connection:  "Connected"
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Subpixel Order:  0
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper: RRScreenChangeNotify
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Window: 27262981
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Root: 481
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Rotation:  "Rotate_0"
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Size ID: 0
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Size:  1920 1200
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     SizeMM:  493 302
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper: RRNotify_OutputChange
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Output:  446
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     CRTC:  0
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Mode:  0
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Rotation:  "Rotate_0"
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Connection:  "Disconnected"
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Subpixel Order:  0
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper: RRNotify_OutputChange
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Output:  449
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     CRTC:  442
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Mode:  450
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Rotation:  "Rotate_0"
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Connection:  "Connected"
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xcb.helper:     Subpixel Order:  0
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr: XRandROutput 446 update
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     m_connected: 1
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     m_crtc QObject(0x0)
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     CRTC: 0
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     MODE: 0
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     Connection: 1
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     Primary: false
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr: Output 446 : connected = false , enabled = false
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr: XRandROutput 449 update
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     m_connected: 0
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     m_crtc XRandRCrtc(0x555f7ed94c50)
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     CRTC: 442
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     MODE: 450
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     Connection: 0
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     Primary: true
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr: Output 449 : connected = true , enabled = true
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr: XRandROutput 446 update
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     m_connected: 1
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     m_crtc QObject(0x0)
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     CRTC: 0
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     MODE: 0
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     Connection: 1
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     Primary: false
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr: Output 446 : connected = false , enabled = false
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr: XRandROutput 449 update
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     m_connected: 0
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     m_crtc XRandRCrtc(0x555f7ed94c50)
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     CRTC: 442
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     MODE: 450
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     Connection: 0
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr:     Primary: true
9/13/19 5:23 PM    org.kde.KScreen    kscreen.xrandr: Output 449 : connected = true , enabled = true

---

### Post by Autodave on 2019-09-14
It might not be that you have too little RAM, but your RAM could be going bad, overheating, etc.  I would suggest running memtest and see what that shows.

Are all of your fans clean and operating properly?  Do you need higher flow fans?  Putting a good GPU in an otherwise "simple" computer can cause stress to everything other than the GPU.  If you think that heat buildup could be an issue, remove the side cover first and see if that helps.  You could also place a small fan to blow into the inside of the machine.

Most PCs that I see are just horribly dirty.  The cooling fins on the CPU are sometimes so bad that I get my compressor out to blow the dirt out of them because the compressed air cans don't have enough pressure.  (Just make sure that you hold the fan blade so that the high flow rate doesn't cause damage to it.)

---

### Post by mastablasta on 2019-09-16
psensor application will show temp.

how did you install the drivers?

---

