---
title: "Installed ATI radeon driver, now screen has blank edges!"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by sallam on 2011-10-18
Greetings

When I first installed ubuntu 11.10, clean install, my HD screen size was full. I then installed my card's specific driver (ATI/AMD Radeom 5670). Now I have blank edges around all 4 corners of the screen. That card did the same in Windows 7, but I used the ATI tool that was installed with it, which allowed me to use scaling, which is a slider that you drag until the desktop touches the 4 screen edges fully. But I don't know how to find the same tool under ubuntu, or where to find ATI tool that was supposedly installed with the driver.

Any help please?

---

### Post by sallam on 2011-10-18
I found out that this driver is problematic with gnome 3, as said [here]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch"). I've followed the steps mentioned:
> Problem: Need to fully remove -fglrx and reinstall -ati from scratch

Here is a more aggressive recipe which removes both -fglrx and -ati, and reinstalls the latter:

  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg

Then I restarted the computer, and the screen now is beautifully filling up the whole screen again.
I hope this helps others who have the same issue with ATI/AMD proprietary driver. Had I knew this, I wouldn't have installed it, and left the default ubuntu graphic driver as is.

---

