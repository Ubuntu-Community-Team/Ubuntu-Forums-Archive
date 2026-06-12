---
title: "Finding the right keyboard"
date: 2015-03-09
forum: New to Ubuntu
---

### Post by peter.h.m.brooks on 2015-03-09
When installing ubuntu, it sets up the keyboard by asking you to type some keys.

What is the utility? I'd like to run it again.

I'm actually trying to get my Apple Wireless Keyboard to work properly - not as a wireless keyboard, I'm running ubuntu under virtual box, but with the right key mappings.

What I'd really like to be able to do is to get cmd-C and cmd-V working as cut and paste ( apple-C an apple-V or Super-C and Super-V) - I've hunted through lots of forum posts but found no way to do this yet.

---

### Post by Vladlenin5000 on 2015-03-09
The "utility" is part of the installer. I'm not sure it can be run afterwards but it doesn't matter because it won't do what you want it to.
That "utility" has been designed to "guess" the keyboard layout based on the user's inputs and answers. It is intended for finding out the specific regional layout when the user doesn't know (or is unsure). It has nothing to do - and therefore can't help you at all - with mapping combo keys in a VM. Often you CAN'T use those in a VM and when you can that's achieved via the VM software functions/menus.

---

### Post by peter.h.m.brooks on 2015-03-10
OK, so how do I find the right key layout for an apple wireless keyboard?

---

### Post by Vladlenin5000 on 2015-03-10
It has nothing to do with the keyboard layout. Keyboard layouts are the mappings for special characters (ç, á, è, etc.) which vary according the region/country where a given keyboard is being sold (US International, French, German, Spanish, Portuguese, etc.). The combos are exactly the same, CTRL+ALT+DEL (in PCs) is the same everywhere and even works when there's a mismatch between the physical keyboard layout and the one configured in the OS.
Your problem has to do with using it in a virtual machine where - again - it usually don't work. Example: The aforementioned CTRL+ALT+DEL will always affect the host OS and not the VM;  In order to use it in the guest OS, and assuming it's being run with Virtualbox, you would have to go to the Virtualbox's menus and find the option to "send CTRL+ALT+DEL". How is it done with MacOS being the host and with Apple's hardware/peripherals I don't know, never use it, but it must be similar.

---

