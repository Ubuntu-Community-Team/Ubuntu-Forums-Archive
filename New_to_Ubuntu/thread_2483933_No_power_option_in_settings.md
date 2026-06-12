---
title: "No power option in settings"
date: 2023-02-13
forum: New to Ubuntu
---

### Post by braincramps on 2023-02-13
I'm trying to change the time that my computer locks between activity and after reading, I realize it is in the "power" section, but when I go to activities and search for power as noted in the help section, I only see power statistics.  I have tried to search for it on the forum, but have been unsuccessful in finding it.  I'm running 20.10, instead of 20.04, could this be the reason?  Any guidance would be appreciate.
Thanks

---

### Post by MAFoElffen on 2023-02-13
Official support for Ubuntu 20.10 ended on July 22, 2021. You have not received any security updates since then... You now have other priorities of getting to a supported release.

---

### Post by TheFu on 2023-02-13
+1.  Ninja'd by MAFoElffen!

Support for 20.10 ended in 2021.  Please learn about non-LTS vs LTS releases.  If you can't commit 100% to installing a new OS every 6 months, then you need to only run LTS releases.  Most desktop LTS releases have 3 yrs of support.

So, first need to move to 22.04 and since 21.04 support ended, that means a fresh install.

---

### Post by braincramps on 2023-02-13
Thank you for the reply, I downloaded and ran 22.10 and misspoke, when I said 20.10.  I apologize for my error.  I know now that I should have downloaded the LTS version.  Is there a way to migrate backwards?  I now realize I don't have anyway to add a printer and I'm sure there are other things that are missing with this version.  You thoughts would be appreciated.  Thank you.

---

### Post by MAFoElffen on 2023-02-13
Do a good backup first... Then: [https://www.golinuxcloud.com/downgrade-ubuntu/](https://www.golinuxcloud.com/downgrade-ubuntu/) ... substituting jammy for focal. As it says, there may be unforseen problems. Therefor the backup to go back to, or to restore data.

Also reference: [https://askubuntu.com/questions/49869/how-to-roll-back-ubuntu-to-a-previous-version](https://askubuntu.com/questions/49869/how-to-roll-back-ubuntu-to-a-previous-version)

---

### Post by Dennis N on 2023-02-13
> when I go to activities and search for power as noted in the help section, I only see power statistics.
In the Settings section of the Activities screen, beneath the "Power Statistics" you will find "Power". That is what you want. You can also just type "Settings" to bring up the entire settings dialog and click "Power" on the left side.

As to 22.10, it is a matter of informed choice whether you use it or not. I'm using it because it is the first release that offers Gnome 43 and its improvements. Ubuntu 22.04 LTS uses Gnome 42, and  it is unlikely you will see Gnome 43 (or later) in an LTS until April 2024. When 22.10 goes out of support, I plan to do an upgrade to 23.04 from the Software Manager.

---

### Post by MAFoElffen on 2023-02-13
True. Of course with Interim releases, you are locked into doing a release upgrade every 6 months, because of lose of support... It is easier to stay with LTS releases, where you upgrade the release very two years, but is supported for 5 years.

Is a personal choice.

I test Dev Cycle releases (pre-release), but my daily driver is LTS.

---

### Post by grahammechanical on 2023-02-13
When you clicked Activities did you search for Settings? Another way is to look for Settings in the drop down menu we use to power off/log off. That will open a GUI utility that will allow us to adjust many settings.

Regards

---

### Post by TheFu on 2023-02-13
> **braincramps said:**
> Thank you for the reply, I downloaded and ran 22.10 and misspoke, when I said 20.10.  I apologize for my error.  I know now that I should have downloaded the LTS version.  Is there a way to migrate backwards?  I now realize I don't have anyway to add a printer and I'm sure there are other things that are missing with this version.  You thoughts would be appreciated.  Thank you.

Ah ... details matter when it comes to computers.  We all make mistakes, so no problem whatsoever.

Going backwards would depend on your backups.  Before migrating releases, hopefully, you did make a full system-level backup.  Over the years, I've learned that if I didn't have backups, then something bad would happen, but if I did, things would go more smoothly.  Odd how that works.

I'd say that adding a printer shouldn't be hard in any Ubuntu desktop since 2016.  It has been crazy easy since about that time for me.  

The trick is to ensure that avahi is working ... which will basically discover and install for us in about 10 seconds any printers.  I dislike avahi for many reasons, but I put it on my systems, install the printers, then remove it, because it makes that 1 task so very trivial.   

Just checked it.  I launched system-config-printer from a terminal (this is probably in some menu somewhere too) and it said "Printing service no available. Start the server on this computer or connect to another server. .... 
I pick "Connect" and a "Connect to CUPS server" modal window is show.  I fill in my print queue server computer name (it is in the LAN DNS), click "Connect" and I immediately see 5 choices ... 2 printers, a fax machine.  3of the 5 choices are for the same Black-n-White laser printer with a green checkmark for the default alias "laser" that I configured many, many, years ago.

Ok, so now I pull up a print dialog and see the installed/found printer names with "laser" already selected in the pull down menu.  That's not on 22.10.  Just last week, I deleted my play 22.10 install.  Let me reinstall 22.10 xubuntu ... it should fit in 10G, unlike the other versions.   Actually, I didn't even install it.  I use the "Try Xubuntu" option and found the printer tool, system-config-printer. Ran that and it already had populated 3 printers with ZERO action on my part.
The fax machine, the color inkjet and the laser printer that are connected to the other computer on the network. They each were already there with names like:
* BRFAX_romulus
* MFC240C_romulus
* Samsung_ML_1740_romulus
"romulus" is the name of the other physical computer on the network with the USB connections for each printing device.  In short, it "just worked".  

If it isn't just working for you, I'd encourage a thread for each separate issue, unless they are really related and tiny.

---

