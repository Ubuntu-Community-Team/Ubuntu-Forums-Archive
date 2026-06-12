---
title: "[SOLVED] NVIDIA Confusion"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by MaxVK on 2008-07-28
I have been happily using Ubuntu since January on my old workhorse machine, and everything is fine. I have just installed Ubuntu (7.10) on my games system (Dual boot with XP) and I'm getting a bit confused about the NVIDIA drivers and settings.

The restricted drivers manager shows that I am using the NVIDIA drivers. Good so far, but now I want to use the settings for my card and I'm not sure what I'm supposed to use.

If I go into synaptic I can choose the logically named nvidia-settings, however, this says that it will uninstall nvidia-glx-new. Is this right? Isn't nvidia-glx-new my driver?

There is also nvidia-xconfig, which doesn't appear to want to remove anything.

Which settings program do I need, and is it right that one of them wants to remove nvidia-glx-new?

Regards

Max

---

### Post by Bachstelze on 2008-07-28
You don't need to install anything. The nvidia Settings Pannel has been installed with your drivers, and should appear in your menu. If it doesn't, you can run it with the command [font="Courier New"]nvidia-settings[/font].

---

### Post by MaxVK on 2008-07-28
Ah! Thanks for that. However, when I close the program my settings are not being saved and I get the following error:

ERROR: Unable to open file '/home/max/.nvidia-settings-rc' for writing.

any ideas how to fix this?

Thanks 

Max

---

### Post by MaxVK on 2008-07-28
Bah! Dumbass! I just used sudo nvidia-settings and the problem was fixed.

Now then, since this is a graphical app I need to use gksudo. Is this correct?


regards

Max

---

### Post by Bachstelze on 2008-07-28
> **MaxVK said:**
> 
Now then, since this is a graphical app I need to use gksudo. Is this correct?

Yes. However, you should **not** need to go root in order to write to a file that is in your home directory.

---

### Post by MaxVK on 2008-07-29
hmm. However, this file *is* in my home directory, its a hidden file, and it has the icon to show that it belongs to root, which is confirmed if I check the file properties.

Naturally the settings are saved as soon as I gksudo the nvidia-settings application.

So *why* does this file belong to root if it is not supposed to do so, and can I (safely) change its permissions? (and if so, how?)

thanks

Max

---

### Post by kdb424 on 2008-07-29
I think that it is like that because it is hidden. Random. You can sudo up your favorite file explorer and change the permissions. Should work fine.

---

### Post by Elfy on 2008-07-29
I have the same file - didn't know it was there, I have permissions for the file not root.

But to get nvidia-settings to save to the xorg conf file you do have to use gksudo or settings aren't saved.

---

### Post by MaxVK on 2008-07-30
Hmm, thanks guys. I *can* change the permissions of the file, but I still need to run it as root to get the config saved, so I just added gksudo to the launcher on the menu.

Thanks for all your help

Max

---

