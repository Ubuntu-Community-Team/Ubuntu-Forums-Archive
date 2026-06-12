---
title: "Help KDE wont load"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by DFord425 on 2008-10-18
When i start my computer, it gets to the Starting K Display Manager: kdm. After that i get a message Starting up... and then Loading, please wait... Then it loads to a terminal. It also takes a while on the step "*Reloading Mail Transport Agent (MTA) sendmail. and tries to do it again before i log in. I also get the message [PHP]kinit: name_to_dev_t(/dev/disk/by-uuid/d5e7d080-e839-48eb-b25d-f862eadeb605) = sda5(8,5)
kinit: trying to resumre from /dev/disk/by-uuid/d5e7d080-e839-48eb-b25d-f862eadeb605
kinit: No resume image, doing normal boot...[/PHP]4

Also i just did an update, any idea what is wrong. What is the command to load the kde, i could try that.
Thanks

---

### Post by Zzl1xndd on 2008-10-18
try startx to load your GUI from the command line. If you still have issues you might want to select the Safe Graphics mode from your Grub menu during boot.

---

### Post by DFord425 on 2008-10-18
I tried startx but that didnt work. The main message i got was: ```
Failed to initialize the NVIDIA kernal module! 
Please ensure that there is a supported NVIDIA GPU in this system and that the NVIDIA device files have been created properly. 
Please consult the NVIDIA README for details.
*** Aborting ***
Screen(s) found, but none have a usable configuration.
```
Further down the screen i see another message:
```
Fatal server error:
no screens found
giving up.
xinit: Connection reset by peer(errno 104): unable to connect to X server
xinit: No such process (errno 3): Server error.
```

Any ideas what this means? Could it be a driver problem?

Also, i just say this error:
```
Error: API mismatch: the NVIDIA kernal module has version 96.43.05, 
but this NVIDIA driver componet has version 173.14.12. 
Please make sure the kernal module and NVIDIA driver componets have the same version.
```

---

### Post by Zzl1xndd on 2008-10-18
How did you install the Drivers for you Video card? If they where installed threw a method other then the Driver Manager then this will likely happen with every Kernel update. 

Try restarting and when Grub comes up hit escape and there should be an option that says recovery mode, Select that and see if you are able to boot into Kubuntu.

---

### Post by DFord425 on 2008-10-18
When i try booting into recovery mode, i still cant load the KDE and get the same error what i run startx.

---

### Post by Zzl1xndd on 2008-10-18
Ok lets try this, Boot up logo into the terminal session and then :

```
sudo dpkg-reconfigure xserver-xorg
```

Select the defaults and then reboot and we'll see if that takes us anywhere.

---

### Post by DFord425 on 2008-10-18
That worked, thank you for your help

---

### Post by Zzl1xndd on 2008-10-18
No problem, you will need to reinstall your Video Drivers though. Like I said before I would recommend using Driver manager for them. If you drivers are not listed I would try using Envy, that way you can at least run that from the command line to reinstall your drivers.

---

