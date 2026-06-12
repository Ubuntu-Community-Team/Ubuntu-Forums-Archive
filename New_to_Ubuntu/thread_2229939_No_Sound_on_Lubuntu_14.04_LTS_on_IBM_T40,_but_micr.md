---
title: "No Sound on Lubuntu 14.04 LTS on IBM T40, but microphone picks up voice"
date: 2014-06-16
forum: New to Ubuntu
---

### Post by Deltastraw14 on 2014-06-16
Hello

I'm new to linux recently put the latest version of lubuntu as a dual boot with Windows XP on my old IBM T40 in order to keep it going as a general browsing and writing laptop for when I want to laze about on the sofa.  However a slight problem is that I don't seem to have any sound, which makes using you tube and anything involving sound pointless.  

I have tried mostly everything that google has thrown at me, such as checking alsamixer hasn't randomly muted the output, purging and reinstalling alsamixer and installing the dev audio drivers, but to no avail.  There is still no audio output through either headphones or speakers.  However the microphone does work and it does pick up an input.

My laptop according to alsamixer has an Intel 82801DB-ICH4 sound card installed with an Analog Devices AD1981B chip. The other one that is available to select is the Thinkpad audio console control and selecting that does nothing either. 

With the exception of the sound issues, I am very impressed with Lubuntu. It runs much faster than Windows XP does and has a far smaller footprint.

Thank you for any help :)

---

### Post by sudodus on 2014-06-16
Welcome to the Ubuntu Forums :-)

1. I suggest that you install ***pulseaudio*** and ***pavucontrol*** and use the menu of pavucontrol to try to tweak the settings until it works. In a terminal window, run the following commands

```
sudo apt-get install pulseaudio
sudo apt-get install pavucontrol
```

2. If still no luck I suggest that you try either of

***Xubuntu 12.04 LTS*** (supported until April 2015) or

a community re-spin based on Ubuntu 12.04LTS,*** Bento, Bodhi or LXLE*** (promising support until April 2017)

There is a fair chance that the older version 12.04 LTS works better with your old hardware. You might need fake-PAE with 12.04 depending on the kernel version. (I have a similar Thinkpad T42, where the sound works with both 12.04 and 14.04.)

---

### Post by Deltastraw14 on 2014-06-16
The pulse audio and pavucontrol commands worked, I now have sound. Thank you very much for fixing this :)

---

### Post by sudodus on 2014-06-16
I'm glad it works for you :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED, and welcome back when you have another problem or something to share or discuss.

---

