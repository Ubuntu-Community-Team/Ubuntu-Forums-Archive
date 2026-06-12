---
title: "Audio issue."
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Lenus on 2008-09-23
The LTS version 8.04 (HH) which I have installed inside Windows as an application (WUBI) is really going on great. But I have stuck up with a problem. Whenever I connect my external speakers on to the machine using the regular port for speaker (like the USB port) I am getting very low volume output. But when I try connecting the headphones using the regular phones jack its working fine.

What is causing this issue? I tried searching on for a while to get results which says about the incompatibility of Linux kernel with certain drivers for audio. But my problem doesn't seem to be so as the headphones are working fine.

Any thoughts on this will be helpful.

---

### Post by Lenus on 2008-09-23
Hope this is not because I have not installed Ubuntu as a complete OS.

---

### Post by Orange_and_Green on 2008-09-23
Hello

You could try ```
alsamixer
``` and see if all volume bars are up to 100% (0 dB), and if there are any strange channels or boosts that you can mute or unmute with the 'm' key. Use the ESC key to save & quit.

I think you should fix it by playing around a little with that (for example, my speakers don't work if I don't mute the 'external amplifier' channel).

Good luck :KS I think you need not panic as I have never heard of an OS being incompatible to a speaker set.:)

Although, to be honest, I must confess this is the first time I have heard of USB speakers either...;) You mean they are powered via USB, but they still have an audio jack don't they?

---

### Post by Lenus on 2008-09-23
Hi, thnx for the update. Yes the speakers are powered via USB ports and has nothing else. I will try with alsamixer as am on the Crash ;-) box now.

But my doubt is, since the speakers are getting powered via a USB port, can that hamper the sound amplication process?

---

### Post by Lenus on 2008-09-23
Is there any bug reported for audio devices when running Ubuntu as an exe (WUBI)in Windows ???

---

### Post by markbuntu on 2008-09-23
The usb port might not be providing enough power to the speakers but if they work OK in windows this should not be the problem. The alsamixer will have a separate section for the usb speakers so be sure to look in there. Really, you should get:

gnome-alsamixer

with synaptic. It is a lot easier to use. Also check in the volume control. Right click on it and choose open volume control go to File/Change Device and select the usb speakers. Trun them up. Then choose Edit/Preferences and check the box for master. close the volume control and see if you can control them with the Volume Control.

---

