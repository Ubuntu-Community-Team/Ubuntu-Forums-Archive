---
title: "Video Resolution on Live Disk"
date: 2013-03-07
forum: New to Ubuntu
---

### Post by vineyridge on 2013-03-07
I'm testing various flavors on Linux this way before I commit and install.

Today is my first ever try at Ubuntu/Xubuntu, and the standard video is 1024x768.  My VGA CRT monitor is capable of higher resolution, and on this 17 inch monitor, only about half or less of a page shows before I have to start scrolling.  I went to the Display section in the settings manager and 1024 x 768 is the highest resolution shown.  60 hz is the only refresh rate shown, and this monitor will go up to 85.

How do I adjust the resolution?  Am I stuck?

  Will this be a problem when Linux is installed?  The monitor never had its own drivers, but always used the Windows generic ones and/or the Intel ones that came with integrated chipset.  Once Ubuntu is actually installed, the icon for my Intel graphic control will show up, won't it?  

I have ordered a new graphic card, Nvidia 620, but the monitor will remain the same

---

### Post by vineyridge on 2013-03-07
Apparently video resolution is a very common Ubuntu problem.  I've read a bunch of old threads and it seems that the xorg.conf file was deleted in Ubuntu 9.04.  This is a "legacy" CRT monitor, and it seems that Ubuntu just doesn't like my set up.  Found a thread where a fellow had my exact motherboard with integrated graphics chipset.  The solution seems to be creating an xorg.conf file and then manually adding all the parameters which is a PITA.  

I tried Puppy linux a while back and hated the interface.  But the Live CD did include an xorg utility that allowed the user to set the screen resolution.  Why doesn't Ubuntu have something similar?

---

### Post by vineyridge on 2013-03-08
Bump.  

I cannot live with 1024 x 768 resolution on this monitor.  If that's all Ubuntu will let me have, I'll have to start looking at other Linux versions.  I really like the Xubuntu interface though, and before giving it up, I'm going to experiment with some of the other flavors that I have Live Disk ready.

---

### Post by bab1 on 2013-03-08
> **vineyridge said:**
> Bump.  

I cannot live with 1024 x 768 resolution on this monitor.  If that's all Ubuntu will let me have, I'll have to start looking at other Linux versions.  I really like the Xubuntu interface though, and before giving it up, I'm going to experiment with some of the other flavors that I have Live Disk ready.

All modern digital monitors provide the specs when the OS is booted up (via ESID).  This is true for all Linux distros I believe.  Your problem is that you are using an analog monitor that provides no setup info (no ESID).  This means you have to configure it by hand.  No magic bullet here.  You need to know the working specs and create your own Xorg.conf file.

I found this out after fighting an old video card that had only VGA output.  The monitor has both VGA and DVI.  When I got a new video card with DVI and used that port, my monitor was detected and the correct settings were automatically applied.  If you can afford it I would dump the CRT and get a digital monitor with a  video card that has a digital (DVI) output.

This is not an Ubuntu specific problem.  This is a Linux kernel and Xorg (x-server) situation.

---

### Post by vineyridge on 2013-03-09
> **bab1 said:**
> All modern digital monitors provide the specs when the OS is booted up (via ESID).  This is true for all Linux distros I believe.  Your problem is that you are using an analog monitor that provides no setup info (no ESID).  This means you have to configure it by hand.  No magic bullet here.  You need to know the working specs and create your own Xorg.conf file.

I found this out after fighting an old video card that had only VGA output.  The monitor has both VGA and DVI.  When I got a new video card with DVI and used that port, my monitor was detected and the correct settings were automatically applied.  If you can afford it I would dump the CRT and get a digital monitor with a  video card that has a digital (DVI) output.

This is not an Ubuntu specific problem.  This is a Linux kernel and Xorg (x-server) situation.

I have the original manual that came with this 19" CRT monitor.  It shows 11 different resolutions and the Horizontal and vertical HZ (maximum I suppose) for each one.  There is another page with electrical specifications.  This is a very capable monitor with a maximum resolution of 1600x1200 (non-interlaced) at 75 hz and 1280 x 1024 at 85 hz.

So how do I set up an xorg.conf file?  If I'm going to use ubuntu, I need better resolution.  And, quite honestly, I cannot afford a new monitor.  I also happen to think that CRTs render color better than the flat screens, much as I think that vinyl records render sound better than digital media.

---

### Post by bab1 on 2013-03-09
> **vineyridge said:**
> I have the original manual that came with this 19" CRT monitor.  It shows 11 different resolutions and the Horizontal and vertical HZ (maximum I suppose) for each one.  There is another page with electrical specifications.  This is a very capable monitor with a maximum resolution of 1600x1200 (non-interlaced) at 75 hz and 1280 x 1024 at 85 hz.

So how do I set up an xorg.conf file?  If I'm going to use ubuntu, I need better resolution.  And, quite honestly, I cannot afford a new monitor.  I also happen to think that CRTs render color better than the flat screens, much as I think that vinyl records render sound better than digital media.

I can't say you won't be able do this to your satisfaction, but I will say that it's a royal PITA.

I would start with the man pages.  From the terminal you can get the manual page for *xorg.conf* like this```
man xorg.conf
```

 Then you can move on to this info: [_**[COLOR="#FF0000"]https://wiki.ubuntu.com/X/Config/]("https://wiki.ubuntu.com/X/Config/") [/COLOR]**_ and maybe 
here: [**_[COLOR="#FF0000"]http://samuelmartin.wordpress.com/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/[/COLOR]_**]("http://samuelmartin.wordpress.com/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/").

Later you can check out these 2 Google searches [**_[COLOR="#FF0000"]here[/COLOR]_**]("https://www.google.com/search?q=configure+xorg.conf+for+analog+monitor+ubuntu&btnG=Go!#hl=en&q=configure+xorg+conf+for+monitor+ubuntu+12.04&sa=X&ei=wek6UcH9JLCPyAGNloHoAQ&ved=0CFoQjxg&bav=on.2,or.r_qf.&bvm=bv.43287494,d.aWM&fp=cb1b7779090da6f2&biw=1268&bih=668") and [**_[COLOR="#FF0000"]here[/COLOR]_**]("https://www.google.com/search?q=configure+xorg.conf+for+analog+monitor+ubuntu&btnG=Go!#hl=en&sclient=psy-ab&q=configure+xorg.conf+for+analog+monitor+ubuntu+&oq=configure+xorg.conf+for+analog+monitor+ubuntu+&gs_l=serp.3..33i29i30.267756.268551.2.270448.5.5.0.0.0.0.164.780.0j5.5.0.les%3B..0.0...1c.1.5.psy-ab.F3-PEl8h0OY&pbx=1&bav=on.2,or.r_qf.&bvm=bv.43287494,d.aWM&fp=cb1b7779090da6f2&biw=1268&bih=668").

Beware of blogs or posts with information for older Ubuntu versions (earlier than 10.04) ; things change.  

Good luck!

---

