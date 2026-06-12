---
title: "Restart/Shutdown problem after update"
date: 2011-09-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ArtLaForge on 2011-09-15
After this mornings update I can't shutdown the computer! Restart doesn't seem to go through a complete restart and shutdown drops to the login screen.  Interesting! Maybe a fix on the next update?:confused:

---

### Post by mdhollis on 2011-09-15
That's funny in gnome-shell I don't have any shutdown options.  I can shutdown and restart via the terminal with no issue.

---

### Post by ArtLaForge on 2011-09-15
> **mdhollis said:**
> That's funny in gnome-shell I don't have any shutdown options.  I can shutdown and restart via the terminal with no issue.

Yep, I can shutdown or restart from the terminal also. When I click on the icon "top bar" furthest icon to the right I can choose (sutdown) then the option to restart or shutdown. either choice will take me to the login screen. If I log in the screen shifts to the left hiding the unity icons. If I do a hard reset or power off the computer the restart works fine, log in and screen is centered. Only beta 1 looks like there is a ways to go. :P

---

### Post by RomeReactor on 2011-09-15
I'm getting that after today's updates, along with not being able to mount other partitions/disks with the error:
> Unable to mount XX GB Filesystem
Not Authorized
Where XX is the size of the partition. To mount or unmount partitions I have to use Disk Utility:
```
gksu palimpsest
```

---

### Post by ArtLaForge on 2011-09-15
Now I have lost unity?? I did another update/safe-upgrade and installed another 22 updates, several of which were unity updates.  After a reboot it appeared that I was in unity 2D, lost my 3D. Another reboot (from terminal) I had no unity at all. CCSM locked up and I rebooted to a plain desktop. No classic or unity.  I'll try some more hacking, see what happens.

---

### Post by Harry33 on 2011-09-15
Perhaps it is the new LightDM?
Did you all install the new version 0.9.6-0ubuntu1.

You may then try to downgrade it.

I can see this both in my 32-bit setup (with gnome-shell from Oneiric repos) and
in my 64-bit setup (with gnome-shell from Ricotz PPA).

---

### Post by ArtLaForge on 2011-09-15
> **Harry33 said:**
> Perhaps it is the new LightDM?
Did you all install the new version 0.9.6-0ubuntu1.

You may then try to downgrade it.

I can see this both in my 32-bit setup (with gnome-shell from Oneiric repos) and
in my 64-bit setup (with gnome-shell from Ricotz PPA).


I was up to date on LightDM, I think what got me was 1 unity lib file was removed on my morning upgrade and I didn't see any other unity files in the que. Now in my search for the fix I have discovered a RAM problem, so before I can go any further I need to go buy some new RAM. ):P

---

### Post by flipper T on 2011-09-15
just to add to the confusion : prior to latest updates, shutting down from the terminal or me menu would hang my laptop. now working fine.

:)

---

### Post by Harry33 on 2011-09-15
If nothing else helps:

1) To reboot
hold down Alt and SysRq, then holding them dow, write r e i s u b (one letter at a time)

2) To shutdown, see above, but the last letter is o instead of b

---

### Post by Harry33 on 2011-09-15
And here is the bug report (850995), thanks to Doug McMahon

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/850995](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/850995)

Go there and mark "affects me too".

---

### Post by mc4man on 2011-09-15
The new lightdm also does something else that's a bit more obscure though annoying here.

I generally make use of a .pkla to avoid passwords on some constantly used actions during dev, the new lightdm ignores it totally

For the few, if any, - 
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/851135](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/851135)
(I may try moving the .pkla from 50-local.d to 10-vendor.d though it really does belong in the local dir.

---

### Post by rtalcott on 2011-09-15
One machine has the problem and one does not...the one that does is an ECS board with onboard nVidia graphics and the other machine (which shuts down) is a gigabyte with AMD/ATI...both machines with AMD cpu's

EDIT: My error!  I thought the "working" machine was "upgraded" but it was NOT...after upgrade it does not shut down properly!
rt

---

### Post by RomeReactor on 2011-09-15
Downgrading lightdm to [0.9.5-0ubuntu2]("https://launchpad.net/ubuntu/oneiric/i386/lightdm/0.9.5-0ubuntu2") fixed all the issues here; switching to GDM also worked, but the user indicator (indicator-session, I think) wasn't diplayed.

---

### Post by vulfgar on 2011-09-15
> **ArtLaForge said:**
> Now I have lost unity?? I did another update/safe-upgrade and installed another 22 updates, several of which were unity updates.  After a reboot it appeared that I was in unity 2D, lost my 3D. Another reboot (from terminal) I had no unity at all. CCSM locked up and I rebooted to a plain desktop. No classic or unity.  I'll try some more hacking, see what happens.

Same here. I saw the file libunity5 was removed so I reinstalled it, but I still can't get unity to work.

Edit: Changed to gdm to see if it's the same bug, but unity still doesn't work,

Edit2: I started CCSM and "Unity MT Grab Handles" had been unchecked for som obscure reason. I checked it unity was up and running. Got a bunch of compiz-craches in the process.

Edit3: Filed a bug [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/851224](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/851224)

---

### Post by Harry33 on 2011-09-16
The restart / shutdown issue is fixed (like the unauthorised mounting issue too) with the latest update of lightdm, v. 0.9.7-0ubuntu1.

---

### Post by grandtoubab on 2011-09-16
> **Harry33 said:**
> The restart / shutdown issue is fixed (like the unauthorised mounting issue too) with the latest update of lightdm, v. 0.9.7-0ubuntu1.

Not Here :o :o
Still unable to shutdown the PC
it affects me with
@ubuntu-desktop:~$ lsb_release -a
LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu oneiric (development branch)
Release:	11.10
lightdm 0.9.7-0ubuntu1
gnome-session 3.1.91-0ubuntu2
linux-image-3.0.0-11-generic-pae 3.0.0-11.18

---

### Post by Harry33 on 2011-09-16
> **grandtoubab said:**
> Not Here :o :o
Still unable to shutdown the PC
it affects me with
@ubuntu-desktop:~$ lsb_release -a
LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu oneiric (development branch)
Release:	11.10
lightdm 0.9.7-0ubuntu1
gnome-session 3.1.91-0ubuntu2
linux-image-3.0.0-11-generic-pae 3.0.0-11.18

How did you try to shutdown?
Did you try
Alt+SysRq r e i s u o
or reboot with
Alt+SysRq r e i s u b

---

### Post by DogMatix on 2011-09-16
> **Harry33 said:**
> If nothing else helps:

1) To reboot
hold down Alt and SysRq, then holding them dow, write r e i s u b (one letter at a time)

2) To shutdown, see above, but the last letter is o instead of b

Whoa! I didn't know that!

---

### Post by ArtLaForge on 2011-09-16
> **Harry33 said:**
> The restart / shutdown issue is fixed (like the unauthorised mounting issue too) with the latest update of lightdm, v. 0.9.7-0ubuntu1.

So there really was a glitch, I had some RAM errors on a test so I wanted to fix that before continuing, the store also had some HDD's on sale so as long as I had the case open what the heck.  Since my main HD was an IDE and the rest SATA I replaced the IDE with another SATA, that solved another problem I was having with mixed IDE/SATA HDD's.  Downloaded the 9/15 daily, fresh install and I'm back up.  Thanks for all the posts I see I wasn't the only one affected.):P

---

### Post by grandtoubab on 2011-09-17
> **Harry33 said:**
> How did you try to shutdown?
Did you try
Alt+SysRq r e i s u o
or reboot with
Alt+SysRq r e i s u b

As it don't shutdown but put me back on Lightdm login screen, I press Ctrl + Alt +F1
on TTY1 windows terminal that opened, I logon with my admin user and then
[HTML]sudo halt[/HTML]

I submit a neaw bug
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/852084](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/852084)

---

### Post by Harry33 on 2011-09-17
> **grandtoubab said:**
> As it don't shutdown but put me back on Lightdm login screen, I press Ctrl + Alt +F1
on TTY1 windows terminal that opened, I logon with my admin user and then
[HTML]sudo halt[/HTML]

I submit a neaw bug
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/852084](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/852084)

Well shutdown your system the way told you:
Hold down Alt and PrtScn/SysRq,
Keeping those two pressed, write the following letters one at a time:
r e i s u o

Then start the system again and see if it works.

---

### Post by grandtoubab on 2011-09-17
> **Harry33 said:**
> Well shutdown your system the way told you:
Hold down Alt and PrtScn/SysRq,
Keeping those two pressed, write the following letters one at a time:
r e i s u o

Then start the system again and see if it works.

I am sorry but your way is not at all better than mine. My fingers are only five by hands and too short  :lolflag:
As of some updates from this morning it seems the standard shutdown works back again  ):P

---

### Post by Harry33 on 2011-09-17
> **grandtoubab said:**
> I am sorry but your way is not at all better than mine. My fingers are only five by hands and too short  :lolflag:
As of some updates from this morning it seems the standard shutdown works back again  ):P

OK :P
You may use our both hands, each little finger on those alt and sysrq, then with thumbs the letters r e i s u o.

---

