---
title: "Low resolution after reboot."
date: 2008-07-27
forum: New to Ubuntu
---

### Post by SandyM on 2008-07-27
Hi!! I am new to ubuntu and have been stumbled by a very critical problem.I enabled all repositories synaptic packaging manager. Then I downloaded certain packages and files as per my understanding of them through the details provided by synaptic. Afterwards I installed my Nvidia drivers.
Thereafter when I restarted ubuntu  I found that my PC was running on low resolution mode and ubuntu refused to recognise my 8800GT card.

Please help me revert this problem .I think some packages are conflicting with my display drivers,but i don"t know which.also i dont remember all the packages and iles i downloaded through synaptic. Also tell IF THERE IS ANY WAY WHICH CAN HELP ME RESTORE UBUNTU TO ITS DEFAULT WITH DEFAULT PACKAGES?

---

### Post by Troll_the_Great on 2008-07-27
I think you upgraded to kernel 2.6.24-20.Lots of people had problem with it because it comes from the proposed repositories.
When you reboot, press ESC if you don't see the Grub menu, and select an older kernel (like 2.6.24-19).
Post back any results.
Cheers!

EDIT: You said that Ubuntu won't recognize your video card.Did you look at System-Administration-Hardware Drivers?What does it says about your video adapter there?

EDIT 2: In System-Administration-Software Sources-Updates, uncheck (if they are checked) the boxes "Pre-released Updates (Hardy Proposed).

---

### Post by SpEcIeS on 2008-07-27
Have you tried altering your xorg.conf?

Here is an example of altering a **xorg.conf**. Try this out for a starters:
**[http://www.simplehelp.net/2008/05/29/how-to-increase-the-screen-resolutions-available-to-ubuntu-804-hardy-heron-while-running-in-parallels-desktop/](http://www.simplehelp.net/2008/05/29/how-to-increase-the-screen-resolutions-available-to-ubuntu-804-hardy-heron-while-running-in-parallels-desktop/)**

Also, give **Google** a try. :D

---

### Post by SandyM on 2008-07-28
> **Troll_the_Great said:**
> I think you upgraded to kernel 2.6.24-20.Lots of people had problem with it because it comes from the proposed repositories.
When you reboot, press ESC if you don't see the Grub menu, and select an older kernel (like 2.6.24-19).
Post back any results.
Cheers!

EDIT: You said that Ubuntu won't recognize your video card.Did you look at System-Administration-Hardware Drivers?What does it says about your video adapter there?

EDIT 2: In System-Administration-Software Sources-Updates, uncheck (if they are checked) the boxes "Pre-released Updates (Hardy Proposed).
Thanks a lot .You were right as I did check Pre-released Updates (Hardy Proposed) in proposed repositories and was using kernel 2.6.24-20.
Also advise me if I shoud use the latest Nvidia drivers downloaded from Nvidia website or should I resort to older versions downloaded from ubuntu hardware drivers manager. the latest version is 173.---- something and older is 169.---something (sorry this is what I remembered)

---

### Post by SandyM on 2008-07-28
> **Troll_the_Great said:**
> I think you upgraded to kernel 2.6.24-20.Lots of people had problem with it because it comes from the proposed repositories.
When you reboot, press ESC if you don't see the Grub menu, and select an older kernel (like 2.6.24-19).
Post back any results.
Cheers!

EDIT: You said that Ubuntu won't recognize your video card.Did you look at System-Administration-Hardware Drivers?What does it says about your video adapter there?

EDIT 2: In System-Administration-Software Sources-Updates, uncheck (if they are checked) the boxes "Pre-released Updates (Hardy Proposed).
Thanks a lot Troll_the_Great .You were right as I did check Pre-released Updates (Hardy Proposed) in proposed repositories and was using kernel 2.6.24-20.
Also advise me if I shoud use the latest Nvidia drivers downloaded from Nvidia website or should I resort to older versions downloaded from ubuntu hardware drivers manager. the latest version is 173.---- something and older is 169.---something (sorry this is what I remembered)

---

### Post by Troll_the_Great on 2008-07-28
> **SandyM said:**
> Also advise me if I shoud use the latest Nvidia drivers downloaded from Nvidia website or should I resort to older versions downloaded from ubuntu hardware drivers manager. the latest version is 173.---- something and older is 169.---something (sorry this is what I remembered)

If your video card is working I would suggest not to mess with it.If you really want the latest drivers, install them with EnvyNG.If you don't have it, open a terminal and type:
```
sudo apt-get install envyng-gtk
```.
After that you can find it under Applications-System Tools-EnvyNG.Run it and will install the drivers automatically (the menu is really easy).
Cheers!

---

