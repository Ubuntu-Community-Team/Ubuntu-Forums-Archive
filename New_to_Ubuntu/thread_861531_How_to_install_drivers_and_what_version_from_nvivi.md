---
title: "How to install drivers and what version from nvivia???"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by sillyboy on 2008-07-16
Just installed my new Nvidia FX 5500 card.  I put the cd in and nothing happens.  I opened the cd up and there is no 'RUN' on the menu.  How do I install drivers in Ubuntu?  Also, I went to Nvidia site for latest drivers and don't know which ones to download.  There are 5 to choose from.:confused:

Thanks:)

---

### Post by SuperSonic4 on 2008-07-16
Have you tried 
System -> Administration -> Hardware Drivers

it's how I installed my nvidia driver

---

### Post by UbuntuNerd on 2008-07-16
Install the nvidia- drivers. Open synaptic (system > administration ) search for nvidia-driver you need and install. Or Add/remove programs interface (programs > add/remove programs at the bottom and search for nvidia new! Reboot. Now it should work with the nvidia driver (otherwise also install the linux-restricted-modules-generic - this includes all restricted formats to your kernel). Via synaptic or "sudo apt-get install linux-restricted-modules-generic" without the quotes.

---

### Post by RomeReactor on 2008-07-16
Hi. Just to comment on this, as SuperSonic4 and jperez78 pointed out, you can install the driver though the repositories, instead of downloading it from nVidia's site. This is the recommended way of installing programs and drivers in Ubuntu. However, in Synaptic (System->Administration->Synaptic) you get three different drivers, depending on how old your card is; another--perhaps easier--way to install the driver is to go to 'System->Administration->Hardware Drivers' and check the box for your card there, as SuperSonic4 said.

The drivers on the CD won't be of help because they're made for windows.

---

### Post by sillyboy on 2008-07-16
> **jperez78 said:**
> Install the nvidia- drivers. Open synaptic (system > administration ) search for nvidia-driver you need and install. Or Add/remove programs interface (programs > add/remove programs at the bottom and search for nvidia new! Reboot. Now it should work with the nvidia driver (otherwise also install the linux-restricted-modules-generic - this includes all restricted formats to your kernel). Via synaptic or "sudo apt-get install linux-restricted-modules-generic" without the quotes.

I don't know if the drivers installed.  I saw at the top of the screen to reboot the computer.  I did and the resolution was very high (I'm 60 years old and could not see the screen very well.) I then changed the resolution to 1024xwhatever and now all I get on screen is 4 columns and 4 pointers and a whole bunch of horizontal lines, and I can't read anything on screen.
I am writing this from my Windows computer.  I NEED HELP!!! Please

---

### Post by Barnetto on 2008-07-16
Start in recovery mode by pressing ESC on Ubuntu startup and enter recovery mode and login and in the terminal run this:

```
sudo aptitude install envyng-gtk
```


Run with System Tools > EnvyNG

Click Nvidia

then Install the NVIDIA driver (Automatic Hardware Detection)

and then Apply

Hope this helps, let me no.

Barnetto

---

### Post by RomeReactor on 2008-07-16
> **Barnetto said:**
> Start in recovery mode by pressing ESC on Ubuntu startup and enter recovery mode and login and in the terminal run this:

```
sudo aptitude install envyng-gtk
```


Run with System Tools > EnvyNG

Click Nvidia

then Install the NVIDIA driver (Automatic Hardware Detection)

and then Apply

Hope this helps, let me no.

Barnetto

This probably shouldn't be done when the drivers are already installed through Synaptic. The message to reboot the system means they are installed.

sillyboy, try rebooting and when Grub comes up, press ESC and then choose the 'Recovery' or 'Safe' mode. You should be able to correct the resolution there.

---

### Post by sillyboy on 2008-07-16
> **RomeReactor said:**
> This probably shouldn't be done when the drivers are already installed through Synaptic. The message to reboot the system means they are installed.

sillyboy, try rebooting and when Grub comes up, press ESC and then choose the 'Recovery' or 'Safe' mode. You should be able to correct the resolution there.

When I press esc when grub is seen I get a choice of 8 things
1st: Ubuntu  8.04.1 Kernel 2.6.24-19-generic
2nd: Ubuntu  8.04.1 kernel 2.6.24-19 generic (recovery mode)
3rd: U...     "        "   2.6.24-14 generic
4th: U...      "       "   2.6.24-14 generic  (recovery mode)
5th
6th ect.

When I pick the second one down (2nd) I get this on my screen:
Recovery Menu
Resume-Resume normal boot
DPKG- Repair broken packages
ROOT-Drop to root shell prompt
XFIX- Try to fix x server

I'm freaking lost!!

What ever I pick it reboots back to an unseeable screen.

Help

---

### Post by RomeReactor on 2008-07-16
Did you select 'XFIX'? This is the option you want.

---

### Post by sillyboy on 2008-07-16
No.  I will now.

Thanks

---

### Post by Barnetto on 2008-07-16
xfix does fix the res but i would do my post as it worked for me and i have the fx5500.

---

### Post by sillyboy on 2008-07-16
> **sillyboy said:**
> No.  I will now.

Thanks

OK all most everything is back to normal?:lolflag:.  I now have a empty folder sitting on my desk top and I can not get rid of it.  There is no delete in the right click menu.

---

### Post by Barnetto on 2008-07-16
delete on the keyboard???

---

### Post by RomeReactor on 2008-07-16
> **sillyboy said:**
> OK all most everything is back to normal?:lolflag:.  I now have a empty folder sitting on my desk top and I can not get rid of it.  There is no delete in the right click menu.

Do you get the 'Move to Trash' option in the right click menu? Does the folder have icons on it, like a lock?

---

### Post by sillyboy on 2008-07-16
There is no delete, with a right click.  I used the move to trash. Thanks

Is there some kind of list that would give the linux term and the Windows equivilent?

---

### Post by RomeReactor on 2008-07-16
> **sillyboy said:**
> There is no delete, with a right click.  I used the move to trash. Thanks

The absence of a delete option by default in the right-click menu is to prevent accidentally deleting a file or folder; you can enable this option in Nautilus (the file browser) by going to its 'Edit->Preferences' window, and on the 'Behavior' tab check the box that reads 'Include a Delete command that bypasses Trash'. Note that with this option enabled, 'Delete' will appear in the right-click menu, and that deleting files this way won't send them to the trash can, and *will delete the file permanently*. You should leave that option unchecked, unless you *really* need the option to delete files immediately instead of sending them to the trash can.

Pressing SHIFT+DEL when a file is highlighted will also permanently delete it, bypassing the trash.

Just be careful with these options, and don't use them on important files.

> Is there some kind of list that would give the linux term and the Windows equivilent?

Not that I know of; Ubuntu has some differences, but it's more about getting used to the (in some cases) slightly different terminology. Try the 'Help' button on the top panel; it has a lot of information regarding file management in Ubuntu.

Glad you got the problem solved.

---

