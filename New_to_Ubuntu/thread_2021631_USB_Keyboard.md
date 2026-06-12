---
title: "USB Keyboard"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by Viral Luna on 2012-07-09
Hey guys,

you have most probably already met with users complaining about this problem thousands times as I have myself found plethora of posts on internet, however to no avail. I am a newborn to the world of Linux.

I am running dual-boot Ubuntu 12.04 LST with Windows 7. I own Trust GXT 18 USB keyboard. It works absolutely fine in Windows but it does not work in Ubuntu. Only the backspace and the key between CTRL and WINDOWS-KEY work. 

Also, the keyboard worked just fine in the menu you get when you boot Ubuntu from LiveCD/USB. After the selection is made it does not work anymore.
The PS2 keyboard works just fine. Interestingly, if I press NumLock on the PS2 keyboard the NumLock LED switch on/off on both USB and PS2 keyboards (does not work for CapsLock and ScrollLock).

I have already tried playing with the Legacy USB option in the BIOS.
Other USB devices such as mouse work perfectly.
If you need more info regarding this problem just ask.

Thanks in advance,
Viral Luna

---

### Post by DoctorVarney on 2012-07-09
Have you tried configuring your keyboard settings?  You'll find them in the dash.  Just type in "Keyboard" and see if the right layout options are set.

I'm also new to Ubuntu, so forgive me if this isn't the best answer.

---

### Post by Viral Luna on 2012-07-09
Hi, thanks for the reply. I have looked into the Keyboard options but I have found nothing relevant to my problem. Or I have missed it. Thanks anyway.

---

### Post by Viral Luna on 2012-07-10
I do not know whether this information is helpful but the keyboard stops responding during the quite longer black screen just before the Ubuntu desktop shows up and after the text about kernel.

---

### Post by DoctorVarney on 2012-07-10
Okay, you've verified the keyboard works on Windows but it still might be worth trying an alternative, if you have one or can borrow one, just as an extra troubleshooting measure. Just to be sure, Is this particular keyboard you're using right now, PS2 or USB ?  If the latter,  you're not using a USB-PS2 adaptor by any chance?

---

### Post by Viral Luna on 2012-07-10
Hi DoctorVarney,

thanks for the reply.

I have found another USB keyboard that works just fine right now. And the keyboard I wrote  the first three messages was an old PS2 keyboard. I am writing this one with the new USB keyboard.

So far it seems that the USB keyboard that does not work is malfunctioning. Quite weird, it is just few days old.

Also while I was waiting for a response to my problem I have found an interesting topic talking about my model of keyboard:[INDENT]> i.e. the device presents 32k of cosumer usages, which is beyond the limit on the number of usages the current parser in the kernel supports ( 12288 ). Bumping up the HID_MAX_USAGES constant would work around the problem, but I don't believe the keyboard is actually generating such a wide range of consume page usages.

The keyboard is pretty standard, with a boot interface and a report interface. The report interface has two problems:  - as you noted, the device presents 2^15 consumer usages, much larger than the HID_MAX_USAGES=12288 limit - no LED usage block is presented, preventing any use of the num/caps/scroll LEDs in report mode 

[/INDENT]Could the HID, whatever it is, be the problem why the one particular keyboard does not work? And if so, is there any workaround?

Thanks in advance.

---

### Post by Viral Luna on 2012-07-10
I found a **hid.h** inside the **/usr/src/linux-headers-3.2.0-23/include/linux/hid.h** and on a 346th line I found:
```
#define HID_MAX_USAGES            12288
```I have rewritten the value to 32768 and I would like to know what do I need to do in order for this change to take effect.

Thanks in advance,
Viral Luna

---

### Post by blumenwiese on 2012-07-17
Same problem here. Keyboard works perfectly fine with Windows, Grub2 and the first screen when booting Ubuntu Alternate CD but not when I go on. gPartEd Live CD had the same problem. Old PS2 Keyboard works.

For me it seems like you have to compile a new Kernel for changes in hid.h to take effect…

---

### Post by Sirron on 2012-07-22
I have this keyboard. I got it working with the patch [_here_]("http://www.spinics.net/lists/linux-usb/msg62270.html"). But I had to patch and compile the kernel from source. Obviously that patch needs to find its way *into* the kernel.

Does anyone know the correct procedure from here?

---

