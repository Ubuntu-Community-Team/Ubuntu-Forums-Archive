---
title: "Ubuntu 12.04LTS black lines on screen"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by MonsterSound on 2013-03-03
Hello!

I am hoping someone may be able to shed some light on an issue that I have been having since installing my new OS.  :confused:

 

 I am new to the forum, but have been using Ubuntu for a number of years and have a basic knowledge of the OS but this issue has me stuck! So down to business... I have an AMD A6-3620 APU (64bit) with **AMD Radeon HD 6530D **and I have installed the **ATI/AMD proprietary FGLRX driver installed **(post released updates installed).

 

 The issue that I am having is that upon start-up once I have logged in I get numerous black horizontal lines flash on the screen. They are consistent and come on as soon as the screen logs in. I have discovered a temporary fix by opening the AMD catalyst control program and  changing the refresh rate to 30hrz even though this is the default and what it is set to in the first place... after applying this and clicking OK the lines disappear. I have been doing this every day for several weeks, but although this removes the lines they come back upon reboot and I have to go through the same process.

 

 I hope that someone can make sense of this. Please let me know if you need any further info.

 

 Thanks in advance.

---

### Post by Sef on 2013-03-03
How did you install the drivers: from the driver manager or through ATIs site?

---

### Post by MonsterSound on 2013-03-03
Hi Sef,

Thanks for your reply. I installed the driver via the driver manager.

Thanks

---

### Post by deadflowr on 2013-03-03
A refresh rate of 30 seems pretty low. Have you tried increasing it?
That's half of what a standard monitor would read.

---

### Post by MonsterSound on 2013-03-03
Hi deadflowr,

The refresh rate max is 30... I also thought it was low as my old monitor was running at 75! I am currently using an led TV via an HDMI which might have something to do with it, however it seems to look pretty good in terms of the display. Well apart from the black lines! 

Thanks.

---

### Post by MonsterSound on 2013-03-06
Any further help?

---

### Post by Bradley129 on 2013-03-06
I suggest gong back to additinal drivers manger and installing the regular stable drivers and not the post release ones i had this issue and using the stable ones fixed it the post release ones is very unstable i learned that the hard way once you get the regular ones installed remeber to deactivate the post release ones

---

### Post by cortman on 2013-03-06
It sounds as though you've installed the fglrx driver- I've always had better luck with the radeon (open source) drivers. If you want to try using the open source drivers instead, open /etc/modprobe.d/blacklist.conf and add the line

```
[FONT=Ubuntu Mono]blacklist fglrx_pci
```
[/FONT]
to the end of it. Save and reboot. If that doesn't work for you, you can unblacklist it by removing said line.

---

### Post by oleink on 2013-03-06
^this.  Also maybe get drivers from another source if that doesnt work.  You should not be getting such low refresh rates or lines on the screen

---

### Post by MonsterSound on 2013-03-06
Thank you for the replies...
So I have uninstalled the drivers (which I have done in the past to try and solve this issue) the problem now is that although the BLACK LINES HAVE GONE! The display is "zoomed in", by that I mean that the edges of windows and the unity bar etc. are off to the side of the monitor. 

Any suggestions?


Please note that on the subject of the refresh rate this is now set to 75 or atleast that is what is being indicated by CompizConfig Settings Manager.

---

### Post by MonsterSound on 2013-03-06
Update:
Since uninstalling the drivers which had been previously installed... and the black lines going (nearly solved) I have come across another issue. The sound no longer works via the HDMI output. Infact the HDMI option has been lost from the sound menu output options, as it was part of the driver package I presume. Any help on this would also be highy appreciated! :)

Thanks

---

### Post by cortman on 2013-03-06
> **MonsterSound said:**
> Thank you for the replies...
So I have uninstalled the drivers (which I have done in the past to try and solve this issue) the problem now is that although the BLACK LINES HAVE GONE! The display is "zoomed in", by that I mean that the edges of windows and the unity bar etc. are off to the side of the monitor. 

Any suggestions?


Please note that on the subject of the refresh rate this is now set to 75 or atleast that is what is being indicated by CompizConfig Settings Manager.

What is the output of 

```
xrandr
```

Does it give you the correct screen resolution as an option?

---

### Post by cortman on 2013-03-06
> **MonsterSound said:**
> Update:
Since uninstalling the drivers which had been previously installed... and the black lines going (nearly solved) I have come across another issue. The sound no longer works via the HDMI output. Infact the HDMI option has been lost from the sound menu output options, as it was part of the driver package I presume. Any help on this would also be highy appreciated! :)

Thanks

Check alsamixer (run that command in the terminal) to make sure you indeed don't have an HDMI option there.

If you don't, please post the output of

```
lspci | grep -i vga
 lshw -C video


```

as we'll need this info to make any more suggestions.

---

### Post by zrdc28 on 2013-03-07
I believe now you can go to "settings" and then "display" and change the resolution and you might be ok

---

### Post by MonsterSound on 2013-03-07
Hi Cortman,

Thanks for the info. I have spent hours trying to sort this out and after uninstalling the driver etc upon reboot the screen became unstable and unable to read! (it was zoomed into the top corner for some strange reason) I tried everything I could think of and in the end reinstalled Ubuntu as it was a pretty fresh install anyway. So I am now back to square one, I have had to reinstall the AMD catalyst control center and the black lines are back up and running! :(

Output of xrandr
```
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 1920 x 1920
DFP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 16mm x 9mm
   1920x1080      30.0*+   25.0     24.0     30.0     24.0  
   1776x1000      25.0     24.0     30.0  
   1680x1050      24.0     24.0  
   1400x1050      24.0     24.0  
   1600x900       24.0  
   1280x1024      24.0     24.0  
   1440x900       24.0  
   1280x960       24.0  
   1280x768       24.0  
   1280x720       60.0     50.0     59.9     24.0  
   1024x768       24.0  
   1152x648       50.0     59.9  
   800x600        50.0     59.9  
   720x576        24.0     25.0     50.0  
   720x480        24.0     30.0     60.0     30.0     59.9  
   640x480        24.0     60.0     59.9  
CRT1 disconnected (normal left inverted right x axis y axis)
```

Output of:

lspci | grep -i vga  lshw -C video```
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Radeon HD 6530D]
```

Please note that this is on a fresh install with the drivers reinstalled!... according to the Catalyst Control Center the refresh rate is back to 30hrz.

Thanks so much for the help so far!

---

### Post by cortman on 2013-03-07
Well, I wasn't interested in the output of xrandr with the proprietary drivers installed. I have no idea how to troubleshoot them and like I said I've never had a positive experience with them yet. If you get all the resolution options from xrandr with the open source driver loaded, it may be as simple as resetting the screen resolution. Or it may not be, can't say for certain.

---

### Post by MonsterSound on 2013-03-07
Cortman,

Understood... what would be your recommendation as to the best way to get the open source driver?

Thanks

---

### Post by cortman on 2013-03-07
> **MonsterSound said:**
> Cortman,

Understood... what would be your recommendation as to the best way to get the open source driver?

Thanks

If you blacklist the fglrx (proprietary) driver per my instructions earlier, the kernel falls back on the open source driver by default. It's already included in the kernel.

---

### Post by MonsterSound on 2013-03-08
Cortman,

Thanks for the reply and help. I have reinstalled with original driver I had... which was previously causing the black lines. As when I blacklisted the fglxr driver the open source once pushed most of the display off the monitor making the PC nearly unusable. However strange it may be the reinstalation of the driver has somehow worked and the black lines have vanished! 

Thanks.

---

### Post by cortman on 2013-03-08
Well, that's good I guess. *scratches head.
If it ever comes back post back. Good luck!

---

