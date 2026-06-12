---
title: "Phonon issue, doesnt store the changes I've made"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by TPAKTOPUCTA on 2012-06-14
Hello all,
I am newbie in linux and I have the following problem-
When I tried to change the settings in phonon and I exit the program, it automatically restore the previous settings :(. 
My problem is that initially I did not have any sound, so I did a small investigation and I discovered that phonon set my HDMI as the default playback device, therefore I do not have any sound on build in speakers and headphones (I installed the kubuntu on my laptop). So furtherer on I installed pavcontrol and using this program I managed to change the default playback to "build in audio" but again, when I restart the OS the phonon just automatically change the default playback device to HDMI audio, and to have sound I have to start pavcontol and do the settings again. Is there a way to prevent phonon to change the default playback device?

Thank you in advance.

---

### Post by SeijiSensei on 2012-06-14
You didn't tell us which version of Kubuntu you're using, but 11.04 had a [bug]("https://bugs.launchpad.net/ubuntu/+source/phonon/+bug/769274") where Phonon settings were not saved properly.  I didn't encounter this bug in 11.10 or 12.04, so perhaps an upgrade to 12.04 will do the trick.

---

### Post by TPAKTOPUCTA on 2012-06-14
> **SeijiSensei said:**
> You didn't tell us which version of Kubuntu you're using, but 11.04 had a [bug]("https://bugs.launchpad.net/ubuntu/+source/phonon/+bug/769274") where Phonon settings were not saved properly.  I didn't encounter this bug in 11.10 or 12.04, so perhaps an upgrade to 12.04 will do the trick.

Sorry for that. I am using the latest version, herewith is the output of lsb_release -a 

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04 LTS
Release:        12.04
Codename:       precise
 
at least now when I restart and phonon change the default playback device I have an option to dismiss the change with a button, and the sound is back.

---

### Post by samigina on 2012-06-15
Just right click on the volume icon in the systray, then, Select Master Chanels and choose the right one. The setting will be autosaved for your session.

---

