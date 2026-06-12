---
title: "Four problems."
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Jookia on 2008-04-26
1. I accidently removed the system tray from my panel.
2. My mouse is acting up, sometimes it takes me 2-5 tries to make the right click menu to stay open for over 5 milliseconds.
3. My keyboard is UK-style. It displays " when I press the @ key (The @ is copied from google).
4. My sound is choppy.

Also, as a really small problem, my bootloader resolution is higher then my screen can handle, and a low gamma. Any fixes?

---

### Post by dangerpl on 2008-04-26
I can help you with the first problem. Right click on your panel and choose Add to Panel... From there you can select things you want on your panel.

---

### Post by dangerpl on 2008-04-26
Also, if you go to System-->Administration--> Language Support. You can choose the language you need.

---

### Post by warbread on 2008-04-26
> **Jookia said:**
> 1. I accidently removed the system tray from my panel.


Right click on the panel you want the system tray on and click "add to panel".  System tray is on there as "Notification Area" at the bottom.

> 2. My mouse is acting up, sometimes it takes me 2-5 tries to make the right click menu to stay open for over 5 milliseconds.

Sounds like a hardware problem.


> 3. My keyboard is UK-style. It displays " when I press the @ key (The @ is copied from google).

While you're in the "Add to panel" dialogue, add "Keyboard indicator".  Right click on that and go to 'Preferences'.  Layouts is the second tab.  Add U.S. English and remove U.K. English, in that order.
> 
4. My sound is choppy.

What's your sound card?

---

### Post by Dr.Gringo on 2008-04-26
Please post the output of terminal:

```
lspci
```

---

### Post by Jookia on 2008-04-26
Warbread:

Thanks for the keyboard fix..

Also, the mouse.

TIS NOT A HARDWARE PROBLEM. I'll record a video of it.

Also, Gringo..

```
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation GeForce 7100 GS (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
05:03.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
```

---

### Post by warbread on 2008-04-26
> **Jookia said:**
> Warbread:

TIS NOT A HARDWARE PROBLEM.



How have you ruled it out?

---

### Post by Jookia on 2008-04-26
> **warbread said:**
> How have you ruled it out?

It worked in 7.10.

---

### Post by Riffer on 2008-04-26
> **Jookia said:**
> 1. I accidently removed the system tray from my panel.
2. My mouse is acting up, sometimes it takes me 2-5 tries to make the right click menu to stay open for over 5 milliseconds.
3. My keyboard is UK-style. It displays " when I press the @ key (The @ is copied from google).
4. My sound is choppy.

Also, as a really small problem, my bootloader resolution is higher then my screen can handle, and a low gamma. Any fixes?

1: We have a "SystemTray"?  Right click on your panel and use the "Add to panel" function.  In there you can add applets and icons for apps.

2:  Not sure what to do but it could be and xserver problem, you may want to reset that, (command line stuff and I'm not sure of the syntax).  You could try the "mouse' configuration found in the drop down menu "System>Preference".

3:  Again in the drop down menu "System>Preference" there is one for keyboard.  You could try a different layout.

4:  Without your hardware specs its hard to give advice.  Find out what sound card you have and it will be a lot easier to help.  

Your last one I can't help you with.

Also the search function for this forum is great, it was a BIG help for me when I started, (still is :) ).

Good Luck

:) darn people beat me too it

---

### Post by warbread on 2008-04-26
> **Jookia said:**
> It worked in 7.10.

Alright, I'll buy that.  

For now, this may help with your sound card:
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by Jookia on 2008-04-26
I fixed my soundcard. Now it's just the mouse. I have to hold the right mouse button in for it to open the menu.

---

### Post by warbread on 2008-04-26
Are you using Compiz effects?  It could be an animation issue.  Try disabling the animations altogether and see if that makes a difference.

---

### Post by amohanty on 2008-04-26
> **Jookia said:**
> 1. I accidently removed the system tray from my panel.
2. My mouse is acting up, sometimes it takes me 2-5 tries to make the right click menu to stay open for over 5 milliseconds.
3. My keyboard is UK-style. It displays " when I press the @ key (The @ is copied from google).
4. My sound is choppy.

Also, as a really small problem, my bootloader resolution is higher then my screen can handle, and a low gamma. Any fixes?

First find out what your framebuffer supports:
sudo apt-get install hwinfo
sudo hwinfo -framebuffer

Then check to see if /etc/usplash has xres and yres values that are not in the output of the previous command, if so change to somehing specified there.

Then in you /boot/grub/menu.list in line 89 if there is something like vga=.... then you probably customized the splash, change the value after vga= to the hex value corresponding to the value you put in /etc/usplash. Make the same changes in the root entries later on in the file.

Finally update initramfs using:
sudo update-initramfs -uv

HTH
AM

PS: also that is how you can make your usplash look prettier :)

PPS: shouls have mentioned I was referring to the last problem

---

### Post by Jookia on 2008-04-26
I'm *not* using compiz effects.

I *can't* apt-get, amo, since the servers are so boggy and I can't find another source.

---

### Post by amohanty on 2008-04-26
backup your /etc/apt/sources.lst

edit it
and replace xx.archive.ubuntu.com 
with a mirror from here:
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

worked like a charm today morning (pacific time) while downloading the ISO.

HTH
AM

---

### Post by Jookia on 2008-04-26
jookia@ubuntu-8:~$ sudo hwinfo -framebuffer
oops: don't know what to do with "framebuffer"

---

### Post by amohanty on 2008-04-26
sudo hwinfo --framebuffer

sorry missed the extra minus sign

am

---

### Post by Jookia on 2008-04-26
It's all fine, except for some reason my screen won't go over 1024x768 @ 60hz

I presume the bootloader is 1024x768 @ 75hz

---

### Post by amohanty on 2008-04-26
you can always go lower by simply using the instructions above, or removing the word splash _completely_ from the commented part too (grub-install uses the commented part to update menu.lst) to get rid of the splash screen and get nice old text back.

sm

---

### Post by Jookia on 2008-04-26
How would I remove it? It'd like to see the text. I'm not exactly sure how.

---

### Post by amohanty on 2008-04-26
It will occur in the file: /boot/grub/menu.lst

89:# defoptions=splash vga=795
132:kernel		/vmlinuz-2.6.24-16-generic root=UUID=562d2f02-d597-49e7-9cde-7f1b4aa49b7e ro splash vga=795

at line 89 and somewhere down below too. Simply 

sudo gedit /boot/grub/menu.lst and find and replace the word "splash" with nothing.

hth
AM

---

### Post by PippoSniffo on 2008-06-16
Hi, can someone tell me how can I set a widescreen resolution in menu.lst ?

I've used [i]hwinfo[/it] but it shows only 4:3 resolutions while I have a 14.1" widescreen display capable of 1280*800

Thanks

P.S.: i'm using xubuntu

---

