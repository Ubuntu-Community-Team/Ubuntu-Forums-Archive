---
title: "X server / Login Issues"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by krustenBrot on 2012-11-25
Hey there
I am getting some strange errors on boot up since yesterday. Everytime I reboot, right before the login screen appears I only see a blinking cursor and then a window shows up(just the window on black background, with an **X** as my cursor), that says *there has been issues with your display,graphic card or input device* and then gives me the option to reconfigure it, **but** if I click *reconfigure*  or any other option just nothing happens it goes back to the initial window. I did a BIOS update yesterday, but I am not sure that that is the one that caused it.

Now the *strange* thing - if I switch to tty1 with Ctrl+Alt+F1 and start *lightdm* manually everything works lika a charm. I am using bumbleebee and already tried reinstalling it.
Tested it with *glxspheres* and both graphic cards seem to be working just fine.

Here is my *lspci -v* output regarding the Nvidia card:```
01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 520M] (rev ff) (prog-if ff)
    !!! Unknown header type 7f

```Well that doesn't look too good, any idea how to fix this - or generally how to reinstall the graphic drivers without wrecking bumblebee?

---

### Post by krustenBrot on 2012-11-25
Update: since i could not change anything within the xserver pop up i tried reconfiguring my xserver or light dm using the terminal here is the exact output: > aaron@aaron-U36SD:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for aaron: 
aaron@aaron-U36SD:~$ sudo dpkg-reconfigure lightdm
aaron@aaron-U36SD:~$ 


nothing has been cut ... it just doesnt do anything. The usual dialog isnt showing up :/

---

### Post by krustenBrot on 2012-11-30
Solved. The latest update somehow fixed it. At least lightdm is starting correctly and i can login. Did not test if *dpkg-reconfigure *isworking againt.

---

