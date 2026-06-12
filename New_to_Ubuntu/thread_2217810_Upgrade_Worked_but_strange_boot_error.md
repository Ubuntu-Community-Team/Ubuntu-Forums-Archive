---
title: "Upgrade Worked but strange boot error"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by wiggy25 on 2014-04-18
I have been using Ubuntu for a little while, and today installed the Xubuntu desk top to see what is what like.

I logged out of Unity which is set as default and logged back in selecting Xubuntu session I think it was.
Had a play about for a bit then logged back out and in to Unity.

I switched off the PC and on turning it back on later it starts up as Xubuntu, but fails all of the time.
I created a Live USB with Ubuntu 14.04 on hoping that I would get the option to upgrade the old version so as not to loose anything.

This all worked fine and did indeed upgrade, but when turing on the PC it starts up as Xubuntu, not Unity, there are no other desktop environments at all!
Any ideas or suggestions, I do have a number of things I don't want to loose and would like to have the Unity desktop back.

Thanks

Ian

---

### Post by grahammechanical on 2014-04-18
When we install an alternative desktop we get a login screen option to load that session and it becomes the default session. If we have automatic login then it will automatically login to the default desktop session.

Please confirm

1) that you do not have automatic login.
2) that you do not get an option at the login screen to select Ubuntu.

If Xubuntu is the default session then an icon of a mouse should be in the top right corner of the login panel. Upgrading to Ubuntu 14.04 would not have removed the Xubuntu desktop. But it may not have upgraded the Xubuntu desktop to the 14.04 version.

Have you tried going to the software centre and seeing if Unity is installed? If it is still installed (and why would it not be?) you can use the software centre to remove the Xubuntu desktop. Or re-install it if you wish to continue with it.

Regards.

---

### Post by monkeybrain20122 on 2014-04-18
BTW, if you just want an alternative desktop you should install xfce4 instead of xubuntu-desktop, you don't need all the default applications that come with xubuntu. Just log into xubuntu session and check the menu, you will find a big mess of duplications. :)

---

### Post by wiggy25 on 2014-04-18
> **grahammechanical said:**
> When we install an alternative desktop we get a login screen option to load that session and it becomes the default session. If we have automatic login then it will automatically login to the default desktop session.

Please confirm

1) that you do not have automatic login.
2) that you do not get an option at the login screen to select Ubuntu.

If Xubuntu is the default session then an icon of a mouse should be in the top right corner of the login panel. Upgrading to Ubuntu 14.04 would not have removed the Xubuntu desktop. But it may not have upgraded the Xubuntu desktop to the 14.04 version.

Have you tried going to the software centre and seeing if Unity is installed? If it is still installed (and why would it not be?) you can use the software centre to remove the Xubuntu desktop. Or re-install it if you wish to continue with it.

Regards.


I do have automatic login.
There is an option to select Ubuntu!! 
It's in a different position when logged out from XFCE.
This is why i'm confused, I was using Ubuntu and installed Xfce but that wasn't the default desktop.
I logged out of Xubuntu-session and back in to Ubuntu did a bit of stuff then shut down the PC when I came to switch it back on again it had the blue Xbuntu splash screen which failed to load, kept getting an error can't remember what now.
Hence trying to upgrade Ubuntu from 13.10 to 14.04
This worked but The PC only boots up as Xubuntu.

Need to see where Xubuntu is loaded and uninstall it now!

Very strange!

Cheers

Ian

---

### Post by wiggy25 on 2014-04-18
Ok,

In the software centre it doesn't show that Xubuntu is installed.
I have managed to log out and back in again selecting Ubuntu as the desktop environment.

When I shut down the PC it shuts down using the Xubuntu splash screen.
When I restart the PC it starts up with the Xubuntu splash screen but actually opens using the Unity desk top!

How can I remove the XFCE and Xubuntu desk tops when they are not shown in the software centre?
I could use the synaptic package manager but I'm unsure of exactly which packages to remove don't want to kill it completely!

Cheers

Ian

---

### Post by wiggy25 on 2014-04-19
I have followed the instructions for repairing/reinstalling Grub.

But when I switch on the PC it has the blue screen with Xubuntu showing.
It then opens to the Unity desktop and everything works fine.

When I log out there are no other desk top options to choose from, only Ubuntu.
I can log back in and everything works fine.
When I shut down the PC it shuts down with the blue sceen and Xubuntu being shown.

How can I take it back to Ubuntu?

Thanks

Ian

---

