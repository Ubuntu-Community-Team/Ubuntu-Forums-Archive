---
title: "Help installing NVIDIA drivers for GeForce 640M on Ubuntu 13.04 64-bit"
date: 2013-07-14
forum: New to Ubuntu
---

### Post by Eleutharios on 2013-07-14
Hello

I need some help installing drivers for my NVIDIA GeForce 640 card on Ubuntu 13.04 64-bit. I know similar questions have been posted before but none of the solutions have worked for me. My problem is that my system detects the graphics card properly (I believe). Below is the output from 'lspci'. However, the Additional Drivers window shows nothing - it just had a bland field and says "No proprietary drivers are in use". How do I fix this?
```
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 640M] (
rev a1) (prog-if 00 [VGA controller])
        Subsystem: Dell Device 054f
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d0000000 (32-bit, non-prefetchable) [size=16M]
        Memory at a0000000 (64-bit, prefetchable) [size=256M]
        Memory at b0000000 (64-bit, prefetchable) [size=32M]
        I/O ports at 3000 [size=128]
        Expansion ROM at b2000000 [disabled] [size=512K]
        Capabilities: <access denied>
        Kernel driver in use: nouveau
```
I have tried installing nvidia-current, but this didn't help at all.
```
sudo apt-get install nvidia-current
```
I know I can install the driver manually from the NVIDIA website but I would rather not do that as it would not update automatically and I read that it could cause conflicts. How can I get Additional Drivers to show the proper dirves for my system (or any at all)? Thanks in advance for the help.

---

### Post by Gone fishing on 2013-07-14
This ia an optimus card which allow you to switch between the Nividia and the onboard card? In which case you will need bumblebee. Have a look at this [http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html](http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html)

---

### Post by Eleutharios on 2013-07-14
Ok. i had thought that Optimus support was added in 13.04 so you didn't need Bumblebee. I just added it, though, and my computer is running quieter at least. lspci gives the following output though:
```
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 640M] (rev ff) (prog-if ff)
    !!! Unknown header type 7f
```
I still can't see anything in Additional Drivers, though.

---

### Post by CinTUX on 2013-07-14
Hi,

I also had the same problem as yours with my old laptop, maybe following 
this official installation guide from here will help?

[https://wiki.ubuntu.com/Bumblebee?action=show&redirect=bumblebee](https://wiki.ubuntu.com/Bumblebee?action=show&redirect=bumblebee)

---

### Post by Bashing-om on 2013-07-14
Eleutharios; Hi !

One still has to download and install the PPA for BumbleBee. Here is the latest I am aware of in respect to installing BB onto 13.04:
[http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html](http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html)

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Gone fishing on 2013-07-15
> Ok. i had thought that Optimus support was added in 13.04 so you didn't need Bumblebee. I just added it, though, and my computer is running quieter at least. lspci gives the following output though:

I thought so too. However I had the same problem on a laptop, the howto I linked worked. I guess that the reason the driver is not being found and installed is that it is using the onboard card and not seeing the Nvidia card, hence you need bumblebee, no doubt in the fullness of time this will not be needed and close to automatic.

---

### Post by Eleutharios on 2013-07-15
So I tried reinstalling ubmblebee using the instructions provided by ihsancingisiz without change. I also tried the instructions on the official website but cuoldn't get bumblebee gui to run (it appeard in dash but wouln't start). I am still not able to see any proprietary nvidia drivers.

---

### Post by CinTUX on 2013-07-16
> **Eleutharios said:**
> So I tried reinstalling ubmblebee using the instructions provided by ihsancingisiz without change. I also tried the instructions on the official website but cuoldn't get bumblebee gui to run (it appeard in dash but wouln't start). I am still not able to see any proprietary nvidia drivers.

You could try downloading the driver from: [http://www.geforce.com/drivers](http://www.geforce.com/drivers)
And try install it from terminal with 'bash', 'sh', or './[FILE]'.

Good luck.

---

### Post by Gone fishing on 2013-07-17
It may be working if you run optirun -b primus glxspheres do you get a higher frame rate than glxspheres if so bumblebee and the driver are working

---

