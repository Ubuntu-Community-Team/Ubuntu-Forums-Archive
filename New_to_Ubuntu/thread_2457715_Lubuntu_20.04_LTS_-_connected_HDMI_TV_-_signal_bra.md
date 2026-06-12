---
title: "Lubuntu 20.04 LTS - connected HDMI TV - signal brakeing"
date: 2021-02-07
forum: New to Ubuntu
---

### Post by hrvojedbk on 2021-02-07
Hi,


First of all let me tell that I am a total beginner regarding linux. I did a clean install of Lubuntu 20.04 LTS, on my old Asus -x553ma laptop, so no dual boot only lubuntu. My problem is regarding external display (TV) connected via HDMI.


I have one monitor, connected via VGA to the laptop and  a TV connected to the laptop via HDMI. The displays are set to “clone” mode. The thing is that the HDMI signal to the TV starts to brake (it is manifesting with the TV screen going black for cca 2 sec.) The interval of this happening is totally random. Sometimes starts happening right after truning on the TV, and sometimes after half an hour/hour or so. And the frequency of the occurrence is totally random too – sometimes it is often and sometime is scares. I did not manage to find any conncetions with anything.


Note that I had windows 8.1 before instaling Lubunutu and all was ok. Ok, to be honest the “flick” would accure cca once per 2 weeks.


I bought a new gold plated cable from Delock– all the same.
I “played” with the resolutions ans refresh rates after googling – all the same
I set the sound output on “Analog Stereo Output” (via Pulse Audio) hoping that removing the sound from the HDMI data flow would do the trick, but nothing. 


I had some issues with the system not remmembering the display settings though, which I solved with these instructions:
( [https://askubuntu.com/questions/166777/how-can-you-make-a-sh-file-come-on-at-startup-in-lubuntu-12-04](https://askubuntu.com/questions/166777/how-can-you-make-a-sh-file-come-on-at-startup-in-lubuntu-12-04))


After extensive googling I haven’t found anything helpful. The nearest tip to a helpful one is this:
( [https://askubuntu.com/questions/812324/external-hdmi-monitor-blinking-after-upgrade-to-16-04](https://askubuntu.com/questions/812324/external-hdmi-monitor-blinking-after-upgrade-to-16-04) )
*As you can see it is for Ubuntu, which doesn’t have to matter, but the key thing is that I do not have the monitors.xml file to edit, as the tip sudgests.


I don’t know what to do, I am desperate, I use the comp. primary for waching movies and stuff on the TV and with the above mentioned issue it is imopossible to wach anything.


I wold be very greatfull for ANY help.

---

### Post by guiverc on 2021-02-07
For starters, the Lubuntu 20.04 LTS desktop is LXQt.

Your reference to [https://askubuntu.com/questions/166777/how-can-you-make-a-sh-file-come-on-at-startup-in-lubuntu-12-04](https://askubuntu.com/questions/166777/how-can-you-make-a-sh-file-come-on-at-startup-in-lubuntu-12-04) should thus be used with adjustment, as when it refers to the Lubuntu/LXDE desktop, that isn't your desktop.

Yes your system uses Openbox & parts of the page does apply, but parts do not. 

 Lubuntu 18.04 LTS was the last Lubuntu which used the LXDE desktop (*it's depreciated as it relies on the  upstream dead GTK2 libraries*).

I would likely explore booting a *live* system off thumb-drive and seeing if the issue occurs there (probably your Lubuntu 20.04 LTS first, but then I'd move to other systems using different kernels, maybe Lubuntu 18.04 LTS for example, especially an older build using 4.15 kernel or other kernel; ie. older than 18.04.5).  Your Lubuntu 20.04 system I assume is fully upgraded, thus is using the 5.8 kernel? but may have started on 5.4 kernel, so I'd aim for something different to that.

ie. I'd explore other *live* systems to see if the same occurs. If it does, does it occur on all *tested* live systems, or were there some where you didn't have the issue occur. I'd hope findings would provide some clue (if it occurs on all; I'd doubt changing configuration on Lubuntu 20.04 would thus help much).  I'd also likely test a non-Ubuntu build (where Lubuntu as a Ubuntu build; eg. a Fedora or something rather different as it's just testing, and not Mint or something based on Ubuntu)

The other thing could be video driver in use (different kernel versions tested using *live* may provide clues there), but windows 8 would be using a different *driver*/kernel.module.  I'd provide that detail, and easy way to get it is

```
sudo lshw -C video
```

where `sudo` raises privileges, `lshw` will list hardware, the -C will limit output to class=video. I wonder if that would provide clues, and should a *live* system work, I'd compare the `driver=` section & of course kernel version with what doesn't work.

These are just thoughts, as I don't know. It's just where I'd likely start.

---

### Post by guiverc on 2021-02-08
Also asked at [https://askubuntu.com/questions/1314730/external-hdmi-tv-set-as-second-display-blinking-brakeing-signal-randomly](https://askubuntu.com/questions/1314730/external-hdmi-tv-set-as-second-display-blinking-brakeing-signal-randomly)

---

### Post by ActionParsnip on 2021-02-08
Make sure you have the latest BIOS too

---

### Post by chrischang2021 on 2021-02-09
I read you description 
   -- assumed anything haven't been changed monitor setting etc. That do you try to reinstall the OS ( easier and low cost), 
   -- record anything rough temperature of laptop and loading etc. Maybe you can inspect some wrong.
   -- Random problem is harder to handle and sometime to found root cause. keep try.


      Good luck

---

### Post by hrvojedbk on 2021-02-09
> **guiverc said:**
> For starters, the Lubuntu 20.04 LTS desktop is LXQt.

Your reference to [https://askubuntu.com/questions/166777/how-can-you-make-a-sh-file-come-on-at-startup-in-lubuntu-12-04](https://askubuntu.com/questions/166777/how-can-you-make-a-sh-file-come-on-at-startup-in-lubuntu-12-04) should thus be used with adjustment, as when it refers to the Lubuntu/LXDE desktop, that isn't your desktop.

Yes your system uses Openbox & parts of the page does apply, but parts do not. 

 Lubuntu 18.04 LTS was the last Lubuntu which used the LXDE desktop (*it's depreciated as it relies on the  upstream dead GTK2 libraries*).

I would likely explore booting a *live* system off thumb-drive and seeing if the issue occurs there (probably your Lubuntu 20.04 LTS first, but then I'd move to other systems using different kernels, maybe Lubuntu 18.04 LTS for example, especially an older build using 4.15 kernel or other kernel; ie. older than 18.04.5).  Your Lubuntu 20.04 system I assume is fully upgraded, thus is using the 5.8 kernel? but may have started on 5.4 kernel, so I'd aim for something different to that.

ie. I'd explore other *live* systems to see if the same occurs. If it does, does it occur on all *tested* live systems, or were there some where you didn't have the issue occur. I'd hope findings would provide some clue (if it occurs on all; I'd doubt changing configuration on Lubuntu 20.04 would thus help much).  I'd also likely test a non-Ubuntu build (where Lubuntu as a Ubuntu build; eg. a Fedora or something rather different as it's just testing, and not Mint or something based on Ubuntu)

The other thing could be video driver in use (different kernel versions tested using *live* may provide clues there), but windows 8 would be using a different *driver*/kernel.module.  I'd provide that detail, and easy way to get it is

```
sudo lshw -C video
```

where `sudo` raises privileges, `lshw` will list hardware, the -C will limit output to class=video. I wonder if that would provide clues, and should a *live* system work, I'd compare the `driver=` section & of course kernel version with what doesn't work.

These are just thoughts, as I don't know. It's just where I'd likely start.

Hi,

I did a live boot from the instalation dvd of my Lubuntu 20.04 LTS, and entered the command for the video detailes - the detailes are identical to those when the command is entered on a HDD boot of the system. 

The glitch still happens in a live session. 

BUT - I figured that when I set my vga monitor as *inactive* in Arandr or in Monitor settings of the  LXQT configuration center - the issue stops! Furthermore, if I set the LAPTOP monitor to *active* (along with the hdmi tv) it is all well too!

It would seem that the issue accures only when the vga monitor and hdmi tv are both set to *active* at the same time (changing the *primary* value on any display has no effect on the issue) This all happens in a live session too. 

So, what could it be -is it the driver, I have no idea??

Still it is not much but gives me some confort knowing what to do if I want to watch a movie - de-activate the  vga monitor :)

Until I find a final solution - I still can use the comp as I intended.

---

### Post by Bashing-om on 2021-02-09
Hello Agohrvojedbk -

I do not see where you list the graphic's hardware - Nvidia - hybrid setup ?
then see:
[https://9to5linux.com/how-to-connect-your-laptop-to-an-external-monitor-on-linux-fix-for-hdmi-no-signal-issue](https://9to5linux.com/how-to-connect-your-laptop-to-an-external-monitor-on-linux-fix-for-hdmi-no-signal-issue)

[INDENT]my bit to try and gelp
[/INDENT]

---

### Post by chrischang2021 on 2021-02-10
happy you to solve the issue. I thought it will be sample to show to other people. for two or multiple run monitor.

---

### Post by hrvojedbk on 2021-02-13
Hi, 

Sorry I didn't post anything in response, in any case I figured that if I set bot displays on 1600x1200 resolution (in Arandr) everything works, furthermore it seems thata ANY resolution is ok besides the recommended 1920x1080. 

Here is mine graphic hardware (if it the right info :) )

VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0e)

---

### Post by hrvojedbk on 2021-02-21
There is a new development! :/ It seems that little by little my desktop starts to "shrink". The thing is after a few days ago first a finger-thick black bar appeared on the top of the desktop. Then yesterday the bar spread to the sides of the screen as well! The bars seem to represent a border to which the desktop content can be displayed, but still when I set, for example, a movie to full screen, it goes beyond the bar meaning it extends to the entire screen. The anomaly appears not to respond to resolution changes on any of the screens - regardless of what res. I set the bars are there. Furthermore a few seconds after boot the bars are gone and the desktop extends across the whole of the screens, but then they appear. I do not even begin to understand where to look for the corresponding setting. I tried in Arandr and in the LXQt monitor setting - whatever I do nothing seems to have affect to the mentioned bars. Please help!

The good thing it does not effect the movie full screen mode so I can, at least watch movies, but it is frustrating, furthermore when knowing it is progressing.

The thing is when I set the movie to full screen it does not

---

