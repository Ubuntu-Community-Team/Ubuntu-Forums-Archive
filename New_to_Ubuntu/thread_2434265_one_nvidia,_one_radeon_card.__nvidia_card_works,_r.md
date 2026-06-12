---
title: "one nvidia, one radeon card.  nvidia card works, radeon does not."
date: 2020-01-02
forum: New to Ubuntu
---

### Post by psiphre on 2020-01-02
fresh windows refugee.  fresh install of 18.04 as of new year's day.  using a gtx 1060 to push my main monitor, which works perfectly (i've gotten lutris with wine to run my favorite game!).  the second card, a radeon HD7870, refuses to display video when the system is running.

the output of lspci lists both video cards, detected properly as the correct model.  so the system is clearly aware of the card.  

my console (ctrl+alt?+f4 for example) is flooded with messages like:
[  617.252346] radeon 0000:02:00.0: ring 0 stalled for more than 581020msec
[  617.252354] radeon 0000:02:00.0: GPU lockup (current fence id 0x0000000000000001 last fence id 0x0000000000000002 on ring 0)

i've tried creating an xorg config file, starting with this:
```
Section "Device"
    Identifier  "Screen0"
    Driver      "nvidia"
    BusID       "PCI:01:00.0"
EndSection

#Section "Device"
#   Identifier  "Screen1"
#   Driver      "radeon"
#   BusID       "PCI:02:00.0"
#EndSection
```



but booting with that in place causes the system to hang [here]("https://i.imgur.com/m9kkiuF.jpg"): [URL="https://i.imgur.com/m9kkiuF.jpg"]

o[/URL]n advice, i changed the grub file so that it reads:    GRUB_CMDLINE_LINUX_DEFAULT="nvidia-drm.modeset=1 quiet splash" but that didn't work either.

all of the troubleshooting steps that i've tried and advice i've received are documented here: [https://old.reddit.com/r/Ubuntu/comments/eit3dd/windows_refugee_trying_to_get_multiple_monitors/](https://old.reddit.com/r/Ubuntu/comments/eit3dd/windows_refugee_trying_to_get_multiple_monitors/)

---

### Post by CatKiller on 2020-01-03
> **psiphre said:**
> fresh windows refugee.

Take out the AMD card and just use multiple outputs or multi-streaming from your Nvidia card.

It probably *is* ultimately possible to do what you want these days with Prime offloading, but multimonitor and Optimus are individually a pain to configure and using AMD rather than Intel as the other component is a *really* uncommon configuration.

Your AMD card just isn't bringing anything to the table to make it worthwhile. When you're (a lot) more experienced with Linux it might be an interesting project - in a mountain-climbing sense - but it's something that you should steer well clear of on your first day.

---

### Post by psiphre on 2020-01-03
it's bringing four extra monitors at a cost of $0 - it's the card that i upgraded from when i bought the 1060.  i had this configuration working in 30 minutes before the switch to ubuntu.

the system sees and identifies both cards.  i have both drivers.  they both work.  the system even outputs video to the second card when it's shutting down.  what's causing the GPU to lock up?

---

### Post by CatKiller on 2020-01-03
In reverse order. 

> **psiphre said:**
> what's causing the GPU to lock up?

I have no idea; I don't use AMD cards, so I haven't played with their driver. 

> the system even outputs video to the second card when it's shutting down. 

Displaying framebuffer things is an entirely different thing to having an X server running a display on a monitor. At the moment you haven't configured X to use any of your displays, it's just autoconfiguring a single display on a single monitor on one card, since that's relatively straightforward to do.

The nvidia proprietary driver essentially implements its own X server, different to the one that Intel/AMD use, so that they can maintain parity with their Windows driver. You would need both X servers to be able to communicate with each other and coordinate what they're doing. You haven't yet got to the point that you've told the system what you want to do. 

You can make that process a lot simpler by only using one card, or at least one X server implementation. While you can, of course, continue to experiment, it's much more complicated than you realise and will require a lot of learning before you'll be able to make it work.

---

### Post by psiphre on 2020-01-04
ok.  what i understand is that the thing that i want to do, linux just can't.  so i have to figure out a different way about it.

so pretend that i removed the amd card and swapped in another nvidia card.  afterwards my nvidia-settings panel looked like this:  [http://i.imgur.com/rWC2vLn.png](http://i.imgur.com/rWC2vLn.png)

i think, based on googling, that i want to put the additional two monitors that i have plugged in to the second card (which will eventually be four) on a second "X screen", and then enable xinerama so i can move windows around freely.  does that sound about right?

---

### Post by CatKiller on 2020-01-04
> **psiphre said:**
> i think, based on googling, that i want to put the additional two monitors that i have plugged in to the second card (which will eventually be four) on a second "X screen", and then enable xinerama so i can move windows around freely.  does that sound about right?

That's broadly the case. For multiple displays on one nvidia card TwinView is an additional configuration option, and for identical nvidia cards SLI Mosaic mode is another option. The [nvidia readme](http://download.nvidia.com/XFree86/Linux-x86_64/440.31/README/index.html) is a good resource for learning about the options and limitations.

The issue is that the X Server is very (very) old, and has been extended with various hacks that made sense at the time, and nvidia really don't play nicely with others. In addition, X Server development was stopped in favour of a completely new framework - Wayland - which hasn't yet materialised. So, as it stands, it's all quite clunky and fiddly, with seemingly arbitrary hard limitations. 

One monitor on one card is easy. Lots of monitors on one card is only a little bit harder. After that it gets really arcane quite quickly.

---

### Post by psiphre on 2020-01-04
> **CatKiller said:**
> The issue is that the X Server is very (very) old, and has been extended with various hacks that made sense at the time
That makes sense; i recall wrestling with x every time i've given this linux thing a shot, all the way back to red hat 6(? i think? it was a long time ago).

> **CatKiller said:**
> One monitor on one card is easy. Lots of monitors on one card is only a little bit harder. After that it gets really arcane quite quickly.

yes, so speaking of which.  i can activate the second X screen, and i can get "something" displaying on it.  i can move the mouse cursor from the main monitor on the first card to either monitor on the second card, but it changes from a  pointer to the X cursor.  they are even (logically) arranged how i set them up in the panel.  but i can't figure out how to do anything after that, and if i try enabling xinerama, i get the system to hang during boot waiting for some 121 process and have to reboot to repair mode and delete my x.org.conf in order to get back.  any ideas?

---

### Post by CatKiller on 2020-01-04
> **psiphre said:**
> any ideas?

It's a long time since I played with multimonitor stuff, but you could post the xorg.conf that you're trying to use and I can try to spot anything obviously wrong with it. 

If your TTYs are working (*sometimes* the nvidia driver only gives a blank screen unless you set Grub options) you can just use something like Ctrl-Alt-F3 to get to a command line so that you can edit/delete your xorg.conf and try again. To switch back to the graphical environment it will probably be Ctrl-Alt-F1, or possibly Ctrl-Alt-F7. Nano is a fairly user-friendly command line text editor. ```
sudo service <name of display manager> restart
``` is a fairly quick way of getting it to pick up the changes that you've made. The display manager will be called something like gdm, lightdm, sddm, depending on which desktop environment you're using.

The [Arch wiki](https://wiki.archlinux.org/index.php/Multihead) has useful information on the different approaches. Both Xinerama and RandR are X extensions, with RandR being the newer one that allows more on-the-fly changes. RandR might be easier, but that was created since the last time that I played with multimonitor stuff.

The X server log file is at /var/log/Xorg.0.log, which might have useful information for you, too.

---

