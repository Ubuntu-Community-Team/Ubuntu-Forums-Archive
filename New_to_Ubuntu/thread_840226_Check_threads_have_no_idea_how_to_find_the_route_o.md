---
title: "Check threads have no idea how to find the route of my crashes"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by firechipmunk on 2008-06-25
Hi 

I know this issue is all over the website. I a complete noob. i can install a few things but thats about it. 

I was running ubuntu on a Intel D845GVSR mother board with 2.6 ghz, Geforce 6200 pci graphics card and 512 mb of ram. It ran fine. No crashes. I recently upgraded just my motherboard to an intel D101GGCL mother board with 3.0 ghz HT. I now am having random crashes. Tried ACPI=off from terminal each time i boot up but still get crashes. Ive checked the Xorg.0.log and cant seem to see anything. Tried both installing nvidia drivers manually and throught the restricted drivers option

Anybody have any clues. Which logs should i concentrate looking. is there any software that will monitor crashes

Thank you

---

### Post by codeslicer on 2008-06-25
Did you try running Ubuntu in recovery mode (available as an option from the GRUB bootloader when you first start your computer)

Or did you check the System Log? It's found at System->Administration->System Log.

If that doesn't work, you can try reconfiguring Xorg by running this command in a terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

Good luck! :)

---

### Post by firechipmunk on 2008-06-25
I will try your advice when i get home could you explain what

loading in recovery will do, is just to see if it will run stable?
what does reconfiguring Xorg do?

Thanks

Simon

---

### Post by codeslicer on 2008-06-25
Sorry for the late reply.

Recovery mode logs more consistent information and also turns off some features that may cause the bug. It may also allow you to reconfigure the X-Server.

Because you have changed your motherboard, your computer may not be adjusted to the new motherboard, resulting in crashes (What I think), and reconfiguring Xorg should update the configuration and hopefully fix any problems that you can fix.


Also, when your computer "crashes", can you still press Ctrl+Alt+Backspace? This will quickly reset your desktop and log you out. Also, when the crash occurs, you might want to shut down by holding Alt+SysRq (Print key) and pressing these buttons in order: R, E, I, S, U, B. This basically unmounts the drives and ensures a safer shutdown then by just hitting the power button.

---

### Post by rbanavara on 2008-06-25
see it this way: there are 2 interfaces for linux. Command line interface & Graphical interface which is GNOME for ubuntu. You need to be sure where you have issues. is it with the system itself, which you can make out from Command line boot from recovery mode. If you have a stable system, then its the GUI (or some other component which is not loaded in recovery console mode) which is the culprit. the reconfiguring Xorg resolves issues with GUI interface.

EDIT: You beat me codeslicer!

---

### Post by firechipmunk on 2008-06-25
So i boot into recovery mode which loads a terminal shall I then type "startx" or "gdm start" in order to get a desktop up?

I have installed ubuntu 7.1/8.04 and xubuntu 7.1/8.04 multiple times and i have still have the random crashes. Because i have installed multiple version do you think my computer will be adjusted to the motherboard?

I will also try your button configurations to tonite. When the crashes occur its a full lock. ctrl+alt+F1 does not work mouse does not move.

---

### Post by markbuntu on 2008-06-25
Look in your other logs. Like the system log and kernel log and the messafe and dmesg log. These can sometimes catch a segfault or something just before the system crashes and give you a clue. They can also tell you if there are faulty modules trying to load or errors loading them, etc.

The System/Administration/System Log is a good friend when things like this happen.

---

