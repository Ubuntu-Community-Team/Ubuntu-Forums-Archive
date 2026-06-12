---
title: "Can't restart, can only boot in recovery mode, can't change display resolution"
date: 2018-06-28
forum: New to Ubuntu
---

### Post by browntower on 2018-06-28
I've just installed Ubuntu 18.04 LTS on a newly built PC with a AMD Ryzen 5 2400G processor, a Gigabyte AB350m-DS3H motherboard, using an Acer Full HD 1920x1080 monitor (I don't know how much of this info is relevant).  I've run into a handful of issues so far that some Googling was not able to satisfy.

One, I can only boot in recovery mode.  Once I boot in recovery mode, I get the option to continue with regular boot, and it works fine.  What needs to happen to make a regular boot work and to happen automatically?

Two, restarting does not work, it simply shuts down the computer, although the power remains on; I have to press and hold the power button to shut off, then turn the computer back on. Is this be related to the inability to boot normally?

Finally, these issues came to light through several reboots in my attempts to manually add a display configuration for my monitor, since Ubuntu doesn't recognize my display ("Unknown Display"), and only gives me one option for resolution of 1024x768.  xrandr returns "Failed to get size of gamma for output default," which is the same error I get when attempting to add the configuration.  It also doesn't recognize the input as HDMI, it simply calls it "Screen 0", although I don't know if that is actually an issue.  It seems possible that drivers need to be updated, but I can't seem to manage that either.

Any help would be greatly appreciated!

---

### Post by oldfred on 2018-06-28
You may need a newer kernel than default currently in Ubuntu.
Or boot parameters.

       Asus B350M-A needs newer kernel that 18.04 default
[https://ubuntuforums.org/showthread.php?t=2391892](https://ubuntuforums.org/showthread.php?t=2391892)
MSI Tomahawk B350 with Ryzen R5 1600 New UEFI required
[https://ubuntuforums.org/showthread.php?t=2390475](https://ubuntuforums.org/showthread.php?t=2390475)
ASUS PRIME B350M-E major issues
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux)
ryzen acpi=off only 1 cpu, needs nomodeset & then nVidia driver instead
[https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu](https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu)

---

### Post by browntower on 2018-06-28
Thanks for pointing me in the right direction!  It seems like moving to kernel 4.17 has fixed the issues.

---

