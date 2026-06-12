---
title: "Video driver help"
date: 2012-08-24
forum: New to Ubuntu
---

### Post by Farfy on 2012-08-24
Hello,

I recently installed ubuntu, and have not had much experience as I can't use it right now.  I have an nvidia 7950 gt video card, and I've installed the drivers from the nvidia site and tried to use the 'recommended' drivers from ubuntu, however half of my screen is missing.

when I first boot in, the right half of my screen is black and it looks like the desktop is overlapping (as in if I had 2 monitors half on one and the other half on that one).  I can log in, and switch to terminal, and after trying sudo lightdm restart i can typically get the desktop to function (not always).  Once I have a functioning desktop if I switch too many times between desktop and terminal, the terminal will start to 'leak' to the desktop, so anything I type in a field on the desktop also is typed into the terminal.  Ive been on the IRC chat and attempted to get help but nobody was able to assist.  I'd really like to stay with ubuntu but I can't use it right now.  If anyone has any suggestions or tips they'd be greatly appreciated.  

Thank you

---

### Post by bogan on 2012-08-24
Hi!, Farfy.

I have no knowledge or experience of the symptoms you describe, but pretty clearly a video driver problem is the cause, in the absence of any hardware issues.

Certainly you do not want both the nvidia and ubuntu drivers installed at once, and if you did not 'remove --purge' the first before installing the other, they will conflict.

For reasons beyond explanation, the ubuntu 'Recommended' nvidia-current is still the bug-ridden 295.40, and even the 'post-release' is only 295.49.

Please Post:```
lspci -nnk | grep  -iA3 VGA 
sudo apt-cache policy nvidia-current
cat /sys/module/nvidia/version 
sudo nvidia-installer --latest
```If you have a version of the nvidia.com driver installed, the third command will return its version number. If not then both the third and fourth will show' no such...' or 'not found...'.

If you have one installed, then the fourth command will show the  installed and latest available version numbers but will not alter  anything - but it will confirm if your Internet connection is working,  and open the path to correct things without a re-install of ubuntu, if  that** is **what you want.

*[In Posting, highlight the cmd & output and select the '#' symbol in the toolbar of the 'New Reply' text edit box, to put it in Code boxes for easy reading. *]

Edit: Can you get the Grub menu? and if so, Does the same thing happen if you boot to recovery> safe mode.
Chao!,** bogan**.

---

