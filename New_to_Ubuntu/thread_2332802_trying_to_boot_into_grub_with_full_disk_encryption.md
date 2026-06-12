---
title: "trying to boot into grub with full disk encryption"
date: 2016-08-04
forum: New to Ubuntu
---

### Post by Jonathan_McNeill on 2016-08-04
I've got a fresh install of Ubuntu-Gnome 16.04 and I've updated all the software. I selected full disk encryption when I installed Ubuntu. I'm using a Dell Inspiron 17R with a 500GB hard drive. 

I've had some video issues with flickering. I was reading about a possible fix here:
[http://askubuntu.com/questions/760934/graphics-issues-after-installing-ubuntu-16-04-with-nvidia-graphics](http://askubuntu.com/questions/760934/graphics-issues-after-installing-ubuntu-16-04-with-nvidia-graphics)

When I try to enter a TTY with ctrl-alt-F1 my screen goes black and the laptop reboots. The solution at the page above is to first boot into GRUB. 

The full disk encryption prompts me for the decrypt password when I reboot or boot up. I'm trying to boot into GRUB but pressing shift before the descrypt prompt or after the decrypt prompt doesn't get me to the GRUB menu.

I am guessing I'm doing something wrong. Anyone have any suggestions?

I would be grateful. Thank you.

---

### Post by grahammechanical on 2016-08-04
For clarity. You can load into Ubuntu? But you have some issues with flickering? Is that the situation?

The  suggestions offered in the AskUbuntu post are for those who cannot load  to a desktop environment. Or the desktop environment loads but is  frozen so pressing Ctrl+Alt+F1 does not work.

I can think of these ways to change a video driver.

1) System Settings>Software & Updates>Additional Drivers tab and change the video driver.
2)  Access a command line and run commands to purge an existing proprietary  video driver and then either using the default open source video driver  or using a command to install another version of the proprietary video  driver.

Accessing a command line

2a) Use the Dash to load the Terminal application
2b) Right click the desktop wallpaper and select Open Terminal
2c) Press Ctrl+Alt+T
2d)  Open a Linux console or tty by pressing Ctl+Alt+F1. That will get us to  tty1. We can also use Ctrl+Alt+F2 or F3 through to F6. And we will get  tty2 through to tty6. We log in and run commands.
2e) At the Grub  menu select Advanced options for Ubuntu. Then select a recovery mode  kernel. And at the recovery menu select Network to get internet access  and put the file system into read/write mode and then select Root shell  prompt. After running the commands we get back to the recovery menu by  typing exit. Then we select Resume to load to a desktop.

If there  is a conflict with a proprietary video driver then selecting Resume at  the recovery menu may get to a working desktop using a fallback video  driver.

Now, which of the above options is available to you? If  pressing Ctrl+Alt+F1 is causing the machine to reboot then it may be  that that key combination is doing the equivalent of Ctrl+Alt+Del =  reboot. May be.

Do you have an Nvidia graphic adapter? The commands in that Askubuntu post are for those of us who have Nvidia graphic adapters.

Regards.

---

### Post by oldfred on 2016-08-04
Most new systems are UEFI and then you have to press escape right after Dell logo to get grub. You may have to press several times.
If BIOS you have to hold shift key from Dell logo.
Also new UEFI systems have fast boot so you may not even get Dell logo, it just immediately boots assuming no hardware or configuration changes and you do not have time to press a key before boot starts. 

But specs look like that is a Haswell Intel chip with only Intel graphics.

Depending on kernel version, and Intel chip version, one of these boot parameters sometimes helps.
 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
 i915.preliminary_hw_support=1 #Skylake some versions of Ubuntu -For linux kernels older than 4.3.x, i915.preliminary_hw_support=1 must be added to your boot parameters for the driver to work on the new Intel Skylake (6th gen.) GPUs. On a fully updated system running kernel 4.3.x and up, this step is unneccesary.

---

### Post by Jonathan_McNeill on 2016-08-04
ctrl+alt+F1 gets me a black screen. ctrl+alt+F2 brings me back to the ttyl I am working in. Weird. ctrl+alt+F3 also takes me to a black screen.

Don't know if the full disk encryption option that I selected when I did the fresh install of 16.04 matters. 

I've seen the NVidia additional drivers tab. I have the following on the additional drivers tab:
Using NVIDIA binary driver - version 361.42 from nvidia (proprietary  and tested)
Using NVIDIA legacy binary driver - version 304.131 from nvidia-304-updates (proprietary)
Using NVIDIA legacy binary driver - version 304.131 from nvidia-304 (proprietary)
Using NVIDIA binary driver - version 340.96 from nvidia-340 (proprietary) 

I'm currently using X.org X Server -- Nouveau display driver 

There is also an option under UNKNOWN
Using Processor microcode firmware for Intel CPUs from Intel-microcode (proprietary)

Some time in the past I attempted to use Ubuntu 14 and when I switched to the NVidia driver it jacked up my system. It was a desktop system as opposed to the laptop I'm using now. I was worried I wouldn't be able to roll back if the nvidia driver didn't work. Especially since my entire disk is encrypted.

---

### Post by oldfred on 2016-08-04
If laptop does not have nVidia chip, then you do not install nVidia drivers.

 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA

---

### Post by Jonathan_McNeill on 2016-08-05
My laptop has an nvidia chip.

---

### Post by Jonathan_McNeill on 2016-08-05
First let me say THANK YOU. I really appreciate the help and suggestions here.

I used the driver [COLOR=#000000]NVIDIA binary driver - version 361.42 from nvidia (proprietary and tested) from the additional drivers tab and now my lap won't finish booting. I can do a ctrl-alt-F2 and see a message that a start program is waiting for the boot to finish time limit infinite. 

Thank you to oldfred because I did need to hit esc to get to the grub menu. 

Tried the instructions in the askbuntu link which were to press E. (though come to think of it I did a lower case "e" instead of an upper case "E" hmmm)
That took me to an emacs editor of a config file. 
Then I added nouveau.modeset=0 to the end of the line that starts with linux and pressed F10 to boot. 
After entering the encryption password I still get the black screen mentioned above. 

So I can now get into the grub menu. Which is good!

I tried going to the advanced ubuntu options in grub and then selecting recovery, same black screen, then the basic video option and I got a message that said my video and input devices could not be detected. Now my keyboard (assuming one of the input devices) gets no response basically nothing until I power cycle the laptop. 

Any suggestions as to how I can roll back the video driver are appreciated. Thank you very much in advance![/COLOR]

---

### Post by Jonathan_McNeill on 2016-08-05
Well I think I finally fixed it!

With oldfred's help I was able to get into grub. From there I go to the recovery menu, dropped into a root shell and did a purge on the nvidia.  
Rebooted and Ubuntu came up with the default nouveau drivers
added ppa:graphics-drivers/ppa to my repositories and updated
Then my additional drivers options changed and I now could select 
NVIDIA binary driver - 367.35 from nvidia-367 (open source)

I selected the above nvidia driver and installed it via the additional drivers tab under software and updates
Rebooted and everything worked.

I want to say thank you again to everyone who replied here and helped me. I really appreciate it!!

---

