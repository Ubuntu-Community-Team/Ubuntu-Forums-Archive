---
title: "(Almost) Every time package installed in terminal, bootup goes to terminal"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by Pilapodapostache on 2013-03-17
I apologize if this isn't in the right place, if it's not, can a mod please move this thread?


Hi!

I recently installed gEdit on my laptop, (and a few other applications through the terminal), and pretty much 9 times out of 10 when I reboot after a package is installed through the terminal, I end up booting into the basic terminal thing (I'm really sorry for the bad terminology, linux newbie). I have to ctrl-alt-f1 to log in. I give the commands startx or startxfce4 but I get either "Display already Initialized on display 0, delete log/xorg.0.log (or something to that extent, which I delete but then it says it can't start the server)

Here, I either have to sudo killall -9 Xorg (which sometime works) to get the login screen to boot or either update packages through Aptitude (which sometimes works) before issuing startx or startxfce4.

Those two options have really been the go-to for me in the way for fixing it, only on one occasion those fixes didn't work and I just kind of gave up and kept restarting till it worked.

Any assistance in this would be absolutely awesome.

PS running Xubuntu 12.10

---

### Post by oldos2er on 2013-03-17
What graphics card are you using? 

There's no need to reboot after installing most packages, except for new kernels and kernel modules (including video drivers).

---

### Post by Pilapodapostache on 2013-03-17
I've got a laptop with nVidia Optimus. I have Intel HD graphics  as well as an nVidia 650M. I DO have bumblebee installed, so it should be okay in that department.

---

### Post by Pilapodapostache on 2013-03-18
Bump. I'd like some assistance with this problem asap. D:

---

