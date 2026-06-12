---
title: "issue with nvidia-settings only when remote desktop is used from Windows 10"
date: 2018-10-24
forum: New to Ubuntu
---

### Post by mstrozier on 2018-10-24
Hello all, I'm completely new to ubuntu/linux as a whole.  However I do have extensive knowledge of Windows and IBM I-Series  / OS/400 and do development in RPGILE (20 years).  I've decided to tackle on Linux and have setup an old machine to work with running a FX-6300, MSI FX970 gaming MB, 16gb ram and a GTX 1050ti vid card (old gaming rig as my main machine is a Ryzen 2600 with GTX 1070).   

I have ubuntu installed and setup on a Samsung 64gb thumb drive (fit plus usb 3.1).   And so far working ok.  Took me 2 days to finally get all the updates and settings done so that the system is running stable and nvidia drivers are working correctly.  I have my card drivers at the latest nvidia release 410 and cuda cores library upgraded to 10.0.   This is the current release levels of Ubuntu I am running:
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic


Now when I am directly on this box, nvidia settings works correctly.  I can load nvidia x server app just fine.  I can change settings, which the main one is going into the GPU fan control and change from 30% to 60% (for some reason it remains at this level until the card reachs 70c then it starts to increase to 38% and finally 44%, just not enough to cool in my opinion).  I know in linux there isn't a direct method to set fan curves like in windows 10 using EVGA precision or MSI Afterburner.   So I'm manually selecting a sweet spot that works.

Now the issue I am having, as this all works perfectly while I am physically on this box.  The issue comes up when I am on my Windows box or my company laptop and I remote desktop into the Ubuntu box.  If I select nvidia X Server from the apps list, nothing happens.  If I go into terminal and type nvidia-smi that works fine, I see the current stats of my gpu.    However if I type nvidia-settings  I get the following error:

ERROR -- Unable to load info from any available system.

My profile is root access and this occurs rather I run the command as nvidia-settings or sudo nvidia-settings.   And again only when I remote in.   

How can I fix this?

---

### Post by mstrozier on 2018-10-24
I've also tried setting up a startup.sh file (called is startocgpu.sh) saved it to my desktop and added to the startup process.  Again, works fine when I'm physically on the box.  However once I sign off and remote desktop in, everything is back to original settings and cannot access nvidia x server.  :(  I'm assuming this has to be some form of setup, just can't figure it out.

---

### Post by mstrozier on 2018-10-24
Another update.  Got a work around for now.  Got the box running, start up script works fine while I am directly on the box and logged out of my session, however box still running.   Now when I remote desktop in, my GPU settings are in place, fans at 75%.   Just can't control them from the remote side however at least it's progress.  So for the meantime, when I need to make changes to the settings I'll just have to sign onto the box directly.

Only reason for this is that I'm leaving the box running with no monitor or keyboard, which is why I wanted to make these changes remotely but this will work.   Thanks

---

