---
title: "Problem with GUI"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by pkj on 2008-08-06
Hi,
Was working fine with Ubuntu...
The GUI has vanished and i am restricted to the Command Line Interface...

Which files/components i need to re-install to get back my GUI..

pkj

---

### Post by Pijits_1 on 2008-08-06
You could try going into recovery mode through grub and selecting fix X Server. This is just a quick fix to return the X Server back to default and won't install any graphics drivers. If installing a graphics driver is what caused it you could try installing a program called envy. Can be found in Synaptic.

Hope this helps

---

### Post by pkj on 2008-08-06
thanks..iwill try it out

pkj

---

### Post by yragrelluf on 2008-08-06
happened to me too, easy fix for me, try this command in terminal:

sudo apt-get install ubuntu-desktop

that should do it, let me know.

---

