---
title: "Installing Ubuntu 12.10 on a new laptop"
date: 2013-01-18
forum: New to Ubuntu
---

### Post by prodriver on 2013-01-18
A major PC Manufacturer sells a laptop with Ubuntu version 11.10. I want to buy a new Windows 8 laptop (64bit)at a lower price and do a complete install of Ubuntu version 12.10. I am concerned that there might be some issues. Is there anything that I should be aware of or do before the installation to insure that it will work without any problems. I'm worried that the built in Wireless might not work after wiping out Windows 8. Thanks for any suggestions.

---

### Post by verymadpip on 2013-01-18
Test your hardware from a LiveCD/DVD/USB environment first.

When you boot from your chosen medium select the "Try Ubuntu" option.

---

### Post by prodriver on 2013-01-19
Thank ypo

---

### Post by audiomick on 2013-01-19
It is quite likely that you will have to install proprietary drivers to get the wireless working. This is generally possible with out too much drama, but you will need a wired internet connection to get it done easily. I strongly suggest having a wired connection when you do the "try ubuntu" test, and particularly when you are installing. 

In the live environment, the "try ubuntu" option, you can run the additional drivers utility to see if it offers you proprietary drivers for anything. You can install them, and see if they work, but they will be gone next time you boot into there, unless you are using an installer on a USB stick with persistance.

---

### Post by drawkcab on 2013-01-19
Sometimes when you buy cutting edge hardware it takes a bit for the kernel to catch up to it so that everything works.  If you're really worried about wireless, intel cards usually work very well with Linux.

---

### Post by quarkhirad on 2013-01-19
i agree with audiomick. 

While you are using the "Try ubuntu" test you can download and install the proprietary drivers using your wired net connection. Now according to me (if i am wrong please correct me) synaptic(or the package manager that installs your proprietary drivers) downloads the package and saves it in the directory /var/cache/apt/archives directory.So all you have to do is stick your pen-drive in and then copy the downloaded packages.That way after you install your ubuntu all you have to do is stick that pen-drive in and then install your proprietary drives and "tada" you have your wireless drivers installed. Off course you can always use the wired connection and download the packages again. 

Another thing that you might want to do some reading on is about the nvidia optimus technology that new laptops are coming with ( if your laptop has a nvidia graphics card). Off course there is a solution.
There are many sites for the solution one is 

[http://bumblebee-project.org/](http://bumblebee-project.org/)

---

