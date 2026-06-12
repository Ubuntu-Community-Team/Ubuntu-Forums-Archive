---
title: "Nvidia driver &quot;not in use&quot;.. Cant change it..."
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Kestol on 2008-05-12
Hello as my title stated i cant change the following:

[IMG]http://i78.photobucket.com/albums/j114/alundra_photos/Screenshot.png[/IMG]

I dont know why... The box was already checked when i entered the menu the first time.. So i tryed to disable and enable it... It told me to restart but still "not in use" after that...

What to do?

---

### Post by oedha on 2008-05-12
first...go to system - administration - software sources
activate the repositories by clicking those boxes
close - reload
open terminal and type : sudo apt-get install ndivia-glx-new
then sudo /etc/init.d/gdm restart or sudo reboot

---

### Post by Gone fishing on 2008-05-12
I had the same problem. It was because I was accessing the net through a proxy and the package manager couldn't contact the net as I hadn't got round to adding the proxy setting in synaptic.

As soon as I put the proxy settings in synaptic the propriety drivers wizard downloaded the correct driver and installed it (presumably you also need to tell synaptic to use the propriety driver repository). Alternatively you can install the driver directly from synaptic

---

