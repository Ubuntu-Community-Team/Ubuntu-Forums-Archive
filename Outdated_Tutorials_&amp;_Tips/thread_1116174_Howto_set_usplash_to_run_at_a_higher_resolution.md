---
title: "Howto set usplash to run at a higher resolution"
date: 2009-04-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Jose Catre-Vandis on 2009-04-04
Assumes knowledge of how to use nano (if not use gedit or mousepad)
Assumes users monitor can run at resolutions specified (if not system will complain and offer choices), if you know the native resolution of your monitor, don't go beyond that.

The native resolution of my monitor is 1280 x 1024 so I have used the settings for that.

**_1. Framebuffer Setting in menu.lst_**

First you need to organise your display that you see before X starts running. You can do this by adding a **[COLOR="Red"]vga=rescode[/COLOR]** to the end of your kernel line in the grub menu. 

Before submitting to your menu.lst, you can try this on boot by first getting to the boot menu (if you see a 321 countdown press ESC to get the menu) when you see the menu just press the down arrow on your keyboard to stop the boot process.

Select the boot line you want and press "e"
Select the kernel line and press "e"
Move to the end of the line and add (after a space) [COLOR="Red"]**vga=rescode**[/COLOR]
For all resolution codes available see point 4.
Then press "Enter", press "Enter" again and then press "b"
If all goes well your pre X resolution should be in evidence, if not your PC will ask you to provide a working code.

Now to make this permanent:

```
nano -w /boot/grub/menu.lst
```

Scroll down to the boot sequence you want to change, and add the vga code to the end, and save out. here is an example:

> title           IBEX Ubuntu 8.10, kernel 2.6.27-7-generic
uuid            efde92a2-e50d-4896-8170-8004782871f1
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=efde92a2-e50d-4896-8170-8004782871f1 ro quiet splash **[COLOR="Red"]vga=794[/COLOR]**
initrd          /boot/initrd.img-2.6.27-7-generic
quiet

**_2. Edit /etc/usplash.conf_**

Now we need to tell usplash to run at that resolution

```
nano -w /etc/usplash.conf
```

edit your usplash as below, replacing your resolution as appropriate

```
# Usplash configuration file
#original
#xres=1024
#yres=768
[B][COLOR="Red"]#new
xres=1280
yres=1024[/COLOR][/B]
```

**_3. Update initramfs_**

Run this in a terminal

```
sudo update-initramfs -k all -u
```

This will ensure your usplash is centralised on the screen.
Reboot and everything should be dandy.

**_4. Common Framebuffer Settings_**

```
VGA Resolution Codes for GRUB & Lilo

--- Depth --

Colors  bits  640x480  800×600  1024×768  1152×864  1280×1024  1600×1200
   256    8   vga=769  vga=771   vga=773   vga=353   vga=775    vga=796
 32000    ?   vga=784  vga=787   vga=790   vga= ?    vga=793    vga= ? 
 65000   16   vga=785  vga=788   vga=791   vga=355   **[COLOR="Red"]vga=794[/COLOR]**    vga=798
 16.7M   24   vga=786  vga=789   vga=792   vga=795   vga=799
```


To undo, simply re-edit usplash.conf to your original settings, remove the vga=rescode from your menu.lst, and run the code in 3. again.

---

