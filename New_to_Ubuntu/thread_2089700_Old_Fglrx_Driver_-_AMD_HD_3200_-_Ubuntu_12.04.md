---
title: "Old Fglrx Driver - AMD HD 3200 - Ubuntu 12.04"
date: 2012-11-30
forum: New to Ubuntu
---

### Post by lololol123 on 2012-11-30
I've been using Ubuntu 12.04 64 bit for about 2 weeks now and I installed the latest Fglrx driver (Graphics Card- AMD HD 3200, PC- Acer Aspire 5336, 4GB RAM, 500GB Harddrive). The problem is that sometimes video's lag and play out of sync sometimes the windows take long to show up after I've clicked them etc. After looking around I found a video on Youtube by Ubuntu help guy and in the video he recommended using an older driver if you have an older graphics card, his was about 4 years old (same as mine) and he used the 11.10 catalyst driver so I decided to try it.

I removed the previous installation of the driver and then installed the 11.10 driver. However, when I restarted it instead of going to the GUI it goes to a terminal like window and asks for my login. Now its pretty clear I need to remove the old driver and go back to using the latest one. The only problem is I'm not sure where I saved the latest driver and in order to connect to the Internet I need to change /etc/resolv.conf (I use a static IP). So what should I do?

Also anyone from personal experience, what propitiatory driver works best with my graphics card? As in the version.

Thanks :)

---

### Post by squakie on 2012-11-30
I would leave the old there and try one or more of the following boot options:

nomodeset

acpi=no

noapic

---

### Post by lololol123 on 2012-11-30
Could you go through how to do that exactly as I'm still a beginner.
Now I've removed the driver using 
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
then I rebooted.
After reboot I managed to get to the login screen but now when I login I get a blank screen for a few seconds then it returns to the login screen. What do I do now?

---

