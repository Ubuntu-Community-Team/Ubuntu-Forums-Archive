---
title: "Toshiba Brightness Keys Working Unusually"
date: 2014-07-13
forum: New to Ubuntu
---

### Post by basica on 2014-07-13
Wasn't sure where to put this, hopefully this section will do: 

I see the question regarding brightness on Toshibas asked a lot, and I personally managed to fix it by adding the **acpi_backlight=vendor** line to my grub boot options and I can now adjust the brightness via the Settings -> Brightness menu. However, my function keys still do not work properly. The function keys on my particular laptop are F2/F3 to adjust brightness, but on my system they simply suspend the computer.


Even more unusual, I discovered by accident that if I F5 and F6 together, or F6 and F7 together I can adjust the brightness up/down. Anyone have any ideas what's behind this and what I can do to fix it?

Forgot to add, this is for Ubuntu 14.04 and the laptop is a Toshiba C50-B032

---

### Post by Toz on 2014-07-13
A couple of suggestions:

First, you could try to re-map the F2 and F3 keys to see if it works. Have a look at the last entry (the one by MikeyBunny) [here]("http://askubuntu.com/questions/214129/brightness-control-doesnt-seem-to-work-on-a-toshiba-satellite-m115-laptop"), to see if it works. It may or it may not.

If not, you might want to look at other kernel parameters instead of acpi_backlight=vendor. I would suggest trying, one grouping at a time, the following:
- **acpi_osi=**
- **acpi_osi= acpi_backlight=vendor**
- **acpi_osi='!Windows 2012'**
- **video.use_native_backlight=1**
...boot the system with each set and try out both the slider and the keyboard shortcut keys.

You may wish to try the temporary method of trying out kernel parameters by following the instructions [here]("https://wiki.ubuntu.com/Kernel/KernelBootParameters").

---

### Post by basica on 2014-07-13
I tried your first suggestion regarding the key mappings, but was not successful. I'll have a go with these kernel parameters and let you know how I went

---

### Post by basica on 2014-07-13
I was unsuccessful on all attempts, the last option reproduced my semi-successful result with the option I mentioned earlier (i.e. I can use controls to change the brightness but not the keys) while the rest of the options did not allow me to change the brightness with the menu or the keys. I should also add I tried the acpi_oci= with a nomodeset earlier in the day, and my system did not like it one bit.

---

### Post by pqwoerituytrueiwoq on 2014-07-13
you may be able to make your own key combo, for example use the [super]+[F2]/[F3] and bind that to run a backlightx command, if it works
another script you can try is this one [http://pastebin.com/HzzHrS2g](http://pastebin.com/HzzHrS2g) you may need to adjust line 5

the xev command can be used to see if the OS gets to see the brightness key combo or if the bios suppresses it

---

### Post by basica on 2014-07-13
@pqwoerituytrueiwoq - Thanks for the suggestion, I came across this link [here]("http://ubuntuhandbook.org/index.php/2013/11/install-brightness-indicator-in-ubuntu-13-10-saucy/") not that long before you posted. By the looks of it this PPA has the same functionality as the script you suggested. Right now I have the shortcuts set to alt + up and alt + down. I think this will have to do for now. I'm assuming this is a bug of some kind though, who does this go to - the ubuntu guys or somewhere upstream?

---

### Post by pqwoerituytrueiwoq on 2014-07-13
probably a kernel bug bugzilla.kernel.org

---

