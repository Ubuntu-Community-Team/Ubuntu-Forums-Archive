---
title: "Not possible to set up dual monitors"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by hatrack on 2008-11-08
Hi All !

This message was originally posted last night as a continuation of the original thread but it is not appearing as a "New Post" (because the original thread is now so old ?).
 
I have been trying for some two weeks to set up a simple dual-monitor configuration on a dual-boot machine running Win XP/Ubuntu 8.04. (Please see my thread, "Newbie needs help with dual monitors"). All I need is to spread my desktop across the two monitors. 

After many abortive attempts, I decided to completely re-install Ubuntu so that the drivers available were known to be free from corruption. Even after all this work, it is absolutely impossible to get a dual-monitor set-up running. When this is specified in xorg.conf, the machine defaults into a low-res mode. An example of the xorg.conf. files used is  --

```

# xorg.conf to drive twin monitors -- Originally created 27.10.2008
# Modified 05.11.2008

# For Ubuntu Ver: 8.04, running on Dell GX-520: IGb RAM.
# Main monitor - TFL 19" connected to Intel 82945G on motherboard
# Second monitor - 17" CRT connected to Radeon 7000-series grahics card in PCI slot

# Standard info ---
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "gb"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

# Identifying & setting up dual monitors -- Modified
# Device No.1
Section "Device"
    Identifier    "Intel 82945G"
    Driver        "Intel"
    BusID        "PCI: 0:2:0"
EndSection

# Device No.2
Section "Device"
    Identifier    "Radeon 7000"
    Driver        "ati"
    BusID        "PCI: "4:0:0"
EndSection

# Note -- Various names have been tried to identify the driver native to Ubuntu - the above is one example.

# Monitor No.1
Section "Monitor"
    Identifier    "Main Monitor"
    Option         "DPMS"
    HorizSync    28-80
    VertRefresh    43-75
EndSection

# Monotor No.2
Section "Monitor"
    Identifier    "Second Monitor"
    Option         "DPMS"
    HorizSync    28-80
    VertRefresh    43-75
EndSection

# Info for First monitor --
# Screen No.1
Section "Screen"
    Identifier     "Default Screen"
    Monitor        "Main Monitor"
    Device        "Intel 82945G"
    DefaultDepth    24

        SubSection "Display"    
            Depth    24
            Modes    "1024x768"
        End Subsection
EndSection

# Info for Second monitor --
# Screen No.2
Section "Screen"
    Identifier    "Second Screen"
    Monitor        "Second Monitor"
    Device        "Radeon 7000"
    DefaultDepth    24
    
        SubSection "Display"    
            Depth    24
            Modes    "1024x768"
    End Subsection
EndSection

# Additional info --
Section "ServerFlags"
    Option "Xinerama" "true"
EndSection

# Specify position of two monitors relative to each other
Section "ServerLayout"
    Identifier    "Twin Head"
    Screen        "Default Screen"
    Screen        "Second Screen" LeftOf  "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

```During one of my last runs, I noticed that when I start Nautilus, it throws up the following message, although it subsequently starts and runs satifactorily --

```

** (nautilus:6122): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```Questions ---
[1]  Is this relevant to my problem ?
[2]  Can anyone please tell me how to enable sharing ? I do not actually need to share files on my stand-alone computer but, if it is indeed needed to allow dual monitors to work, then I need to know how to enable it. I have searched this forum and the three books on Ubuntu that I have but (in my ignorance ! ) nothing seems relevant.

I am getting thoroughly frustrated by this whole business, so any advice will be most gratefully received.

Best regards to all ...

---

### Post by ohzopants on 2008-11-10
From what I can tell from your xorg.conf your 2 screens are connected to 2 differents video cards, is that correct?

If that is the case, I don't think it can be done.

---

### Post by Bölvaður on 2008-11-10
> **hatrack said:**
> 
```

# Identifying & setting up dual monitors -- Modified
# Device No.1
Section "Device"
    Identifier    "Intel 82945G"
    Driver        "Intel"
    BusID        "PCI: 0:2:0"
EndSection

# Device No.2
Section "Device"
    Identifier    "Radeon 7000"
    Driver        "ati"
    BusID        "PCI: "4:0:0"
EndSection

```

So device number 1 which perhaps is connected to left monitor is connected to Intel graphical card... my guess is that it is either the integrated card or your ati card is wrongly identified.

Are you sure this card allows dual monitor setup? I had very similar card but I just cant remember if I could have 2.

You could take a backup of the file and change device number 1 to match the driver and identifier... but you would have to know the busID for it to work :-/   are you sure it is correctly connected or if it is correctly detected with only 1 monitor connected at a time.

Please send us how the file will be when you have vga plugged and then when you have DVI. So we can taka a closer look of what is going wrong.

---

### Post by hatrack on 2008-11-10
Thank you very much for your reply ... I'm beginning to despair of ever cracking this problem !

OK ... I do indeed have two graphics "devices" ... the first (which I call Main Monitor) is an Intel chip integral with the motherboard. This only has one outlet. The second device is a Radeon 7000 card. This has the normal VGA outlet plus another female outlet consisting or an array of 24 pins plus (to one side) 4 others arranged in the shape of a cross. I presume that this is what you mean when you speak of a DVI outlet ? I have never used this since I have been running MS software until converting to "Hardy" about 4-6 weeks ago.

At present, my computer is set up for dual-boot (Win XP/Ubuntu). Under Win XP, the configuration of two graphics devices and two monitors works perfectly to give a dual-monitor set-up. Under "Hardy", I get output from the Intel chip only.

Using the "lspci" command, I have determined the BusID values for both devices and included this information into the xorg.conf file, which I have edited  extensively over the past weeks. When I re-installed "Hardy", this automatically generated a minimal xorg.conf file, as follows ---
```

# THIS IS THE ORIGINAL FILE GENERATED BY UBUNTU @ INSTALLATION


# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "gb"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection

```An example of the xorg.conf file used in an attempt to run dual monitors is ---
```

# xorg.conf to drive twin monitors -- Originally created 27.10.2008
# Modified 09.11.2008

# For Ubuntu Ver: 8.04, running on Dell GX-520: IGb RAM.
# Main monitor - TFL 19" connected to Intel 82945G on motherboard
# Second monitor - 17" CRT connected to Radeon 7000-series grahics card in PCI slot

# Standard info ---
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "gb"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

# Identifying & setting up dual monitors -- Modified
# Device No.1
Section "Device"
    Identifier    "Intel 82945G"
    Driver        "Intel"
    BusID        "PCI: 0:2:0"
EndSection

# Device No.2
Section "Device"
    Identifier    "Radeon 7000"
    Driver        "radeon"
    BusID        "PCI: 4:0:0"
EndSection

# Monitor No.1
Section "Monitor"
    Identifier    "Main Monitor"
    Option         "DPMS"
    HorizSync    28-80
    VertRefresh    43-75
EndSection

# Monotor No.2
Section "Monitor"
    Identifier    "Second Monitor"
    Option         "DPMS"
    HorizSync    28-80
    VertRefresh    43-75
EndSection

# Info for First monitor --
# Screen No.1
Section "Screen"
    Identifier     "Default Screen"
    Monitor        "Main Monitor"
    Device        "Intel 82945G"
    DefaultDepth    24

        SubSection "Display"    
            Depth    24
            Modes    "1152x864", "1024x768"
        End Subsection
EndSection

# Info for Second monitor --
# Screen No.2
Section "Screen"
    Identifier    "Second Screen"
    Monitor        "Second Monitor"
    Device        "Radeon 7000"
    DefaultDepth    24
    
        SubSection "Display"    
            Depth    24
            Modes    "1152x864", "1024x768"
    End Subsection
EndSection

# Additional info --
Section "ServerFlags"
    Option "Xinerama" "true"
EndSection

# Specify position of two monitors relative to each other
Section "ServerLayout"
    Identifier    "Twin Head"
    Screen        "Default Screen"
    Screen        "Second Screen" LeftOf "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

```Following on from my continuing efforts to resolve this problem, I found yesterday some advice suggesting that connecting the second monitor to the DVI outlet (and ignoring the integral Intel chip) is "reported" to be the best way to solve this problem. 
I'm not at all sure about this and (so far) have not been able to find anything about the xorg.conf that I should write to control this configuration.

I'm an absolute newbie to Ubuntu and find myself much puzzled by the complexity compared with the various "Windows" systems I have used over the years so any advice or comments that you can make will be most gratefully received.

I thank you for taking the trouble to look at my post and for considering this lengthy reply.

Best regards,

---

### Post by ohzopants on 2008-11-12
I second the recommendation of connecting both screens to the ATI card.

The connector you describe is in fact a DVI connector.  You can buy an adapter that will allow you to connect a VGA monitor to a DVI card.

You will have to "tweak" the settings in windows, but the ATI control panel should be able to set up your screens just the way you want rather easily.

If you do connect both screens to the ATI card you should read the instructions here:
[https://help.ubuntu.com/community/XineramaHowTo#ATI](https://help.ubuntu.com/community/XineramaHowTo#ATI)

Also, if you do opt to not use your intel chipset you may be able to disable it in the bios.  The benefit to this is that you will gain access to whatever shared memory it was using (since integrated video chipsets use your main ram as video ram).

---

### Post by hatrack on 2008-11-12
Thank you for your reply.

Following on from the recent  previous posts, I yesterday went down to my local electronics store and there learned of the adapter of which you speak and I purchased this. Now, with two monitors running from the Radeon card, I couldn't get any graphics output at all !

I had to power-off the "hard" way (simply using the switch, irrespective of the state that the computer had reached in its boot sequence) and then, reconnect a monitor to the Intel on-board chip. No damage done but ... definitely NOT the way to treat a computer system !

I think you will agree that this whole business is getting silly ... I've spent about four weeks working on the problem with absolutely no success, so far. The reason I have a computer is so that I can do graphics processing, not to "play" with it and since buying this particular machine in September, I haven't processed one single image. 

Admittedly, I had not found the "Wiki" for which you kindly supply the URL. I'm going to study this tonight and try out the ideas presented there. If that doesn't produce a dual-monitor set-up, I'm going to give up on the whole idea. I'll have to change my methods of working and (when funds allow) buy a 22" monitor but that's a better option than endlessly experimenting with configuration and not doing any work ... even if this is a hobby.

In the meantime, I would like to express my thanks to all on this Forum who have tried to help with this problem. I have no idea why something which can be achieved almost automatically in Win XP is virtually impossible under Ubuntu and also, why so many users report that they have success setting up dual monitors. My thought now is that perhaps this is an artefact of the on-board grahics controller. (I note that this idea in different form has occurred to you too).

This machine (Dell GX520) has been "refurbished" (i.e. it is a second-hand office machine) and I have no documentation for it and therefore, no idea how to disable the on-board graphics controller, although I agree with you that this is probably a BIOS setting. However, without information on how to recover, I hesitate to take this drastic step.

I hope that I can put up a new post tomorrow reporting success at last but ... as "they" say ... I'm not holding my breath on this one !

I repeat my thanks and send my best regards to all ...

---

