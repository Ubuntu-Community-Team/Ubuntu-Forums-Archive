---
title: "new install issue"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by The Gaz on 2011-10-16
Hi All, 
Just installing ubuntu for the first time on a pc with no OS but the installation of V11.4 got interupted.
 
I now have a pc that will not boot up with or without the ubuntu disc I created. All I get is a black screen and a few noisy keys !
 
Any ideas how to get into the pc os or get ubuntu to load
 
thanks

---

### Post by Lisiano on 2011-10-16
The PC might not be booting from the CD because it's BIOS is dictating it to boot this way: 1st HDD, 2nd CD, 3rd USB, 4th LAN.
You need to set it so that HDD is tried after CD or USB (Depending on what you wish to install with)
Entering a BIOS depends on the machine in question, most systems I encounter put the key to enter the BIOS on Del, F2, F1 and F10. For the Boot Order I usually encounter it to be on F12. Both keys are usually displayed during the POST/OEM Logo, to stop the PC from booting past the POST/OEM Logo, press the Pause key. To resume, press any key except the Pause key.

---

### Post by d4m1r on 2011-10-16
If your system got disrupted while the OS was installed, chances are you'll have to reinstall everything. Pop the liveCD back in, reformat the hard drive, and reinstall.

---

