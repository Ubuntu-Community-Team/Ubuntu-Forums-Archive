---
title: "fail to get logon screen"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by m_eoin on 2008-09-30
Hi

been using ubuntu for 6 months or so and was trying to update a reinstall  library (libpond.. or something of that nature).

Anyway after the reinstallation I noticed that I had no synaptic manager, nor firefox or a number of tools that I used to use.

I did a reboot and after the progress bar, I get a command tool window asking for my logon. I am logged on as root at the moment. I have tried using the recovery version without success. I have tried using the fix X session option and this just comes back with some message.

After I try sudo apt-get update I get some error message such as 

Failed to fetch [http://es.archive.ubuntu](http://es.archive.ubuntu)........
Could not reolve es.archive.......

I guess it looks like I am not online but I can assure I am. I am now using my laptop so if you need some command printouts can you let me know how I can mount my memory stick and copy the files there (as I have no access to a GUI interface).

I suspect I will have to install another image but I´d love to proved wrong .

---

### Post by Sycron on 2008-09-30
Login and type ```
fsck
```. Reboot and see what happens.

If does not work do a ```
sudo dpkg --configure -a
``` .

Otherwise you may try tying ```
sudo gdm
```.

---

### Post by m_eoin on 2008-09-30
I tries fsck and tried the reboot.

Now it just hangs when it gets to the ubuntu screen with the progressbar. The progress bar starts and then freezes. Obviuosly now I cannot get a terminal to try the dpkg and gdm commands.
Is there another way I can enter to get a terminal?

---

