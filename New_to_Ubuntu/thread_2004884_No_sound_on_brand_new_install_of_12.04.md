---
title: "No sound on brand new install of 12.04"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by Inglonias on 2012-06-16
I cannot get sound out of any of the sound ports on the back with a brand new Ubuntu install. It's an older motherboard with an integrated soundcard. The motherboard is a Gigabyte GA-EP35-DS3L.

Running ```
aplay -l
```gives me the following output:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Can anybody help me?

EDIT: The sound works when I plug speakers into the front headphones port, but not into the back. While my problem is kinda sorta solved, I would still like to have it fixed.

---

### Post by blackbird34 on 2012-06-16
Have you tried the "Sound Settings" or "PulseAudio Volume Control" (search for them in the Dash) to see if your devices aren't accidentally disactivated? There are several configuration interfaces for sound in Ubuntu so might as well start with those before doing all the command line fu.

---

### Post by Hadaka on 2012-06-16
Hi, open up a termnal.ctrl/alt/t
and enter   alsamixer

if nothing is muted
try this
in terminal ...enter code:

sudo gedit /etc/modprobe.d/alsa-base.conf

#and add this line at the end of the file#

options snd-hda-intel model=generic

#save and close, then restart , this should fix your problem.#

---

### Post by sandyd on 2012-06-16
> **Inglonias said:**
> I cannot get sound out of any of the sound ports on the back with a brand new Ubuntu install. It's an older motherboard with an integrated soundcard. The motherboard is a Gigabyte GA-EP35-DS3L.

Running ```
aplay -l
```gives me the following output:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Can anybody help me?

EDIT: The sound works when I plug speakers into the front headphones port, but not into the back. While my problem is kinda sorta solved, I would still like to have it fixed.

You are affected by bug #945917.
See [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/945917](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/945917)

Please subscribe to the bug by following the steps below so that you are notified of further developments.

[LIST=1]
[*]Go to [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/945917](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/945917)
[*]Log in. (or Register if you do not have a account)
[*]Click on "This bug affects X people. Does this bug affect you?"
[*]Select "Yes"
[*]On the right side of the screen, click on the words "Edit bug mail"
[*]I suggest you choose the last option (only receive email when this bug is closed), as the others will cause any further comments to the bug to be sent to your email.
[/LIST]

Now, whenever the bug is closed (i.e. fixed/incomplete/invalidated), you will recieve an email alert.

Regards,

---

### Post by codingman on 2012-06-16
This bug has been reported, I suggest you use those front ports until this bug is fixed, I suggest you make a launchpad account, very useful to report your bugs in. It's always a good idea to contribute to the community!

---

