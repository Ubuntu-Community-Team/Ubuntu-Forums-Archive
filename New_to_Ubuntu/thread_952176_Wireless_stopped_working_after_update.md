---
title: "Wireless stopped working after update"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by brandoncolorado on 2008-10-18
Hello,

I just recently installed Ubuntu 8.10 through Windows Vista.  After I restarted, my wireless worked fine.  I connected to my WPA network and used the internet for a while.  After an update (Ubuntu told me I could only do partial update), my wireless no longer works, and the wireless LED light on my laptop is not illuminated in Ubuntu.  

Does this mean that the driver was blacklisted?
I use the Intel 394ABG wireless adapter on an HP laptop DV2700

---

### Post by mikewhatever on 2008-10-18
8.10 is still a beta, so issues like that should be expected. Try checking if the driver is loaded with <sudo lshw -C network>. You may also get better help in the Development sections rather then in Absolute Beginners.

---

