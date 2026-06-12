---
title: "video woes, please help"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by wordmaster on 2008-05-04
After I loaded Ubuntu, I loaded the proprietary driver found in system/administrator/hardware drivers and it worked fine, gave me all the high screen resolutions, but would not let me use the normal or extra visual effects.

The fine folks here told me that is just due to my nvidia Geforce 2 vid card. However, after I loaded the java plugin for firefox, it told me to reboot and when I did, it came up and told me I was in low resolution mode.

All I could get was 800X600 or less. I went back in to the hardware drivers and it showed the driver loaded but not in use. 

I went into synaptics and unloaded the nvidia drivers it showed loaded there, thinking I could go back into the hardware drivers and reload the driver.

Needless to say it didn't work. Now no proprietary driver shows up and I can't find a driver that gets me back out of the low res mode. 

I have opened all repositories but can't find the correct driver and have no idea what to do next. Any help would be appreciated.

---

### Post by wordmaster on 2008-05-05
bump

---

### Post by wordmaster on 2008-05-06
Is my best bet to uninstall Ubuntu and start over?

---

### Post by shifty_powers on 2008-05-06
sudo apt-get install envyng-gtk

this is a program designed to look at you graphics card, determine the appropriate driver and then install it.

try that before you get into the realms of reconfiguring x etc... and before a reinstall

---

### Post by wordmaster on 2008-05-07
Hmmm, ran this and it showed I had a Java problem, offered to fix it, but did not. Didn't show anything about the vid card.

The java ran until it came up to a text license screen that would not allow me to do anything except scroll to the bottom. The terminal screen with command line prompt was not visible and the text screen was like it was superimposed on the terminal. All I could do was scroll to the bottom of the text box and then close the terminal. It said  <ok> at the bottom of the text box, but there was no way to clik the ok or to type y or yes.

Any ideas?

---

### Post by spiderbatdad on 2008-05-07
use arrow keys to highlight <ok> then hit enter.

---

