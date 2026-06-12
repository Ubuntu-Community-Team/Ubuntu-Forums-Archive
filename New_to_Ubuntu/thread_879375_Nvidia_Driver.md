---
title: "Nvidia Driver"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by sarahdanielle on 2008-08-03
I'm having trouble enabling visual effects in Ubuntu. I believe the problem is that I'm missing a driver for my GeForce 8400M. Through System->Administration->Hardware Drivers, there is no option available for my graphics card. I've tried installing the driver through Envy, but the program crashes every time. In Synaptic only the legacy drivers show up. Through the terminal I get (after purging nvidia-glx):
sudo apt-get install nvidia-glx-new
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for nvidia-glx-new
No candidate version found for nvidia-glx-new
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
(etc.)
How do I install "nvidia-glx-new"?

---

### Post by tuxxy on 2008-08-03
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by zxscooby on 2008-08-03
Do you have the proper repositories enabled?
[https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

I think you need the restricted.

---

### Post by ellgor on 2008-08-04
Hi,

You dont say which distro you are using (Hardy-Gutsy- whatever) so anyway go to System>Admin and click on Restricted-drivers, either it will be enabled or not, it sounds like not, enable it and it will either download the relevant driver or update the installed one, hope this helps.

Regards, Ellgor.

---

