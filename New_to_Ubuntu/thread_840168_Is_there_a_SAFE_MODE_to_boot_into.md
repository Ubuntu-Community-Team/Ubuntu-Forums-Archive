---
title: "Is there a SAFE MODE to boot into ?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by beatman on 2008-06-25
Hi, I'm back again after a year away from Ubuntu, I have just installed 8.10 and all was working well until I pushed my luck by going for the most superior graphics in system>preferences.
I was advised that I hade to download a Nvida update and asked to restart....
From booting this results in a black screen ??? 

How do I recover to undo my selection. is there any way to get to a SAFE MODE during booting the system  so that I can recover the installation... or do I have to delete ALL and start again ?

I am now typing this in Vista but would love to get back to my Ubuntu installation.. 
Any assistance would be appreciated, thanks in advance....

---

### Post by spiderbatdad on 2008-06-25
You can select failsafe gnome from the options menu at the login screen.

---

### Post by Canis familiaris on 2008-06-25
(1) Failsafe GNOME. = Safe Mode
In the login Window: Options->Session->Failsafe GNOME

(2) Recovery Mode = Safe Mode with Command prompt
In the GRUB menu select Ubuntu (Recovery Mode)

---

### Post by Canis familiaris on 2008-06-25
> **beatman said:**
> Hi, I'm back again after a year away from Ubuntu, I have just installed 8.10 
Are you using Intrepid or did you mistype 7.10 as 8.10?

---

### Post by RomeReactor on 2008-06-25
Hi. Try this if you can't get to the login screen: As you turn on the PC, you should see a screen with a counter going down to zero; press ESC then to access the menu (usually you only have three seconds to do so before the system boots normally). You should see paired listings of the kernels you have installed. Each pair represents booting normally or in 'Recovery Mode' or 'Safe Graphics Mode'. Select this and press start. Your system should be able to boot then.

---

### Post by beatman on 2008-06-25
Not a morning person.... Rome Reactor you were on the button...
I pressed escape selected the fist recovery mode> fix broken... same black screen.

I rebooted.. pressed escape again... selected second recovery mode> fix X server and now here I am typing this BIG THANK YOU from my Ubuntu 8.04 installation again.

Cheers my friend....

---

