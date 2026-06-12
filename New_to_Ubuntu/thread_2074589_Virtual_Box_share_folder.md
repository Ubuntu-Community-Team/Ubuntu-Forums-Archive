---
title: "Virtual Box share folder"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by 3dmatrix on 2012-10-22
I know there must be a lot of discussion on several threads and websites about this but i am trying since a long time but not able to figure out any suitable option.

I opted for the folder on the linux host which i wish to share. The original name of the folder is Driver but i have nicknamed ubuntu.
and then when i pass the command at the Xp command prompt 

**net use x: \\vboxsvr\ubuntu**

or

**net use x: \\vboxsvr\ubuntu**

or

**net use x: \\vboxsvr\Driver**

I just get a **System error 53**

plz advise

.

---

### Post by 3dmatrix on 2012-10-27
Any Sugession !

---

### Post by asaleemsajid on 2012-10-28
When you start vbox and are in the guest operating system then


1.In the setting tabs of the virtual box you can select the shared folders.

2.Click the devices tab on the menubar and select shared folders.

Click the + icon and add folders. it is very intitutive.

---

### Post by howefield on 2012-10-28
Use the automount option...

---

### Post by 3dmatrix on 2012-10-29
> **howefield said:**
> Use the automount option...

Yes i tried all that b4 writing here.

---

### Post by deadflowr on 2012-10-29
Did you install the guest additions?

---

### Post by 3dmatrix on 2012-10-29
> **deadflowr said:**
> Did you install the guest additions?

Of course, else i will not be allowed to share folder.
The Virtual Box interface shows **Shared folder : 1** but it is finally not able to access it.

---

### Post by ccrs8 on 2012-10-29
Do you get the same error when you just type the following in Start->Run:
```
\\vboxsvr\ubuntu
```

---

### Post by s1baker on 2012-10-29
Are you included in the "vboxusers" group?

---

### Post by 3dmatrix on 2012-10-29
> **s1baker said:**
> Are you included in the "vboxusers" group?

Sorry for my ignorance but what is that ?

.

---

### Post by madinc on 2012-10-30
> **3dmatrix said:**
> Sorry for my ignorance but what is that ?

.

Show the output of this:

```
cat /etc/group
```

---

### Post by wheeze on 2012-10-30
EDIT: Just noticed your guest OS is Windows XP. Here's more info from the User Manual, [https://www.virtualbox.org/manual/ch04.html#sharedfolders](https://www.virtualbox.org/manual/ch04.html#sharedfolders)

---

### Post by 3dmatrix on 2012-10-30
> **wheeze said:**
> EDIT: Just noticed your guest OS is Windows XP. Here's more info from the User Manual, [https://www.virtualbox.org/manual/ch04.html#sharedfolders](https://www.virtualbox.org/manual/ch04.html#sharedfolders)

What is mentioned there which i did not do ?

.

---

### Post by wheeze on 2012-10-30
You tell us.

I erroneously posted info regarding a Linux guest OS. Once I realized my mistake I put a link to the User Manual instead of just emptying my post, since it seems you can't delete posts here.

FWIW

---

### Post by dannyboy79 on 2012-10-30
> **3dmatrix said:**
> I know there must be a lot of discussion on several threads and websites about this but i am trying since a long time but not able to figure out any suitable option.

I opted for the folder on the linux host which i wish to share. The original name of the folder is Driver but i have nicknamed ubuntu.
and then when i pass the command at the Xp command prompt 

**net use x: \\vboxsvr\ubuntu**

or

**net use x: \\vboxsvr\ubuntu**

or

**net use x: \\vboxsvr\Driver**

I just get a **System error 53**

plz advise

.not sure what you mean by, "The original name of the folder is Driver but i have nicknamed ubuntu."
can't you just use My Networking Places" -> "Entire Network" -> "VirtualBox Shared Folders" when inside windows xp?

did you follow a guide like this?
[http://www.giannistsakiris.com/index.php/2007/09/28/virtualbox-access-shared-folders-from-windows-xp-guest-os/](http://www.giannistsakiris.com/index.php/2007/09/28/virtualbox-access-shared-folders-from-windows-xp-guest-os/)

---

### Post by s1baker on 2012-10-30
I have XP running as a guest OS on Ubuntu.
In my "users and groups" on Ubuntu there is a group call "vboxusers" and it is checked on mine.
You may want to look and see if it is checked for you.
  

That said, if you have your shared folder set up and you are running XP now, but can't find your shared folder in XP, go to "start" and then select "control panel"
( This is classic XP ) then you will see a tab at the top of the "control panel" window called "folders".
Click on that and look at the left side and see if you can see your shared folder in there.
I made a desktop link for mine and I put it on the XP desktop.

---

### Post by kanikilu on 2012-10-30
I read somewhere that the "System Error 53" can be caused by many things (usually network/firewall issues)...how do you have the virtual network adapter configured? NAT? Bridged?

Also, for at least one person, simply using a capital letter for the drive made the difference between it working or not, e.g.:

```
net use X: \\vboxsvr\sharename
```

---

### Post by 3dmatrix on 2012-10-31
I think the attached pic will give a good idea abt what has been done on my system and will give reply to a lot of questions raised here.

---

### Post by kanikilu on 2012-10-31
> **3dmatrix said:**
> I think the attached pic will give a good idea abt what has been done on my system and will give reply to a lot of questions raised here. Ok, most of that looks fine, but you can definitely stop trying "\\vboxsvr\Drivers" since your share is clearly called "ubuntu"...

Anyways, it's an old thread, but a lot of people have reported that simply reinstalling the Guest Additions helped them with the same problem. Maybe give that a try? Can't hurt...

[http://ubuntuforums.org/showthread.php?t=844181](http://ubuntuforums.org/showthread.php?t=844181)

---

### Post by s1baker on 2012-10-31
My VirtualBox shared folder setting shows that my setting for access is "Full" and it is blank under the auto-mount setting. 

Otherwords, under the settings for the shared folder,
have only "make permanent" checked and try leaving read-only and auto-mount unchecked.

---

### Post by s1baker on 2012-10-31
also, my shared folder is not under "My Network Places" on my guest XP. It has it's own folder as shown in the attached. Note it is named as "XPshare on Vboxsvr"

---

### Post by 3dmatrix on 2012-10-31
Well, i can not make out where is that '**make permanent**' check box.

And sorry for my ignorance but after installing the '**Guest Additions**' now i can not locate it any where for reinstallation.

---

### Post by s1baker on 2012-11-01
close down XP and close the oracle virtualbox manager window.

In ubuntu, navigate to the folder you want to share.
Right click on the folder and select "properties. Select "permissions" and make sure that you, as the owner of the folder, have the folder access set to "create and delete files".
If you have button on there that says something like:
"apply permissions to enclosed files", then hit that to.

Run virtualbox and check the shared folder settings.
If that doesn't work, you may also may want to try another folder in you directory.




If you want to try and re-install guest additions, run XP, and then look at the top of XP ( or at the bottom if you are running XP in full screen mode ) and look under "devices"you will see a selection to install guest addtions.

---

### Post by 3dmatrix on 2012-11-01
> **s1baker said:**
> close down XP and close the oracle virtualbox manager window.

In ubuntu, navigate to the folder you want to share.
Right click on the folder and select "properties. Select "permissions" and make sure that you, as the owner of the folder, have the folder access set to "create and delete files".
If you have button on there that says something like:
"apply permissions to enclosed files", then hit that to.

Run virtualbox and check the shared folder settings.
If that doesn't work, you may also may want to try another folder in you directory.

If you want to try and re-install guest additions, run XP, and then look at the top of XP ( or at the bottom if you are running XP in full screen mode ) and look under "devices"you will see a selection to install guest addtions.


*** **Is the folder permission shown in the attachment ok for this sharing ?
*** **I can not figure out where i could reinstall Guest additions.

---

### Post by kanikilu on 2012-11-01
Are you using the default desktop environment? If so, the "Devices" menu should be at the top panel on your screen when you hover over it, just like all the global menu applications...

Secondly - I don't think you had the Guest Additions intalled in the first place, because it usually runs in your Windows systray, and I do not see the icon there in your screenshot.

BTW, the hotkey to install the Guest Additions is *Host*+D. On mine, the right CTRL key is the host key...

---

### Post by 3dmatrix on 2012-11-01
> **kanikilu said:**
> Are you using the default desktop environment? If so, the "Devices" menu should be at the top panel on your screen when you hover over it, just like all the global menu applications...

Secondly - I don't think you had the Guest Additions intalled in the first place, because it usually runs in your Windows systray, and I do not see the icon there in your screenshot.

BTW, the hotkey to install the Guest Additions is *Host*+D. On mine, the right CTRL key is the host key...

I am using **LXDE**.

I thought i have been able to sucessfully install Guest Additions. How can i find out if it has been done or not. If it is not done how can i install / reinstall it again ? Can any one kindly post a snapshot.

I will try out the hot key. Hope it works.

Thanx

---

### Post by s1baker on 2012-11-01
I think you may not in the proper "view" mode on XP to see the "devices" tab.

Try using your hot key to switch to "full" screen mode.

By default, the hot key to do this is usually :
Hold down the right "control" key and hit the "F" key.

This should allow you to switch back and forth between the screen views. When in full screen mode, position mouse at the bottom of screen and get the pop up panel and select "devices". You should see the "install guest additions" there.

---

### Post by kanikilu on 2012-11-01
Yeah, I'm pretty sure you are in what VirtualBox calls "Scaled Mode", which does not show the menus. Either go to fullscreen as s1baker suggested, or just press *Host*+C to get back to windowed mode.

---

### Post by 3dmatrix on 2012-11-03
B4 starting this thread i tried to install guest additions and it seemed it was done but in reality it was not. Thanx to you all, i could locate the problem and reinstall it. And yes Xp was running in scaled mode and so the devices tab was not visible.

Thanx a lot to all of you for helping me solve the problem.

---

