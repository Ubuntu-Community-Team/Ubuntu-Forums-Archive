---
title: "Extremely confused Ubuntu won't run"
date: 2013-03-27
forum: New to Ubuntu
---

### Post by nyjudodad on 2013-03-27
I have a dell laptop amd64 triple core processor that came with windows 7. Windows is no longer an option and for several weeks now I've been scouring this site and the internet trying to get information for this to work. I have tried installing 10, 11 and 12 both from cd and usb. All work on my other computers as live, dual boot and full installs but this laptop is a nightmare. I either get hung up on the purple ubuntu screen or a blank screen with a functional mouse cursor. My last option is to ask for help. I've read and tried so many fixes for this but obviously I'm missing something. I sure could use some help.

---

### Post by Bashing-om on 2013-03-27
nyjudodad; Hi, Welcome to the forum.

Perchance a graphics driver problem ? Try this:
Boot up ubuntu, at the purple screen hit any key -> language screen, escape key to accept default;-> boot screen
At this boot screen depress the f6 key for some preset boot options, try "nomodeset" first; enter to accept selection(s) and f10 to continue the boot process. Once to the desktop find "Additional Drivers" (location varies depending on version of ubuntu) and install the recommended driver. 
If this works in the trial, further advise is forthcoming to get you up on the installation. Advise which version you are installing.

Then maybe UEFI is a factor, some Windows 7 had that boot sector ? Is Windows still bootable ?
[INDENT=2]
try'n to help

[/INDENT]

---

### Post by arpanaut on 2013-03-27
It would be helpful for you to tell more spec's of your machine, memory, graphics chip, etc
If you have nVidia or amd/ati it may be helpful to set nomodeset at boot to get to a GUI, then install the proper driver for your system.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

HTH

Edit: missed the post above mine.

---

### Post by nyjudodad on 2013-04-03
Thank you for getting back to me.  Apparently my problem is specific to my particular machine Dell Inspiron 15R M5010 AMD triple core processor.  The fix is here: [http://ubuntuforums.org/archive/index.php/t-1633642.html](http://ubuntuforums.org/archive/index.php/t-1633642.html)  

Although the thread is talking about 10.10 I was able to successfully install 12.04 and I'm happy as a clam.  To Bashing-om and arpanaut; I tried for days to find my specific system specs to give you an intelligent answer without much luck.  I got debian 6.07 running on the machine for some functionality but I am not a fan.  I couldn't get the wireless to work and information on debian is not nearly as straightforward as the info on ubuntu.  12.04 recognized my home network right out of the gate and found drivers for my equipment automatically.  Thank you for your time and assistance.

---

### Post by Bashing-om on 2013-04-03
nyjudodad;
Pleased you are up and running, "happy as a clam". Good thing also in that you took the initiative to isolate the issue.
Remember, this forum exist to assist in any manner, no question is "dumb", and all help is appreciated.

Please mark this thread as solved; interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button[INDENT=3]
come back often

[/INDENT]

---

