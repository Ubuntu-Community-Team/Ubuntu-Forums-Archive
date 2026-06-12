---
title: "display problem"
date: 2012-10-29
forum: New to Ubuntu
---

### Post by TrikIops on 2012-10-29
hello all

 i  cant remember what version it was but about 6 months ago i tried  switching to lubuntu as i figured it would work best with the amount of  ram i have. lubuntu installed perfectly but when the computer restarted  all i had was the lubuntu wallpaper with a small amount of taskbar  showing at the bottom.
[[IMG]http://t.imgbox.com/adbqVHn7.jpg[/IMG]]("http://imgbox.com/adbqVHn7") [[IMG]http://t.imgbox.com/abxlwnNR.jpg[/IMG]]("http://imgbox.com/abxlwnNR") 

i was finally able to raise the taskbar but instead of it going from one side of the screen to the other there was a space on each side.
[[IMG]http://t.imgbox.com/acnrVdnj.jpg[/IMG]]("http://imgbox.com/acnrVdnj") 

the other problem i noticed was the font was extremely small in the start menu and taskbar, yet the display setting box was readable. another site i found said to do something in the terminal with xrandr, despite it not working i couldnt even see what i was typing anyways the text was so small (picture below is not blurry or zoomed in to much, thats just how small the text was)
[[IMG]http://t.imgbox.com/acqJ1GAP.jpg[/IMG]]("http://imgbox.com/acqJ1GAP") 

i am about to do a clean install of xp but i would like to get away from windows. i have also tried dsl and SliTaz both had tiny text. 

do any of you guys or gals see anything that might be conflicting with lubuntu causing me to have display problems? amd athlon maybe??? 

[[IMG]http://t.imgbox.com/abu6ohl3.jpg[/IMG]]("http://imgbox.com/abu6ohl3") [[IMG]http://t.imgbox.com/acsApPgT.jpg[/IMG]]("http://imgbox.com/acsApPgT") [[IMG]http://t.imgbox.com/acxyRTHT.jpg[/IMG]]("http://imgbox.com/acxyRTHT") [[IMG]http://t.imgbox.com/acztqwpi.jpg[/IMG]]("http://imgbox.com/acztqwpi")

  thank you

images hosted by imgbox with family safe content selected

---

### Post by shreepads on 2012-10-29
If I understood correctly you are unable to run any LiveCD on your system, or rather there is no display when you run a LiveCD. Is that correct?

If yes, please post complete details of your system in text, Imgbox is blocked for me...

---

### Post by TrikIops on 2012-10-29
[COLOR=black]hello shreepads - the problem is after i install lubuntu everything is off the screen and text is very small. adjusting the screen resolution in lubuntus display settings menu does not fix it.

[COLOR=blue]Operating System[/COLOR][/COLOR]
    Microsoft Windows XP Home Edition 32-bit SP3
[COLOR=blue]CPU[/COLOR]
    AMD Athlon XP
    Barton 0.13um Technology
[COLOR=blue]RAM[/COLOR]
    1.00 GB DDR @ 200MHz (2.5-3-2-7)
[COLOR=blue]Motherboard[/COLOR]
    ASUSTek Computer INC. Kelut (Socket A)    
[COLOR=blue]Graphics[/COLOR]
    FLM-323B (1024x768@60Hz)
    VIA/S3G UniChrome IGP
[COLOR=blue]Hard Drives[/COLOR]
    75GB SAMSUNG SP0802N (PATA)    
[COLOR=blue]Optical Drives[/COLOR]
    LITE-ON COMBO SOHC-4832K
    DVD-16X DVD-ROM BDV316E
[COLOR=blue]Audio[/COLOR]
    Realtek AC'97 Audio for VIA Audio Controller


[COLOR=blue]Monitor[/COLOR]
      Name ______________FLM-323B on VIA/S3G UniChrome IGP
      Current Resolution ___1024x768 pixel
      Work Resolution _____1024x768 pixels
      Monitor Width _______1024
            Monitor Height ______768
            Monitor BPP ________32 bits per pixel
            Monitor Frequency ___60 Hz
            Device  ____________                                                 \\.\DISPLAY1\Monitor0

        [COLOR=blue]VIA/S3G UniChrome IGP[/COLOR]
                                Memory               _______64 MB
                                Memory type       ___2
                                Driver version __    6.14.10.0194-16.94.42.03
        [COLOR=blue]OpenGL[/COLOR]
                                Version ______1.2
                                Vendor ______   S3 Graphics
                                Renderer    _____VIA/S3G UniChrome IGP/MMX/K3D
            GLU Version    ___1.2.2.0 Microsoft Corporation

[COLOR=blue]Motherboard[/COLOR]
    Manufacturer __________ASUSTek Computer INC.
    Model ________________Kelut (Socket A)
    Chipset Vendor ________VIA
    Chipset Model _________KM400
    Chipset Revision _______00
    Southbridge Vendor ____VIA
    Southbridge Model  ____ VT8237
    Southbridge Revision  ___00
    
        [COLOR=blue]BIOS[/COLOR]
            Brand ___Phoenix Technologies, LTD
            Version _3.03
            Date ___02/09/2004

):P

---

### Post by squakie on 2012-10-29
I don't know exactly what is going on, but I can tell you a couple of things:

[LIST]
[*]The VIA/S3G Unichrome is not a very good IGP
[*]When I had one of these several years ago, the only way I could get it to even try to work was with the OpenChrome driver, but it still wasn't very good.
[*]Don't look to be doing much in the way of games, compiz or other graphics applications with this adapter
[/LIST]
Just my experience from several years ago now.  I can't imagine they've done any more work on a VIA/S3G driver for linux.  I had problems with the apparent desktop size being way outside what showed on my monitor.  As a result, some printing was also very hard to read.  I think right now you are fighting a battle between resolution selected and what your monitor (as defined to linux, or perhaps more accurately, not defined to linux) will support for resolution at certain clock rates.

---

### Post by shreepads on 2012-10-30
Have a look at this...

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

You could try the proprietary VIA drivers mentioned in the page.

Also see this: [http://phoronix.com/forums/showthread.php?57627-Via-vt1632a](http://phoronix.com/forums/showthread.php?57627-Via-vt1632a)

You could try with Puppy Linux...

---

### Post by amjjawad on 2012-10-31
Hello and Welcome to Ubuntu Forum,

Thanks for choosing and using Lubuntu. I'm one of Lubuntu Team Members and I'd like to help you as much as possible.

Well, first of all, I couldn't open the attached images at all. Would you please use: [www.tinypic.com](www.tinypic.com) instead? or just attach the files here:

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8046[/IMG]

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8047[/IMG]

Second of all, do you know that you can actually change the font? Yes indeed and it is quite easy:

To change the font of your LXPanel:
1- Right Click on the Panel
2- Panel Settings
3- Geometry
4- Done

To change the font of other components:
1- Menu
2- Preferences
3- Openbox Configuration Manager
4- Please see the attached screenshot.

Oh and by the way, that is 12.04 :)

---

