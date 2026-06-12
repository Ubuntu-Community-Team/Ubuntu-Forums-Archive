---
title: "Battery Life Issues"
date: 2013-09-27
forum: New to Ubuntu
---

### Post by christian3 on 2013-09-27
Hello everyone. I have a computer on which I have just installed ubuntu 13.04. I went from having a battery life of over 6 hours on Windows 7 to a maximum of 2.5  on ubuntu. I have used powertop as well as tlp to diagnose the problem. Powertop says that I have consistently over 1000 cpu wakeups per second, and my battery discharge is 37 W. I have installed tlp to help improve battery life but it's not doing much. Does anyone have any suggestions for me? Battery life is a must. I don't know how to post anything about my computer hardware or anything, sorry.

---

### Post by JonasDeMoor on 2013-09-28
Hello,

Open a Terminal (Icon upper left hand corner, and type in Terminal). Then type in the following command:

```
sudo apt-get install hardinfo
```

This will install the application hardinfo on your computer. You can also install it by using the Software Center. 
Then open up the program by typing "hardinfo" in the Dash. Now you will be able to view system information, similar to Control Panel in Windows.


Now, for your battery issue: it is normal that you have less battery life in Linux than in Windows. You can try improving it by installing a program called Jupiter. Instructions on how to install it are located here: [http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html](http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html)  

WARNING: I've noticed that Jupiter only supports Ubuntu up to version 12.10 :( So I don't know it will work on Ubuntu 13.04. Install this program at your own risk. 

Can someone confirm that Jupiter works on Ubuntu 13.04?

---

