---
title: "No Fan Or Temperature Until re-login"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by markoid8 on 2008-10-01
I have been using Ubuntu since 7.04, and have become almost an enthusiast. But I recently bought a laptop, and i am having a problem that simply baffles me. My laptop is a Compaq C762NR running Ubuntu 8.04 fresh install, and dual boot with Vista. When i boot ubuntu, it runs fine, BUT my laptop fan is not on and my temperature sensor registers 0 degrees Celsius. I have used many programs, [acpi and many GNOME applets], and they all say 0. If i log out and then login again, my fan will start and my temperature will register the correct value [usually 48-63 degrees]. I am not sure why this is happening. Is there some script that runs when you login to GDM? Vista works fine with some windows monitoring software, so i know that it is not my hardware. Any help would be much apperciated. Thanks in advance.

---

### Post by markoid8 on 2008-10-03
I found out that if I simply stress my CPU to the point at which it heats up, the fan and temperature will begin to register and work correctly. I think that logging in and out can stress the CPU enough to cause it to work upon logging in the second or third time.

---

### Post by markoid8 on 2008-10-04
Since no one answered me, I kept trying and ended up finding a solution. I got libsensors configured correctly, and so i no longer needed to use acpi. libsensors is correct for both cores. The fan seems to turn on after the CPU reaches about 53 degrees. I even got the HDD temp to work.

---

