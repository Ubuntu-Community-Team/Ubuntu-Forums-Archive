---
title: "Mouse sooo slooooowww.  GUI rendered usless"
date: 2013-08-04
forum: New to Ubuntu
---

### Post by ben5 on 2013-08-04
I found some mouse freezing threads but I think this is different.  It is always happening even after completely rebooting.  The mouse is so slow I can move the mouse and the pointer will move five or 10 seconds later.  It's so bad I can't even really do anything.  It's hard to actually get the mouse over something and click on it without overshooting.  

This is happening during the install process and I had to abort install twice because it totally froze eventually. Both of those times I was using the touchpad.  The third time I tried a USB mouse and it was completely normal and responsive.  So I assumed it was just a touchpad driver issue.  

After install it still worked okay and then I realized that my speakers did not work at all.  So I followed the advice here
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
and ended up trying to manually install each of the 3 Intel drivers and then ended up trying this...
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

After that and rebooting. (I believe this was the first reboot after installing - so not 100% sure if it was the sound stuff or just the overall software updates I ran maybe)  it came back up and I had the mouse issues that I originally had during install with the touchpad but now it's also affecting the USB mouse.  It basically renders the GUI useless.  I can get into single-user mode and run some commands if anyone has some suggestions.  



 Thanks!

FYI my laptop is a Toshiba Satellite A505-S6005 with RAM upgraded to 8GB.

---

