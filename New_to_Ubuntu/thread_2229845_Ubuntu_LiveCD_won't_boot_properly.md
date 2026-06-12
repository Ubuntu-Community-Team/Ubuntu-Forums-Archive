---
title: "Ubuntu LiveCD won't boot properly"
date: 2014-06-15
forum: New to Ubuntu
---

### Post by joe114 on 2014-06-15
Hi, 

I downloaded the latest Ubuntu Desktop Edition (14.04) and burnt the ISO to a DVD-R. When I boot the CD (by pressing F11 and selecting my CD drive from the boot list upon startup), the purple Ubuntu screen with five dots beneath appears. However, after about a minute, this screen vanishes and a black screen appears which does not change. 

I checked the disc integrity and no errors were found. Additionally, I downloaded the ISO twice more and burnt the ISO to a USB drive and a DVD-RW and booted using these. The same result occurred.

Interestingly, both DVDs and the USB will successfully boot into the Ubuntu live desktop when used in VMware Player on Windows 7. 

Please note: My system specifications surpass the minimum system specifications for Ubuntu 14.04.

Any help is appreciated, 

Thanks!

---

### Post by Bashing-om on 2014-06-15
joe114; Hello, Welcome to the forum.

Maybe a graphics driver issue ? .. Are you using ATI or Nvidia -- hybrid graphics also not considered:
Try the "nomodeset" boot parameter:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

[INDENT][INDENT]maybe yes,
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-06-15
Welcome. When you get to that purple screen when booting from the disk, hit F6. If that doesn't work, try 'return'. Any luck/change?

---

### Post by joe114 on 2014-06-16
Bashing-om: I'm using an AMD Radeon HD7870. Furthermore, using the "nomodeset" parameter reduces the resolution but the black screen still appears after the initial "Ubuntu" screen (with only 4 dots). 

Bucky Ball: Pressing F6 at the purple screen brought up a command line of sorts. At the start it read: "mount: mounting /dev/sda5 on /cdrom failed: invalid argument" and "pwconv: failed to change the mode of /etc/passwd- to 0600". At the end it read "Starting Restore Sound Card State [FAIL]". Everything else was "[OK]".

I should also state that about 6 months ago I had Ubuntu 12.04.4 installed on my HDD and the 12.04.4 LiveCD worked. I removed it when I was forced to wipe my HDD. However, the LiveCD not work now. 

In addition, I tried using the Linux Mint 17 LiveCD but this did not work either (got stuck on "lm" icon screen).

Thanks!

---

### Post by Bucky Ball on 2014-06-16
Please be aware that Linux Mint is not officially supported in the main support forums here. 

Any reason you can't install 12.04 LTS? It is supported until April 2017 and you can do an upgrade or clean install of 14.04 when it reaches the point release, 14.04.1, or perhaps in a year or two. You might find you don't have these troubles then (14.04 is still very new).  

Having said that, curious as to why this is not working with 14.04 and could be helpful to find out for the community and devs ... :-k

---

### Post by joe114 on 2014-06-16
Having plugged my CD drive into SATA port 3 (as opposed to 2) and having booted the LiveCD with the "acpi=off", "noapic", "nolapic" and "nomodereset" boot parameters, the LiveCD successfully booted. I am not sure what caused the original failure but I greatly appreciate the help.

Thanks to both Bucky Ball and Bashing-om.

To clarify, the 12.04.4 LiveCD would not boot either (same error as the 14.04 LiveCD).

---

### Post by Bucky Ball on 2014-06-16
Okay. Glad you got over that, good job. Post new threads for any other questions/issues you may have. Enjoy! ;)

---

