---
title: "Editing grub.cfg directly without using scripts - GRUB Background"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by avnd on 2012-04-09
Hello!

I have a system where I have installed GRUB 2 to the MBR with the /boot folder in a 'dedicated GRUB partition'. 

I used a Live CD to install the GRUB and hence I don't have the scripts that generate the grub-cfg file. So, I have to create it manually.

Now, I wish to have a background image for my GRUB splash screen and I'm having trouble setting it up. All the guides on the web only give guidelines to change the splash background by making changes in the script files. I don't have that option. I have to make the entries in the grub-cfg file manually.

I tried reading the GNU GRUB manual and various grub-cfg files I could find, and came up with the following. But I'm nowhere near to having the background image. This is my current grub-cfg file.

```
# Timeout for menu (in seconds)
set timeout=60

# Default option to boot (number starts from 0)
set default=0 

set root=(hd0,1)
insmod gfxmenu
insmod gfxterm
insmod jpeg
insmod font
set font=/boot/grub/fonts/unicode.pf2
set background_image=/boot/grub/backgrounds/imagejpeg.jpg
set gfxmode=1024x768x32
set color_normal=black/black
set colot_highlight=magenta/black


menuentry "Windows" {
	set root=(hd0,2)
	chainloader (hd0,2)+1
}

menuentry "Lubuntu" {
	set root=(hd0,6)
	linux /boot/vmlinuz root=/dev/sda6 ro
	initrd /boot/initrd.img
}

```

I have copied the fonts from a live Ubuntu CD to the 'fonts' folder I created at /boot/grub/fonts in the GRUB partition. My background image is a 1024x768 pixels jpeg image located at 'backgrounds' folder I created at /boot/grub/backgrounds in the GRUB partition. 

Can anyone provide me some guidelines or direct me to a discussion which deals with my issue?

Thanks.

---

### Post by Doug S on 2012-04-09
Maybe this will help you: [https://help.ubuntu.com/community/Grub2#GRUB_2_Splash_Images](https://help.ubuntu.com/community/Grub2#GRUB_2_Splash_Images)

---

### Post by oldfred on 2012-04-09
If you want the full theming, but I think that includes some script changes.

Post Your Grub 2 Themes -  drs305
[http://ubuntuforums.org/showthread.php?t=1823915](http://ubuntuforums.org/showthread.php?t=1823915)
A Beginner's Guide to Theming GRUB2 - towheedm
[http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)

---

