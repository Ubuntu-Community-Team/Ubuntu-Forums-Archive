---
title: "uninstalling a windows program through wine"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by le singe on 2008-07-13
Hi, another question from me about wine.

First, I have to say how much of a help these forums are.  Maybe when I've asked enough questions and I know what I'm doing in Ubuntu I can start answering some.

So, trying to install both Steam and Half Life 2, I basically had some problems ejecting/unmounting the CD ROM in order to continue the multi-disc install.  I figured out what the problem was (omitting the : from the "wine eject d" command - heh) but in the process I messed around installing/trying to uninstall steam that now Steam is not letting me type my password at the login screen.

I want to try a clean uninstall of steam and any bits of HL2 that I installed off the first disc, then perhaps attempt reinstalling it all another time.  Thing is, I can no longer run the uninstall (navigating through wine>programs>valve>steam>uninstall steam) - when I click on it the uninstaller doesn't load.  Also, Steam is not recognized under wine's list of programs to uninstall.  Yet when I click on steam through wine, it opens and the login screen pops up so I don't think it is uninstalled.

Is there a way around this?  
If I just delete the entire valve>steam folder found in my home>.wine>drive_c would that be a full clean uninstall?  I know normally in windows you're supposed to run uninstall programs, if not residual files and registry items may remain.  Would simply deleting the program's folder from the .wine directory be problematic in any way?

---

### Post by philinux on 2008-07-13
Apps>Wine>uninstall wine software.

You will see a list of installed apps.

---

### Post by le singe on 2008-07-13
> **philinux said:**
> Apps>Wine>uninstall wine software.

You will see a list of installed apps.

Yeah, but when I go there the program is no longer listed, yet it is still installed as it will open.

---

### Post by philinux on 2008-07-13
If these are the only 2 apps you got then I would uninstall wine.

Delete the .wine directory from your home folder and start from scratch. That way nothing gets left behind to mess it up.

---

### Post by le singe on 2008-07-13
> **philinux said:**
> If these are the only 2 apps you got then I would uninstall wine.

Delete the .wine directory from your home folder and start from scratch. That way nothing gets left behind to mess it up.

okay, thanks for your help philinux.

One last question, is this way (deleting the entire .wine directory) preferable to using ubuntu's add/remove programs under applications>add/remove... ?

---

### Post by philinux on 2008-07-13
> **le singe said:**
> okay, thanks for your help philinux.

One last question, is this way (deleting the entire .wine directory) preferable to using ubuntu's add/remove programs under applications>add/remove... ?

The .wine directory is not removed by add/remove or synaptic. They are hidden config file folders.

Go your home folder press ctrl h then select .wine and delete it.

It will be recreated when wine runs the first time.

---

### Post by hackerseraph on 2008-07-13
the wine uninstall thing has always had a hold on my attention; I always wondered where the shortcuts where still being stored when I would uninstall a windows app. It kind of irks me in an OCD kind of way xD

---

### Post by rjklindsay on 2009-03-19
I have the same problem with Wine.
I installed ActiveSync into Wine, and now cant get rid of it.

ActiveSync created a Gnome menu Icon at Applications>Wine>Programs>ActiveSync.
There is no entry for ActiveSync under "Uninstall Wine Software",so I deleted all traces of ActiveSync from the c_drive.
Then I uninstalled the wine and wine-geco packages with synaptic, using the "Mark for Complete Removal" options, and finally deleted the /home/<user>/.wine folder.

However, as soon as I re-install Wine, the ActiveSync menu icon is back!
The only way I could get rid of it, was to 'delete' the icon from the Gnome menu. However, this just creates a xml file at /home/<user>/.config/menus/applications.menu
which tells the gnome menu to hide the ActiveSync icon.
So, the ActiveSync icon is still there, its just hidden now.

Unless someone has a better suggestion, my last resort will be to re-format my harddrive, to get rid of ActiveSync. 
Does anyone know how manually uninstall wine software?

---

