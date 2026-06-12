---
title: "Resolution stuck at 640x480"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Djbb on 2008-05-01
Alright guys, I upgraded to 8.04 from 7.10 a few days ago and everything was working fine up until this morning. The highest resolution I can set my monitor to is 640x480. After reading around various forums, I've tried 'sudo dpkg-reconfigure -phigh xserver-xorg' and then 'sudo reboot', which didn't fix the problem. I also tried disabling my Nvidia drivers through Admin>Hardware Drivers and then re-enabling them hoping maybe the drivers would update, but no, that didn't work either.

---

### Post by OffAxis on 2008-05-01
try running the dpkg command without the -phigh switch

```
sudo dpkg-reconfigure xserver-xorg
```

This'll walk you through the entire xserver setup, but at the end you will be able to specify available resolutions.

---

### Post by Cap'n Redbeard on 2008-05-01
Hi Djbb,

Yep, i had the same problem when i updated from Gutsy to Hardy - screen stuck at 800x600 or lower.

i cured it by running "displayconfig-gtk" from command-line as sudo. It gave a whole load of options for driver, video card and telly. The on-board video of this machine wasn't there, so i just selected the telly, a "Samsung SyncMaster 710n".

Be careful NOT to select a screen resolution too high otherwise it'll come out all squiggly. i had to re-start in "re-build" mode to set it properly !

Best o' :)

---

### Post by Cap'n Redbeard on 2008-05-01
Sorry, selected "generic vga", then this telly !

---

### Post by wermeulen on 2008-05-01
Don't know if your problem is related, but I use Hardy + Intel GMA 3100 + Philips 170s LCD, and although everything is detected correctly it doesn't allow me to set maximum resolution on default install and all Xorg.conf settings are ignored. The following is a recap of what I did to fix it--might not work for you, but the commands used might prove useful in detecting your problem. (Type "man <command>" to get information on the commands.)

Start with running "sudo ddcprobe" to see if your videocard + monitor are detected correctly. (If it is not installed, run "sudo apt-get install xresprobe".) You will get a lot of output, but read it anyway. The name of your videocard and a list of its supported modes (mode: width x height x colourdepth) should be in there, and your monitorname should also be there and a list of its supported timings (timing: width x height @ refreshrate). **Or just post the output of that first here :)**

Then run "xrandr" to see how everything is running now, and more importantly what your output device is. From the example below you can see output it to TMDS-1 (DVI to LCD) and running at 1280x1024@60.
```
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
[COLOR="Red"]TMDS-1[/COLOR] connected 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
   1280x1024@60   60.0*

```

Now just use xrandr to force another resolution; as long as it is supported for both your videocard and monitor according to ddcprobe this should work. First though, you need to get a modeline for the resolution you want. For example, if you want 1280x1024 at 60Hz, run "gtf 1280 1024 60". Example output follows, where I colour code the parts to reuse in the next step.
```
  # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline [COLOR="Lime"]"1280x1024_60.00"[/COLOR]  [COLOR="Plum"]108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync[/COLOR]

```

Now, using the information gathered from the above commands you can run the following three to create a new video mode, add it your supported list and force a switch to that mode:
```
xrandr --newmode [COLOR="Lime"]"1280x1024_60.00"[/COLOR]  [COLOR="Plum"]108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync[/COLOR]
xrandr --addmode [COLOR="Red"]TMDS-1[/COLOR] [COLOR="Lime"]"1280x1024_60.00"[/COLOR]
xrandr --output [COLOR="Red"]TMDS-1[/COLOR] --mode [COLOR="Lime"]"1280x1024_60.00"[/COLOR]
```

If it goes wierd, just press ctrl+alt+backspace to reboot your graphical environment.

To enable this a login time (after you checked it works), add these commands just before the last 'exit 0' statement in /etc/gdm/Init/Default.

---

### Post by arpad on 2008-05-01
I went through the steps you detailed and when I reboot I go right back to my original 1024x768. Any further ideas?

---

### Post by Djbb on 2008-05-02
> **Cap'n Redbeard said:**
> Hi Djbb,

Yep, i had the same problem when i updated from Gutsy to Hardy - screen stuck at 800x600 or lower.

i cured it by running "displayconfig-gtk" from command-line as sudo. It gave a whole load of options for driver, video card and telly. The on-board video of this machine wasn't there, so i just selected the telly, a "Samsung SyncMaster 710n".

Be careful NOT to select a screen resolution too high otherwise it'll come out all squiggly. i had to re-start in "re-build" mode to set it properly !

Best o' :)

Thanks man, that fixed it

---

