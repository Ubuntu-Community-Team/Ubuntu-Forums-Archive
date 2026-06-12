---
title: "An easy how to switch between TV and 2nd monitor"
date: 2006-08-14
forum: Outdated Tutorials &amp; Tips
---

### Post by alienseer23 on 2006-08-14
I got this to work using an Nvidia GeFOrce 6200. It has dual monitor out, and TV out. Wouldn''t it be cool if I could have all 3 of those?
Anyway, just install the nvidia-glx or legacy. FOrget about NVTV, it still hasn't found my card.

after you have the drivers installed thru synaptic (easiest way imo), open a terminal and type:

sudo nvidia-xconfig --separate-x-screens

This will automatically reconfigure your xorg.conf to handle 2 screens. You can undo this using the same nvidia tool.

If you want twinview, just open a terminal and type:

sudo nvidia-xconfig --twinview

no problem. Everything is automated this way. :KS 
The next thing you have to do is add your tv info manually to your xorg.conf file.

add this to your "monitor" section, or replace the current values:

    HorizSync 30-50
    VertRefresh 60

then add this to your second device listing:

        Option          "TVOutFormat" "Composite" #or SVIDEO etc 
   	Option          "TVStandard" "PAL-G" #or NTSC etc 
   	Option          "ConnectedMonitor" "TV" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci

change that to suit your tvoutformat needs, your tv standard needs (ntsc-m for the US, check your own if not), and your BusID info. 

Check your work, save and exit.

Now, if you have both monitors and TV all connected to one card, all you have to do to switch between them is restart x (ctrl + alt + backspace) with the 2nd monitor on to use it, or the second monitor off, and the tv on to use it.

Thats it.
Kind of a hack, but it's the easiest way I know of. The use of the nvidia-xconfig tool really makes the whole thing alot easier than manually editing the entire section of your xorg.conf file, imo.

If anyone knows of a better/easier way, please let me know!! This is my first how-to, I put it up because I ran into alot of issues and headaches trying to finad a way to make this easy and simple, and I am still working out a better way, so. I would love to know a way to do this without restarting X, but as far as I know, this is not possable.

I really hope this is helpfull to someone!
Please comment if you have used this, or if you have any suggestions to improve.

---

