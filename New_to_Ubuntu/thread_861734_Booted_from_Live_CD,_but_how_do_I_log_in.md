---
title: "Booted from Live CD, but how do I log in???"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by BillyBoy2 on 2008-07-16
I've downloaded ubuntu, burned a CD. 

o I boot off that CD.
o I select running without changing the system.
o I wait.
Eventually I get that login screen with the annoying sounds and a countdown and threat to login as user "ubuntu".

What the heck am I supposed to type to get logged in and get to a command prompt?

(Aside from the login screen, I am never asked for a username and password during the boot process.)

---

### Post by scragar on 2008-07-16
The username is **ubuntu** and there is no password.

To be quite honest though you shouldn't be seeing that at all unless you chose to log out once the liveCD had loaded(since it uses autologin)... That's the second request for the liveCDs login info recently, maybe it should be looked into...

---

### Post by BillyBoy2 on 2008-07-16
I tried booting from scratch again, and restrained myself from touching keyboard or mouse.

Same result - I'm in that login loop. And user ubuntu/no password doesn't work.

One other data point: This is a 64-bit system.

---

### Post by nkri on 2008-07-16
Did you do a checksum or check for errors on the disc?  If not, put in the CD and turn on the computer.  In the first screen, there's a "Check for Errors" (or something like that) option.  Try this and see if it returns anything bad.  If you already checked, I'm afraid I can't help:(.

Oh, wait.  Did you download the right .iso file from ubuntu.com?  There are two options: Standard x86 PC (32-bit) and 64-bit.  Are you sure you got the 64-bit one?

Good luck!
-nkri

---

### Post by bodhi.zazen on 2008-07-16
The live CD will log you in automatically. If needed, the default user is "ubuntu" without quotes and the password is blank (just hit enter).

This is true of the desktop edition, 32 or 64 bit.

If your CD is not behaving this way either you do not have the Ubuntu desktop CD or your CD is corrupt.

---

### Post by BillyBoy2 on 2008-07-17
1. I ran the CD check - claims everything is fine.

2. I am sure I have the 64-bit download.

3. I notice a couple of fd0/logical block 0 buffer I/O errors at the start of the boot process. (I ASSUME - perhaps unwarranted - this is after a ramdisk has been built.) These seem to have no further effect, as all of the stuff that scrolls up the screen is pretty clean, an in the end reports no errors.

4. I tried booting in "safe" mode. Start of process looked the same as before, but near the end of the boot process I got a popup about a settings daemon error. I clicked that away, and the system is now apparently logged in, as I have various - I assume ubuntu - menus and applications available.

---

### Post by bodhi.zazen on 2008-07-17
yes, sometimes the live CD gives those errors, I am not sure why.

If you re start X (log out and back in or hit Ctrl-Alt-Backspace) the desktop loads without errors.

---

