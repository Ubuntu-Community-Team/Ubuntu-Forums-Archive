---
title: "HOWTO: Fix Feisty NVIDIA Problems"
date: 2007-04-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Kimm on 2007-04-24
[CENTER]**WARNING NOTE OF DOOM:** This works for **ME**, there is no guarantee that it will work for you! (actually, it is only a theory that it should work for most other prople...)
You should also understand that this will limit you to one screen resolution/update frequenzy (the others will be there, but they may cause you to "revert back"
This might also only work in XFCE/GNOME/KDE (point 4)[/CENTER]

**1.** Make a backup of your xorg.conf 
This is an **important** step, since you might want to revert back to the old one, if the NVIDIA drivers are fixed in the future!!

> 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup


**2.** Install nvidia-settings

> 
sudo apt-get install nvidia-settings


**3.** Run NVIDIA settings **as root**
Click on "X Server Display Configuration" and plainly change whatever is wrong with your X Server (in my case, it was the Update Frequenzy, unfortunently people are having different problems with the X Server, so I cant go in any more closely on what you should do). When you are satisfied, click on "Save to X Configuration File", this will make sure that the changes you have made are permanent!

**4. Only if you are not using an English keyboard (like me):**
Your keyboard layout will now be english, to change this you need to go into the configuration manager of your Desktop environment and change the layout to whatever corresponds to your language (in my case, using XFCE, I had yo use the GNOME configuration tool).

**5. Only if you are using TV-Out (and the TV has turned black and white):**
You need to add these lines:

```

    Option         "TVOutFormat" "SVIDEO"
    Option         "TVStandard" "PAL-G" 

```

to the device section that corresponds to your TV. In my case, it looks like this:

```

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "TVOutFormat" "SVIDEO"
    Option         "TVStandard" "PAL-G" 
    BoardName      "GeForce FX 5500"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

```

**THE END**

I understand that I might have been a bit "unclear" about some of the instructions, but it is not very easy to be clear when different people experience different problems!
I hope this can help someone anyway :)

---

### Post by dcstar on 2007-05-02
Some people have also found that the Feisty** nvidia-settings** package does not run on their systems (like me!, apparently it is a known bug).

My solution was to install the Edgy version of **nvidia-settings** (which works on my Feisty install) using this generic procedure:

   1. Manually download the old .deb package (from the old repository or wherever);
   2. Remove the package you want to replace with an old version;
   3. Install the old package;
   4. Use the "Lock Version" feature in Synaptic on the package.

---

### Post by amd321 on 2007-09-13
hello, 
i have a problem , i see only white and blue.  i got component device and the computer think that i have composite. have can i change it?

---

