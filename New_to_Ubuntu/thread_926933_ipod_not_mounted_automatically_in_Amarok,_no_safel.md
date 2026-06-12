---
title: "ipod not mounted automatically in Amarok, no safely  disconnect possible"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by Cozze on 2008-09-22
Hi,

I configured my ipod in amarok and is displayed in the device tab, but I am still encountering a few problems:

1) when I connect my ipod it is not automatically mounted, even when I click on the connect button I get a message "media devices: no mounted ipod found". However, when I select the music folder (after clicking the ipod icon on my desktop) the files stored on my ipod are displayed in Amarok.

2) when I want to disconnect my ipod safely by clicking the disconnect button i get the following message "Post-disconnect command failed, before removing device, please make sure that it is safe to do so.

Anyone some advice,
Many thanks from the absolute beginner

---

### Post by qstraza on 2008-09-22
well i always umount the device from the console, thats all you can do, basically

---

### Post by clive littlewood on 2008-09-22
Hi

It appears that some types of ipod will give this error.

You should have an icon on you desktop when the ipod is mounted.

Right click on this and click unmount to be sure.

cl

---

### Post by Cozze on 2008-09-23
> **qstraza said:**
> well i always umount the device from the console, thats all you can do, basically

Hmm ... thanks but, like I said I am an absolute beginner :lolflag: could you give me some details about the exact command in console.

Thanks, Cozze

---

### Post by Cozze on 2008-09-23
> **clive littlewood said:**
> Hi

It appears that some types of ipod will give this error.

You should have an icon on you desktop when the ipod is mounted.

Right click on this and click unmount to be sure.

cl

Hi,

thanks for your help: I am getting there slowly ... mounting/connecting my ipod this way works just fine. but when I try to savely remove by right clicking the ipod I get following message

Unfortunately, the device system:/media/sdd2 (/dev/sdd2) named 'KOEN COSYNS' and currently mounted at /media/KOEN COSYNS could not be unmounted. 
Unmounting failed due to the following error:
Device is Busy:
Moreover, programs still using the device have been detected. They are listed below. You have to close them or change their working directory before attempting to unmount the device again.
                     USER        PID ACCESS COMMAND
/media/KOEN COSYNS:  koen       5681 F.... amarokapp

would be great if you could help.
Cozze

---

### Post by qstraza on 2008-09-23
well i use gtkpod and not amarok... 
but this "Device is Busy:" is becouse some one or some thing is still using it.

You cannot unmount the device if you are in its dir.

```
sudo umount /dev/sdd2
```

I think that if you "safely remove" the devices on windows, u can see the change on ipod, like, ready to disconnet (well ipod goes into the menu). But on linux, this cannot be achieved, at least i dont know how. Same goes for my nokia n95, after unmounting it, nokia still thinks that its attached...

---

### Post by mc4man on 2008-09-23
> when I connect my ipod it is not automatically mounted, even when I click on the connect button I get a message "media devices: no mounted ipod found". However, when I select the music folder (after clicking the ipod icon on my desktop) the files stored on my ipod are displayed in Amarok
That's because the ipod, while showing up **isn't mounted**, by clicking the icon your mounting it.
Right click on the ipod icon -> properties -> mounting. Click to enable 'mount auto....'


> i get the following message "Post-disconnect command failed

Ignore, but **always disconnect first from amarok** before removing as below

Amarok treats an ipod as a removable medium so it wants to 'safely remove' from the right click menu which doesn't work properly.

Atm the best way to **properly remove** an ipod is first **disconnect** from any app like Amarok. 
Then for a proper removal you have to use the konsole (
```
sudo eject /dev/[COLOR="Red"]sdc1
```[/COLOR] is mine 

Adjust red to match yours.  (hold your mouse cursor over the ipod icon  to get /dev/sd? in the pop up

When you properly remove, the ipods screen will switch from a red circle and x to the the ipod menu.

> the files stored on my ipod are displayed in Amarok

The other issue is that when set as the default (auto open, auto connect) the ipod is not *connecting properly* to Amarok .While it's connected it's loading *all the songs* into a playlist.

It should only show your Ipod playlists on left side and a blank Amarok playlist (which you would loads albums, tracks of your own choosing ect.
This is the fault of Kubuntu ans Amarok not you
See screen

I just figured a way in Kubuntu to plug in the ipod, have Amarok open and auto-connect properly as in screen. Based on this method for doing in ubuntu. ( basically just create the script, chmod it and then create a new notification using the script as it's launch command

Note: this is only for Ubuntu 8.04 not Kubuntu  
[http://ubuntuforums.org/showthread.php?p=5562637#post5562637](http://ubuntuforums.org/showthread.php?p=5562637#post5562637)

If you'd like I'll post a step by for Kubuntu

---

### Post by Cozze on 2008-09-24
Now this is what I call a usefull explanation, you rock :guitar:!! :)

And yes it would be great to have a step by for Kubuntu.

Thanks in advance, man




> **mc4man said:**
> That's because the ipod, while showing up **isn't mounted**, by clicking the icon your mounting it.
Right click on the ipod icon -> properties -> mounting. Click to enable 'mount auto....'




Ignore, but **always disconnect first from amarok** before removing as below

Amarok treats an ipod as a removable medium so it wants to 'safely remove' from the right click menu which doesn't work properly.

Atm the best way to **properly remove** an ipod is first **disconnect** from any app like Amarok. 
Then for a proper removal you have to use the konsole (
```
sudo eject /dev/[COLOR="Red"]sdc1
```[/COLOR] is mine 

Adjust red to match yours.  (hold your mouse cursor over the ipod icon  to get /dev/sd? in the pop up

When you properly remove, the ipods screen will switch from a red circle and x to the the ipod menu.



The other issue is that by default the ipod is not *connecting properly* to Amarok .While it's connected it's loading *all the songs* into a playlist.

It should only show your Ipod playlists on left side and a blank Amarok playlist (which you would loads albums, tracks of your own choosing ect.
This is the fault of Kubuntu ans Amarok not you
See screen

I just figured a way in Kubuntu to plug in the ipod, have Amarok open and auto-connect properly as in screen. Based on this method for doing in ubuntu. ( basically just create the script, chmod it and then create a new notification using the script as it's launch command

Note: this is only for Ubuntu 8.04 not Kubuntu  
[http://ubuntuforums.org/showthread.php?p=5562637#post5562637](http://ubuntuforums.org/showthread.php?p=5562637#post5562637)

If you'd like I'll post a step by for Kubuntu

---

### Post by mc4man on 2008-09-25
Two preconditions to getting auto open and a proper auto connect with amarok when plugging in the ipod.

The ipod must have been previously configured in Amarok
The **ipod must be set to mount automatically** when connected to your pc. (right click on ipod icon -> properties -> mounting -> ck. ' mount automatically' (should always show 'green arrow'

Suggested - In amarok -> settings -> configure amarok. I uncheck 'remember current playlist on exit'


[U]If your Ipod is connected remove with the sudo  eject /dev/sd? as previously noted and unplug.
[/U]
Open up dolphin (kmenu -> System -> Dolphin file manager) and in home directory right click -> create new text file. Name it ```
test1
``` **with no extension**. You can name it anything you want as long as it matches the notification command, for purposes of copy and paste from here just use test1

I'm fairly new to using kubuntu so I don't know what to make of this _ if you look closely there will be a period to the right of your cursor, I prefer to remove. Use your mouse to click the cursor to the right of the period and then backspace it away. 

Then copy and paste this into the file (test1

```
#!/bin/bash
amarok -m %d -m
```

Save and exit.
Open the konsole and run this

```
chmod +x test1
```
You should be *returned directly to your prompt* - no messages. close the konsole. 

Click on the kmenu icon -> 'System Settings' and under 'look and feel' open 'Notifications'. If the left box choose (highlight) ' Storage Media Notifications' (see screen 1.

Click 'add' and In the left side box highlight 'Mounted Removable Medium'. Then click on the arrow button to add to right side box (->). (screen 2

After it's added, change the name 'Unknown" to whatever you want (I used Ipod)

Click on the red X icon and pick whatever you want from box that opens (i picked the amarok icon

In the command box replace konqueror %u with this (see screen 2

```
./test1
```
Click 'OK' and then back in the notifications screen click 'Apply' (screen 1

Now plug in your ipod and you should see screen 3 (takes several seconds, the ipod is detected, mounted and the notify screen is called.

If you want you can ck. the 'always do' box and then choose 'Ipod' (you'll never see that pop up again)  or leave it so the notification box always pops up and just choose 'Ipod' to start and connect properly to Amarok. 

Note: Atm I have no idea how to revert from 'always do' to getting the popup.

That should do it, i don't think you'll have any problems if you follow exactly and use copy and paste on the code boxes.

Note
I've tested with both Amarok not running and running (Amarok icon in system 'tray' - *bottom panel right side*. It's worked fine though once with Amarok running a 2nd instance was opened. (Close 'amarok' and use amarok (2).  If for some reason that kepts happening then make sure Amarok isn't running when the Ipod is plugged in. (and let me know, I'll see if I can make it happen again to see why or how to stop.

final note about the eject command
If no other usb device is connected when you plugin the ipod then the same command will be used (ex. sudo eject /dev sdc) Your konsole keeps a history of commands used, after opening just use the up arrow on keyboard to parse, you can always double ck .with the mouse over ipod icon, saves typing

---

