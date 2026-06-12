---
title: "How to Save Settings"
date: 2016-05-05
forum: New to Ubuntu
---

### Post by Brad_Agera on 2016-05-05
This is the first time I have used Linux. I'm running Ubuntu 14.04 off a live USB with persistence. It is partitioned. How do I get it to save settings and files to the USB?

---

### Post by howefield on 2016-05-05
If the USB media has been created with persistence, it should save your changes automatically.

Are you saying, in your case, it doesn't ?

---

### Post by Brad_Agera on 2016-05-05
Yes. I had a friend make the drive and it is created with persistence. It is a 4G drive with about 500 megs for the user partition.

Is there a certain setting I need to enable? I have not installed it to the hard drive, and when boot up I selected the option to run it and not install. I dont want it on my HD just in case something happens, I have Windows to fall back on

---

### Post by howefield on 2016-05-05
No, if you have a bootable USB media created with persistence, any changes you make will be saved automatically.

Try it, boot it up and change the wallpaper - then reboot, does the wallpaper reflect your change ?

---

### Post by Brad_Agera on 2016-05-05
I did. Wallpaper, moved the installation file originally on the desktop, nothing works. I even backed it up and tried to restart and load the backup and it disappeared.

---

### Post by grahammechanical on 2016-05-05
We do not mean that. Open System Settings. There should be an icon for it in the launcher at the left side of the screen. Or click the power/cog icon in the top panel and select System Settings. Then go to Appearance and change the desktop background image (wallpaper) by clicking on an image in the right hand pane. The change should be instant. But will it stick? Shut down & restart to find out.

Another thing you can do is to open Libreoffice and create a document and save it to the Documents folder. Then shut down and restart. Your document should still be there. The changes we make persist just like they would if Ubuntu was installed to a hard disk.

None of this happens if we simply "burn" an ISO image to a USB stick for the purpose of running a live session or to install to the hard disk.

Regards.

---

### Post by arochester on 2016-05-05
There are 3 different ways of using a USB stick
1) Usual. This is like a LiveCD. All changes will be lost when you switch off.
2) With persistence. This is like having a Home folder on the USB stick. SOME things will be remembered ,only if saved to the persistence partition, BUT NOT ALL.
3) Full. This is, as it says on the tin, a full install. You have a full Ubuntu system on the USB stick. All changes are remembered. (Assuming your USB stick is big enough.)

---

### Post by Brad_Agera on 2016-05-05
I tried changing the wallpaper just like you said. It failed again. I am not sure what to do next. This doesn't make sense. How is the easiest way to make it a Full install?

Is there anyway that since my drive is only 4 gigs that it could be a problem?

---

### Post by arochester on 2016-05-05
"Ubuntu needs about 4.5 GB to install, so add a few extra GB to allow for your files." --- [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

---

