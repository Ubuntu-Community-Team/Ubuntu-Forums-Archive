---
title: "why its suggesting Proprietary Driver for Optimus"
date: 2013-01-17
forum: New to Ubuntu
---

### Post by sagarvarule on 2013-01-17
I have Nvidia Optimus Card. I installed Ubuntu 12.04 and it detected my card and suggested me to install Proprietary Drivers. I have search net and I came to know Optimus technology is not supported on Linux. Then why Ubuntu is showing/suggesting me to install the proprietary driver. And what are these driver if there are no drivers to support Optimus technology.

I am posting the question to understand ubuntu working better.

Any help is appreciated. And want to learn heart of Ubuntu.

---

### Post by mastablasta on 2013-01-17
> **sagarvarule said:**
>  And what are these driver if there are no drivers to support Optimus technology.

 
 
they are nvidia drivers that will enable the full use of nvidia card. 
 
you can look into project bumblebee to see how to do manual switching in ubuntu between CPU's low powered graphics chip and nvidia's high powered graphics chip. 
more here: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by westie457 on 2013-01-17
To get Optimus cards working you need to install 'Bumblebee'.

Here is a link to the instruction page. [http://bumblebee-project.org/install.html](http://bumblebee-project.org/install.html)

---

### Post by 3rdalbum on 2013-01-17
> **sagarvarule said:**
> I have Nvidia Optimus Card. I installed Ubuntu 12.04 and it detected my card and suggested me to install Proprietary Drivers. I have search net and I came to know Optimus technology is not supported on Linux. Then why Ubuntu is showing/suggesting me to install the proprietary driver. And what are these driver if there are no drivers to support Optimus technology.

I am posting the question to understand ubuntu working better.

Any help is appreciated. And want to learn heart of Ubuntu.

Optimus is a system that lets you switch between a high-powered GPU and an energy-efficient GPU.

Optimus is not supported, but the high-powered GPU is. That GPU is run by the Nvidia proprietary driver.

---

### Post by sagarvarule on 2013-01-17
Ok to Run Optimus on Linux i need Bumblebee project. I installed bumblebee before and it works i knw. But then why Ubuntu is suggesting Proprietary Nvidia Drivers for my card. Knowing in any case suggested driver is not going to work and will crash the system.

My point is why suggest some thing which is not gonna work. And  also I want to highlight that it also mentions that these drivers are Tested By Ubuntu Developer which is so deceiving.

---

### Post by mcduck on 2013-01-17
> **sagarvarule said:**
> Ok to Run Optimus on Linux i need Bumblebee project. I installed bumblebee before and it works i knw. But then why Ubuntu is suggesting Proprietary Nvidia Drivers for my card. Knowing in any case suggested driver is not going to work and will crash the system.

My point is why suggest some thing which is not gonna work. And  also I want to highlight that it also mentions that these drivers are Tested By Ubuntu Developer which is so deceiving.

Beacuse, like others have explained, the nVidia driver is going to work perfectly fine with your nVidia graphics card.

(like 3rdalbum said, Optimus is just a mechanism of switching between two different GPUs. You can use either GPU without Optimus, and each GPU will also need it's own normal drivers to work regardless of if you are using the GPU switching or not.)

---

