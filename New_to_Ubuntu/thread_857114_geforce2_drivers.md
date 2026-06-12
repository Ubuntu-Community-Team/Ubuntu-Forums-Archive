---
title: "geforce2 drivers"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by thefreddy on 2008-07-12
Hi all
Just installed ubuntu 8.04.1 no probs great instal,
but cant get resolution better than 640x480 (prob cos of my old 3d blaster geforce2 graphics).
Can anyone point me in the direction of better drivers? if they exist?:)

regards

---

### Post by Troll_the_Great on 2008-07-12
Try this link and see, but your card is very old...I don't know if you will find what you need.Hope this helps.
Cheers!
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by thefreddy on 2008-07-12
Many thanks Troll_the_Great,
but no luck
regards

---

### Post by PmDematagoda on 2008-07-12
Did you already install the drivers? If so, how?

---

### Post by thefreddy on 2008-07-12
hi PmDematagoda
only the drivers in the distro, and these were updated automatically rapidly by prog,
Haven't found any other drivers...
regards

---

### Post by PmDematagoda on 2008-07-12
> **thefreddy said:**
> hi PmDematagoda
only the drivers in the distro, and these were updated automatically rapidly by prog,
Haven't found any other drivers...
regards

Try and install the nvidia-glx-legacy package after removing the nvidia-glx-new package(in case it is installed):-
```
sudo apt-get install nvidia-glx-new nvidia-glx && sudo apt-get install nvidia-glx-legacy
```
then see if the problem is fixed.

---

### Post by thefreddy on 2008-07-12
Hi PmDematagoda,
Thanks for advise but the legacy drivers still only give max resolution of 800x600
sadly this isnt useable so I will have to abandon ubuntu for the moment.
Best wishes and thanks

---

### Post by Hairy Heron on 2008-07-20
I have just started using Ubuntu. I've jumped straight in with Hardy Heron. I found that when it had finished installing and asked if I wanted to install updates, it also detected my GeForce2 MX card. The odd thing was that it then installed the NVIDIA graphics driver - NOT the legacy driver which is what I would expect with the GeForce2.

It all works ok, and when I tried forcing the legacy driver, through Synaptic, it then reverted to 800x640, no acceleration. So I let it revert back to the non-legacy driver which works fine with my GeForce 2.

You can see which driver it is running with through the following menus:

System -> Administration -> Hardware Drivers

---

### Post by steveneddy on 2008-07-20
> **thefreddy said:**
> Hi PmDematagoda,
Thanks for advise but the legacy drivers still only give max resolution of 800x600
sadly this isnt useable so I will have to abandon ubuntu for the moment.
Best wishes and thanks

They give up so easily without trying to understand.

---

