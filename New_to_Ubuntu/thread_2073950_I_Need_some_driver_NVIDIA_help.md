---
title: "I Need some driver NVIDIA help"
date: 2012-10-20
forum: New to Ubuntu
---

### Post by agentcocopuff on 2012-10-20
SPECS-
Ubuntu 10.04 64bit amd64 3gb ram nvidiageforce9600gt



Alright im not a total noob at linux, ive been using ubuntu for about 4 months now and gotten used to terminal. 

Alright

So i am having the typical ubuntu hardware problem,

I installed my upgrades from the update drivers section from system
section, and i got a glitch where it kept flashing a green screen and the login screen, so i had to uninstall it and it worked again, tried it with both driver versions and nothing...
so then i tried doing it manually throught terminal and sh ./ turning off the x server.... that stuff and an error popped up can somebody please find me the right driver or tell me how to fix this! im about to switch back to windows! (JK)

---

### Post by agentcocopuff on 2012-10-20
BUMP

Can somebody help me?!?

---

### Post by sandyd on 2012-10-20
You are talking about trying the drivers in the hardware drivers window right?

What is your computer model?

Also, can you post the output of
```

lspci | grep VGA
```?

You can do this by going to the terminal (Unity Dash -> Type in 'terminal', and selecting terminal)

and copying the command that is in the box above.

Also, I want to add that if you are using one of those optimus cards, you will have to use the bumblebee project to make graphics switching work.

---

### Post by fballem on 2012-10-20
When I was running 12.04, there were a lot of problems with my nVidia card and the drivers in the repository.

There is a ppa that contains more current nvidia drivers that may solve your problem.

To install from a terminal:

This will add the repository:
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
```

This will refresh the software list:
```
sudo apt-get update
```

This will update the nvidia driver, if you already have one installed, or install the nvidia driver if you don't.
```
sudo apt-get install nvidia-current
```

This will update the x-org configuration.
```
sudo nvidia-xconfig
```

When you are done, reboot your machine. There are two ways to do this:

If you have a gui screen, then just do a restart.
If you don't have a gui screen, but do have a terminal, then execute the following command ```
sudo reboot
```.

Hopefully, this will solve your problem,

Regards,

---

### Post by agentcocopuff on 2012-10-20
VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)

---

### Post by agentcocopuff on 2012-10-20
No the same error happend, where it flashes green then starts in low res and the screen is messed up

---

### Post by fballem on 2012-10-20
> **agentcocopuff said:**
> No the same error happend, where it flashes green then starts in low res and the screen is messed up

It would help to know to which post you were replying to.

Thanks,

---

### Post by agentcocopuff on 2012-10-21
> **fballem said:**
> It would help to know to which post you were replying to.

Thanks,

Yours sorry

---

### Post by NikTh on 2012-10-21
Hi , 
try  

```
sudo apt-get remove --purge nvidia-current 
sudo rm /etc/X11/xorg.conf 
sudo apt-get update 
sudo apt-get dist-upgrade
sudo apt-get install nvidia-173
sudo nvidia-xconfig
```
Reboot your system.

Thanks

---

### Post by agentcocopuff on 2012-10-21
> **NikTh said:**
> Hi , 
try  

```
sudo apt-get remove --purge nvidia-current 
sudo rm /etc/X11/xorg.conf 
sudo apt-get update 
sudo apt-get dist-upgrade
sudo apt-get install nvidia-173
sudo nvidia-xconfig
```
Reboot your system.

Thanks

Ubuntu rebooted, but the drivers were not installed

---

### Post by NikTh on 2012-10-21
Give the results of 
```
lspci -nnk | grep -iA2 vga 
dpkg -l | grep -i nvidia
``` 

Thanks

---

### Post by agentcocopuff on 2012-10-21
> **NikTh said:**
> Give the results of 
```
lspci -nnk | grep -iA2 vga 
dpkg -l | grep -i nvidia
``` 

Thanks

Here it is

lspci -nnk | grep -iA2 vga 


02:00.0 VGA compatible controller [0300]: nVidia Corporation G94 [GeForce 9600 GT] [10de:0622] (rev a1)
	Kernel driver in use: nouveau
	Kernel modules: nvidia-173, nvidiafb, nouveau

------------------------------------------------------------------------------


dpkg -l | grep -i nvidia 


ii  nvidia-173                            173.14.27-0ubuntu1                              NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-173-modaliases                 173.14.27-0ubuntu1                              Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-96-modaliases                  96.43.18-0ubuntu1                               Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-common                         0.2.23                                          Find obsolete NVIDIA drivers
rc  nvidia-current                        304.60-0ubuntu1~lucid~xup1                      NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current-modaliases             304.60-0ubuntu1~lucid~xup1                      Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-settings                       304.60-0ubuntu1~lucid~xup2                      Tool of configuring the NVIDIA graphics driver

---

### Post by NikTh on 2012-10-21
Give these commands 

```
sudo apt-get purge nvidia* 
sudo rm /etc/X11/xorg.conf 
sudo apt-get install nvidia-current 
sudo nvidia-xconfig 
```

And reboot.

After reboot give the results of 

```
lspci -nnk | grep -iA2 vga
dpkg -l | grep -i nvidia
```

Put the results between the brackets **[noparse]```
here
```[/noparse]**, so can be easy to read.

Thanks

---

### Post by agentcocopuff on 2012-10-21
```
corey@ubuntu:~$ lspci -nnk | grep -iA2 vga
02:00.0 VGA compatible controller [0300]: nVidia Corporation G94 [GeForce 9600 GT] [10de:0622] (rev a1)
	Kernel driver in use: nouveau
	Kernel modules: nvidia, nvidiafb, nouveau
corey@ubuntu:~$ dpkg -l | grep -i nvidia
ii  nvidia-current                        304.60-0ubuntu1~lucid~xup1                      NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                       304.60-0ubuntu1~lucid~xup2                      Tool of configuring the NVIDIA graphics driver
corey@ubuntu:~$ 

```

---

### Post by NikTh on 2012-10-22
Your installation is correct now , but the driver is not. Still loads the nouveau. 

We will force it to load the nvidia driver and we will blacklist the nouveau. 

**In case** that you cannot login (or you see only a black screen) you have to boot from recovery mode (hold down [Shift] key during boot if you haven't grub menu) and undo the changes. 

Give these 2 commands 

```
echo 'blacklist nouveau' | sudo tee -a /etc/modprobe.d/blacklist.conf 
echo 'nvidia' | sudo tee -a /etc/modules
```Reboot your system. 

To undo you must remove the entries from /etc/modprobe.d/blacklist.conf and /etc/modules. 

You can use nano editor from terminal or consolse mode (Recovery mode)
```
sudo nano /etc/modprobe.d/blacklist.conf **#** and remove the entry **blacklist nouveau** at the end of the file 
sudo nano /etc/modules **#** and remove the entry **nvidia**
```To save the changes with nano press Ctrl+X ,then Y(es) , then [Enter] key. 

Thanks

---

