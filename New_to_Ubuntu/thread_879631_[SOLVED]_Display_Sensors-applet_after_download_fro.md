---
title: "[SOLVED] Display Sensors-applet after download from Synaptic"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by Dumpy Dumpster on 2008-08-04
I feel a bit stupid because I have managed this before, but cannot work out how I did it! My previous thread does not help me. I have had to reinstall Hardy.
I have installed 'sensors-applet' and libsensors-applet-plugin 0' from Synaptic, I have tried 'sudo apt-get install sensors-applet'  only to be told it is all there and the latest version. Also I have tried 'sudo /usr/sbin/sensors-detect.  But I cannot find it to display on my lower panel.  Where is it and how to display, please?
Thanks - it can't be far away!

---

### Post by philinux on 2008-08-04
> **Dumpy Dumpster said:**
> I feel a bit stupid because I have managed this before, but cannot work out how I did it! My previous thread does not help me. I have had to reinstall Hardy.
I have installed 'sensors-applet' and libsensors-applet-plugin 0' from Synaptic, I have tried 'sudo apt-get install sensors-applet'  only to be told it is all there and the latest version. Also I have tried 'sudo /usr/sbin/sensors-detect.  But I cannot find it to display on my lower panel.  Where is it and how to display, please?
Thanks - it can't be far away!

You run sudo sensors-detect
If all goes well it will set up the sensors.

Then right click add to panel and IIRC it's called Hardware Sensors.

---

### Post by sharks on 2008-08-04
right click and select add to panel. find hardware sensors

---

### Post by Dumpy Dumpster on 2008-08-04
Thanks philinux and sharks.  Ran 'sudo sensors-detect',answered 'yes' to all, tried to 'Add to Panel' but alas it came up 'No sensors found'!  I have tried 'sudo get-apt install libsensors-applet-plugin0' but that came up with 'Command not found'
Sorry more help needed!

---

### Post by Ubuntized! on 2008-08-04
The packet from synaptic is 'sensors-applet'.
Install that, then have another look in the "add to panel" dialog!

---

### Post by silkstone on 2008-08-04
Install **lm-sensors** from Synaptic, as well as **sensors-applet**.

In a terminal, enter **sensors** and see what appears.

You should be able to add the applet to a panel as already suggested...

'Add to Panel' and then find 'Hardware Sensors Monitor'.

---

### Post by Dumpy Dumpster on 2008-08-04
Thank you silkstone, it was the lm-sensors (now called ksensors it seems!) that was missing.  Pity it was not 'bundled' with 'sensors-applet' and 'libsensors-applet-plugin0', it would have saved you all some trouble.

---

