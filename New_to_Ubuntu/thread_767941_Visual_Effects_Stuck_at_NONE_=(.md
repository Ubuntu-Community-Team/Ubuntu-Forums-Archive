---
title: "Visual Effects Stuck at NONE =("
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Ice Dragon on 2008-04-26
System, preferences, appearances, visual effects.. its set to None, and whenever i try to change it to any of the other two (desired it extra), it says it wont take effect.

Also, in system, administration, hardware drivers, it lists nvidia-new as being the driver im using (my screen resolution is working great at 1680x1050) however even though the check box to enable this driver is checked, it says beside it NOT IN USE with a red bubble.

I imagine this is why i cant enable visual effects, how do i get this driver active?

My video card is a Nvidia 8800 GTS  340 ram i believe.

---

### Post by axor1337 on 2008-04-26
have you enabled the restricted driver or used ENVY?  try a restart i know it sounds like a windows thing to do but it will restart X and that has helped me in the past

---

### Post by alienexplorers on 2008-04-26
You should try running Envy to set your video card up.  I believe the 8xxx series cards use the nvidia-glx-new driver.  You can load Envyng-core and Envy-gtk from the repositories.

---

### Post by Saturn357 on 2008-04-26
When I tried my visual effects in my old computer (Celeron processor), it was probably because my video card wasn't up to par.

I wasn't aware of these programs that could configure your card, but if that doesn't work, you may consider getting a better video card?

I'm new, too. Just my 2 cents.

---

### Post by revpfil on 2008-04-26
With an 8800 of any sort, you should have full ability to run the effects, as you have more than enough horsepower. However, the default nvidia driver is worthless. The first step you should try is using the restricted driver manager to install the restricted nvidia drivers in System->Administration->Hardware Drivers. If this doesn't work, try installing the proprietary drivers using envy found at [http://albertomilone.com/nvidia_scripts1.html. ]("http://albertomilone.com/nvidia_scripts1.html")
For a final fix, if even that doesn't work for you, use thi actual nvidia binary located at [http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us"). To properly install this, you must: 

change to a different terminal (Ctrl-Alt-f1)

stop the GDM with /etc/init.d/gdm stop

 and install the driver by typing 
sudo ./ 
followed by the driver name (eg sudo ./NVIDIA-Linux-x86_64-173.08-pkg2.run). T

restart the gdm with /etc/init.d/gdm start

his will run the driver install, building from source if necessary, for your card. Note, this method may also require you to get some dependancies (most often libc6-dev) which you can get with:

sudo apt-get install libc6-dev.

I hope this helps, and you can get all the pretty up and running :)

---

### Post by shazbut on 2008-04-26
I had the same problem with a fresh hardy install yesterday, geforce4 4200 video.  Found the problem was actually with retrieving the binary driver from the local (au) repository.  Because the servers have been under such a high load these last couple days it has taken me a few tries to get anything to dowload (updates, add/remove programs, etc).  I just kept retrying until they came through, now I have 3D acceleration working fine.

To get the restricted driver to work I had to go back into Sys->Admin->Hardware Drivers and check the box again, then after a few failures at getting the file, it finally worked.

---

