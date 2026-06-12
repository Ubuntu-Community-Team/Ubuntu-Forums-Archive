---
title: "[SOLVED] command question"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Pnkmaggt on 2008-05-21
im trying to turn off my annoying as hells system beep that doesnt just turn off when i click the preferences -> sound option and disable it there.  YES it turned off the beep when i hit delete too many times or whatever but it still sounds when i boot up.  
Looking around i found this:

sudo rmmod pcspkr

but i wasnt sure if that would turn off all sound completely?
and i know that -rm can be bad juju so i figured i would ask bfor i try it out lol.
TY!

---

### Post by tompickles on 2008-05-21
when you boot - it isnt ubuntu that beeps, its your motherboard - so, bootinto your bios settings and have a read and see if somewhere there is a system alerts option to turn off.

however, it may also turn off the beeping if you ever overheat..... try it... i may be wrong

---

### Post by Pnkmaggt on 2008-05-21
i couldnt really find anything about system beep/ or alarms or anything in bios . . .

sorry i forgot to say: Running Dell Latitude D820 with Gutsy

---

### Post by nick_h on 2008-05-21
> and i know that -rm can be bad juju so i figured i would ask bfor i try it out lol.
rmmod will remove a module from the kernel.  It doesn't delete anything from your disk so you are safe to try it.

The module will be reloaded when you next reboot.  You can also load it again with the modprobe command.

---

### Post by MaindotC on 2008-05-21
If you feel like opening your tower there should be a 4-pin cable from the sound board to a tiny speaker - usually near the front or if you have headphone/mic jacks in the front.  You can disconnect that to stop the hardware beep.  It won't affect any other sound capabilities like speakers or headphones.

---

### Post by N.N. on 2008-05-21
Just blacklist it, i.e. prevent it from being loaded on boot. Use the following command to edit the list of blacklisted devices: ```
sudo nano /etc/modprobe.d/blacklist
``` Then add the following line at the end of the file to blacklist the annoying pc speaker once and for all: ```
blacklist pcspkr
``` (Use CTRL+X to exit. Make sure to save changes).

Cf. the following post on tombuntu: [http://tombuntu.com/index.php/2007/07/17/disable-your-internal-speakers-beep-in-linux/](http://tombuntu.com/index.php/2007/07/17/disable-your-internal-speakers-beep-in-linux/).

---

### Post by Pnkmaggt on 2008-05-21
hey worked like a charm.  Disabled that #$%^&*( beep and kept my speakers alive for music/etc TY sooooo much i was bout to break the damn thing

---

