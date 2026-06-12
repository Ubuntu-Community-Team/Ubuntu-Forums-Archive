---
title: "Intel GMA X3100 issues"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by mike-smith260466 on 2013-08-22
Hi.

Please bear with me if this has been covered before, I am new to this and there are so many threads to look through I could spend forever just looking to see if anyone has had the same problem.

I have an MSI PR600 Laptop which has integrated graphics provided via Intel GMA X3100.

The system came with Windows Vista pre-installed. I have now set up the laptop to dual boot with Ubuntu 13.04.

The system appears to operate properly and I am able to get a good resolution picture on both the laptop screen and my Samsung Plasma TV however I have had an issue with the brightness on my laptop screen flickering. I have noticed many others having the same problem but have not seen a solution.

If I go to** System Settings** then under the System heading select **Details** I am given the following information under **Overview**...

Memory          2.0Gib
Processor        Intel® Core™2 Duo CPU T7100 @ 1.80GHz × 2
Graphics         Intel® 965GM x86/MMX/SSE2
OS type          32-bit
Disk               444.9 GB

Selecting **Graphics** gives the following...

Driver            Intel® 965GM x86/MMX/SSE2
Experience     Standard

One thread mentioned disabling dithering but I can find no opton for this in the system settings. The same thread mentioned that if this was not available then check the video driver being used in the /etc/x11/xorg.conf file.

When I go to the relevent folder I find 8 files as follows...

1. default-display-manager (Text file)
2. rgb.txt (Text file)
3. X (Link to Unknown)
4. Xreset (Program)
5. Xsession (Program)
6. Xsession.options (Text file)
7. XvMCConfig (Text file)
8. Xwrapper.config (Text file)

I have selected the option to view hidden files but there does not appear to be an xorg.conf file in this folder. Am I missing something?

I am also experiencing dreadful refresh rates when playing any 3d games.

Help would be gratefully appreciated.

If any other information is required then Please let me know.

Thanks.

Mike

---

### Post by mastablasta on 2013-08-22
there is no xorg.conf by default but you can create one: [http://askubuntu.com/questions/217758/how-to-make-an-xorg-conf-file](http://askubuntu.com/questions/217758/how-to-make-an-xorg-conf-file)

the chip is nothing special. and also the driver might be poor. one possibel solution is upgrading them via xorg edgers PPA.

another thing to consider is that Unity in Ubuntu uses 3D effect and hardware acceleration. perhaps you would get better results with something like Xubuntu or gnome classic.

---

### Post by mike-smith260466 on 2013-08-23
Mastablasta, thanks for the help. After reading your reply I decided (albeit raher ill-fatedly) to generate an xorg.conf file following the instructions given in the thread that you pointed me to. The process completed successfully but causing my system to slow down DRAMATICALLY!

When checking via **System Settings** I noticed that the **graphics** driver was now being reported as

Graphics        Gallium 0.4 on llvmpipe (LLVM 3.2, 128 bits)

The xorg.conf file is as below...


Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "DefaultRefresh"         # [<bool>]
        #Option     "ModeSetClearScreen"     # [<bool>]
    Identifier  "Card5"
    Driver      "vesa"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen2"
    Device     "Card2"
    Monitor    "Monitor2"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen3"
    Device     "Card3"
    Monitor    "Monitor3"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen4"
    Device     "Card4"
    Monitor    "Monitor4"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen5"
    Device     "Card5"
    Monitor    "Monitor5"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

I do not appear to have the correct permissions to alter or delete the file (plus I imagine just deleting the file would only cause further problems) so how do I go about reverting to the original driver?

I appreciate what you said about the alternative Xubuntu but other than 3D gaming (which I don't do much of anyway) and the flickering brightness, I am more than happy with the way my system operates. I have no problems with unity, with wobbly windows and other effects working at full speed. The only thing I could not enable was 'Cube' but I imagine that may be due to a lack of hardware acceleration on this chipset? Again as already mentioned I could find no options for the graphics driver when looking for dithering (which apparently can cause the flickering I'm experiencing), which is why I asked for help in the first place.

I have noticed that there is now an updated intel driver (which supports my chipset) in the software centre. I have installed this hoping that it would solve the new problem but to no avail and System Settings still shows the graphics driver as being Gallium.

I appreciate the time and effort given to help me as a newbie can be a bit tedious but was wondering if you could help again. I need instructions on how to revert back to the original driver and then I will just live with the flickering.

Thanks again.

Mike

---

