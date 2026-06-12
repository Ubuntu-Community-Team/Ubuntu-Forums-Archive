---
title: "USB Keyboard/Mouse not responding after install."
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Porpherion on 2008-07-17
Hello, I'm a new user to linux, and was told by friends that Ubuntu is great to learn on. I downloaded the 8.04 x86_64 cd, as I run 64-bit hardware, and the install went great! However, upon rebooting my computer, I hang at login screen due to the fact that neither my usb keyboard or mouse will respond. Is the something I can do to fix this? I have no problem reinstalling if need be, as I didn't have the opportunity to select packages the first time through, so I may have missed something. Thanks in advance!


[EDIT] Tried rebooting to get more info, and it seems I am getting an error along the lines of "usb 2-7 not accepting address 9, error -110". I don't think this is exact, but very close, as it went away before I got a good look. I do know the error message is correct.

---

### Post by nowshining on 2008-07-17
just ctrl+alt+f1 and ctrl+alt+f7 to get back to a gui

from ctrl+alt+f1 press the shift key and the up button until u find the error and if there are any more - write them down and come back and let us know what they are...

no need to exit programs, etc.. when u go and come back from the ttys ;)

---

### Post by Tony Flury on 2008-07-17
nowshining - I would be impressed (and slightly worried) if Ctrl-Alt anything worked when the OP says that his keyboard is not responding.:lolflag:

Porpherion - does your system have ps/2 style inputs for keyboard and mouse ? can you borrow a ps/2 style kb and mouse (or get a USB to ps/2 adapter).

---

### Post by nowshining on 2008-07-17
> **Tony Flury said:**
> nowshining - I would be impressed (and slightly worried) if Ctrl-Alt anything worked when the OP says that his keyboard is not responding.:lolflag:

Porpherion - does your system have ps/2 style inputs for keyboard and mouse ? can you borrow a ps/2 style kb and mouse (or get a USB to ps/2 adapter).

lolz, i guess ur right - :) I stayed up all night of course.. and thanks for the heads up. :)

---

### Post by Tony Flury on 2008-07-17
Porpherion - One thing that springs to mind - is your USB port on your m/c a mother board mounted port, or is it an expansion card. If it is an expansion card you might need a linux driver for the thing before it will work (which clearly you can get if you can't boot).

If you have mother board mounted USB ports you could try attaching keyboard and mouse to them - as they are likely to have native BIOS support and might be recognised correctly by the Linux kernel.

---

### Post by Porpherion on 2008-07-17
Sorry, had to get few hours' sleep :p

I unfortunately don't have access to a ps/2 keyboard and mouse. The current keyboard and mouse are connected through motherboard mounted ports, leading me to believe the BIOS is reporting something incorrectly.

---

### Post by silverglade00 on 2008-07-17
On some machines I play with, I have to use a certain USB port for the keyboard and/or mouse. Trying moving them around to different ports, especially try the keyboard in a port if you see it marked "1".

---

