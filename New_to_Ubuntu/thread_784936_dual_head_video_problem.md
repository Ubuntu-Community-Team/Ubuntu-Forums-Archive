---
title: "dual head video problem"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by ben_ezzell on 2008-05-06
I have installed Ubuntu 8.4 but I can not create an extended desktop for two monitors. I'm using a laptop (Toshiba) and an external monitor (Xerox) and, under WinXP have these configured as an extended desktop without problems.  The video card is a Mobile Intel 945 GM Express Chipset.

At present, Ubuntu insists on treating both as the same monitor, using the resolution of the larger monitor for both (the laptop is 1280x800, the external 1280x1024).

I've tried using xrandr to change the resolutions / arrangement but without success (see log below):

ben@Drampa:~$ xrandr --output LVDS --below VGA
xrandr: screen cannot be larger than 1280x1280 (desired size 1280x1824)
ben@Drampa:~$ xrandr --output VGA --above LVDS
xrandr: screen cannot be larger than 1280x1280 (desired size 1280x1824)
ben@Drampa:~$ 
ben@Drampa:~$ xrandr --fb 1024x2080
xrandr: specified screen 1024x2080 not large enough for output VGA (1280x1024+0+0)
ben@Drampa:~$ xrandr --output LVDS --below VGA
xrandr: screen cannot be larger than 1280x1280 (desired size 1280x1824)
ben@Drampa:~$ 

Does anyone have any solutions / suggestions?  Should I be using a different version of Linux?  Or should I replace Gnome?  Any help appreciated -- I'm very new to Linux but would like to make a complete switch.

Thanks,

Ben

---

### Post by HotShotDJ on 2008-05-06
> **ben_ezzell said:**
> Does anyone have any solutions / suggestions?  Should I be using a different version of Linux?  Or should I replace Gnome?  Any help appreciated -- I'm very new to Linux but would like to make a complete switch.Well... yes & no.  You need to set your Virtual Desktop size manually in /etc/X11/xorg.conf  -- BUT there is a complication.  The video card in your laptop cannot give you the right sized Virtual Screen without automatically disabling 3D effects... that means no Compiz, no 3D games, no Googleearth.  If you are ok with that, then I can give you more detailed instructions.  Let me know.

HMMMM... scratch that.  I think it might work fine.  Stand by for more detail...

---

### Post by HotShotDJ on 2008-05-06
Ok... from a terminal (Applications --> Accessories --> Terminal) run "gksudo gedit /etc/X11/xorg.conf" (without the quotes, of course)

Now, find the section called "Screen" and edit it so that it looks like this:
> 
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 1280 1824
        EndSubSection
EndSection

Reboot, and then run the xrandr commands.  This will allow you to use either "below" or "above" options.  Left or right will not work and may cause 3D problems that I mentioned before.

---

### Post by ben_ezzell on 2008-05-07
Okay!  The "virtual" was all that was necessary and it's working fine.

Oh, 3-D doesn't seem to have been affected at all.

I thank you very much ... now let's see what other problems I can get into.  If I can get my email and contact lists/calendar/memos moved over than I'll be pretty happy.  I've looked at Evolution but I think I'm going to stick with Thunderbird and J-Palm.

Again, thank you very much ... 

Ben

---

