---
title: "SD card containing root partition not recognised on boot by internal card-reader"
date: 2014-11-20
forum: New to Ubuntu
---

### Post by Arronical on 2014-11-20
I've put the root of a Trusty install on a flash SD card,  which I will eventually configure as read only, using an overlayFS to  make some necessary parts writable, such as /etc. I know it might sound a  bit mad to do that, but it's not where I'm having problems.
  The Ubuntu installer doesn't recognise the multi-card reader on the  front of the machine, so I use a usb card reader to side-step this  problem. Then, when the installation is complete, pop the SD card into  the multi-card reader and away I go.
  This has worked perfectly on 2 Foxconn NanoPCs with 2012 firmware,  though we've recently purchased newer models, with newer firmware, and  this is where the problem has appeared.
  When I switch from the USB card reader to the internal one, the  system loses track of the SD card whilst running local-top scripts, and  drops to a shell in initramfs, giving the message;
  Gave up waiting for root device.  Common Problems;
  -Boot args (cat /proc/cmdline)
    -Check rootdelay= (did the system wait long enough?)
    -Check root= (did the system wait for the right device?)
  -Missing modules (cat /proc/modules; ls /dev)
ALERT!   /dev/disk/by-uuid/XXXXXXXXXXXXXX does not exist. Dropping to a shell!
  It seems to me that the hardware isn't passing the UUID to the system at the point that the root filesystem is being mounted.

  Is there any way to make the initramfs point to the internal card reader, or search for the SD card by anything other than UUID? 
  Alternatively, am I barking up the wrong tree, is there something else I should try?
It's just occurred to me that a major difference between the working and non working systems is that, when choosing BIOS boot options, if the SD card is in the internal reader the working system shows the name of the SD card (Generic multi-card 1.00) but in the non working systems it always shows as USB card reader 2.0. Does this suggest that it's a firmware issue?

---

