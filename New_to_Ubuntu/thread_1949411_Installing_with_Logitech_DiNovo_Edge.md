---
title: "Installing with Logitech DiNovo Edge"
date: 2012-03-30
forum: New to Ubuntu
---

### Post by Hilazing on 2012-03-30
Hi everybody,

Hopefully new Linux user here - if I can ever get it working!

I currently have a test machine which runs on Windows 7 and Vista on a dual boot, I'm trying to add Ubuntu as a 3rd boot option but I'm having some issues.

Recently moved back to the UK after living in Australia for a few years, and got rid of all but my best spare PC parts to save space in shipping my stuff back.

All I have left in terms of a keyboard is my Logitech DiNovo Edge wireless keyboard.

I downloaded Ubuntu 11.10 and made a bootable USB stick, but as soon as Ubuntu loads, I lose the ability to use the keyboard.

I have a mini USB mouse which i can plug in and works fine, but no alternative to the DiNovo keyboard. I can't get any further than the "choose a username" screen when trying to install Ubuntu, because it requires keyboard input.

I had a quick look around, and people suggest using the on screen keyboard to make changes to the files on the OS, but apparently this only works for upgrades, because the on screen keyboard is not available from the version of Ubuntu on the USB stick.

Any help people have with this would be greatly appreciated, as I plan on wiping windows and turning this machine into a Ubuntu/XBMC HTPC when I've finished testing on it.

Thanks in advance for any help.

---

### Post by Cheesemill on 2012-03-30
Check your BIOS, you may have to enable 'legacy USB mode' or whatever it's called in your particular BIOS.

---

### Post by Hilazing on 2012-03-30
Hi Cheesemill.

Thanks for the help, however the keyboard works fine on Windows Vista/7 and also for entering and making changes to the bios, So I believe it is an issue with Ubuntu's handling of the bluetooth adapter for the keyboard.

If I try to use the touchpad on the keyboard, or press any keys, I get a pop up message advising that my keyboard is trying to connect and would I like to let it connect. I hit yes, check the box saying to always let it connect, but it still does not work.

Looks like I'm stuck using windows until such a time as I can lay my hands on a wired keyboard to get Ubuntu installed.

---

### Post by airdelroy on 2012-04-30
I believe this is a bug.  And it still exists in kubuntu 12.04.  I fixed this by editing /lib/udev/rules.d/62-bluez-hid2hci.rules (/lib/udev/rules.d/97-bluetooth-hid2hci.rules in 12.04) and changed "hiddev" to "hidraw".  Then rebooted.

Aaron

---

