---
title: "ubuntu 10.04 and no sound or wireless"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by Nu2ubun on 2012-02-25
i downloaded ubuntu 10.04 and this is the first time ever using linux and i don't have any sound and my wireless does not work don't know what else doesn't work haven't had a whole lot of time to check but i downloaded the drivers for the wireless i just don't know how to install them yet can someone tell me how give me a walk through or something need some help

---

### Post by wolfen69 on 2012-02-25
Is it a relatively new computer? If so, 10.04 is a bit dated as far as hardware support. I'm not going to tell you to not use it, but a more recent version of ubuntu such as 11.10 might be better on your hardware.

---

### Post by ahiung on 2012-02-25
> **Nu2ubun said:**
> i downloaded ubuntu 10.04 and this is the first time ever using linux and i don't have any sound and my wireless does not work don't know what else doesn't work haven't had a whole lot of time to check but i downloaded the drivers for the wireless i just don't know how to install them yet can someone tell me how give me a walk through or something need some help

Linux don't use drivers. You got the problem from fresh install or after installed or using it with several *thing*s ?

---

### Post by HeroOfCanton on 2012-02-25
Wireless can be tricky on linux. More details would help.

Start by typing this in terminal and posting the results here. Post inside the code tag (pound sign in the editor) so we read easily.

```
lspci -v
```Did you download windows drivers? For using those you will want to read up on ndiswrapper. [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

This tutorial may also be some help [https://help.ubuntu.com/11.04/ubuntu-help/net-wireless-troubleshooting-hardware-check.html](https://help.ubuntu.com/11.04/ubuntu-help/net-wireless-troubleshooting-hardware-check.html)

---

### Post by Nu2ubun on 2012-02-25
ok so i did the lspci -v and this is what i got


 	Code:
# 00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1510
    Subsystem: Advanced Micro Devices [AMD] Device 1510
    Flags: bus master, 66MHz, medium devsel, latency 32

00:01.0 VGA compatible controller: ATI Technologies Inc Device 9804
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=256]
    Memory at f0400000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA  Controller [AHCI mode] (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    I/O ports at 5118 [size=8]
    I/O ports at 5124 [size=4]
    I/O ports at 5110 [size=8]
    I/O ports at 5120 [size=4]
    I/O ports at 5100 [size=16]
    Memory at f0449000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0  Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at f0448000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI  Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at f0447000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev  40)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at f0440000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller  (rev 40)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev  40) (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2  Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at f0446000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=05, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: f0300000-f03fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:15.1 PCI bridge: ATI Technologies Inc Device 43a1
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Prefetchable memory behind bridge: 00000000f0100000-00000000f01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:15.3 PCI bridge: ATI Technologies Inc Device 43a3
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f0200000-f02fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0  Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at f0445000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI  Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at f0444000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Device 1700 (rev 43)
    Flags: fast devsel

00:18.1 Host bridge: Advanced Micro Devices [AMD] Device 1701
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Device 1702
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Device 1703
    Flags: fast devsel
    Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Device 1704
    Flags: fast devsel

00:18.5 Host bridge: Advanced Micro Devices [AMD] Device 1718
    Flags: fast devsel

00:18.6 Host bridge: Advanced Micro Devices [AMD] Device 1716
    Flags: fast devsel

00:18.7 Host bridge: Advanced Micro Devices [AMD] Device 1719
    Flags: fast devsel

02:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, fast devsel, latency 0, IRQ 5
    Memory at f0300000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, fast devsel, latency 0, IRQ 27
    I/O ports at 3000 [size=256]
    Memory at f0104000 (64-bit, prefetchable) [size=4K]
    Memory at f0100000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176  (rev 01)
    Subsystem: Hewlett-Packard Company Device 1629
    Flags: bus master, fast devsel, latency 0, IRQ 11
    I/O ports at 2000 [size=256]
    Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>#

---

### Post by Nu2ubun on 2012-02-25
if a newer version will work better how do i donwload it cause on the website it tells me to go to the update manager to download it if i don't have 10.10 or something like that

---

### Post by HeroOfCanton on 2012-02-25
> **Nu2ubun said:**
> if a newer version will work better how do i donwload it cause on the website it tells me to go to the update manager to download it if i don't have 10.10 or something like that

[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

I would upgrade and if you continue to have problems with the sound and wireless let us know.

---

### Post by Nu2ubun on 2012-02-25
could the root of my problem be the fact that i might have downloaded a 32 bit os rather than a 64 bit os cause my computer was a 64 bit windows 7 computer so could that affect the sound and wireless and things like that

---

### Post by wildmanne39 on 2012-02-25
Hi, the issue with your wireless is you need to install the driver, you can do that with this link, post 8. 

You must have a wired connection to install the driver.
[http://ubuntuforums.org/showthread.php?p=11715526#post11715526](http://ubuntuforums.org/showthread.php?p=11715526#post11715526)
Thanks

---

### Post by audiomick on 2012-02-25
> **Nu2ubun said:**
> could the root of my problem be the fact that i might have downloaded a 32 bit os rather than a 64 bit

As far as I know, whilst a 64 bit image will not work on 32 bit hardware, a 32 bit image will work on both 32 bit and 64 bit hardware, so no problems there.

Some advice: when you post a lot of output like you did in post #5, use code tags. There is a button at the top of the post window marked #. Click on that, and post your output between the tags, like here [tag] here [/tag] where it says "code" instead of "tag".

Secondly, make the effort to use punctuation in your posts. The people who are trying to help you here are all volunteers who are helping you out of the goodness of their hearts. If you want good help, you would do better to make your post as easy to understand as possible.

---

### Post by Nu2ubun on 2012-02-25
Well i do apologize for making myself look like an illiterate donk. To wild man thank you my wireless is now working. Would you happen to know a way to do the same for my sound? that would be greatly appreciated thank you again.

---

### Post by wildmanne39 on 2012-02-25
Hi, I am glad the wireless is working, here is a link for sound issues.

I am not experienced with sound problems really but if you need more help post in this link and you should get the help you need.
[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)
Thanks

---

### Post by Nu2ubun on 2012-02-26
Thank you for all your help. I am still working on my sound , but i do have wireless now. if anyone else has an idea for how to get my sound to work i would be more then happy to give it a try thank you for the help so far and for the future help that you may provide.

---

### Post by audiomick on 2012-02-26
What is with the sound? Absolutely nothing, or do the system sounds work, but it wont play music?

You would probably have noticed the icon in the bar at the top right that looks like a loudspeaker. I assume you have looked in there, checked that it isn't just muted or something silly like that. Do the settings in there in the "Audio Settings" look like they make sense?

From your lspci output
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev  40)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at f0440000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```

This is your audio device. On the hardware tab, have a look to see that it is being used. I'll attach a screenshot of what mine looks like. It's not the same audio device as yours, but it is a 10.04 install (on a laptop) that hasn't been messed around with to any great extent.

Mine is set to internal Audio. "1 Ausgabe / 1 Eingabe" means "one output / one input".

I've seen people having problems because the drop down at the bottom of the window wasn't set right. As far as I know, Analogue Stereo Duplex is generally right for "normal" use. That means that you can input and output at the same time.

The check box up at the top labelled "stumm" is the master mute. When it is selected, all sound is off.

---

### Post by Nu2ubun on 2012-02-26
after digging a little deeper i still don't know where my problem lies. but i get sound out of my headphones but i can't get sound out of my speakers any ideas?

---

### Post by wolfen69 on 2012-02-26
> **Nu2ubun said:**
> after digging a little deeper i still don't know where my problem lies. but i get sound out of my headphones but i can't get sound out of my speakers any ideas?

Did you go into the sound settings and check all the levels?

---

### Post by Nu2ubun on 2012-02-26
yes i did and everything seems normal input is about half. The output choose output device for sound output it has internal audio analog stereo selected and that is the only one.

---

### Post by Nu2ubun on 2012-02-26
Oh and also for whatever reason i went to my father in laws house with my wife today, and ,my wireless wasn't working. not sure what i did wrong but it has stopped i am about to do a fresh install on my computer. then update it to the latest updates then do the wireless thing again cross your fingers hope it works.

---

### Post by wolfen69 on 2012-02-26
Try the live cd of ubuntu 11.10, [http://www.ubuntu.com/download](http://www.ubuntu.com/download)  and see if the issues clear up.

---

### Post by Nu2ubun on 2012-03-01
I would like to thank everybody for their help in solving my issues. I now have 11.10 and my sound and wireless work great. thank you, but now my dvd player isn't working the computer is a compaq presario cq57 the cd part of the cd-dvd player works, but it won't play a dvd. Any ideas or sloutions to the problem? thank you in advance

---

### Post by morhin on 2012-03-02
The dvd may be encoded. I had to get the following to get mine to work (running 10.04).

Go to Applications/Ubuntu Software Center 
(I used search to find these as they may not be part of the title. Even then I had to look a bit but they were there)

gst-plugins-base

gstreamer0.10-plugins-good

gstreamer0.10-plugins-bad

gstreamer0.10-plugins-ugly

gst-ffmpeg

libdvdread4

Now the final and essential steps. Go to Applications/Accessories/Terminal and type in

sudo apt-get install libdvdread4 

hit enter, when it returns type in

sudo /ust/share/doc/libdvdread4/install-css.sh

hit enter

Once the terminal returns you are done. I restarted the pc and put the dvd in. I got an error message so I did the last 2 steps again, restarted and got the same error message which disappeared and the dvd started playing. I prefer using VLC as my computer (Acer 53250) seems to like it best for full screen.

I got this info from Ubuntu for Non-Geeks by Grand and Bull. I really like this book for reference and will get the next version when I move to the next stable release (I think that's 12.04)

Take care
Morhin

---

### Post by Nu2ubun on 2012-03-02
> **morhin said:**
>  sudo /ust/share/doc/libdvdread4/install-css.sh

hit enter

every thing seems to work but this one can you please check it out and see if you may have typed it wrong or something it would be greatly appreciated. thank you very much and god bless

---

