---
title: "USB card reader issues."
date: 2011-10-20
forum: New to Ubuntu
---

### Post by oldsoundguy on 2011-10-20
Note to Mods .. move this as you see fit!

Here is the problem in a nutshell.

Have a USB card reader that is installed in the box.

lsusb:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Use CF cards in my Nikon.
Put the card in the reader and get NOTHING.

Is it because of the format of the card or am I missing something.

(Automount is set to TRUE.)

Any help would be appreciated .. and once it works, how to open GIMP upon insertion?

THANKS!!

---

### Post by oldsoundguy on 2011-10-21
As a way to bump would add that this type of unreliability of plug in devices is the primary reason I keep a Windows machine with Photo Shop and plug ins plus other photographic software to be able to do my (crude) amateur photography.  Would LOVE to dump the Windows box as the monthly maintenance as a ROYAL PITA .. but, as far as Ubuntu Linux is concerned .. photographers are still shut out if they do anything more than just take the occasional snapshots!

(BTW .. FORGET trying to upload a shot from a phone! unable to do so with my phone unless I eMail it!)

Using a Hyperthreaded 3.06 w/2mb ram
Ubuntu 10.04LTS
dual hard drives 40gb & 250gb
Gerneric USB internal card reader .. same identical unit as the one I have on the Windows box.

Would love to give a serious shot at photography on Linux as GIMP is nice and there are some newer programs that look promising .. but have to have the hardware working PROPERLY before could even consider the move.  (the PHYSICAL Wacom air brush is still a problem, also.  The mouse and pen DO work, but not as well as in Windows.)

---

### Post by Shazaam on 2011-10-21
Not an answer but when I put a flash card in a usb reader and plug it into my pc (while pc is running) it mounts fine. Close nautilus, remove flash card from usb reader (with reader still plugged in). Put card back in reader and no auto mount. I would bet if you put the card in your internal reader before booting your pc it will mount fine but you will have the same problem as I.
Xubuntu has an app called thunar-volman. I will reboot to xubuntu and post back results.

---

### Post by Shazaam on 2011-10-21
What I found...
Ubuntu (nautilus) has "Eject Volume" and "Safely Remove Volume"
Xubuntu (thunar) has only "Eject Volume"

Ubuntu- If you safely remove, no way to automount. Must use the cli for that. If you eject, automount works.
Xubuntu- as I said before it only has eject. This allows for automount.

Now, I don't know if just ejecting it will be a problem later on or not. Windows will probably claim that the flash card was improperly unmounted and give you fits.

---

### Post by oldsoundguy on 2011-10-21
Thanks for the effort!!  NOPE re-booted several times, with the card in and the card out.  The drive(s) (multi-card reader) show up in lsusb either way .. but no content!  This is not a deal breaker, but would be nice to be able to get it to work.

Will try doing the camera direct sometime this evening when I get the time and post the results of that venture then.

---

### Post by Big Lizard on 2011-10-21
@oldsoundguy

Do you have another card reader, like a portable/external card reader? Try that and see if you get the same results. My point is, trying a different reader would help isolate whether the problem is with the cards or the original reader you use.

---

