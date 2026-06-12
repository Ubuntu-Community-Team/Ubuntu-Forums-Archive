---
title: "[SOLVED] driver for gtx 260"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by tuts69 on 2008-11-29
hi there people any 1 can tell me how can i get a driver for my graphics card evga gtx 260? thanks i appreciate.

---

### Post by robertyou on 2008-12-01
If you're using Ubuntu 8.10, the hardware driver manager can be used to install driver for your card from depo. 
System -> Administration -> Hardware Drivers

---

### Post by tuts69 on 2008-12-01
> **robertyou said:**
> If you're using Ubuntu 8.10, the hardware driver manager can be used to install driver for your card from depo. 
System -> Administration -> Hardware Drivers
i used ubuntu 8.04, that's ubuntu 8.10 is the new released right. i'll try to make a copy of that 8.10, thanks i appreciate.

---

### Post by robertyou on 2008-12-01
Well. In 8.04, it's called "Restricted Drivers" in System -> Administration

---

### Post by tuts69 on 2008-12-02
> **robertyou said:**
> Well. In 8.04, it's called "Restricted Drivers" in System -> Administration

yap i try that procedure b4 but no one or any hardware show up.

---

### Post by w4ett on 2008-12-02
Review this thread: [http://ubuntuforums.org/showthread.php?t=890316](http://ubuntuforums.org/showthread.php?t=890316)

Some advice: I've always had better luck using Envy [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) or using the drivers directly from the Nvidia website: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by tuts69 on 2008-12-03
> **w4ett said:**
> Review this thread: [http://ubuntuforums.org/showthread.php?t=890316](http://ubuntuforums.org/showthread.php?t=890316)

Some advice: I've always had better luck using Envy [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) or using the drivers directly from the Nvidia website: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

thanks for help i try the nvidia website but and i call the manufacturer they said the driver for 260 gtx is not yet available. but i keep trying to search and ask for help to others. anyway thanks for all your response and help once i get the driver i let you know guys.

---

### Post by robertyou on 2008-12-03
Looks like you have to get the driver yourself and install it in console..

You need to look for the driver from nVidia sites or forums. I found a page for the latest linux display driver -> [http://www.nvnews.net/vbulletin/showthread.php?t=122931](http://www.nvnews.net/vbulletin/showthread.php?t=122931)

If you browse through the README files for [x86]("http://us.download.nvidia.com/XFree86/Linux-x86/177.82/README/index.html") and [x86-64]("http://us.download.nvidia.com/XFree86/Linux-x86_64/177.82/README/index.html"), you can find gtx 260 in the supported GPUs list.

Let me know if you need help with installing.

---

### Post by robertyou on 2008-12-03
I'm not sure why nvidia don't have a complete support product list on their website as they have in the driver's release archive.

Every version of linux display driver is made as a unified driver, supporting all of the nvidia gpu models except for certain gpus (i.e. legacy..).

I don't think there will be a problem for you to install 177.82 driver. In the worst case, you only need to reconfigure xorg file.

---

### Post by tuts69 on 2008-12-04
> **robertyou said:**
> Looks like you have to get the driver yourself and install it in console..

You need to look for the driver from nVidia sites or forums. I found a page for the latest linux display driver -> [http://www.nvnews.net/vbulletin/showthread.php?t=122931](http://www.nvnews.net/vbulletin/showthread.php?t=122931)

If you browse through the README files for [x86]("http://us.download.nvidia.com/XFree86/Linux-x86/177.82/README/index.html") and [x86-64]("http://us.download.nvidia.com/XFree86/Linux-x86_64/177.82/README/index.html"), you can find gtx 260 in the supported GPUs list.

Let me know if you need help with installing.

alright thanks much robert i really appreciate for your help:D and i let you know if i need help. ok thanks once again.

---

### Post by linuxfueled on 2008-12-16
Thanks for all the help in the above threads. The how-to and info worked great on my older system (Intel D820). The only difference some of you might need to do is run the downloaded driver file in its full name from command line instead of pointing to it with a abbreviations in command line, no idea why I had to do that but it worked.


I would also like to add I just built a new Intel i7 system fresh install of Ubuntu 64 bit version and all I had to do for the EVGA GTX260 was select the driver in system driver settings as described above. Even compiz was working once I selected the animated desktop options.

thanks

---

