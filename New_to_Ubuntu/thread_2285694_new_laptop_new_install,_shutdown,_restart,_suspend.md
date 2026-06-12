---
title: "new laptop new install, shutdown, restart, suspend problem"
date: 2015-07-07
forum: New to Ubuntu
---

### Post by crip720 on 2015-07-07
I have a new Acer E15 ,ES-511 laptop with Intel Pentium N3530 cpu and HD Graphics.  Has 8GB mem.   The laptop came with Win 8.1 and I installed Win 10 beside 8.1.  I have also installed Ubuntu 15.04 64bt and the install and booting/working of 15.04 is good.  My problem is with Shutdown, restart and/or suspend.  The computer will freeze/stop working with only the fan going into overdrive/superspeed for a second at a time.  Hard power off seems to be only solution.  etc/grub/default was listed with "quiet splash"  Laptop is using UEFI and secure boot off.   journalctl does not have any warnings or errors [lines 1-23]  I have uncommented the quiet splash line for next shutdown.  System Log seems okay, but it does mention something about cleaning up some 'dirty bits', probably from hard shutdown.  I do not  want to try any of the solutions I have found so far, but the ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=bios"
``` seems like a good contender,but do not know if this will work on UEFI.  Any more info you need or any suggestions you 
can give me. Thank you, Colin.   pps also have this problem when trying to load a live dvd or live flash drive, will freeze on loading screen and fan will run very fast for a second at a time.

---

### Post by crip720 on 2015-07-09
Some more info, I have Ubuntu 14.04 on external hard drive, this OS was installed with another laptop that had old BIOS.  I plugged in the USB cable for the hard drive and ran update-grub.  14.04 loaded up good and also no problem with shutdown.  Only have shutdown freeze with Ubuntu 15.04.  Having to do a hard shutdown with the main power button all the time cannot be good for the OS or trying to install updates that require a restart.  Any help or ideas you can give to fix this would be helpful.  If you need more info, let me know.  Thank you, Colin.

---

### Post by crip720 on 2015-07-10
I have the problem half solved, I changed grub cmdline linux=quiet splash, to reboot=acpi.  15.04 will turn off now with a minor hang.  Unfortunately  it will reboot instead of shutting down, using the GUI shutdown button.  reboot=efi causes 15.04 to hang during boot up.  Does anyone know what I can use so that 15.04 will work correctly for shut down and/or reboot?  Thank you, Colin

---

### Post by oldfred on 2015-07-10
I have these in my notes:
 Acer Aspire ES1-512: ubuntu 14LTS USB install over Windows 8.1  Set shim as secure in UEFI
black list some drivers for shutdown issues - post #9 link to Mint
[http://ubuntuforums.org/showthread.php?t=2256083](http://ubuntuforums.org/showthread.php?t=2256083)
Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

Never force shutdown, remember the elephants.
      
 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by crip720 on 2015-07-11
To OLDFRED thanks for your links, I think I have solved this problem by using your link that said to blacklist two drivers.  I blacklisted them with terminal and had to do one hard shut down and the next shut down worked like it should.  I think my problem was not in the OS shutdown, but in the final power-off.  Looking thru the shut down info[?] page it did go all the way to "shutdown target reached"   I guest the OS shut down, but would not power-off the laptop.  R.E.I.S.U.B.  command would not work.  I changed the cmd line grub to " ", will now change it back to "quiet splash"  I did check on the specs of the laptop they were using to make sure it was using Intel as is mine.  Thank you, problem solved.  Colin.

---

### Post by oldfred on 2015-07-11
Glad that worked. :)

---

### Post by Damian_Kober on 2016-03-13
Hi, I was having this issue (shutdown did not turn the notebook off) with my ACER E15

I read that the problem was related to usb ([http://ubuntuforums.org/showthread.php?t=2067259&p=12389814#post12389814](http://ubuntuforums.org/showthread.php?t=2067259&p=12389814#post12389814))

I solved it by disabling xHCI support (usb3 related support) on the BIOS and now it shuts down fine

---

### Post by RobGoss on 2016-03-13
> **Damian_Kober said:**
> Hi, I was having this issue (shutdown did not turn the notebook off) with my ACER E15

I read that the problem was related to usb ([http://ubuntuforums.org/showthread.php?t=2067259&p=12389814#post12389814](http://ubuntuforums.org/showthread.php?t=2067259&p=12389814#post12389814))

I solved it by disabling xHCI support (usb3 related support) on the BIOS and now it shuts down fine


Thanks for sharing your findings with the forums

---

### Post by david504 on 2016-03-19
I had something like that on an acer e15 start es1-512-c96s

I just disabled the xCHI usb 3.0 and it restarts, shutsdonwn, and lid close function works normal. there is  something about that 3.0 controller ic they are using.

---

