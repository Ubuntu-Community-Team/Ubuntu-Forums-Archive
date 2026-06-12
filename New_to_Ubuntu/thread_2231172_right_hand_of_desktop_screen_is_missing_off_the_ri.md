---
title: "right hand of desktop screen is missing off the right hand of monitor"
date: 2014-06-23
forum: New to Ubuntu
---

### Post by Un_Known on 2014-06-23
i'm on ubuntu 14.04,with xfce as desktop.
i use an offboard monitor as the laptop monitor is broken. but all is good apart from that.
now,the monitor that we do use(plugged in via MDMI) is normally perfect. but tonight has started displaying the screen with the right hand side off-screen.
ie, all the buttons normally on top right of screen (settings, date/time, log-off, etc are all too far off the screen to use properly.
and there arnt any settings in settings-display that seem to help.
any ideas? (i've tried auto on the monitor,and a few other simplesettings,but no luck yet.

---

### Post by Un_Known on 2014-06-23
SOLVED!
i found a fix (forgot to save the page it came from on ask ubuntu,but here it is) and it is:
xrandr --output VGA1 --left-of LVDS1

fixed issue of screen too far right so we couldnt see certain func tions,and browser was ssame.now all fixed!

---

### Post by Un_Known on 2014-06-24
it's not, as it turns out really solved.
when you reboot,the right hand side of desktop, and browser is missing as its too big for monitor. nothing i can find in settings will at all help.
it will fix till you reboot.like many other ubuntu things.

it did click this as "solved",but it is notsolved, so i'm de-clicking it.

---

### Post by Un_Known on 2014-06-26
again, this issue hasnt gone away.
and then this morning i boot up., and for one secnond the screen looked normal (that is, screen too far to right of monitor,as this is how my ubuintu always begins each day) BUT this time, after that first second, it changed.and then went too far to the left!!!!
i tried fixing it, by adding "left" to the command above, and for a second it worked, then everything from my desktop except wallpaper vanished. i had to reboot to cure.

maybe time to uninstall ubuntu alltogether. i havnt has ONE SINGLE DAY where i dont have to spend the whole day fixing things. useless. i cannot work on this.
and will NOT be re-installing till it proves otherwise... somehow. doubt it tho.

---

### Post by Un_Known on 2014-06-26
besides,probably due to the fact that NONE of my issues have been GENUINLY fixed, i dont get ANY replies anymore.
so when there is a REAL problem, you dont get any help.
this better not be screwing my laptop

---

### Post by QIII on 2014-06-26
Perhaps, Un-Known, it is your demeanor that drives the paucity of answers to your questions - which, I have noticed, often take the form of rants.

I suggest:

1.  That you change your posting style.

2.  That you stop assuming that just because you have a bunch of problems that it must be the same for everyone and we are somehow ignoring it.

Up to you.

---

### Post by uRock on 2014-06-26
I've had problems like that in the past. Once I hit a button on the monitor to center the image, the problem would go away permanently. This problem only occurred after fresh Linux installs.

A more optimistic approach does genuinely gain the interest of those who are willing to help. I admit I have had quite a few problems with ubuntu in the past, but I've also had problems with Windows, IOS, and other Linux distros. Being positive has helped me get through them.

---

### Post by newb85 on 2014-06-26
The suggestions so far have been good.  I also suggest you provide more useful information about your problem.  In this case, the problem is most likely related to your graphics card and drivers, so specifics about them would be good.

```

sudo lshw -C display

```

will give some info.

---

### Post by trag on 2014-07-08
Your Laptop is only capable of outputting a few HDMI resolutions,and your TV is only able to receive a few HDMI resolutions.Because there is no single resolution they both can agree on you are experiencing over scan.You will need a VGA/HDMI adapter between the laptop and the tv. Sound to the tv will continue over HDMI but the video will be converted to VGA,adjust your tv to receive a VGA signal and you will get a picture that fits the screen

---

### Post by newb85 on 2014-07-10
> **trag said:**
> Your Laptop is only capable of outputting a few HDMI resolutions,and your TV is only able to receive a few HDMI resolutions.Because there is no single resolution they both can agree on you are experiencing over scan.

If it really is a hardware compatibility issue, I think the OP would have experienced it while using Windows.  It doesn't sound like they did, although it would be helpful if they provided this info.

It could also be related to the graphics drivers, which they still haven't provided any info on.

---

### Post by Un_Known on 2014-07-30
> **newb85 said:**
> The suggestions so far have been good.  I also suggest you provide more useful information about your problem.  In this case, the problem is most likely related to your graphics card and drivers, so specifics about them would be good.

```

sudo lshw -C display

```

will give some info.
i tired the above command,and here is the resulting info!
thanks everyone for the generaladvice, and for the particular technicaladvice.very appreciated.

" *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:f0000000-f03fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f04fffff"

however the problem seems to have worsened now.
recently everytime i boot my laptop up once all has loaded, i then have to go straight to terminal,  type in:
xrandr --output VGA1 --right-of LVDS1 which has always centred screen (until shut down),now dosnt work.
now what happens is that the desktop background (which is a changing slide how style background i've been using) suddenly is allthat appears.
and have to shut down manually (laptop physical on/off button).
also, when screen loads,sometimes it now has a different font, and icons have allmoved around.

in short,the "xrandr --output VGA1 --right-of LVDS1" dosnt appear to be working anymore. just causes desktop to vanish,and desktop background, only, is visible!

ideally,it would be nice not to have to use the"xrandr --output VGA1 --right-of LVDS1" at all,each time i boot up. so fingers crossed!
and again, thanks everyone.

---

### Post by Un_Known on 2014-07-30
it'strue that i didnt have this problem with windows,except when only just setting it to suit me personally.
this is a new issue for me!
 but have provided display driver details now, above, so fingers crossed some light will be shed.
 a big warm thanks to newb85 for the sudo for display details.
hope that helps?

---

### Post by Un_Known on 2014-08-15
still struggling with this issue.
now when i try the sudo command "xrandr --output VGA1 --right-of LVDS1" to centre screen from the right, my desktop vanishes, and i just get ubuntu backgrounds,and do get main menu from right clikcing on desktop,but no top bar for my tabs.

but if i dont use that command "xrandr --output VGA1 --right-of LVDS1", then bottom of browser is below screen, so cant resize it.
very limiting. will try re-googling to see if anything new anywhere.
i supplied graphics card details, but not had any replies on that yet.
fingers crossd though.

---

### Post by Un_Known on 2014-08-15
" *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:f0000000-f03fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f04fffff"

---

