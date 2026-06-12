---
title: "Kernel Problems"
date: 2019-04-08
forum: New to Ubuntu
---

### Post by sabbarth on 2019-04-08
Hello i am new to ubuntu. I am running a dual boot windows 10 and Ubuntu 18.04 for the past month. I am having this problem, whenever i am trying to update the kernel the laptop freezes on boot getting stuck forever on the ubuntu screen. So i am forced to reboot start on recovery mode and uninstall the kernel again. 

Right now the kernel version is this 

4.18.0-17-generic



but Ukuu keeps poping up a window saying that a major release is available and every time i do the update the system freezes on boot. 

Can anyone please help me with it ?

---

### Post by RedDirtDog on 2019-04-08
What are you using to do the update?  apt-get from command line, or GUI software updater?

---

### Post by Impavidus on 2019-04-09
4.18.0-17 is the latest kernel available for 18.04 from the official repositories. Is there any special reason why you want to install a later kernel? If not, there's no need to use ukuu. Just stay with the repository version.

---

### Post by sabbarth on 2019-04-09
Thank you very much for your replies !!

RedDirtDog i was trying both with terminal and with Ukuu to upgrade , but every time and with different versions of Kernel my laptop is being stuck on boot screen. 


Impavidus no there isn't a special reason why i want to install a later kernel. As i said i am new to Linux , to be honest i thought that a later version of kernel would make my 
laptop work even better. It appears that is not the case :)

---

### Post by Impavidus on 2019-04-09
Indeed, it isn't. Sometimes you need a newer kernel because your hardware isn't properly supported by the old kernel, but if the kernel from the official repositories works, use it. It gets all the important bug fixes and security updates, but not the new features and therefore less new bugs. The 4.18 kernel will be supported on Ubuntu until end July, when you will be automatically upgraded to the kernel used by Ubuntu 19.04 – I assume that will be 5.0.

---

### Post by sabbarth on 2019-04-10
Impavidus , once again thanks a lot for your reply and all the information !!

---

