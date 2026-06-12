---
title: "Restore as when just installed"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by bilbo.san on 2008-05-03
Hey,
I would like to know, how can I restore Ubuntu?
You see, I installed the nvidia setting program to be able to improve the screen res a little more. It worked fine, but when restarting the system, the opening logo of Ubuntu was gone and showed texting instead... later then, the whole thing started to look different, there were no x buttons for closing windows and weird functioning.

Thanks
b.

---

### Post by mac9416 on 2008-05-03
I hate it, but I don't think that there is a "system restore" for Ubuntu except for reformat and reinstall.
Sorry. Maybe someone else knows better.

---

### Post by nowshining on 2008-05-03
A) Did you install from the CLI/Terminal and stop gdm first? The driver from the Nvidia website needs to be installed from the Terminal, exit all programs ,ctrl + alt + f1 - f6 choose one, inputr ur username and pw (pw won't show as you type),

issue the command:

 sudo /etc/init.d/gdm stop, enter your pw

cd to the place of the Nvidia.sh file and issue sud sh nameofnvidiafile.sh and enter ur pw

then re-start gdm with sudo /etc/init.d/gdm start

...........

for your other problems if you did it correct, it could be a problem with compiz, etc.. try turning it off and all special effects and see if you have the same problem and if need be try logging out and backin after the disabling of such a program.

---

### Post by bilbo.san on 2008-05-03
Hi
Thanks for the info... I took off the Nvidia Settings, went back to the old res and re-installed the nvidia drivers that Ubuntu first provided... almost everything went back to normal... but you know, I realized that the opening logo is smaller before it disappears, and looks bigger when Ubuntu logs off. 

I do not know much about this stuff, but I have the impression that the loading bar when the system starts is not compatible with a higher res. .. now... How or where could I change the resolution setting for the opening logo?

b.

---

