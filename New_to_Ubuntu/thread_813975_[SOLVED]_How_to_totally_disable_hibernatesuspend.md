---
title: "[SOLVED] How to totally disable hibernate/suspend?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Triple_X on 2008-05-31
Hello all.

I am running Hardy (latest with all updates) on a Dell Optiplex GX630.
P4D 3.2GhZ, 4GB RAM, ATI Radeon x1950PRO 256MB, 80GB HDD.
/ = 10GB
/home = 65GB
/swap = 5GB

After about 30 minutes of non-use, my system hibernates (or suspends). I am unable to wake it up. I must hard boot it.
The same happens when I select Hibernate from the shut down menu.
I have disabled Power Management in all places I know.
System>Preferences>Power Management = Never.
Boot Up Manager = powernowd.early, apmd, acpi-support, acpid, powernowd, and laptop-mode all disabled.
No DPMS option in xorg.conf.

My ACPI-SUPPORT file:

```

# Comment the next line to disable ACPI suspend to RAM
#ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
#ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
#ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES="ptyq4"

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
#USE_DPMS=true

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
# RESET_DRIVE=true

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

So what am I missing? I am getting pretty desperate at this point, it is very annoying (and dangerous to my data).

Thanks for the help!

---

### Post by InfinityCircuit on 2008-05-31
Your problem is very strange.  However, if you want to totally disable these features, you can do the following:

1) back up /usr/lib/hal/scripts/linux/hal-system-power-{suspend,hibernate}-linux

2) Change the contents of those files to say:
```
#!/bin/sh

:
```

3) restart HAL

---

### Post by Triple_X on 2008-05-31
> **InfinityCircuit said:**
> Your problem is very strange.  However, if you want to totally disable these features, you can do the following:

1) back up /usr/lib/hal/scripts/linux/hal-system-power-{suspend,hibernate}-linux

2) Change the contents of those files to say:
```
#!/bin/sh

:
```

3) restart HAL


Thank you much, will give that a try and report back soon!

---

### Post by Triple_X on 2008-05-31
This did not work. :(

Any other ideas?


Thanks again.

---

### Post by sayakb on 2008-05-31
Press Alt+F2 and type in gconf-editor and press Enter.
Navigate to /apps/gnome-power-manager/general
There, **uncheck** can_hibernate and can_suspend
Close the editor window..

---

### Post by Triple_X on 2008-05-31
> **LinuxIsInnovation said:**
> Press Alt+F2 and type in gconf-editor and press Enter.
Navigate to /apps/gnome-power-manager/general
There, **uncheck** can_hibernate and can_suspend
Close the editor window..

Thank you much, giving that a try now. Will report back.

---

### Post by Triple_X on 2008-05-31
argh. still no go.

Any other ideas please? This is getting frustrating! :)

---

### Post by Triple_X on 2008-05-31
:-({|=

---

### Post by Triple_X on 2008-05-31
Up again in desperation. help please!

---

### Post by Triple_X on 2008-05-31
bump for help

---

### Post by Triple_X on 2008-05-31
no one?

---

### Post by Triple_X on 2008-05-31
one more bump for desperation. :(

---

### Post by Triple_X on 2008-06-01
bump!

---

### Post by jamesstansell on 2008-06-02
Just curious - have you checked on the Dell forums?

---

### Post by Triple_X on 2008-06-03
> **jamesstansell said:**
> Just curious - have you checked on the Dell forums?

Hi James :)

No, I have not posted there (yet)...I have it posted in two places right now, and didn't want to push my luck. I have already been warned of excessive bumping. :(

EDIT: Have it posted here as well: [http://ubuntuforums.org/showthread.php?t=814311]("http://ubuntuforums.org/showthread.php?t=814311")

---

