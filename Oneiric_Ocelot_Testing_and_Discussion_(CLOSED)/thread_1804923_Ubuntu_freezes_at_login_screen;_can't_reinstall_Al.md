---
title: "Ubuntu freezes at login screen; can't reinstall Alpha 2 liveCD via USB drive"
date: 2011-07-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by zekopeko on 2011-07-15
I upgraded from Natty to Alpha 1 and kept the machine updated up to kernel 3.0.3. Now I get freezes at the login screen (LightDM), the mouse won't move and the keyboard doesn't work.

Booting in recovering mode freezes after recognizing my disks and USB mouse (I have a PS2 keyboard but even a USB one didn't help).

Ok, the perils of testing. I go and download the Alpha 2 LiveCD and manage to put Alpha 2 via USB startup disk creator on another Ubuntu machine. It displays the Ubuntu splash screen but after some time it just floods the screen with plenty of text (in high tty resolution no less even though I have an Nvidia card) and stops.

I would rather not use the alternate installer. 

Anybody with a fix?

---

### Post by cariboo on 2011-07-15
The solution to the mouse and keyboard freezing has been posted several times, so here it is once again:

> sudo mv /run/udev /run/udev.old

If you start in recovery mode, and choose netroot from the menu, you don't even need sudo.

---

### Post by zekopeko on 2011-07-15
> **cariboo907 said:**
> The solution to the mouse and keyboard freezing has been posted several times, so here it is once again:



If you start in recovery mode, and choose netroot from the menu, you don't even need sudo.

There is only one problem. I can't even get to that point in the recovery mode. As said above it displays the splash screen, then drops to text mode, stops after recognizing my disks and mouse.

---

### Post by jontxo on 2011-07-15
Hello

I have managed to login selecting the other option that appears alongside with the list of users. Once you select it you have to select the ubuntu 2d session, others doesn't work, and enter your user name and password.


Hope it helps.
Regards.

---

### Post by zekopeko on 2011-07-16
> **jontxo said:**
> Hello

I have managed to login selecting the other option that appears alongside with the list of users. Once you select it you have to select the ubuntu 2d session, others doesn't work, and enter your user name and password.


Hope it helps.
Regards.

Thanks for trying to help but I can't select anything because everything freezes at the login screen.

---

### Post by IanW on 2011-07-16
1: Press shift as soon as your PC boots to enter Grub Menu
2: Select latest kernel + "Recovery Mode".
3: Select "Command terminal with networking"
4: Enter the command Cariboo posted above.
5: enter "reboot now"

---

### Post by zekopeko on 2011-07-17
> **IanW said:**
> 1: Press shift as soon as your PC boots to enter Grub Menu
2: Select latest kernel + "Recovery Mode".
3: Select "Command terminal with networking"
4: Enter the command Cariboo posted above.
5: enter "reboot now"

Repeating AGAIN: I can't get Recovery mode to boot to a usable shell. It freezes as well as the regular boot (with X).

---

### Post by Quackers on 2011-07-17
If you are on a desktop unplug and re-plug your keyboard and mouse. They may then work and you can use the fix posted by cariboot907.

---

### Post by zekopeko on 2011-07-17
> **Quackers said:**
> If you are on a desktop unplug and re-plug your keyboard and mouse. They may then work and you can use the fix posted by cariboot907.

Thanks. This worked. No X freezes.

After that I couldn't login into any session because apparently after upgrading from the Recovery Console session my Nvidia driver was borked so no 3D support. I had to install gnome-session-fallback, login into Gnome Classic (No effects) and reinstall the nvidia-current package via synaptic. All is well now.

---

