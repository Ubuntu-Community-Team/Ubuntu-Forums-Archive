---
title: "can't boot 12.04 from external hard drive"
date: 2014-02-01
forum: New to Ubuntu
---

### Post by mark allyn on 2014-02-01
Hello everyone,

Until yesterday I was able to easily boot 12.04 from an external Seagate hard drive. Something happened to change this.  I no longer am able to boot normally, although I can boot from the recovery system.  Using the recovery boot file I get the terminal shell and can run commands as if I had run term, but cannot seem to get the desktop back, and any application that requires the display--for example, QToctave, or gnumeric, or ddd, will not run and displays an error message.  I can't figure out what command to issue that brings up the desktop.

When I attempt to boot from the normal boot file I get the nice mauve background, but no gui desktop and no login dialog.  

Can someone kindly suggest a fix for this.  (BTW,  booting Windows 7 from the internal hard drive works fine....hmmm).

Regards,
Mark Allyn

---

### Post by oldfred on 2014-02-01
To start gui if lightdm:
 sudo service lightdm start
or: gdm, lightdm, xdm, etc 
or: startx

Did you update any packages?
What video driver?

---

### Post by radogost1981 on 2014-02-01
Exactly the same thing as you describe happened to me when i first time installed ubuntu. What caused it was the graphics driver. Ubuntu installed some driver for my nvidia card but there was more drivers on the list when i checked so i installed another (apparently newer version) and after i did that i was getting only a black screen with mouse. Maybe you should check your drivers or reinstall them but i wont be able to help you with that - I'm too new to ubuntu, I had to reinstall the whole system :) - just trying to be useful and give some idea :)

---

### Post by mark allyn on 2014-02-01
oldfred,

Tried all of your suggestions and all failed.  I can't tell you what the video driver is because when I issue lshw the screen I get back doesn't scroll when I'm in the recovery mode and it shoots past that info.  I believe that the boot failure is in fact a result of a fouled-up update.

The only clue I can give you is that if I issue gedit command on the recovery screen I get a message back saying "Cannot open display".  If I type startx, the sys reports back that /usr/bin/X not found.  

And also in recovery mode if I ask for list of environmental vars many are noit present that should be, for example (among many): 
$DISPLAY.

Thanks for trying to help.  I really don't want to reinstall the whole darn system (yet) again.

Regards,
Mark

---

### Post by mark allyn on 2014-02-02
oldfred,

Using lspci I find that the video card is AMD/ATI RS880M.

The problem seems to be in X11.

Mark

---

### Post by oldfred on 2014-02-02
Unless you have gui running, you cannot launch any applications that need gui support. So error on gedit is normal. If wanting to edit a file you have to use a terminal based text editor like nano, or joe(usually not installed by default).

I have nVidia so do not know issues. 
But AMD stopped supporting older cards. Is this older or newer?
If older card and you installed newest driver that may be an issue.

 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1)
> On the proprietary driver side, the AMD Catalyst 12.11 Beta Linux graphics driver was used. For this initial testing, three discrete graphics cards from the AMD Radeon HD 5000/6000 series were used, since pre-HD5000 graphics cards are now on the Catalyst Legacy driver and the latest-generation Radeon HD 7000 series hardware still doesn't fully work with the open-source Gallium3D "RadeonSI" driver.

You can try forcing the generic, with these instead of nomodeset.

 xforcevesa or nouveau.modeset=0

and/or

 copy failsafe to xorg to use vesa as default
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf

---

### Post by mark allyn on 2014-02-02
oldfred,

I don't know how old it is. Around 2-3 years.  Whatever it is, I have never installed a newer card.

Now, here's some info for you to mull over.  I do not have a xorg.conf file in /etc/X11.

Regards,
Mark

---

### Post by oldfred on 2014-02-02
Did you try the boot option to force vesa mode?

---

### Post by mark allyn on 2014-02-02
oldfred,

I don't understand how to do the forcing.  I suspect that when I get into the recovery mode I need to click on the grub option.  After that, not sure what happens.  I know that xforcevesa is a setting in the /etc/default/grub file, but I need some guidance.

Thanks for continuing to help with this.

Mark

---

### Post by mark allyn on 2014-02-02
Hi oldfred,

Well, after much googling around I finally solved the problem of the blank screen.  For some reason--probably a failed update--I had clobbered xorg.conf.  I downloaded and installed xserver.xorg and all is well.

Thanks for your efforts.

Mark

---

