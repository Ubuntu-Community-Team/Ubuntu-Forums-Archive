---
title: "Wanting to test drive 12.04 first but screen goes blank?"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by Bushcraft Bill on 2013-11-04
I have an HP envy-17-jo83ca  I have turned off secure boot and intel smart response technology could it be that its just the nvidea card that it is not happy with?
I get to the install screen and then when I try I try to test drive it and nothing but black screen after that I can tell its trying to load from the DVD  I left it for an hour and nothing just a big black screen what can I do to get it to work I want to make sure it works on a test drive before I try an install with windows8...
yes the dvd works on the wifes so its not the DVD....Also trid this from a usb memory stick same result after the test drive or install screen all I get is black screen....

---

### Post by Bashing-om on 2013-11-04
Bushcraft Bill; Hi !

Try the boot parameter "nomodeset".

Boot the liveDVD;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> f6 key (other options) -> arrow down to the preset option(s), choose "nomodset"; space or enter to accept and then the escape key to exit;
Enter key to continue the boot process to the GUI desk top;
If you get to the desktop and the graphics are degraded;
Try and load the recommended driver.
Left side of the screen is the launcher -> System Settings -> Additional drivers -> install the recommended driver.

[INDENT][INDENT]Hey it could happen
[/INDENT][/INDENT]

---

### Post by Bushcraft Bill on 2013-11-04
I never get to the purple screen! 
I only get to the first option screen to install or test drive <-tried F6 at this screen nothing happens

I think it its not setting up the proper driver for what ever nvidia card is in the puter... but then I would not get the install/test drive screen right?

I just tried 13.10 also and no luck!

Now I have not tried the OEM inatall for manufacturers I am assuming that is something I wont have access to....

---

### Post by Bashing-om on 2013-11-04
Bushcraft Bill; Hey:

Try it like this:
boot the liveUSB, and as soon as the bios screen clears, depress and hold the left shift key -> language screen, escape key to accept the default ->grub boot options screen -> then the f6 key. Remainder of instruction from last should apply.

[INDENT][INDENT]try and try again
[/INDENT][/INDENT]

---

### Post by Bushcraft Bill on 2013-11-04
OK I saw something come up right before the install/try ubuntu screen this is what came up and I think this may be the problem

could not open "\EFI\BOOT\fallback.efi": 14
error: variable 'root' isn't set

I used my camera to get it LOL...

---

### Post by Bashing-om on 2013-11-04
Bushcraft Bill; Shucks !

That must be UEFI related. Version 12.04 requires that it be disabled as well as disabling secure boot.(Version 12.10 and above can deal with UEFI)

All I can think of at the moment.

[INDENT][INDENT]put, it can be done
[/INDENT][/INDENT]

---

### Post by Bushcraft Bill on 2013-11-04
I tried it with 13.10 and same result though!

I can not turn off  UEFI on my puter it does not have legacy boot option..

---

### Post by Bushcraft Bill on 2013-11-05
OK I found online what seems to be the problem figured out that a black screen was actually just the Ubuntu installation screen on a really low brightness setting how do I fix that so I can see ubuntu?

---

### Post by oldfred on 2013-11-05
Instead of nomodeset, some laptops using the Intel video chip needed this. And you may have to use fn key for brightness to make it brighter also.

 Some other Intel boot options
acpi_osi=Linux  acpi_backlight=vendor

Very new systems work better with the very new version of Ubuntu as both kernels and video drivers have many updates for the new hardware.

Other versions with Intel:

 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
 i915.i915_enable_rc6=1

If nVidia or dual video and booting with nVidia you do need nomodeset.
      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If UEFI system you will be able to boot Ubuntu in BIOS/CSM or UEFI modes. This shows both screens.
      
 Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by ajay_varma on 2014-04-02
Hello Bill....I am the having the same problem when booting ubuntu 13.10 from usb.....I am using a lenovo Z570 with windows 7 and Nvidia GPU......I am a new ubuntu user........Just after selecting boot device.....I get this message and disappears in a blink of an eye.......

could not open "\EFI\BOOT\fallback.efi":14

after that just a blank screen appears..........Please help me solve this issue........

---

### Post by oldfred on 2014-04-02
Others with same issue.
 Could not open "\EFI\BOOT\fallback.efi"
[https://bugs.launchpad.net/ubuntu/+bug/1241824](https://bugs.launchpad.net/ubuntu/+bug/1241824)

Some have posted what worked as a temporary fix.

---

