---
title: "ubuntu compatibility with dell dimension e521"
date: 2018-07-20
forum: New to Ubuntu
---

### Post by malachai2 on 2018-07-20
I have installed Ubuntu 14.4.1 on my Dell Dimension E521 and when bootup is finished I get a  screen with no desktop options and no mouse icon. Do I have to install a previous version of Ubuntu? Or what?

---

### Post by kc1di on 2018-07-20
Hello malachai2  and Welcome to Ubuntu Forums,

No you do not have to install former releases. 14.04 is still supported until next year. But it's getting pretty old now. I would consider installing at least 16.04.
I do not have a e521 to test on here but I suspect what your running into is a video card driver problem.  
does that machine have Nvidia video care?  if so you'll need to follow the procedure listed [here]("https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu") to get it going.

---

### Post by mIk3_08 on 2018-07-20
For Boot Repair [Click Here]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by Impavidus on 2018-07-20
So you get no desktop options or mouse cursor. But what do you get? A black screen? A black screen with some text? A desktop with a background but nothing to click?

If [these]("https://www.cnet.com/products/dell-dimension-e521-tower-athlon-64-x2-5000-plus-2-6-ghz-2-gb-320-gb-lcd-20-1/specs/") are the specs, the ram may be a little low for Ubuntu, but Xubuntu or Lubuntu or Ubuntu Mate (all 18.04) should work fine. Just don't load too many websites simultaneously. Or consider increasing the ram to the maximum of 4GB. Also, if those specs are correct, it seems that the graphics card should be [supported by the open source drivers]("https://help.ubuntu.com/community/RadeonDriver").

Note that Ubuntu 14.04 is getting close to end of life. It's not a good idea to install it now. For the lighter flavours, 16.04 is getting close to end of life, so better use 18.04.

---

### Post by NM5TF on 2018-07-21
sounds like you have a nvidia video card....they have dropped support for the new version of Xorg (1.20) on their
older cards....you will need to use the [COLOR="#FF0000"]nouveau[/COLOR] open source driver......do this:

at boot hold down the [COLOR="#FF0000"]shift[/COLOR] key until the boot screen shows....key in [COLOR="#FF0000"]e[/COLOR] to edit the kernel parameters.....on the line
beginning with [COLOR="#FF0000"]linux[/COLOR], add [COLOR="#FF0000"]nouveau[/COLOR] after quiet splash.....use F10 to reboot......did this fix your problem ???

if problem is now fixed, you need to make the changes permanent......by doing this:

```
sudo nano /etc/default/grub

and then add nouveau to GRUB_CMDLINE_LINUX_DEFAULT:

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nouveau"
GRUB_CMDLINE_LINUX=""

And then exit nano with Ctrl+X, BE SURE TO SAVE IT, then simply run:

sudo update-grub

```

---

### Post by mörgæs on 2018-07-21
Some of the C521's have Nvidia Geforce 61xx graphics cards which might need a special treatment. Maybe the same goes for an E521.

Are you able to run any kind of Buntu which gives a useable screen, for example a live boot? 

If so then please copy ```
lshw -C video
``` and paste it to the command line, run it and post the output here in CODE tags. It will give us a better foundation for helping.

---

