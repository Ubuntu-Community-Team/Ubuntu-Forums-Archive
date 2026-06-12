---
title: "System freezing"
date: 2015-05-02
forum: New to Ubuntu
---

### Post by Roger_Moth on 2015-05-02
Hi I am very very new to Ubuntu. I have two pc's one has a very good install of Linux mint rebecca, the other I have win7 and a separate partion for Ubuntu 14.
No matter how I try to install Ubuntu on either pc it freezes. I have tried to install Ubuntu on it's own but still no joy.
I have seen many people on the net have the same problem and it all seems to be to do with the graphics card. However I have looked and the driver for my pc is the latest version. I have also looked at some of the various options to alter the settings but I did not get very far and to be fair I do not understand most of it.
So, before I finally give up, can any one help me in simple laymans terms please. I really would like to try it and it does seem odd that Mint works fine.
Regards Roger.

---

### Post by kc1di on 2015-05-02
Hello Roger_Moth and welcome to Ubuntu,

There could be several reasons for that, including a bad download or burn. Check that first. 
Or video card problem.  we we would need to know more about your machines to tell however so give us a little more information.
seeing how Mint installs which is built on the same base , I tend to think it is a bad download or burn. 
Good luck ;)

---

### Post by Roger_Moth on 2015-05-02
Hi Many thanks for your reply and a bad burn is not something I have seen so it could well be an option. The current machine I am using is as follows:
AMD Sempron 140 Processor 2.70 Ghz.
64 Bit
Display Adapter NVIDIA GeForce 6150SE nForce 430.
I do not know how to find this information in Mint for my other pc. I have been installing from a usb stick but i have also made a disc today so I might try that in the meen time.
Please let me know what other information you might need.
Many thanks Roger.

---

### Post by VMC on 2015-05-02
This is the problem: "**NVIDIA GeForce 6150SE nForce 430**". I have the exact same integrated display. You need to add "**nomodeset**" to the linux line for it to boot, then add propitiatory driver.

Here's instructions: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Installation](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Installation)

---

### Post by Roger_Moth on 2015-05-02
Hi I have seen this before but I do not understand how to do it but I will go to the link and see what happens.
many thanks.

---

### Post by Roger_Moth on 2015-05-02
Hi sorry but I do not understand any of this, complete newbie, if Ubuntu is frozen how do alter anything and what exactly do I do please.
Thanks.

---

### Post by Roger_Moth on 2015-05-02
Hi well I have just gone back into Ubunto but went into the diagnostics settings and then went to repair and low and behold it works perfectly for the first time.!!!!!!!! Not sure what I have done and I hope it still works after a re-boot.
Thanks.

---

### Post by dino99 on 2015-05-02
> **Roger_Moth said:**
> Hi well I have just gone back into Ubunto but went into the diagnostics settings and then went to repair and low and behold it works perfectly for the first time.!!!!!!!! Not sure what I have done and I hope it still works after a re-boot.
Thanks.

hey that's a good news  :p
about the 'nomodeset' parameter, you need to add it before 'quiet splsh' words on the same line into /etc/default/grub; > sudo nano /etc/default/grub

but if you says that all is fine now, maybe you can do without it. But as Mint is ok (gtk2 distro) it should mean that your card have some hard time to run 3D gui, like actual gtk3 ubuntu. A solution is probably to use Lubuntu instead.

---

### Post by VMC on 2015-05-02
Once booted, use Restricted Drivers to install nvidia driver.

---

### Post by Roger_Moth on 2015-05-02
Hi Thanks for all the info. I did manage to find the restricted drivers and installed the Nvidia driver. However after a restart all is not well. I have a mouse but not all the icons are showing and there is nothing else working. Oh Dear so close. I do not know how to add the lines of code described by dino99 so being a newbie I need really detailed instructions.I will have to do a hard reset on the pc and see what happens, may be I should revert to the Nouvou driver if I can. Update after a hard reset it is still not showing much other than the home screen no icons but I do have a mouse. Help.
Thanks.

---

### Post by Roger_Moth on 2015-05-02
Hi Well things are not well after updating to the Nvidia driver, should have left it alone. It does boot to the home screen with all the icons but nothing works, so close again. I did try the repair software packages but no good this time. Now I need detailed instructions please on how I can revert it, I know about the alt-ctrl-f2 to get into the terminal but nothing form there. Please bear with me with your help.
Thanks.

---

### Post by kc1di on 2015-05-02
Ok which driver did you install?  you need the nvidia-304 for your card, it's the same card I have in my machine here. works great once you have the correct driver installed.  you can also use the default nouveau driver - but you have to add "nouveau-noaccel=1" to the boot line to get it to work. 

easiest way fix it now would be to get to a terminal by hitting "CRTL>ALT>F1"  once in the terminal enter the following code:
```
sudo apt-get purge nvidia
```
```
sudo apt-get install nvidia-304
```

after it's finished reboot. should work then. 
Cheers!

---

### Post by Roger_Moth on 2015-05-03
Hi thanks for the detailed information. Ufortunately that did not work. I had the message "nvidia not installed so not removed". Then to re-install nvidia-304 the message was " nvidia-304 is already newest version so not installed. I have the desktop with icons and mouse but nothing works. So can you tell me how and where to install the nouveau. This was the cofiguration that worked before I changed it in setup to nvidia-304 when it all did work after going into system repair.
Many thanks for your patience.

---

### Post by alex375 on 2015-05-03
you need the /etc/modprobe.d/ actions to restore it
in all files add blacklist before all nvidia staff .And remove it before nouveau

---

### Post by Roger_Moth on 2015-05-03
Thanks for that but where do I actually put this information please. I know nothing about this at all.

---

### Post by dino99 on 2015-05-03
> **alex375 said:**
> you need the /etc/modprobe.d/ actions to restore it
in all files add blacklist before all nvidia staff .And remove it before nouveau

Surely not, dont mess up the system, it automatically do the needed stuff

> sudo apt-get install xserver-xorg-video-nouveau
usually it is installed by default, so when nvidia-* is purged you get nouveau used on the next boot.

---

### Post by Roger_Moth on 2015-05-03
Ok Thanks I will try this.

---

### Post by alex375 on 2015-05-03
search all files in /etc/modprobe.d/ for words nouveau and nvidia

comment this lines with #

alias nouveau off
alias lbm-nouveau off
blacklist nouveau
blacklist lbm-nouveau


i mean 'blacklist lbm-nouveau'  to '#blacklist lbm-nouveau'

and add next line to /etc/modprobe.d/blacklist.conf  
 'blacklist nvidia'

---

### Post by Roger_Moth on 2015-05-04
Update, well I have tried several things mainly to purge Nvidia and install Nouveau but none of it made any difference. It could not find Nvidia to purge and it could not find xserver-xorg to install that. So I have re-installed Ubuntu, first I had a blank screen so on reboot I went to recovery mode and then repair broken packages. Fingers crossed this is working very well. There are two options to use Nvidia 304 software but I will leave this alone and get used to the system and above all learn. Thanks to you all for the help especially dino99. If you have any more thoughts or ideas do let me know I am keen to learn all about this system.
Regards.

---

### Post by Roger_Moth on 2015-05-12
Done it. Just to let anyone know I have finally sorted it all out. I have done a mixture of many things to achieve this but the main things seemed to be installing the updated driver for the Nvidia software which I was advised to do earlier. The difference now seems to be that, by fair means or foul, I have installed all updates and also updating the kernal which then folloowed on with a proper install and use of the Nvidia software. When I look at the software in Ubuntu I see that Nouveau has been removed. Now wheather this has made a difference I don't know. But by a combination of help here and all the help available on this topic on the net I have an Ubuntu setup that works very well indeed and I am now looking forward to playing and learning.

---

### Post by dino99 on 2015-05-12
Patience is the master word; skill will happen greater each day ):P

---

