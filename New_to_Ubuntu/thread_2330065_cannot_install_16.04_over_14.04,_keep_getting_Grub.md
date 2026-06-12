---
title: "cannot install 16.04 over 14.04, keep getting Grub menu"
date: 2016-07-07
forum: New to Ubuntu
---

### Post by kindafunnylookin on 2016-07-07
I had Ubuntu 14.04 installed on new computer, worked fine. I put a 16.04 image on disc then started computer. It did not see the image and gave me a grub menu. Now i am stuck with that grub menu every time I start, cannot get to 14.04. It could be that the computer is not looking to boot from disc on start up. is there a command I can use - to use the grub menu to see the CD on startup?

---

### Post by QDR06VV9 on 2016-07-07
Without knowing what Make and Model your computer is... have you tried looking in your Bios to see if you can Boot to a DVD/CD?
And some use the F12 Key to select a boot device while the computer is freshly booting up.

---

### Post by grahammechanical on 2016-07-07
It is normal to see the Grub boot menu if Ubuntu & another operating systems are installed to the hard drive. To boot or load from a DVD or USB memory stick we need to enter the BOIS/UEFI boot system utility and direct the motherboard to load from the DVD drive or USB port instead of the hard drive. Have you done that?

If you have done that and are getting this problem then it could be that the Ubuntu ISO image has not been burnt to the DVD but has been copied on to the DVD instead.

Regards.

---

### Post by buzzingrobot on 2016-07-07
Grub menus typically time out after a period of seconds and then boot the highlighted kernel entry. If you are seeing a grub menu when you boot without the 16.04 DVD in the drive, perhaps it isn't timing out. Try pressing Return.

---

### Post by kindafunnylookin on 2016-07-07
The computer is a Toshiba Tecra. I cannot get to the Bios or anywhere at all. When I boot up it asks for my password, I put that in and it brings me to the GNU GRUB page with the three options: Ubuntu
                    *Advanced options for Ubuntu
                    System setup
the Ubuntu option brings me to a blank page and makes the light on my Caps Lock key flash---The Advanced option does the same---and the System option brings me back to the GNU GRUB page.
I tried the F12 key after the passwrd but no luck.

---

### Post by QDR06VV9 on 2016-07-07
This from Toshiba
> On some models this prompt reads **Press F12 for boot menu**. On others, it may say **Press C to boot from CD-ROM**. On  still others, there may be a row of colored icons representing  the various boot devices (HDD, FDD, CD, LAN, PCMCIA, etc.) Press F12  while these icons are displayed, and then use the arrow keys to move the  cursor from one to another. As new models are released, the wording of  these prompts may change.

On models that offer a text boot device  menu, simply press the key corresponding to the desired boot device  from the list of available devices.The selection of a boot device  from any of these boot device menus affects only the current startup  operation; the next time the computer is started it will follow the boot  priority setting established in BIOS Setup (see the BIOS Setup method,  above).
Source:[http://support.toshiba.com/support/viewContentDetail?soid=403623](http://support.toshiba.com/support/viewContentDetail?soid=403623)

---

### Post by kindafunnylookin on 2016-07-07
I have not gone to the Bios, there is no way to get to it, and it will not see my 14.04 disc either and I have been successful with that before so I don't feel that it is a disk problem.

---

### Post by kindafunnylookin on 2016-07-07
Thank you for that but it did not work either

---

### Post by QDR06VV9 on 2016-07-07
That was not a explanation on how to get to the bios...but selecting your DVD/CD Drive to boot from.

---

### Post by QDR06VV9 on 2016-07-07
> **kindafunnylookin said:**
> Thank you for that but it did not work either

Then if that is the case try another Download or try again Burning the iso to another Disk.
I'm afraid that is all i can help you with.

---

### Post by oldfred on 2016-07-09
What model Techra?

Is this a new UEFI based system?

You may have fast boot in UEFI on. That is different than fast start in Windows.
Fast boot skips all hardware checks and assumes you want to boot with everything exactly as it was with last boot. But it is so fast that you have no time to press f2 or f12 or whatever keys to get into UEFI.

You may be able to get f keys to work, by a cold boot, not warm reboot. You have to unplug system, remove battery if laptop and hold power switch to drain all power for about 10 sec. Then on cold boot it should go thru the full check of system which still will be fast, but then gives you a few seconds to press f key.

If not, some systems have a reset tiny hole in bottom of system. 
A few require disassembly of system and jumpering pins on motherboard or removing the small coin battery on motherboard. That also resets UEFI to default settings and you have to go back into UEFI and redo all the UEFI settings changes.

---

### Post by mook765 on 2016-07-25
When you can not go to your 14.04 installed on the hdd if you restart your computer with an inserted disc, it would mean, that your bios is allready configured to boot from cd/dvd first ( only with a bootable disc inserted ).
What happens if you remove the disc and restart?

---

