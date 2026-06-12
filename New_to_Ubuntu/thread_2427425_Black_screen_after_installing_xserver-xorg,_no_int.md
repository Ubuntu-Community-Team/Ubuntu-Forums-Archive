---
title: "Black screen after installing xserver-xorg, no internet in recovery mode"
date: 2019-09-22
forum: New to Ubuntu
---

### Post by valtiel2 on 2019-09-22
Hello,

after updating my nvidia card on Ubuntu 16.04 LTS (on a Dell XPS 15 9570, with integrated Intel graphics and a 1050Ti), I tried to fix some Intel graphical issues by running  
sudo apt-get install xserver-xorg-video-intel
sudo apt-get install xorg-video-abi-20

The reboot after that gave me a black screen after GRUB, and even though I tried to fix and purge/install new drivers in recovery mode (or in tty1 in upstart mode) the computer cannot connect to internet (the networking tool doesn't work in recovery, "sudo iwconfig essid <your wifi name>" fails, adding "iface wlp59s0 inet dhcp' to /etc/network/interfaces and running "ifup wlp59s0"...).

I don't know what to do and where to start to save my machine. I tried :
-modifying /etc/modprobe.d/i915.conf but it doesn't exist
-"sudo apt-get upgrade" but I don't have internet
-loading a different kernel with GRUB (4.15.0-60 instead of 4.15.0-62), this time I go as far as the login screen (graphics, yay!) but the keyboard isn't recognized
-adding option in GRUB "nomodeset", "i915.modeset=1", removing "blacklist.nouveau=1"
-creating a xorg.conf in /etc/X11 with "cp xorg.conf.* xorg.conf" as there weren't one

I hope I provided enough information, thank you for your help !

---

### Post by mc4man on 2019-09-22
You should mention what release of Ubuntu you are using.. (probably either 14.04.x or 16.04.x) the .x may matter..

---

### Post by #&amp;thj^% on 2019-09-22
Also can we see this:
```
cat /etc/default/grub
```
And yes i read your 1st post. ;)

---

### Post by valtiel2 on 2019-09-22
It gives [URL="https://ibb.co/NSXrmfS"]https://ibb.co/NSXrmfS
[/URL]
GRUB_CMDLINE_LINUX_DEFAULT="nouveau.blacklist=1 acpi_osi=! acpi_osi=\"Windows 2015\" acpi_backlight=vendor mem_sleep_default=deep"

I have a Win10 dualboot

Sorry for the quality !

---

### Post by #&amp;thj^% on 2019-09-22
> **valtiel2 said:**
> 
Sorry for the quality !
That's OK! :)
Usually I have to move my settings before installing/reinstallation:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bk
```

I have the same card "1050Ti" and would you try to add "**nogpumanager**" after this >>{acpi_osi=\"Windows 2015\" }
Now oddly sometimes powering the machine down completely helps:
```
sudo shutdown -h now
```
And wait 30 to 45 seconds before powering up again.
If that does not work we will also have to see the xorg.conf file too. :(

---

### Post by valtiel2 on 2019-09-22
Weirdly enough, "**nogpumanager**" brought a glimpse of hope by getting me to the login screen the first time but the keyboard wasn't recognized, and the following attempts stayed stuck on a black screen.

Other things did not work.


Here is my xorg.conf [https://ibb.co/HVCTydJ](https://ibb.co/HVCTydJ)
The others xorg.conf.* have the same exact content, except for .failsafe and .09222019 [https://ibb.co/nCsbQ31](https://ibb.co/nCsbQ31) [https://ibb.co/M6rtdxq](https://ibb.co/M6rtdxq)

Thank you again !

---

### Post by #&amp;thj^% on 2019-09-23
You know, I pulled an assumption, and thought you would automatically run after making the change I suggested above:
```
sudo update-grub
``` 
Now this will be for your Intel only card, we need to change your xorg.conf:
```
sudoedit /etc/X11/xorg.conf
```
Now remove anything you now see, and add only this:
```
Section "Device"
   Identifier  	"Intel Graphics"
   Driver      	"intel"
   Option 		"TearFree" "true"
EndSection
```
Now save and close.
Next we need to move/copy it to:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.d/20-intel.conf
```
With a little luck you should now be able to login to your system.
And one more question, is there a reason you have blacklisted nouveau?
BTW: Do you have a option in your Bios to disable the Nvidia card?
A reboot will be needed for the changes to take place.

---

### Post by valtiel2 on 2019-09-23
There is some progress !

It goes a bit further than before, but only to display "System running in low-graphics mode" and to tell that the screen, gpu and input device settings could not be detected correctly. I'm stuck there as the keyboard doesn't respond.
[https://ibb.co/jZxFxNt](https://ibb.co/jZxFxNt)

Should I try to complete the xorg.conf more ?

I don't see an option to disable the Nvidia card, and nouveau is  blacklisted because I installed proprietary nvidia drivers (nvidia-418)  and needed to have nouveau blacklisted to make it work properly.

---

### Post by #&amp;thj^% on 2019-09-23
> **valtiel2 said:**
> 
Should I try to complete the xorg.conf more ?

I don't see an option to disable the Nvidia card, and nouveau is  blacklisted because I installed proprietary nvidia drivers (nvidia-418)  and needed to have nouveau blacklisted to make it work properly.
No not yet.
There is something wrong with your install or hardware??
Do you have another Keyboard to use, till we get this sorted?
[/B]
> **valtiel2 said:**
> 
I don't see an option to disable the Nvidia card, and nouveau is  blacklisted because I installed proprietary nvidia drivers (nvidia-418)  and needed to have nouveau blacklisted to make it work properly.
I don't have it blacklisted??? Works just fine hear.
So to be clear you did install the Driver through the Stock Ubutnu Stoftware Repos Right?
And not by downloading it from Nvidia correct?
Show this Please:
```
apt policy nvidia-418
```

---

### Post by valtiel2 on 2019-09-23
[https://ibb.co/Rh0yvhd](https://ibb.co/Rh0yvhd)

I install the driver via "sudo apt install nvidia-418"
I don't think there is something wrong, the Dell XPS 15 9570 has always been a bit touchy to get a dualboot apparently (but I'm not sure I do everything properly).

The keyboard worked fine and still works in recovery mode, GRUB and Windows ! I tried with an external keyboard without success.

---

### Post by #&amp;thj^% on 2019-09-23
Ok I see a Cuda Repo as a install source and a entry for 14.04 also.
But lets change  and edit the /etc/default/grub file by putting the following lines:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi" GRUB_CMDLINE_LINUX="" 
```
and this time no assumption here:
```
sudo update-grub
```
and one quick suggestion, give this a try:
```
sudo apt remove --purge nvidia*
```
Followed with:
```
sudo apt autoremove
```
Now see if we can get a better install with:
```
sudo apt install nvidia-418 nvidia-settings
```
Yep you guessed it, Reboot.
Any Better?

---

### Post by valtiel2 on 2019-09-23
All right ! I made it to the login screen. But still no keyboard, stuck there.

This is weird and never happened before, how couldn't it be detected all of a sudden ?

---

### Post by #&amp;thj^% on 2019-09-24
Well all I suspect/guess is a bad or corrupt install, outside of a hardware problem.
Lets check a few things then, show me this this please.
```
localectl
```

---

### Post by valtiel2 on 2019-09-24
It gives

```

System Locale: LANG=en_US.UTF_8
VC Keymap: n/a
X11 Layout: ca
X11 Model: pc105
X11 Variant: multix
```

---

### Post by mc4man on 2019-09-24
That would appear to be an optimus device, if so did you at any prior point attempt to  enable prime sync? 
(only available in 16.04 from 16.04.3 and later image installs or if using the HWE xserver..

Also, **if an optimus**, what is returned from  ```
prime-select query
```
 & can you switch to Intel? ```
sudo prime-select intel
```

By default a 16.04 and 16.04.1 image install would have already had xserver-xorg-video-intel and been on xorg-video-abi-20 so your command to install them should have done nothing.
If you had installed from an image  > than 16.04.1 you would have been on the HWE xsever so that installing xorg-video-abi-20 would have removed all the xserver hwe packages in favor of the release xserver. Did that happen?

Also note that 418/430 drivers install a conf to /etc/alternatives/x86_64-linux-gnu_nvidia_modconf  Maybe there is some conflicting option in there?

---

### Post by valtiel2 on 2019-09-24
> **mc4man said:**
> That would appear to be an optimus device, if so did you at any prior point attempt to enable prime sync? 
(only available in 16.04 from 16.04.3 and later image installs or if using the HWE xserver..

Also, **if an optimus**, what is returned from ```
prime-select query
```
& can you switch to Intel? ```
sudo prime-select intel
```


I don't know prime sync and didn't try to enable it ! I also apparently purged prime
```
The program 'prime-select' is currently not installed.
```

> **mc4man said:**
> By default a 16.04 and 16.04.1 image install would have already had xserver-xorg-video-intel and been on xorg-video-abi-20 so your command to install them should have done nothing.
If you had installed from an image > than 16.04.1 you would have been on the HWE xsever so that installing xorg-video-abi-20 would have removed all the xserver hwe packages in favor of the release xserver. Did that happen?

Also note that 418/430 drivers install a conf to /etc/alternatives/x86_64-linux-gnu_nvidia_modconf Maybe there is some conflicting option in there?

I installed Ubuntu 10 months ago with the official LTS release and didn't notice the removal of xserver hwe packages.
I don't have x86_64-linux-gnu_nvidia_modconf in /etc/alternatives/

---

### Post by #&amp;thj^% on 2019-09-24
Then show:
```
apt search prime-select
```

---

### Post by valtiel2 on 2019-09-24
```
#apt search prime-select
Sorting... Done
Full Text Search... Done
```

---

### Post by #&amp;thj^% on 2019-09-24
Interesting...
I'm just stabbing in the dark now, but what dose:
```
ls /etc/modprobe.d

```
Show?

---

### Post by valtiel2 on 2019-09-24
Well thank you for the stabbing, it's even darker for me !

[https://ibb.co/q9DYgrs](https://ibb.co/q9DYgrs)

---

### Post by #&amp;thj^% on 2019-09-24
I'm committed now ;) (Like a moth to flames)
What shows here:
```
ubuntu-drivers devices
```

---

### Post by valtiel2 on 2019-09-24
This [https://ibb.co/ZGPWNkQ](https://ibb.co/ZGPWNkQ)

---

### Post by #&amp;thj^% on 2019-09-24
One important question, is Secure Boot enabled? If so disabled it from the bios.
Then run:
```
sudo ubuntu-drivers autoinstall
```
Now before you reboot you'll need to add the "nomodeset" to _/etc/default/grub_. (**After** the driver is installed)
and update grub:
```
sudo update-grub
```
Reboot.

---

### Post by valtiel2 on 2019-09-24
I managed to mount Ubuntu's partition by booting on live USB and ran
```
apt-get update
apt-get install xserver-xorg-input-evdev 
/etc/init.d/lightdm restart
```

The keyboard now works and I can login, but no touchpad and no windows (terminal won't show even if pictured as active on the taskbar, other windows appear buggy : without the top part).

I'll try your suggestion !

---

### Post by valtiel2 on 2019-09-24
These lines on live USB solved it for me

```


apt-get update   
apt-get install xserver-xorg-input-all
apt-get install ubuntu-desktop
apt-get install ubuntu-minimal
apt-get install xorg xserver-xorg
apt-get install xserver-xorg-input-evdev   
apt-get install xserver-xorg-video-vmware 
```

Xorg crashes on startup (but restarts), the resolution is way too big (cannot be rescaled easily in Display) and the wifi doesn't work (restarting network-manager changes nothing)... looks like the laptop disliked something pretty bad. But I have a computer now 

Thank you so much [COLOR=#000000]1fallen for your time and dedication !![/COLOR]

---

### Post by #&amp;thj^% on 2019-09-24
Ah! It was the install, now this makes good sense to me.
Thank You for your kind and considerable efforts.
Kind Regards

---

