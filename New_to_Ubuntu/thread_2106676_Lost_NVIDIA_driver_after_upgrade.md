---
title: "Lost NVIDIA driver after upgrade"
date: 2013-01-19
forum: New to Ubuntu
---

### Post by Henrik Lund on 2013-01-19
I just applied about 140 MB of updates to my Xubuntu 12.04 LTS installation. Before the update I had the "NVidia accelerated graphics driver" installed (GeForce GT 440). Afterwards it was gone, the desktop looked awful  and I was informed that the NVidia X Server was not in use. I activated/reinstalled the driver again and now it works ok.

Can anyone please tell me what the problem may have been and if there is anything I should do before applying upgrades in order to keep my video card working? It seems to me that Ubuntu and NVidia is a bad match.

Best regards.

---

### Post by Frogs Hair on 2013-01-19
In the case an upgrade the driver would be removed but not for an update. If it was an update the software center and synaptic package manager both display update history so checking there might offer a possible cause.

A kernel or xorg update may have required the driver which is 3rd party package to be removed to complete the update. Kernel updates don't cause Nvidia driver problems on my Ubuntu but I don't about Xubuntu.

---

### Post by UltimateCat on 2013-01-19
Hi: Frogs Hair!

Would an newer version of the kernel (Upgrade) cause the Nvidia driver to be uninstalled?

---

### Post by Frogs Hair on 2013-01-20
If you were to upgrade only a kernel say, from 3.5 .xx to 3.7.xx on the same Ubuntu version I would think so.

The Nvidia current driver is tested with the kernel provided with the current Ubuntu version. Updates within the same Kernel family have never affected the driver installation for me anyway. Example: 3.5.21 to 3.5.22

---

### Post by bogan on 2013-01-20
Hi!, **Hendrik Lund**,

Your OP is not clear whether you are asking about an  update or an upgrade, there is a difference, and a lot depends on what nvidia driver you had installed, and whether DKMS is available, or has been removed when uninstalling something else.

My experience with kernal updates has been less trouble-free than **Frogs Hair** reports, but then I have 10 different installations from 10.10 to 12.0 on four different computers, and use lots of different drivers, but in, most cases, any problem has been easily corrected by re-installing the nvidia driver.

The latest update from 3.2.0.5.22 #54 t0 32.0.5.-22-#55 [ from memory ] made a
real mess of things and nvidia threw up a whole bunch of error messages. I ended up having to purge nvida* altogether and install nvidia-current-experimental-304, as nvidia-installer could not find the files it needed.

Dont be discouraged by not getting  answers to 'WHY' questions, stick to the 'HOW' answers!

Chao! **bogan**.

---

### Post by jim Kane on 2013-01-20
Xubuntu 10:4
When i get a kernel update that says (new install) the drivers &#8220;&#65279;accelerated graphics driver" for my Nvidia video card have to be re-installed, 
if it&#8217;s just a ordinary kernel update it&#8217;s not necessary. 

Mike

---

