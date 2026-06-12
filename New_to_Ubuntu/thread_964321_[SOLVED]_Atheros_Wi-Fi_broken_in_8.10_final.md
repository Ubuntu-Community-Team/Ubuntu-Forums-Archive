---
title: "[SOLVED] Atheros Wi-Fi broken in 8.10 final"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by Westies on 2008-10-30
Title says it all. The PC is an Acer Aspire One netbook with an Atheros wifi chipset built in. I had installed Alpha 4 previously (I believe it was 4 at least) and the wifi connection did not function until I plugged in a cat5 cable and did a system update (which I believe at the time consisted of a new kernel amongst other things.) After rebooting the wireless worked fine.

Now that the final release of 8.10 is out, I decided to do a clean install and assumed the wifi would work fine out of the box. Unfortunately, after installing and applying any available updates I'm unable to get it to function. "Hardware Drivers" tells me that the drivers for the device are installed and it is in use, but no wireless connections come up under the Network Manager. Deactivating/reactivating the drivers had no effect.

Any ideas?

---

### Post by teaker1s on 2008-10-30
look here there is discussion regarding issue and either intrepid back ports or compiling madwifi
[http://ubuntuforums.org/showthread.php?t=894852&page=6]("http://ubuntuforums.org/showthread.php?t=894852&page=6")

---

### Post by Westies on 2008-10-30
Thanks. Installing the backports and adding modprobe ath5k to rc.local did it. I assume this is the driver that the alpha used before they switched over to the current one which doesn't appear to work. Makes me wonder why they'd switch, especially so close to release.

Here's another question for anyone willing to answer:
This has been bothering me in the alpha as well. I have the Network Manager set to auto connect to my home wifi network at bootup. Each time Ubuntu starts it asks for the default keyring password. Is there any way to remove the keyring password on the wifi? I don't want it to require a password just to get an internet connection.

Thanks again.

---

### Post by khowe on 2008-10-30
I installed linux-image-rt from multiverse and the ar5007 driver worked.  Just throwing out another option that maybe easy.

---

### Post by Westies on 2008-10-30
Thanks, I'll look into it :) Do the LED indicators work with those drivers? The ath5k drivers I'm using now don't seem to make any use of the LEDs.

---

### Post by teaker1s on 2008-10-30
led did work in previous hardy kernel. Intrepid I'm afraid so far ours doesn't light.

---

### Post by Westies on 2008-10-31
That's a shame, but oh well, it's not really a big deal.

Bump for keyring question.

edit: I suppose I'll ask the keyring question again some other time. I'll mark this as solved for now.

---

### Post by bumanie on 2008-10-31
I ended up having to install a driver via ndiswrapper - was very disappointed when the 'final' kernel wiped out the wi-fi.

---

### Post by psycosmyth on 2008-10-31
> **bumanie said:**
> I ended up having to install a driver via ndiswrapper - was very disappointed when the 'final' kernel wiped out the wi-fi.
Agree! I have had no problem with this card since Warty!! I'm sticking with Hardy for now. I have tested for three years and I am ready to settle down.WNA 1330 Dlink, not happy with Intrepid.

---

