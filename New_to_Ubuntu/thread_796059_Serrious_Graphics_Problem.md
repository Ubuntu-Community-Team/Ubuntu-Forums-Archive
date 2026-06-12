---
title: "Serrious Graphics Problem"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by DarkSaga70 on 2008-05-16
Just installed 8.04 on my friends machine. He was running 7.10 fine and now when he activated his restricted drivers for his Nvidia card he has a desktop and no top bar or bottom bar and the only keyboard shortcut he can use is to open his file browser. How can we fix this I have tried all I know and am my witts end.

---

### Post by EXCiD3 on 2008-05-16
What video card are you using and which driver (nvidia or nvidia-legacy)?

---

### Post by DarkSaga70 on 2008-05-16
gforce 6200 256 meg ram   using the Nvidia GLX new

---

### Post by nicedude on 2008-05-16
There should be plenty of other keyboard shortcuts you can use. Alt+F2 should bring up a run box and Ctrl+Alt+F1 thru F6 will bring up one of the 6 terminal logins adn Ctrl+Alt+F7 will bring you back to your desktop. I would recomend removing the restricted driver manager all togither and installing the Nvidia linux driver from the Nvidia site. I wish they didn't even use the stupid restricted manager in the first place as it is far from perfect while getting the drivers yourself makes sure you are getting the correct ones for your device. If your friend doesn't have wireless network adapter on this machine then his graphics driver is all the restricted manager should be handling. 

The restricted manager is called jockey by the way you can find it in synaptic package manager -> Alt+F2 then type that in and click run in terminal box, also just google Nvidia linux driver and go download the package to install that with from Nvidia ( Please read their directions first though )

Installing your own drivers is the perfect learning experience.

PM me if you want to try this and need help ( Just click my name :-) )

---

### Post by DarkSaga70 on 2008-05-16
I tried every shortcut know to man and the only one that works is the one that opens the file browser.

---

### Post by nicedude on 2008-05-16
If you have to have a simple solution though then you could use envyng it will do it for you. just open a terminal with Alt+F2 and paste in the following and click run in terminal

sudo synaptic

then search in synaptic package manager for envyng and install it and you will probably want the envyng-gtk for a gui interface

after install is complete use Alt+F2 again and type envyng or envyng-gtk and click run in terminal again and let it install your driver and configure your xorg.conf file

---

### Post by DarkSaga70 on 2008-05-16
Alt-F2 does not work. No shortcuts do anything cept the ctrl-f

---

### Post by nicedude on 2008-05-16
Then restart and choose recovery mode then you will have to make changes using the command line and apt-get install & remove commands or use vi to edit text files

---

### Post by DarkSaga70 on 2008-05-16
I have no idead how to do that but thanks for trying. I will just re-install 8.04 and try this again.

---

### Post by nicedude on 2008-05-16
I would start with recovery mode and then once logged in 

sudo apt-get remove jockey
sudo apt-get remove linux-restricted-modules
sudo apt-get remove nvidia-glx-new
sudo apt-get install envyng-gtk

then after all that reboot and while you will be in reduced graphics mode you can open a terminal and run envyng-gtk and install your buddies graphics driver

---

### Post by PmDematagoda on 2008-05-16
I'm rather surprised that you have those problems with the 6200 since I have the card myself and ot plays really well with Linux. Did you try installing the Nvidia driver manually?

---

### Post by EXCiD3 on 2008-05-16
> **DarkSaga70 said:**
> I have no idead how to do that but thanks for trying. I will just re-install 8.04 and try this again.

You will in good time. When i first started i reinstalled ubuntu 13 times in the first week or two :lolflag: Play around with things and you will get the hang of it sooner or later.
Here is a helpful tutorial for installing the nvidia driver manually: [http://amazingrando.wordpress.com/2007/04/10/compiling-and-using-newest-nvidia-drivers-in-ubuntu-its-easier-than-you-think/](http://amazingrando.wordpress.com/2007/04/10/compiling-and-using-newest-nvidia-drivers-in-ubuntu-its-easier-than-you-think/)

---

### Post by nicedude on 2008-05-16
Its a waste of time to always reinstall when instead in the same time that takes you could learn how to fix what is wrong. All he needs to do is reboot and select recovery mode and use the command line in conjunction with apt-get commands to remove his driver and install envyng and then reboot and use envyng to give himself the best driver possible, quite simple really.

I played the reinstall game a few times and then learned it was better to stick out problems and fix them since anything can be fixed and you learn in the process.

---

