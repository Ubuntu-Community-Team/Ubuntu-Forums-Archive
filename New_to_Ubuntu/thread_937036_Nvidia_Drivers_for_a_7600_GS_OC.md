---
title: "Nvidia Drivers for a 7600 GS OC"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by LeeHamo on 2008-10-03
Hi,

I recently installed ubuntu on my system and at first before I installed nvidia driver I had a resolution of 1024x768 and 85hz refresh, after I installed the popup for the nvidia driver it has changed to 1024x768 and 50hz refresh, and I can only change between 51,52,53,54hz options.

Is there anyway to know if i have the right driver or an up to date one, it seems odd the driver has reduced my monitor options.

Cheers.

---

### Post by bobpur on 2008-10-03
I came across something that caught my interest in the forums last night. I was looking for info on a linux driver for my crossfired 3870 X 2's. It said that the 7600 GS cards used the "Nvidia GLX" driver. I thought this a little odd as my  XFX 7600 GT XXX's use the "Nvidia (NEW)" driver.

---

### Post by dingansich on 2008-10-03
You should be able to check your driver version off of the Nvidia X Server Settings control panel.  You should be able to find the panel under either System Tools, or System>Administration on the main menu.  If it's not there, try launching the control panel from the terminal with the command: ```
nvidia-settings
```  The driver version should be listed there, and you can check it against what Nvidia offers on their website.

If you've got the latest driver, and you're convinced that your X Server settings aren't correct, you could try running thefollowing command from the terminal: ```
 nvidia-xconfig
``` But I'm not sure this will make any significant difference in your case.

Sorry I can't be of more help.  There are lots of threads in the forums that discuss configuring Nvidia cards though.

---

