---
title: "Folder reference in older script.. Ubuntu's moved on?"
date: 2021-12-12
forum: New to Ubuntu
---

### Post by nginmu on 2021-12-12
Here is a snippet from a script written in 2006, reputed to work on Ubuntu 17.04 (at least the part of the script I'm looking at).

Part of a udev rules script.

I'm slowly picking my way through, getting a broadband modem working, I have posted the wider effort already in the hardware forum so if this would be considered a double post, mods please remove & my apologies

```

# add the new id in the qmi_wwan driver
SUBSYSTEM=="drivers", \
ENV{DEVPATH}=="/bus/usb/drivers/qmi_wwan", \
ATTR{new_id}="03f0 9d1d"

```

In my latest edition Lubuntu, /bus nor /bus/usb/drivers/qmi_wwan seem to exist.

However, /sys/bus/usb/drivers/qmi_wwan does.

I was hoping move my efforts to get the script working along some by modifying the hard coded references to suit.

Is that a half-sensible idea, or am I being crazy?

---

### Post by SeijiSensei on 2021-12-12
Of course it's a sensible idea, especially when using commands from a script as dated as this one.

Just change the ENV reference to "/sys/bus/..." and give it a try.

---

### Post by nginmu on 2021-12-13
This time I bothered to back up and remove the backup stick! Unfortunately no joy.. looks like there are many other issues also. It didn't seem to do any lasting harm to the system though, not that I can immediately discern. Maybe something will go bang in a week.. might reinstall anyway out of cautiousness.

---

