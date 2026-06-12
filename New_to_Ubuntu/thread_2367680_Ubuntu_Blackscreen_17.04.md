---
title: "Ubuntu Blackscreen 17.04"
date: 2017-08-02
forum: New to Ubuntu
---

### Post by yoyo433 on 2017-08-02
Hello All,

As you can see I am a new user to Linux. I installed Linux on my Win 10 machine. Everything was working fine with no problem until I stumbled upon a youtube video giving info on how to update Nvidia drivers. I did the same and guess what? I reach the Grub Menu and run Ubuntu, Black screen. 
I did try the following steps:
1. Tried placing the command nouveau.modeset=0 in the linux line, I was able to log in and the ubuntu said I have installed the wrong video driver. Then I followed the screens which lead me to a dead end where I couldnt go further ahead (Please dont ask me what was the last message before I restarted the computer)
2. Tried placing the command again, but nothing happened, screen goes blank
3. Again, I restarted the machine, reached Grub, pressed e and entered modeset=0 before quiet splash. I was able to log in only to terminal (I think), then there was some loop which kept coming on the screen and I was not able to enter anything.

I just realized I need to just uninstall nvidia drivers, and update them accordingly. 

4. Restarted the machibne, Tried to go to recovery options- Tried Failsafe X- Nothing happened
                            
Can some one who has the patience to teach a newbie like me on how to go about this problem?
Am I suppose to reinstall Ubuntu and fix the drivers?

---

### Post by BenginM on 2017-08-02
Hiya , welcome to the forums .. and it's GNU/linux , linux is just the kernel and is only 2.5 present of the OS .. anyway i've seen this seems to be a common issue with nvidia and user input faults, basically what you need to do is boot when the GRUB menu appears as you already know Highlight the Ubuntu menu entry and press e . Add nouveau.modeset=0 to the end of the linux line.. not before quiet splash , but after it.. then Press F10 or Ctrl+x to boot Ubuntu OS .. when you get stuck at the black screen switch to a VT (virtual console) with the keys Ctrl+Alt+F4 , login with your user credentials .. once you're in , run:

sudo apt-get purge nvidia*  

sudo ubuntu-drivers devices

to get the list of packages for each driver, and then install the packages using apt-get .. a window should appear like , for example :

```

sudo ubuntu-drivers devices== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==  
vendor   : NVIDIA Corporation modalias : pci:v000010DEd00000DDAsv000017AAsd000021D1bc03sc00i00 
model    : GF106GLM [Quadro 2000M] 
driver   : xserver-xorg-video-nouveau - distro free builtin driver   
: nvidia-304-updates - distro non-free driver   
: nvidia-304 - distro non-free driver   
: nvidia-331 - distro non-free recommended driver   
: nvidia-331-updates - distro non-free

```

install one of the available nvidia drivers for the GPU ..

sudo apt-get install nvidia-XXX

replace XXX with the driver number you've chosen ..

sudo reboot

hopefully you'll reach the display manager and login to a proper DE.

---

