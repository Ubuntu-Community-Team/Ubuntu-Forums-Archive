---
title: "Unable to change visual effects."
date: 2008-10-03
forum: New to Ubuntu
---

### Post by raviramgopal on 2008-10-03
Hi,
I recently installed Ubuntu 8.04.When i try changing the visual effects,i get an error message"desktop effects could not be enabled".How do i fix this.Any help appreciated.
Thanks

PS:The following is my system configuration
INtel Core 2 duo,E8400
MSI P35 neo combo
Nvidia Geforce 9600gt
Transcend 2 GB DDR2 ram.
WD CAVAIR 200GB SATA II

---

### Post by Ryadt on 2008-10-03
> **raviramgopal said:**
> Hi,
I recently installed Ubuntu 8.04.When i try changing the visual effects,i get an error message"desktop effects could not be enabled".How do i fix this.Any help appreciated.
Thanks

PS:The following is my system configuration
INtel Core 2 duo,E8400
MSI P35 neo combo
Nvidia Geforce 9600gt
Transcend 2 GB DDR2 ram.
WD CAVAIR 200GB SATA II
First enable your graphic card in System > Administration > Hardware Drivers.

---

### Post by raviramgopal on 2008-10-03
Thanks for the quick reply.The hardware drivers list is empty:confused:.

---

### Post by Ryadt on 2008-10-03
Try installing it with envy.
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

---

### Post by raviramgopal on 2008-10-03
I tried using envy,but i got an error message saying that "envy doesnt recognise your hardare as it may not support it..You can try installing it manually at ur own risk".
What do i do now?

---

### Post by Ryadt on 2008-10-03
Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver](http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver)

---

### Post by raviramgopal on 2008-10-03
Thanks for the link.Im trying the manual installation.Il update you once its done.
cheers

---

### Post by raviramgopal on 2008-10-03
i installed the driver manually.i can now change visual effects.But my resoltion has gone kaput.The current res is 640X350,and it doesnt allow me to change any further.Help needed urgently.
Thanks

---

### Post by Ryadt on 2008-10-03
Try```
sudo dpkg-reconfigure xserver-xorg 
```

---

### Post by Vishal Agarwal on 2008-10-03
at the desktop make a right click and go for change background. There you will find the visual affects tab. click that and change the visual effects to extra.

---

### Post by raviramgopal on 2008-10-03
@Ryadt
i did what you told me to do.Now the reolution has come back to normal.But now i cant make any changes to visual effects.
When i try opening the Nvidia X server settings,i get a message saying

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

---

### Post by eternalnewbee on 2008-10-03
Maybe you've got an on board vga card which can't handle 3d acceleration.
In system info check your hardware specifications.

---

### Post by raviramgopal on 2008-10-03
Im trying to install my Nvidia 9600gt,I have a MSI P35 neo combo motherboard,i am not sure whether it has onboard graphics.

---

### Post by Ryadt on 2008-10-03
Try to uninstall xserver-xgl in synaptic. Then restart x.

---

### Post by eternalnewbee on 2008-10-03
Check and see if anyone you know knows something about hardware.
When I bought my system, it wasn't just a set. I chose the hardware components myself, Not that I know so much about hardware, but I followed advice from people I know and trust. I found that out more than 10 years ago when I wanted to buy a relatively cheap computer, when someone I trusted, and who knew a lot about hardware and software recommended not to just buy a computer on sale ( usually with an operating system which might not be your first choice) but instead to think about what you want and expect from your hardware, and to buy the separate components separately, and let the guys at the shop set the hardware up. the next step is the brain. the operating system, which we (at least myself) have the prerogative to choose ourselves.
Point: you want compiz. Check (or let someone you know check) if your graphics card can handle 3d acceleration, and carry on from there.
Hope this was helpful...

---

### Post by jrothwell97 on 2008-10-03
> "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

Try running

```
sudo nvidia-xconfig
```

then save any work you have open, then press Control-Alt-Backspace.

---

