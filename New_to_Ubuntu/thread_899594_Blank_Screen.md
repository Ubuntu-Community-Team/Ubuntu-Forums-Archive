---
title: "Blank Screen"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by clparis on 2008-08-24
Last night, I installed ubuntu from the alt cd and it worked. I got all the way through the installation. I ejected the cd and let it reboot and the start up screen comes up and the loading bar goes across then nothing. The laptop is still on but the screen is completely blank. I turned it off and went to bed. Today I turn on the laptop it goes through the load up screen then blank. It has been running for about 2 hours with no change. The laptop is a compaq presario with 30G Hard drive and 256M ram. I did a use all drive space install with no other partions. Can someone tell me what I need to do. Thanks.

---

### Post by kagashe on 2008-08-26
At boot screen there are some options. Scroll down to recovery mode option and you will boot into root console after some time.

Type the following command:
> # nano /etc/X11/xorg.conf
This will open X window configuration file in the editor called nano. Scroll down to Device section and add this entry:
> Driver "vesa"

The section should now read:
> Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection

Press Ctrl o to save the changes
Press Ctrl x to exit.

Reboot with the following command
# reboot

If your installation was complete you will be able to boot. If you succeed post here so that we can guide you further.

---

### Post by overdrank on 2008-08-26
Hi and welcome, to add to kagashe you can use the xfix option if you boot into recovery mode. Recovery mode is usually the second choice from the grub. I offer this suggest as it may be a little easier than editing your xorg unless you are familiar with nano. :)

Also what is the model of the graphics card? With that low memory you may look at something lighter than Ubuntu. Some of the memory is shared with the graphics and may run very slowly.

---

### Post by kagashe on 2008-08-26
@ overdrank
Since he is getting blank screen I would like him to boot with vesa driver. Are you sure xfix will use vesa driver after he reboots?

@ sclparis
When you chose recovery option at boot you will be presented with following options after some time:
```
resume	resume normal boot
dpkg	repair broken packages
root	drop to root shell prompt
xfix	try to fix x-server
```

You can **chose xfix option** as suggested by overdrank. After xfix runs you will again be presented with same options. You can chose resume and see whether your problem is solved if yes thank overdrank.

If it is not solved again chose recovery mode and **chose root option**. This will get you to root console. Follow my procedure and reboot.

nano is a command line linux editor. Scrolling is easy, just move the down and left or right arrow key. Bring cursor at end of the line:
> Identifier "Configured Video Device"

and press enter and you will get a blank line below it. Use Tab key to move cusor now and Type:
> <Tab>Driver<Tab><Tab> "vesa"
in that line

Save with Ctrl o and exit with ctrl x.

kagashe

---

### Post by clparis on 2008-08-30
I thank you for your advice. I tried the xfix option with no luck but the vesa addition worked and I have a desktop. Thanks again.

Corey

---

### Post by kagashe on 2008-08-30
> **clparis said:**
> I thank you for your advice. I tried the xfix option with no luck but the vesa addition worked and I have a desktop. Thanks again.

CoreyGood. Now there is a need to find out the driver for your card so that the screen is not blank. Please post the output of:
> @ lspci | grep VGA

kagashe

---

### Post by IchBin on 2008-09-07
kagashe, Thank you! These posts got me up and running. Was getting the same blank screen here with just the busy mouse icon.Been struggling with the install for a couple of weeks on and off. Finally got it to install with the alternate CD. Booted to a rescue prompt and edited the xorg.conf file. It then booted without a problem. I did the command you showed for the video driver. Just when I did that, Ubuntu asked me if I'd like to install the NVidia driver set. YES PLEASE! I now have a working Ubuntu install. Thank you!

---

### Post by Trusthim on 2008-09-09
Hello,

I am also an absolute beginner to Ubuntu.

I installed it some days ago on my USB Drive.
Everything worked fine (Ver. 8.0.4.1),
but everytime I start Ubuntu I get a blank sreen after the boot screen. 
I already asked some questions in the geramn forum, but nobody could help.

When I use recovery --> XFIX --> resume boot
Everything is ok. (Resolution 1280x800)
But when I start "normal" I get a blank screen...

System: Laptop HP nc6400
Intel 945GM

Anything I could do?

Thanks in advance
Mathias

---
[http://www.lookingforgod.us/](http://www.lookingforgod.us/)

---

