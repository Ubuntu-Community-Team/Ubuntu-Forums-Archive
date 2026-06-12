---
title: "dual video card laptop xorg"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by thr1lla on 2008-09-18
hey guys, 
i am by no means a linux pro but i get by usually; i'm currently stuck with the same xorg resolution problem as everyone else. My problem is I have an ABS g3 revolution (its now the g4 revo for some reason) and it has an onboard intel graphics card (i810) and a geforce card on it that you can switch between with a toggle on the front.  

whenever i switch cards, not that its very surprising, but my xorg gets wiped (maybe?) and i have to reset my configuration and i get stuck with a plug and play 800 600 detected.  I can change all the value to corrent but i still only get a max of 1024 768 and even when i select it it boots into 600 x 800, is there any way i can set up two instance of xorg or set up these cards so i dont have to do this everytime?
thanks

*update* fun fact, i just restarted my laptop in another class and my laptop display got detected right off the bat without me having to set anything up (now i'm just confused), i'm still trying to set up a dual card xorg though so i'd appreciate input

---

### Post by prototype_angel on 2008-09-18
I don't think it's easy to switch between graphics cards just like that. Either if they're both onboard and your motherboard has some kind of really smart designers.

Even if windows somehow supports it I don't think Xorg will support the same.

What you can do is either:
Run:
```
sudo dpkg-reconfigure xserver-xorg
```

Or try restarting your Xserver after you switch using Ctrl+Alt+Backspace.

---

### Post by thr1lla on 2008-09-18
you have to power it off and switch it while the laptop isnt on so it isnt hot switching or anything.

i guess what i need is just something in the xorg that allows the laptop to just designate between the two defaults so it doesnt just give up every time; which i'm assuming is happening.

---

### Post by C.S.Cameron on 2008-09-18
It is easy to get the option to boot to different xorg.conf files at grub.
First install switchconf from the repositories using synaptic.
It will create the directory /etc/switchconf
inside of this create a few more folders thus:
/etc/switchconf/option1/etc/X11/ and /etc/switchconf/option2/etc/X11/ ...
Create one for each xorg option you want
copy your xorg.conf file to each of the X11 folders.
Edit your /boot/grub/menu.lst similar to this:
## ## End Default Options ##

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (option1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=e9e69233-ddcd-476d-8999-a4f67cf863ea ro quiet splash switchconf=option1
initrd          /boot/initrd.img-2.6.24-19-generic


title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (option2)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e9e69233-ddcd-476d-8999-a4f67cf863ea ro quiet splash switchconf=option2
initrd		/boot/initrd.img-2.6.24-19-generic


title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (option3)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=e9e69233-ddcd-476d-8999-a4f67cf863ea ro quiet splash switchconf=option3
initrd          /boot/initrd.img-2.6.24-19-generic


title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (option4)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=e9e69233-ddcd-476d-8999-a4f67cf863ea ro quiet splash switchconf=option4
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=e9e69233-ddcd-476d-8999-a4f67cf863ea ro single
initrd          /boot/initrd.img-2.6.24-19-generic


title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows 2000 Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


### END DEBIAN AUTOMAGIC KERNELS LIST

the important part is switchconf=option1 at the end of each section

When you boot hit Esc at grub and select your option.
You can then install your restricted drivers, set screen modes etc.
Reboot to the next option and set it up.
You now have the option to select between the various xorg.conf at boot.
I have not yet found  way to keep both Nvidia and ATI drivers installed at the same time.

---

### Post by shaunu3s on 2009-02-02
CS Cameron, great advice, worked for me. Having an issue though, upon coming back to my intel card, after switching to the geforce for the first time, compiz is no longer working. 
I was wondering what to do? the xorg.conf file loaded properly, could it have something to do installing the nvidia drivers?

---

### Post by Nepherte on 2009-02-02
I happen to have a laptop with 2 graphic cards as well, one on board intel and the other one a nvidia card. 

A possible solution (one I use) is to run a script on booting up your computer that determines what card is active. Depending on the active card, you simply replace /etc/X11/xorg.conf with a working configuration file (for example xorg.conf.intel and xorg.conf.nvidia) for that card.

create the script:
```
gksudo gedit /etc/init.d/xorg_conf
```
put this text in it and save the file:
```
#!/bin/sh
#
# Set the appropriate xorg.conf and GL links for the speed/stamina video card switch
#

VIDEO=`/usr/bin/lspci |grep -c nVidia`

if [ "$VIDEO" = 1 ]; then
  cp -f /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf
else
  cp -f /etc/X11/xorg.conf.intel /etc/X11/xorg.conf
fi
```
Make the file executable and make sure it runs at boot time:
```
sudo chmod +x /etc/init.d/xorg.conf
sudo ln -sf /etc/init.d/xorg_conf /etc/rc2.d/S12xorg_conf

```

The only thing left is two working xorg.conf files, one for the intel card and one for the nvidia card. It seems like you are already capable of generating one for each card so be sure to save them as /etc/X11/xorg.conf.intel and /etc/X11/xorg.conf.nvidia. Make sure you also have installed the drivers for both cards.

---

