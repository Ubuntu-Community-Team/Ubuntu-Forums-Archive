---
title: "[SOLVED] /casper/initrd.gz"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by GrnFrag on 2008-07-22
HELP!!  I am trying to install off the LiveCD.   After the "loading Linux kernel" gets to 100%, i get this message, /casper/initrd.gz.   if you click ok, it takes you back to the main installer screen, but nothing works.  the computer is not hung, as ctr alt del will reboot.  

ok, i tried to install with the Alternate CD but get a similar message /install/initrd.gz



System specs
1.9g Celeron
512 mg Ram
20g HDD
Plextor burner
Geforce4 video
Linksys nic

---

### Post by dracayr on 2008-07-22
in the menu there should be an option at the bottom with "other options" (or similar). The option is started with a function key (I think F10, but I may be mistaken there). So press that function key and a text box should come up. In that text box, delete the 'splash' part and the 'quiet', if it exists. then try again. The error will occur again, but this time you should get a more detailed error message

dracayr

---

### Post by GrnFrag on 2008-07-22
ok, i hit F6 for install options, removed the splash and quiet options from the end of the string.

And got the same message   :(

---

### Post by GrnFrag on 2008-07-22
i've tried this 3 times, removing the quiet and the splash and the 2 dashes at the end of the string for install Ubuntu.
I've used both CD's and get the same result.   
in the Live cd i get a message (window called boot loader) /casper/initrd.gz
on the Alt CD i get the same window, message says /install/initrd.gz.

When i hit Enter, it goes back to the install window, but selecting anything freezes the installer.   3 finger salute will reboot and the installer starts over.

---

