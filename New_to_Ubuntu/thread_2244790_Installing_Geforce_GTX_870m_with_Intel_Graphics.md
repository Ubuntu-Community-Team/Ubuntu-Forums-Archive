---
title: "Installing Geforce GTX 870m with Intel Graphics"
date: 2014-09-18
forum: New to Ubuntu
---

### Post by Jos_Guilherme on 2014-09-18
Hi,
I'm pretty new in ubuntu, and just loving so far.

But i got a problem while install my GPU, that one works in a laptop.
I try the drivers provided by NVIDIA and through apt-get. Both no success.

So, im just thinking about. 
The predominant video graphics in windows is a Intel Graphics HD (i dont remember the number or the model) and the gtx870m is triggered when needed, for high graphics.
Maybe that is the problem? Theres a way to i can work that GPU in Ubuntu?

Thanks,

---

### Post by redrumrogue on 2014-09-18
Hi there - when you say " no success" what do you mean?  how do you know the nvidia driver is not working / installed correctly?

---

### Post by Michael_McKenney on 2014-09-18
Can you get to a terminal prompt?

ctrl+alt+t (terminal)
lspci

What video adapter is on the list?

---

### Post by Jos_Guilherme on 2014-09-18
Redrumroque,
I get two messages:
"The distribuition-provided pre-install script failed. Continue Anyway?" (i check yes)
"The Nouveu Kernel driver is currently in use by your system. The driver is incompatible with your NVIDIA Driver"
After that setup disable the setup driver, and them i proceed with installation normally. But now the X dont start anymore.

Michael_McKenney,
The video adapter (after installation)
NVIDIA Corporation GK104M [GeForce GTX 870M] (rev a1)

---

### Post by redrumrogue on 2014-09-18
[SIZE=2][FONT=tahoma]Hi Jos,

Are you installing the nvidia driver from the .run file downloaded from the nvidia website? If you are, this is something I've done recently with success by following these steps:
1.  Blacklist the nouveau driver so it doesn't conflict with the new nvidia driver.[/FONT][/SIZE][INDENT=2][SIZE=2][FONT=tahoma]1.  open a terminal window and type ... 
[/FONT][/SIZE][/INDENT]
[INDENT=2][SIZE=2][FONT=tahoma]     ```
sudo -i gedit /etc/modprobe.d/blacklist-nouveau.conf
```
2.  add the following lines in the file ...
     ```
blacklist nouveau
blacklist lbm-nouveau
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off
```[/FONT][/SIZE]
[/INDENT]
[SIZE=2][FONT=tahoma]2.  Now you can reboot your computer, and when you get to the login prompt,  press Ctrl+Alt+F1 to exit to the terminal console. Login with your  username and password.
3.  Stop the display manager ...
     ```
sudo stop lightdm
```
4.  Install linux headers ...
     ```
sudo apt-get install linux-headers-generic
```

5.  move to the folder where you downloaded the nvidia .run file
6.  And now you can finally install the nvidia driver using a code similar to this one:
     ```
sudo sh NVIDIA-Linux-.....run
```
7.  Reboot the machine.
8.  Once you have rebooted you can use the nvidia-installer command in a terminal window to do various things such as check for updates (nvidia-installer --update)

If you ever want to enable the nouveau driver again just delete (or move to your home folder) the /etc/modprobe.d/blacklist-nouveau.conf file and then reboot.

You can also just install the nvidia driver available from the ubuntu repositories by opening the "Software & Updates" utility and going to the "Additional Driver" tab.  Ubuntu will search for available drivers (may take a few moments) and you can then select one of the drivers there (eg: "NVIDIA binary driver - version 331.38 from nvidia-331 (proprietry, tested)".  You will need to reboot after doing this too.

Hope this helps![/FONT][/SIZE]

---

### Post by grahammechanical on 2014-09-18
You have what is called hybrid graphics. That is an integrated Intel graphic adapter and well as a discrete Nvidia adpter. Intel drivers usually comes as Linux modules but to switch between the Intel graphic adapter and the Nvidia adapter is not so easy. Part of the reason is that Nvidia were very, very slow producing a Linux driver. And even now you should not expect the same service from the Nvidia driver as Windows gets from it Nvidia driver.

Read this.

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

Regards

---

### Post by Jos_Guilherme on 2014-09-18
Hey! Thanks for the answer.
Im just tryin, but where the apt-get install linux-headers-generic is stored to i can take it to the same folder of nvidia?

---

### Post by redrumrogue on 2014-09-18
It doesn't matter what folder you're in when you type that command.  You only need to be in the nvidia run file folder when you execute the .run file.

---

### Post by Jos_Guilherme on 2014-09-18
Thats the thing! 
But i still got a problem! If i install nvidia driver, my lightdm stop to work, just a full black screen.
I need to figure out what is going on.

---

### Post by Jos_Guilherme on 2014-09-18
I appreciate ur attention! Very thanks man!
i tried all your steps... No working.

And if i go to "Additional Drivers" tab, nothing appears, only a message "No additional drivers avaliable."
I dont get whats going on...

---

### Post by redrumrogue on 2014-09-18
It can happen that after reboot your system shows a black screen or enters the low graphics mode. To fix this you should exit again to the console terminal (CTRL + ALT + F1), login with your username and password, and then type nvidia-xconfig (I don't know if you need sudo for this).

---

### Post by redrumrogue on 2014-09-19
Hi Jos - from what you have said it appears that you have been able to successfully log in and view the "Software & Updates" utility.  Previously you said that your lightdm stopped working and you just had a blank screen.   What did you do to get lghtdm working again?  Did you uninstall the nvidia driver and remove the blacklist for the nouveau driver?

If you have not uninstalled the nvidia driver then please post the output from from the follow commands in terminal window :
```
nvidia-installer --version
```
and ...
```
lsmod | grep nvidia
```

Thanks.

---

