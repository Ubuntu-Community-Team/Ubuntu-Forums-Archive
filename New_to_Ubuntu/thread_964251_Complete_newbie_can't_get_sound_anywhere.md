---
title: "Complete newbie can't get sound anywhere"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by davefaulkner on 2008-10-30
Having failed to get a dual-boot with Windows Vista working with Wubi, I've resorted to trying out Ubuntu 8.10 in a Sun VirtualBox 2.0.4. I am having a few problems.

With regard to sound, I can't get anything anywhere. The most common error message tells me I may be missing some gstreamer plugins. However, googling for gstreamer has completely confused me. I wouldn't know where to begin.

I've also tried going to System>Preferences>Sound>Devices and playing around with all available options - autodetect, ALSA, you name it. Again, nothing works.

I have the SigmaTel High Definition Audio CODEC installed on the computer, if that's any help.

Any ideas would be much appreciated. Thank you.

---

### Post by Koaguin on 2008-10-30
its been a while since i've used VirtualBox, but I think you have to change a setting in virtualbox to get sound to work

---

### Post by jbrown96 on 2008-10-30
As Koaguin said, there's an option you need to enable. with the VM turned off, go to the VM's settings. There a tab for audio; just select an audio driver (not sure what it would be for windows).

---

### Post by davefaulkner on 2008-10-31
Thanks for the advice. I now have sound working! It took some playing around with the audio settings in VirtualBox to find the right combination of host driver and controller. Inevitably it was the last combination I tried that worked.

Still don't have the monitor resolution problem resolved via Guest Additions (as in my other query that you kindly answered), so back to that one now.

Very grateful for your help.

---

### Post by coldcoffee on 2008-10-31
I forget exactly where it is, shouldn't be to hard to find though. When I used virtual box I had to enable the ALSA section. I believe it is a checkbox. I had to do that before any of the virtual machines had sound. You will have to do it for every virtual machine you create too. It isn't a one time thing that works for every new virtual machine you create. Just click through all the options, it should be fairly easy to find.

Hope that helps.

Edit: Sorry, I missed where you mentioned you tried ALSA.
But being you are trying to run ubuntu, I would almost bet money that ALSA is the option you need. You may have to install some drivers on your virtual machine for your actual hardware to get it to work. I don't know for a fact if it is the only one, but ALSA is the architecture or whatever you would call it that a lot of Linux machines use for sound.

Being that it is a virtual machine I suppose you could play around with it seeing as how it shouldn't mess up your base install. I would suggest going to synaptic and doing a search for alsa. Maybe try alsa-base, alsa-utils, gstreamer0.10-alsa.

Going on about it. I really need to learn to read posts more thoroughly. Not griping or complaining. But to keep idiots like me from looking like idiots you probably should mark this as solved by using thread tools.

---

