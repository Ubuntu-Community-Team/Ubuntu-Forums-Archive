---
title: "Ubuntu and screen resolution"
date: 2019-02-21
forum: New to Ubuntu
---

### Post by falapt on 2019-02-21
[COLOR=#242729][FONT=Arial]So the screen resolution of my monitor is missing in the live environment. Even after installing (Ubuntu 18.04.2) and then installing the latest updates, only some smaller resolutions appear.
My monitor is kind of old, but has no problems at all. It's a VGA monitor, and it's connected through a VGA to DVI adapter to the graphics card (AMD R7 360).

I tried creating the bootable USB using different types of software, and also different USB sticks, which leads me to think there's either a software issue or something with my monitor. I also tried multiple ubuntu based distros, as well as arch based distros, all with the same exact issue.[/FONT][/COLOR]

---

### Post by CatKiller on 2019-02-21
> **falapt said:**
> It's a VGA monitor, and it's connected through a VGA to DVI adapter to the graphics card

Modern monitors advertise the resolutions they are capable of through a mechanism called EDID. Many adaptors do not pass this information along, and some old monitors do not provide it in the first place. 

There are many posts about how to use xrandr to create a setting for the resolution that you want to use when you're missing the EDID information. You should be able to find them now that you know what you're looking for.

---

### Post by falapt on 2019-02-22
Thank you, this definitely helped :)

 Now... I have been able to manually add the resolution running some commands with xrandr, and I'm now able to select the correct resolution. But after rebooting, the change is undone :(

Also, side question: this only means there's an issue with the monitor, it has nothing to do with the graphics card, right?

---

### Post by CatKiller on 2019-02-22
> **falapt said:**
> Thank you, this definitely helped :)
 Now... I have been able to manually add the resolution running some commands with xrandr, and I'm now able to select the correct resolution. But after rebooting, the change is undone :(

I've never had to play around with xrandr, thankfully, so I don't know how permanent it's supposed to be. If it isn't supposed to be permanent, you could either have the xrandr command that works for you run at startup, or use xorg.conf to achieve a similar thing. Basically, just giving it the timing information that would otherwise be provided by EDID.

>  Also, side question: this only means there's an issue with the monitor, it has nothing to do with the graphics card, right?

It might not be the monitor: it might be the adaptor. Either way, not the graphics card.

---

### Post by Holger_Gehrke on 2019-02-22
You might also want to check the cable. Both DVI and VGA contain an I²C-Bus for transmitting EDID. For DVI it's pins 6 (clock) and 7 (data), VGA uses pins 12 (data) and 15 (clock). If those are not connected (or connected wrong), the PC won't get EDID and can't tell what resolutions your display supports. Diagrams of the connectors and pin-numbering can be found on Wikipedia.

Holger

---

### Post by falapt on 2019-02-22
Does it make a difference if I say windows works fine? It must be a software issue then...

---

### Post by CatKiller on 2019-02-22
> **falapt said:**
> Does it make a difference if I say windows works fine? It must be a software issue then...

Not really. The Windows monitor "driver" is simply a text file that contains all the information that you'd put in xorg.conf when you aren't getting EDID information.

The VertRefresh and HorizSync ranges are what you'd put in xorg.conf, btw. With those, X will automagically work out the available resolutions. That was the way it was done prior to the release of xrandr.

---

### Post by richard378 on 2019-02-23
Make sure you have the driver for the video card installed.  It looks like there is a driver for Ubuntu 16.04 LTS [https://www.amd.com/en/support/kb/release-notes/rn-radpro-lin-16-40](https://www.amd.com/en/support/kb/release-notes/rn-radpro-lin-16-40).

---

### Post by falapt on 2019-02-25
I could try with a new cable. I'm thinking that a VGA to HDMI cable could solve the EDID problem. Right now I'm using a VGA to VGA cable that connects to the PC with a DVI adapter. I could try with a VGA to HDMI (no adapters whatsoever). What do you think? 
By the way, thanks for all the help you all :D

---

### Post by CatKiller on 2019-02-25
> **falapt said:**
> I could try with a new cable. I'm thinking that a VGA to HDMI cable could solve the EDID problem.

It might, or it could be that the monitor doesn't provide EDID. I once had a monitor that produced EDID, but it was all lies. Very frustrating.

Since you know that you *can* make the right resolution be available with config tweaks, I wouldn't spend any money on it.

You can get the HorizSync and VertRefresh frequency ranges from the manual, specifications, or Windows "driver." They go in the Monitor section of xorg.conf, if I recall correctly. You may be able to get away with a bare Monitor section as a file in xorg.conf.d, or you might need to set up a skeleton xorg.conf with Screen, Device and Monitor sections. You definitely used to have to do the latter, but a lot of restrictions have been relaxed since then.

The skeleton file would look something like

```

Section "Device"
    Identifier "Default Device"
EndSection

Section "Monitor"
    Identifier "Default Monitor"
    HorizSync www-xxx
    VertRefresh yyy-zzz
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device "Default Device"
    Monitor "Default Monitor"
EndSection

```

where www, xxx, yyy, zzz are the values you've got from the manual.

I think you could use your xrandr timing values to define the new mode directly there, too, if you prefer.

---

### Post by NM5TF on 2019-02-27
use xrandr to set up your monitor like you want it....

then make the changes persistent here....[https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_changes_persistently](https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_changes_persistently)

tommy

---

