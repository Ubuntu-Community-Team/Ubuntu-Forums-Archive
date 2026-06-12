---
title: "No sound after successful installation of Ubuntu11.10"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by smoothedaccorn08 on 2011-10-30
I have an ACER Aspire One Happy Notebook. Originally the main hard drive is damaged or maybe corrupted. I have interest in installing Ubuntu so I install it in an external hard drive just to make my notebook work again. It was a success but unfortunately after it was installed there is no sound at all. I was just bothered because during the trial run of the OS the sound is working properly. Please let me know what I can do. I have read threads regarding sound and the troubleshooting guide from UBUNTU Wiki but was not sure to start because I am new with this system. Thank you! :)

---

### Post by fantab on 2011-10-30
> **smoothedaccorn08 said:**
> I have an ACER Aspire One Happy Notebook. Originally the main hard drive is damaged or maybe corrupted. I have interest in installing Ubuntu so I install it in an external hard drive just to make my notebook work again. It was a success but unfortunately after it was installed there is no sound at all. I was just bothered because during the trial run of the OS the sound is working properly. Please let me know what I can do. I have read threads regarding sound and the troubleshooting guide from UBUNTU Wiki but was not sure to start because I am new with this system. Thank you! :)

By default Ubuntu Sound is muted upon installation. I hope you have tried Unmuting. If you have already done this then go to **System Settings- Sound- Hardware** and select appropriate device from the drop down menu and Test Speakers. Usually Ubuntu does this on its own. 
Also see if the appropriate **connector** is selected in **Output. **

If all the above fails then it could be the Sound Card. 

See if the system is detecting your sound card: open Terminal and run the following command:
```
sudo aplay -l
```**[This Link]("https://help.ubuntu.com/community/SoundTroubleshooting")** should get you started for your basic trouble-shooting.

If you still don't have Sound then run this command from the terminal (you can copy/paste the command below in the terminal):

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*
```and follow the steps described [**here**]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure").


I hope that helps.....

---

