---
title: "mp3 player + amarok = me confuzled"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-04-27
How do i connect my mp3 player up to amarok? its a meizu miniplayer M6 it supports mtp and also drag and drop but i want to try and use it with amarok:lolflag:

thanks in advance

---

### Post by SOULRiDER on 2008-04-27
As far as I know, connecting your device is enough, and you can manage it from Amarok in the Devices tab at the bottom left of your screen.

[img] http://img255.imageshack.us/img255/6104/snapshot1ih4.png[/img]

---

### Post by swimm3r137@gmail.com on 2008-04-27
> **kamitsukai said:**
> How do i connect my mp3 player up to amarok? its a meizu miniplayer M6 it supports mtp and also drag and drop but i want to try and use it with amarok:lolflag:

thanks in advance

ya dawg, all u do is:
1) open amarok
2) settings>configure amarok
3)mobile devices
4) click either "auto-detect" or "add device"

theoretically, this should work homie :)

---

### Post by ssadhale on 2008-04-27
One word of caution though. Sometimes such devices will work or not depends upon their firmware. I had a t30 iRiver. Which I could never get to connect to my gutsy box because its firmware didnt allow. The solution to that was to download the new firmware from iRiver site and upgrade my players firmware. But i have heard some horror stories of doing so, from some other users. After upgrading the firmware their player became completely useless. It didnt even start. Not to scare you, but be careful before you get totally desperate and take any such drastic steps.

---

### Post by monktbd on 2008-04-27
One thing you can try additionally is to put an
```
mtp-detect
```
into the pre-connect-command field in Settings -> Configure amarok -> Media devices -> Configure device settings (for your device).

I have to do that for mine if i want to have it in mtp mode although I prefer using MSC mode and use normal file tranfers with nautilus.

---

### Post by kamitsukai on 2008-04-27
OK i have tried some of your suggestions but it still cant see my mp3 player if i click auto-detect i just get an error saying nothing is connected...

---

### Post by Wartooth on 2008-04-27
I'm in the same boat with my Creative Zen Microphoto 8GB player.  I've tried a few different things, nothing has worked, it's as if the device simply does not exist.  

I've installed something called MTPfs as I'd read that can help, no change.  I've created a mounting point (although I'm rather frustrated by how I've been searching and haven't really found a good explanation of the logic or the 'whys' of mounting just yet).  

Hopefully this thread will lead to some solutions :)

---

### Post by kamitsukai on 2008-04-27
well my mp3 player works fine in rythmbox but i would prefer amarok :)

---

### Post by aigelonic on 2008-04-27
Instead of autoconnect, did you try to manually add the device, as stated above?
Go to Settings->Configure Amarok->Media Devices->Add Device.
Try to use the MTP Plugin when choosing the plugin.
When you have closed the configuration window and go back to devices, there should now be a MTP Media Device in the list under the Connect button. Choose this and try to connect.

---

### Post by kamitsukai on 2008-04-27
> **aigelonic said:**
> Instead of autoconnect, did you try to manually add the device, as stated above?
Go to Settings->Configure Amarok->Media Devices->Add Device.
Try to use the MTP Plugin when choosing the plugin.
When you have closed the configuration window and go back to devices, there should now be a MTP Media Device in the list under the Connect button. Choose this and try to connect.

tried this says that it cannot connect to the device...:(

---

### Post by Wartooth on 2008-04-27
> **aigelonic said:**
> Instead of autoconnect, did you try to manually add the device, as stated above?
Go to Settings->Configure Amarok->Media Devices->Add Device.
Try to use the MTP Plugin when choosing the plugin.
When you have closed the configuration window and go back to devices, there should now be a MTP Media Device in the list under the Connect button. Choose this and try to connect.

Okay, now I can see what is in the device, finally!  Progress!  However, it will only allow me these options when I click on an album or something:

Copy files to collection
Make media device playlist
Refresh cover images
Delete from device.

Is this due to the MTP thing?  Would choosing another plugin somehow make it playable?  

Getting closer, at least.  :)  Thanks!

---

### Post by aigelonic on 2008-04-27
Sorry, but I don't know much about MTP.
I have a Zen Vision mp3-player, which Amarok does not find. I used the procedure I described and Amarok found my device and manages to list all the songs, but I does not manage to play songs from it. 
I've tried to use the other plugins, but without any results.

You might get some tips from this thread:
[http://ubuntuforums.org/showthread.php?t=553294&page=2](http://ubuntuforums.org/showthread.php?t=553294&page=2)

---

