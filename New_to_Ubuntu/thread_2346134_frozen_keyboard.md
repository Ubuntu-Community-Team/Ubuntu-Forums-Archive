---
title: "frozen keyboard"
date: 2016-12-11
forum: New to Ubuntu
---

### Post by mchurcher1 on 2016-12-11
I used a 3.0 USB stick on my new computer with Ubuntu 16.01 installed.  I copied some pics to the USB stick.  The keypad became frozen when I couldn't rename a folder.  Then when I closed down and ejected the USB, I found I couldn't use the keypad at all.  I am a rookie with Linux but it is getting very frustrating.  Help with the keyboard will be appreciated.

---

### Post by DuckHook on 2016-12-11
Since the keyboard also uses the USB bus, one scenario that would explain your symptoms is a HW failure of the USB subsystem. This failure likely coincidentally occurred during your file transfer and was not caused by it. However, you need to provide more information.

[LIST=1]
[*]Full description of your computer specs. We do not even know if it is a laptop or desktop.
[*]Do you physically plug your keyboard in using a USB port?
[*]Does your mouse/trackpad (presumably also a USB) still work?
[*]***Does your keyboard allow you to access the BIOS during POST?*** This is very important. If the keyboard is unresponsive at that point, then it has nothing to do with your OS and is due to hardware.
[*]Does keyboard work with a LiveUSB?
[*]If you dual boot, does keyboard work with another OS?
[/LIST]
Please answer *all* questions. More complete info is the only way to get worthwhile help.

If your machine has a PS/2 port, you can try a PS/2 keyboard. Also try switching USB ports. Sometimes, the problem is in only one set of ports and others will still work. This is especially true if you switch from USB3 to USB2. If none of the above works, and symptoms are as per #4 above, then you must either have the machine repaired, replace the MOBO or install another USB card. However, if the keyboard is actually working, but only until GRUB loads, then the problem is software.

---

### Post by mchurcher1 on 2016-12-13
Thanks Duckhook,  I have more info on my problem frozen keyboard.  I have a laptop Sys 76 Oryx Pro      

[LIST]
[*]8 GB GTX 1070 with 2048 CUDA Cores
[*]3.6 GHz i7-6820HK (2.7 up to 3.6 – 8 MB Cache – 4 Cores – 8 Threads)
[*]32 GB Dual-channel DDR4 at 2400 MHz (2× 16 GB)
[*]512 GB NVMe PCle M.2 SSD
[/LIST]
I can accept the bios on startup.  I started up Ubuntu 16.10 on a live usb but couldn’t move the cursor with the mouse (frozen) or trackpad.  I right clicked on the trackpad to bring up the terminal.  I could type in the terminal but then it froze.  I brought up a 2nd terminal and could type then exited to go back to the first terminal window where I could type again.
Thanks,

---

### Post by DuckHook on 2016-12-15
What version of Ubuntu did the laptop come with? Was it 16.04? If so, did you upgrade to 16.10?

Irrespective, I suggest you try running it with a LiveUSB of 16.04.

16.04 is more stable than 16.10, is also a LTS whereas 16.10 is only supported for 7 more months, and most of the bugs have been worked out of 16.04 whereas 16.10 (meant more for experimenters and power-users) will unlikely have bug fixes, especially since 17.04 is due out in 4 months.

EDIT

As a further thought, try connecting an external keyboard & mouse. If it works at least you have functionality.

---

