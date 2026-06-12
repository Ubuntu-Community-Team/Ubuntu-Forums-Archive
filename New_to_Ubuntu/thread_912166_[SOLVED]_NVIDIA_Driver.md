---
title: "[SOLVED] NVIDIA Driver"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Harpz on 2008-09-06
Im new to Ubuntu and was having some graphics issues with World of warcraft and wine so i decided to download and installed the latest Nvidia driver with EnvyNG.

After EnvyNG was finished and i had rebooted it showed if i went to NVIDIA X Server Settings 
```
NVIDIA Driver Version:173.14.12 
``` which is the version that EnvyNG iinstalled.

I then went to System -> Administration and selected Hardware Drivers and it showed that the NVIDIA accelerated graphics driver (latest cards) was not enabled.

I enabled it and it downloaded the 1.69 version of the driver and installed it. (being a noob i didn't cancel it)

Now after the reboot NVIDIA X Server Setting gives me:
```

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
```

I can now on longer change my visual effects settings in Appearance Preferences they are stuck on none :( also.

The graphics are no longer a smooth as they once were.

Whats the correct way to fix this issues and have the latest driver for my NVIDIA card?

All help appreciated.
Thanks 
Mike

---

### Post by grannyw on 2008-09-06
CODE:

sudo nvidia-xconfig




fix it

---

### Post by jbrown96 on 2008-09-06
check out your xorg.conf file and see if the nvidia drivers are enabled.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
```
```
sudo gedit /etc/X11/xorg.conf
``` replace gedit with kate if you use KDE. 
Find the section like this > Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "UseFBDev" "true"
    Option         "NoLogo" "True"
    Option         "NvAGP" "1"
EndSection


Change the driver line so it matches mine, save, exit and restart X with crtl+Alt+Backspace

---

### Post by men28 on 2008-09-06
When I replaced my Radeon video card with NVIDIA I had a lot of problems to install drivers and Envy resolved all my problems.

I remember when I ran NVIDIA X Server Settings this program changed configuration files without my permissions. Change your resolution settings with something else ( for example with System Settings menu in KDE ).

Try run Envy and then not to run NVIDIA X Server Settings.

I am new in ubuntu too. :)

---

### Post by Harpz on 2008-09-06
> **grannyw said:**
> CODE:
sudo nvidia-xconfig
fix it

Did this and it wouldn't let me view the settings :( just told me to do the same.

I have Driver "nvidia" in my xorg.conf

How would i remove all my drivers and stat from scratch as it says driver is enabled in System -> Administration -> Hardware Drivers but it runs slugguish, not like before i tried to upgrade driver.

Mike

---

### Post by Harpz on 2008-09-06
> **Icerat said:**
> Did this and it wouldn't let me view the settings :( just told me to do the same.

I have Driver "nvidia" in my xorg.conf

How would i remove all my drivers and stat from scratch as it says driver is enabled in System -> Administration -> Hardware Drivers but it runs slugguish, not like before i tried to upgrade driver.

Mike

Think i may have fixed it but not sure if what i did was correct.

What i did was go into synaptic Package manager and searched for nvidia and uninstalled anything with nvidia in it.

I then purged EnvyNG and reinstalled it.

Then I told EnvyNG to auto install the latest NVIDIA driver 173.14.12 and reboted once it was done.

My screen movements are alot smoother now and i can now change my visual effects settings in Appearance Preferences.

NVIDIA X Server Settings shows: NVIDIA Driver Version:173.14.12

I take it im now using this driver?

The only thing im not sure about is that System -> Administration and  Hardware Drivers does not show any drivers to enable in it at all, its blank.

Is this OK. 

Thanks in advance 
Mike

---

### Post by drs305 on 2008-09-06
> **Icerat said:**
> The only thing im not sure about is that System -> Administration and  Hardware Drivers does not show any drivers to enable in it at all, its blank.

Is this OK. 

I use EnvyNG on a couple of machines and this is normal for me.

The steps you followed are actually the ones recommended on the EnvyNG site - Remove all the current drivers, uninstall EnvyNG and then reinstall EnvyNG and allow it to install the drivers.

---

### Post by Harpz on 2008-09-06
> **drs305 said:**
> I use EnvyNG on a couple of machines and this is normal for me.

The steps you followed are actually the ones recommended on the EnvyNG site - Remove all the current drivers, uninstall EnvyNG and then reinstall EnvyNG and allow it to install the drivers.

:) never looked at the site.

Only prob i got to figure out now is why my wow + wine crashes out when loading into game :(

Mike

---

