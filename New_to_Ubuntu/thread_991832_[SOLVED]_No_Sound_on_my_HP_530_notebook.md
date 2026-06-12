---
title: "[SOLVED] No Sound on my HP 530 notebook"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by realmoonstruck on 2008-11-24
I'm using **ubuntu 8.10**, previously everything was fine but suddenly i have stopped getting any sound from my notebook.
I don't get any error messages or warnings thus i can not point out the exact problem.
But I'm sure that it's not a hardware problem cause I can get sound if I boot using my Hardy Heron live CD.
I have reinstalled ***alsa*** and ***pulse audio*** packages, but that did not help...

please help me out guys... :confused::confused::confused:

---

### Post by Dave.YNA on 2008-11-24
Im not sure if this will be connected but I had the same issue on my toshiba nb100 netbook after doing system updates (seems that the update broke the sound). Does the speaker icon on the top right have a mute symbol next to it?

If it does I can provide you with the steps that worked for me. If not then I may not be much help.

---

### Post by realmoonstruck on 2008-11-24
> **Dave.YNA said:**
> Im not sure if this will be connected but I had the same issue on my toshiba nb100 netbook after doing system updates (seems that the update broke the sound). Does the speaker icon on the top right have a mute symbol next to it?

If it does I can provide you with the steps that worked for me. If not then I may not be much help.
ya it did have the mute symbol. but after i adjusted the alsamixerfrom the terminal it has gone...

---

### Post by realmoonstruck on 2008-11-24
think it's the same problem.

---

### Post by Dave.YNA on 2008-11-24
Ok, try the following. This worked for me.

1- Open Terminal
2- Type sudo mv /lib/modules/2.6.24-19-lpia/updates/sound ~/sound
3- Enter your password
3- Type sudo depmod -a
4- Restart machine

I found this on the toshiba website so cant guarantee it will work for you. 

Let me know if it works. 

Good Luck!

---

### Post by realmoonstruck on 2008-11-24
> **Dave.YNA said:**
> Ok, try the following. This worked for me.

1- Open Terminal
2- Type sudo mv /lib/modules/2.6.24-19-lpia/updates/sound ~/sound
3- Enter your password
3- Type sudo depmod -a
4- Restart machine

I found this on the toshiba website so cant guarantee it will work for you. 

Let me know if it works. 

Good Luck!
That didn't work for me.
I had a different kernel version so i had to use

[I][B]sudo mv /lib/modules/2.6.27-7-generic/kernel/sound ~/sound

[/B][/I]then after rebooting the mute sign has appeared again!
on clicking the volume control on the panel, I get the following error message...

[I]The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.[/I]

---

### Post by Dave.YNA on 2008-11-24
That's Strange. Its the exact message I got before I placed the code into terminal. 

If you try and play a sound from the "Sound preferences" e.g. login sound, I bet you will get another big warning message. 

hmm.... As crazy as this might sound, what happens if you run the code again?

It just seems you are in the exact state I was after my software update.

What other things have you tried so far?

---

### Post by realmoonstruck on 2008-11-28
That didn't work for me. but i had to purge the custom settings to make it work.

this is what saved me...
[B]
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2[/B]

from ***[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)*** :lolflag:

---

### Post by realmoonstruck on 2008-11-28
That didn't work for me. but i had to purge the custom settings to make it work.

this is what saved me...
[B]
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2[/B]

from ***[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)*** :lolflag:

---

### Post by realmoonstruck on 2008-11-28
sorry for the repeat post.
didn't know about the edit feature!!!!!!

---

