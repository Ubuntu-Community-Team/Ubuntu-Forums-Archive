---
title: "wi-fi issue in 12.04"
date: 2012-06-02
forum: New to Ubuntu
---

### Post by TFSinclair on 2012-06-02
I'm running Ubuntu 12.04 and have after my DSL router went the way of the DoDo, installed a SBC775 modem/wi-fi model 4111N. It is hard-wired into the Windows XP computer and the Ubuntu computer has a generic Chinese wi-fi USB adapter.
When the Ubuntu computer goes into hibernate and is then "woke up", the wi-fi adapter is no longer initiated. The only way I've found (so far) to re-initiate the wi-fi adapter is to reboot the whole computer.
I've clicked on the connections tab at hte top of the screen abd told it to connect to the router. It appears to have done so but I cannot get on the Web until after the reboot.
Any suggestions for a simpler way of solving this?
TFSinclair

---

### Post by TFSinclair on 2012-06-02
bump

---

### Post by blueshead on 2012-06-02
I used to have this problem with an old usb dongle.

A quick unplug/plug back in of the dongle would get it working without a reboot.

---

### Post by TFSinclair on 2012-06-03
That has not worked. I've unplugged the adapter and plugged it back after 30 seconds and still no life.  What I have found for a solution now is to make the Ubuntu computer NOT go into power saving hibernation.  This does not seem to me to be a permanent solution but it works for now.
Still looking for a permanent solution.
TFSinclair

---

### Post by steeldriver on 2012-06-03
you could try identifying what kernel module it's using then adding it to the SUSPEND_MODULES line in your pm config

[http://ubuntuforums.org/showpost.php?p=11843184&postcount=2](http://ubuntuforums.org/showpost.php?p=11843184&postcount=2)

---

### Post by TFSinclair on 2012-06-03
SteelDriver,
thanks for the link. I followed the directions and it appears this has solved my issue. 
Thank you again!
TFSinclair

---

### Post by steeldriver on 2012-06-03
great! you should really thank chili555 - I would have never figured that one out myself

---

