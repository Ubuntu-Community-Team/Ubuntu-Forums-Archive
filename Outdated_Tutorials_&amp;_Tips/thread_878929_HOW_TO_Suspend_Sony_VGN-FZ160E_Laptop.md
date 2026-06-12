---
title: "HOW TO: Suspend Sony VGN-FZ160E Laptop"
date: 2008-08-03
forum: Outdated Tutorials &amp; Tips
---

### Post by dwitkin on 2008-08-03
[SIZE="3"]I have a Sony VGN-FZ160E laptop. I'm posting this message because I've finally gotten the laptop's suspend mode to work after much trial and error, and wanted to share the configuration changes that appear to have allowed that to happen. 

I'm currently running 8.04 with KDE, but I was previously running Ubuntu 8.04 with GNOME and had the same suspend issue.

The key appears to be in the file acpi-support located in the /etc/default/ directory. I made a number of changes to this file and cannot completely identify exactly which change or combination of changes made the difference, but the settings below work for my Sony FZ160E.

To update the acpi-support file:

1. Open a terminal window.

2. Change to the /etc/default directory
```
cd /etc/default
```

3. Make sure the file is present
```
ls -l acpi-support
```

The terminal should respond by showing you information about the file.

* Note: Thanks to Rocket2DMn for noticing that this step was missing and suggesting that it be added *
4a. Backup the file. At the command prompt, type:
```
cp acpi-support acpi-support.bak
```

4b. As root, open a text editor to edit the file. The following command uses gedit to open / edit the file. You will be prompted for your password after you enter it:
```
gksudo gedit acpi-support
```

5. Replace _all_ of the text in your file with the following text.
```

# Date: 2008-08-02
# File: /etc/default/acpi-support
#
# This file / configuration seems to allow suspend and resume on my Sony
# FZ160E laptop. Note that I loaded an ATI display driver package
# called "xorg-driver-fglrx" using the Ubuntu repositories and the
# Synaptic package manager. When I press the power button and then
# choose the suspend option, it takes a few seconds but works.
# Then, I press the power button again and it resumes to a password
# protected screen saver.
#
# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
# Changed on 2008-08-02 from ""
MODULES_WHITELIST="fglrx"

# Should we save and restore state using the VESA BIOS Extensions?
# Changed on 2008-08-02 from true
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
# Changed on 2008-08-02 from true
POST_VIDEO=false

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
# Changed on 2008-08-02 from true
USE_DPMS=false

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# Changed on 2008-08-02 from commented out
RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

# Spindown time on battery
SPINDOWN_TIME=12
```

7. Reboot the laptop.

8. Login normally.

9. Press the power button and choose the "Suspend" option. The laptop should suspend within about 10 seconds.

10. From the suspend state, press the power button. The laptop should resume to a screen saver within 10 seconds. Enter your password and your desktop should be restored.

I'm also attaching the actual copy of my acpi-support file to this post in case you'd like to save yourself the typing and overwrite your existing file. If you choose this method, make sure to backup your current file before overwriting it with the attached version. Also, to upload the file to this forum, I had to add a ".txt" extension. Rename the file to remove the extension when you place it into the /etc/default directory (i.e., the file name should be acpi-support without any extension).

This file configuration worked after trying a number of various combinations of acpi-support settings. Hope it helps.[/SIZE]

---

### Post by Rocket2DMn on 2008-08-06
You may want to have users make a backup of the acpi-support file before any changes are made to it as step 3.5, there is a backup of the original no matter what changes are made.

---

### Post by rebegin on 2008-09-01
hey,
thanks!!
it works like a charm on my sony vaio VGN-SZ740N :D
i'm going to copy it to the wiki page of my model and write your nick and link of the page too. i hope it's not a problem ;)

---

