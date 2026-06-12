---
title: "Realtek ALC861: No sound, ALSA error and Volume control at 0"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by Ubuntokyo on 2012-03-14
Hi there,

I tried the hardware forum with no luck, maybe I should use this forum as my question is surely from an absolute beginner.

I installed lubuntu 11.10 on a Toshiba Dynabook CX/875LS.
After some digging in windows, I confirmed my soundcard should be a Realtek ALC861.

The sound does not work, there are two issues I can see:
 - In the task bar, the volume control is at 0 and I cannot move it.
 - When first opening Audacious, the following error message is displayed: ALSA error - No suitable mixer element found.

I read a lot of posts but could not find the solution.
I am not sure how to troubleshoot driver issues in Linux

As I am getting lost, I would appreciate your guidance.

Thank you

---

### Post by tbhatia4 on 2012-03-14
check for additional drivers whether available if so you can activate that there
it'll automatically download and install
you need to reboot system after that

---

### Post by Ubuntokyo on 2012-03-15
Thank you, an excellent advise.

I installed something called the software modem.
I do not have the alsa error anymore when opening Audacity.
I could read a mp3 file and hear the sound on my speakers and headphones.

Maybe a piece of explanation:
[INDENT][I]aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0[/I][/INDENT]

So the modem and the sound card seem to be recognized as a sound card.

I still have a last issue, the sound from the mp3 comes from the "PCM" output in the ALSAmixer.

Still impossible to change the master volume in alsamixer, or the volume control in the GUI.

I don't even know how to take and paste a screenshot, but alsamixer is text so could take a text screenshot below:
[http://paste.ubuntu.com/884814/](http://paste.ubuntu.com/884814/)

Any idea how to solve this?

Many thanks

---

### Post by marinara on 2012-03-17
alsamixer allows you to select sound card.  does that help?

---

