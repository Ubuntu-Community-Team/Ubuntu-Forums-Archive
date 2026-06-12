---
title: "Problem after configring nvidia"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by baistaef on 2008-07-12
After i configured nvidia card i can't make the screen resolution more than 1024*768 why is that?
Is there any way possible to make it 1280*1024?

---

### Post by UbuntuNerd on 2008-07-12
go to system > preferences then  screen resolution from the list pick the resolution you want see if that works or did you go there already?

---

### Post by Jim! on 2008-07-12
Is your monitor capable of 1280*1024? If it is then what jperez suggested should do the trick;)

---

### Post by baistaef on 2008-07-12
I did that already and the highest resolution was 1024*768, the list was includes only 1024*768, 800*600 and 640*480
I want to make the screen resolution 1280*1024 how can i do that?

---

### Post by UbuntuNerd on 2008-07-12
were you able to get that resolution before installing ubuntu?

---

### Post by philinux on 2008-07-12
Have you installed manually or via synaptic the app 

nvidia-settings

It has screen res controls .

---

### Post by Jim! on 2008-07-12
Are you even sure your monitor can display resolutions of 1280*1024? If the option to change to said resolution isn't there then I don't think your monitor can display at that resolution. There is a chance it's because your graphics card, what kind of graphics card do you have and is it installed?

---

### Post by UbuntuNerd on 2008-07-12
there is also a way to add that resolution to your xorg config files take a look at this configuration where sombody added that resolution to their xorg files and it worked for them 

Code:

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    RgbPath      "/usr/share/X11/rgb"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/misc"
    FontPath     "/usr/share/fonts/100dpi:unscaled"
    FontPath     "/usr/share/fonts/75dpi:unscaled"
    FontPath     "/usr/share/fonts/TTF"
    FontPath     "/usr/share/fonts/Type1"
EndSection

Section "Module"
    Load  "glx"
    Load  "xtrap"
    Load  "record"
    Load  "GLcore"
    Load  "extmod"
    Load  "dbe"
    Load  "dri"
    Load  "freetype"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    #DisplaySize      330   200    # mm
    Identifier   "Monitor0"
    VendorName   "PTS"
    ModelName    "1911-TLXB"
 ### Comment all HorizSync and VertRefresh values to use DDC:
    HorizSync    30.0 - 80.0
    VertRefresh  56.0 - 75.0
    Option        "DPMS"
    UseModes     "Modes0"
EndSection

Section "Modes"
    Identifier "Modes0"
    Modeline "1680x1050" 181.61 1680 1792 1976 2272 1050 1051 1054 1095
    Modeline "1680x1050" 178.96 1680 1792 1976 2272 1050 1051 1054 1094
    Modeline "1680x1050" 176.48 1680 1792 1976 2272 1050 1051 1054 1094
    Modeline "1600x1024" 168.40 1600 1704 1880 2160 1024 1025 1028 1068
    Modeline "1600x1024" 165.94 1600 1704 1880 2160 1024 1025 1028 1067
    Modeline "1600x1024" 163.64 1600 1704 1880 2160 1024 1025 1028 1067
    Modeline "1600x1000" 164.46 1600 1704 1880 2160 1000 1001 1004 1043
    Modeline "1600x1000" 162.05 1600 1704 1880 2160 1000 1001 1004 1042
    Modeline "1600x1000" 159.80 1600 1704 1880 2160 1000 1001 1004 1042
    Modeline "1400x1050" 151.56 1400 1496 1648 1896 1050 1051 1054 1095
    Modeline "1400x1050" 149.34 1400 1496 1648 1896 1050 1051 1054 1094
    Modeline "1400x1050" 147.27 1400 1496 1648 1896 1050 1051 1054 1094
    Modeline "1280x1024" 134.72 1280 1368 1504 1728 1024 1025 1028 1068
    Modeline "1280x1024" 132.75 1280 1368 1504 1728 1024 1025 1028 1067
    Modeline "1280x1024" 130.91 1280 1368 1504 1728 1024 1025 1028 1067
    Modeline "1440x900" 132.71 1440 1536 1688 1936 900 901 904 939
    Modeline "1440x900" 130.75 1440 1536 1688 1936 900 901 904 938
    Modeline "1440x900" 128.93 1440 1536 1688 1936 900 901 904 938
    Modeline "1280x960" 126.27 1280 1368 1504 1728 960 961 964 1001
    Modeline "1280x960" 124.54 1280 1368 1504 1728 960 961 964 1001
    Modeline "1280x960" 122.69 1280 1368 1504 1728 960 961 964 1000
    Modeline "1366x768" 106.19 1368 1448 1592 1816 768 769 772 801
    Modeline "1366x768" 104.73 1368 1448 1592 1816 768 769 772 801
    Modeline "1366x768" 103.15 1368 1448 1592 1816 768 769 772 800
    Modeline "1280x800" 104.35 1280 1360 1496 1712 800 801 804 835
    Modeline "1280x800" 102.80 1280 1360 1496 1712 800 801 804 834
    Modeline "1280x800" 101.37 1280 1360 1496 1712 800 801 804 834
    Modeline "1152x864" 102.08 1152 1224 1352 1552 864 865 868 901
    Modeline "1152x864" 99.64 1152 1224 1344 1536 864 865 868 901
    Modeline "1152x864" 98.15 1152 1224 1344 1536 864 865 868 900
    Modeline "1280x768" 99.17 1280 1352 1488 1696 768 769 772 801
    Modeline "1280x768" 97.81 1280 1352 1488 1696 768 769 772 801
    Modeline "1280x768" 96.33 1280 1352 1488 1696 768 769 772 800
    Modeline "1024x768" 79.52 1024 1080 1192 1360 768 769 772 801
    Modeline "1024x768" 78.43 1024 1080 1192 1360 768 769 772 801
    Modeline "1024x768" 77.25 1024 1080 1192 1360 768 769 772 800
    Modeline "1280x600" 76.04 1280 1336 1472 1664 600 601 604 626
    Modeline "1280x600" 75.00 1280 1336 1472 1664 600 601 604 626
    Modeline "1280x600" 73.84 1280 1336 1472 1664 600 601 604 625
    Modeline "1024x600" 61.42 1024 1080 1184 1344 600 601 604 626
    Modeline "1024x600" 59.86 1024 1072 1176 1328 600 601 604 626
    Modeline "1024x600" 58.93 1024 1072 1176 1328 600 601 604 625
    Modeline "800x600" 47.53 800 840 920 1040 600 601 604 626
    Modeline "800x600" 46.87 800 840 920 1040 600 601 604 626
    Modeline "800x600" 46.15 800 840 920 1040 600 601 604 625
    Modeline "768x576" 43.52 768 800 880 992 576 577 580 601
    Modeline "768x576" 42.93 768 800 880 992 576 577 580 601
    Modeline "768x576" 42.26 768 800 880 992 576 577 580 600
    Modeline "640x480" 29.84 640 664 728 816 480 481 484 501
    Modeline "640x480" 29.43 640 664 728 816 480 481 484 501
    Modeline "640x480" 29.03 640 664 728 816 480 481 484 501
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPFastWrite"           # [<bool>]
        #Option     "AGPSize"                # <i>
        #Option     "GARTSize"               # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnableDepthMoves"       # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        #Option     "AccelDFS"               # [<bool>]
        #Option     "DDCMode"                # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        #Option     "ColorTiling"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "DynamicClocks"          # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
        #Option     "TVDACLoadDetect"        # [<bool>]
        #Option     "ForceTVOut"             # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "IgnoreLidStatus"        # [<bool>]
    Identifier  "Card0"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "Radeon X1200 Series"
    BusID       "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
        Modes "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
        Modes "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
        Modes "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
        Modes "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
EndSection

---

### Post by baistaef on 2008-07-12
> **Jim! said:**
> Is your monitor capable of 1280*1024? If it is then what jperez suggested should do the trick;)

Yes it is and i use at on windows and even before i configure nvidia with ubuntu

---

### Post by baistaef on 2008-07-12
> **jperez78 said:**
> there is also a way to add that resolution to your xorg config files take a look at this configuration where sombody added that resolution to their xorg files and it worked for them 

Code:

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    RgbPath      "/usr/share/X11/rgb"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/misc"
    FontPath     "/usr/share/fonts/100dpi:unscaled"
    FontPath     "/usr/share/fonts/75dpi:unscaled"
    FontPath     "/usr/share/fonts/TTF"
    FontPath     "/usr/share/fonts/Type1"
EndSection

Section "Module"
    Load  "glx"
    Load  "xtrap"
    Load  "record"
    Load  "GLcore"
    Load  "extmod"
    Load  "dbe"
    Load  "dri"
    Load  "freetype"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    #DisplaySize      330   200    # mm
    Identifier   "Monitor0"
    VendorName   "PTS"
    ModelName    "1911-TLXB"
 ### Comment all HorizSync and VertRefresh values to use DDC:
    HorizSync    30.0 - 80.0
    VertRefresh  56.0 - 75.0
    Option        "DPMS"
    UseModes     "Modes0"
EndSection

Section "Modes"
    Identifier "Modes0"
    Modeline "1680x1050" 181.61 1680 1792 1976 2272 1050 1051 1054 1095
    Modeline "1680x1050" 178.96 1680 1792 1976 2272 1050 1051 1054 1094
    Modeline "1680x1050" 176.48 1680 1792 1976 2272 1050 1051 1054 1094
    Modeline "1600x1024" 168.40 1600 1704 1880 2160 1024 1025 1028 1068
    Modeline "1600x1024" 165.94 1600 1704 1880 2160 1024 1025 1028 1067
    Modeline "1600x1024" 163.64 1600 1704 1880 2160 1024 1025 1028 1067
    Modeline "1600x1000" 164.46 1600 1704 1880 2160 1000 1001 1004 1043
    Modeline "1600x1000" 162.05 1600 1704 1880 2160 1000 1001 1004 1042
    Modeline "1600x1000" 159.80 1600 1704 1880 2160 1000 1001 1004 1042
    Modeline "1400x1050" 151.56 1400 1496 1648 1896 1050 1051 1054 1095
    Modeline "1400x1050" 149.34 1400 1496 1648 1896 1050 1051 1054 1094
    Modeline "1400x1050" 147.27 1400 1496 1648 1896 1050 1051 1054 1094
    Modeline "1280x1024" 134.72 1280 1368 1504 1728 1024 1025 1028 1068
    Modeline "1280x1024" 132.75 1280 1368 1504 1728 1024 1025 1028 1067
    Modeline "1280x1024" 130.91 1280 1368 1504 1728 1024 1025 1028 1067
    Modeline "1440x900" 132.71 1440 1536 1688 1936 900 901 904 939
    Modeline "1440x900" 130.75 1440 1536 1688 1936 900 901 904 938
    Modeline "1440x900" 128.93 1440 1536 1688 1936 900 901 904 938
    Modeline "1280x960" 126.27 1280 1368 1504 1728 960 961 964 1001
    Modeline "1280x960" 124.54 1280 1368 1504 1728 960 961 964 1001
    Modeline "1280x960" 122.69 1280 1368 1504 1728 960 961 964 1000
    Modeline "1366x768" 106.19 1368 1448 1592 1816 768 769 772 801
    Modeline "1366x768" 104.73 1368 1448 1592 1816 768 769 772 801
    Modeline "1366x768" 103.15 1368 1448 1592 1816 768 769 772 800
    Modeline "1280x800" 104.35 1280 1360 1496 1712 800 801 804 835
    Modeline "1280x800" 102.80 1280 1360 1496 1712 800 801 804 834
    Modeline "1280x800" 101.37 1280 1360 1496 1712 800 801 804 834
    Modeline "1152x864" 102.08 1152 1224 1352 1552 864 865 868 901
    Modeline "1152x864" 99.64 1152 1224 1344 1536 864 865 868 901
    Modeline "1152x864" 98.15 1152 1224 1344 1536 864 865 868 900
    Modeline "1280x768" 99.17 1280 1352 1488 1696 768 769 772 801
    Modeline "1280x768" 97.81 1280 1352 1488 1696 768 769 772 801
    Modeline "1280x768" 96.33 1280 1352 1488 1696 768 769 772 800
    Modeline "1024x768" 79.52 1024 1080 1192 1360 768 769 772 801
    Modeline "1024x768" 78.43 1024 1080 1192 1360 768 769 772 801
    Modeline "1024x768" 77.25 1024 1080 1192 1360 768 769 772 800
    Modeline "1280x600" 76.04 1280 1336 1472 1664 600 601 604 626
    Modeline "1280x600" 75.00 1280 1336 1472 1664 600 601 604 626
    Modeline "1280x600" 73.84 1280 1336 1472 1664 600 601 604 625
    Modeline "1024x600" 61.42 1024 1080 1184 1344 600 601 604 626
    Modeline "1024x600" 59.86 1024 1072 1176 1328 600 601 604 626
    Modeline "1024x600" 58.93 1024 1072 1176 1328 600 601 604 625
    Modeline "800x600" 47.53 800 840 920 1040 600 601 604 626
    Modeline "800x600" 46.87 800 840 920 1040 600 601 604 626
    Modeline "800x600" 46.15 800 840 920 1040 600 601 604 625
    Modeline "768x576" 43.52 768 800 880 992 576 577 580 601
    Modeline "768x576" 42.93 768 800 880 992 576 577 580 601
    Modeline "768x576" 42.26 768 800 880 992 576 577 580 600
    Modeline "640x480" 29.84 640 664 728 816 480 481 484 501
    Modeline "640x480" 29.43 640 664 728 816 480 481 484 501
    Modeline "640x480" 29.03 640 664 728 816 480 481 484 501
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPFastWrite"           # [<bool>]
        #Option     "AGPSize"                # <i>
        #Option     "GARTSize"               # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnableDepthMoves"       # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        #Option     "AccelDFS"               # [<bool>]
        #Option     "DDCMode"                # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        #Option     "ColorTiling"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "DynamicClocks"          # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
        #Option     "TVDACLoadDetect"        # [<bool>]
        #Option     "ForceTVOut"             # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "IgnoreLidStatus"        # [<bool>]
    Identifier  "Card0"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "Radeon X1200 Series"
    BusID       "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
        Modes "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
        Modes "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
        Modes "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
        Modes "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes "1680x1050" "1600x1024" "1600x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
EndSection
What file should i edit to insert the new resolution?

---

### Post by baistaef on 2008-07-15
Pleas what file should i edit to insert the new resolution?

---

### Post by baistaef on 2008-07-15
Anybody??

---

### Post by philinux on 2008-07-15
> **philinux said:**
> Have you installed manually or via synaptic the app 

nvidia-settings

It has screen res controls .

Have you got nvidia-settings installed.

---

### Post by baistaef on 2008-07-15
> **philinux said:**
> Have you got nvidia-settings installed.

I installed it and managed to change from it thanks for your help guys.

---

