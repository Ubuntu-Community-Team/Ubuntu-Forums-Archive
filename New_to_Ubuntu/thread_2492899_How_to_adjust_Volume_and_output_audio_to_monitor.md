---
title: "How to adjust Volume and output audio to monitor?"
date: 2023-11-26
forum: New to Ubuntu
---

### Post by nivek2046 on 2023-11-26
Hi! I am totally new to ubuntu.

I am running Ubuntu 22.04.3 LTS jammy on Orangi Pi 5 (aarch64).

[http://www.orangepi.org/html/hardWare/computerAndMicrocontrollers/details/Orange-Pi-5.html](http://www.orangepi.org/html/hardWare/computerAndMicrocontrollers/details/Orange-Pi-5.html)

When I press the volume adjust keys on my keyboard, ubuntu shows volume is adjusting. But when I listen with my headphone via the 3.5mm headphone jack, the volume is in fact not adjusted.

Would you please help me how to adjust the volume with my keyboard please?

My second question is how do I output audio via the HDMI cable to my monitor instead of the 3.5mm headphone jack?

THank you for your help.

---

### Post by TheFu on 2023-11-27
**pavucontrol** is the pulse-audio everything app.  I don't know if it is installed automatically or not. Start in the far right tab and work your way left to control almost everything related to sound output and input on the system.  I usually ensure the correct audio hardware is enabled first and disable the other stuff.  For example, 3.5mm is usually the motherboard audio and HDMI is usually the GPU audio hardware.  

I know nothing about your keyboard audio controls. I don't have a keyboard like that. May need keyboard mapping to make it work.

---

