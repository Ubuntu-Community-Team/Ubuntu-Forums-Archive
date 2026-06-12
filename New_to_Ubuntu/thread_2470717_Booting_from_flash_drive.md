---
title: "Booting from flash drive"
date: 2022-01-08
forum: New to Ubuntu
---

### Post by beckster on 2022-01-08
I've tried hitting Esc repeatedly and nothing comes up.

---

### Post by TheFu on 2022-01-08
What do you expect hitting a key to do?

If you don't provide detailed descriptions, don't expect good answers. We didn't see what you did. When don't know anything about the flash drive. 
Is it plugged in?, 
Does it have some OS on it?  
When did you hit the key?
We don't know, since you didn't tell us.

I'm hitting >esc< now and nothing is happening here either. See how useful that is? LOL.

---

### Post by Autodave on 2022-01-08
Make and model of your PC will help.

---

### Post by oldfred on 2022-01-08
Most systems use f12 to get into UEFI/BIOS boot menu to boot USB flash drives.
The Escape key is for getting grub menu when only one system is installed & grub defaults to booting that system without showing menu.

Check manual for correct key for UEFI boot menu. Many brands use different keys.

---

### Post by sizarpl on 2022-01-09
you may also put F2 or DEL to get into bios

---

### Post by TheFu on 2022-01-09
> **sizarpl said:**
> you may also put F2 or DEL to get into bios

+1 That's what my Dell and Asus motherboard/systems use.

But I still don't know when or why the OP is pressing <esc>.

---

### Post by beckster on 2022-01-09
Ok I guess I have to hold down Esc or F9.

---

### Post by beckster on 2022-01-09
Neither Esc or F9 work and I'm installing from Windows 10. Do I need to buy a new computer?

---

### Post by poorguy on 2022-01-09
Have a look it should tell you what F-Key to hold down upon restarting your computer to display a boot menu.

[https://www.boot-disk.com/quest_bootmenu.htm](https://www.boot-disk.com/quest_bootmenu.htm)

Insert usb drive in a usb slot and restart your computer while holding down whatever F-Key from link above displays boot menu then just follow the prompts.

---

### Post by ajgreeny on 2022-01-10
Which BIOS/UEFI does your machine use?

My laptop uses American Megatrend (I think) and I have to hold F8 immediately after pressing the power button to show the device menu from which I can choose from the installed OSs or a USB if one is inserted.
Different BIOS will need a different key press but your motherboard manual  should tell you which key is needed..

---

### Post by yancek on 2022-01-10
Posting information as requested above (Make, model, mfr) of the computer would be a good start, i.e. HP, Dell, Toshiba,etc.  If it's not any major manufacturer, then you need to post the motherboard information.  You indicate you are trying to boot from a usb, what are you trying to boot and fo what purpose?  Are you trying to boot some Ubuntu Linux to install it?  You indicate you are trying to install from windows 10?   Are you trying to boot a Linux iso on a USB.  You need to post more specific information as what you have posted so far is conflicting.

Most computers will show a message on screen for several seconds immediately upon booting telling you which key to use to access temporary boot options or BIOS firmware.  If you don't see that on boot, posting the manufacturer may help as someone here may be able to tell you which key to use.  Or you could do an online search for the computer model and manufacturer..

---

### Post by ajgreeny on 2022-01-11
> **beckster said:**
> Neither Esc or F9 work and I'm installing from Windows 10. Do I need to buy a new computer?
**You do not install from Windows**; you need to shutdown the computer totally then reboot and press the key you should by now have managed to find which will take you to the BIOS/UEFI setup or to a boot-device menu.

---

### Post by T6&amp;sfpER35% on 2022-01-11
before trying to boot from flashdrive , first search how to get into your BIOS depending what PC you have .
then before inserting the flashdrive ,get into BIOS and change boot sequence so flash/usb boot 1st.
then insert flash and reboot

---

