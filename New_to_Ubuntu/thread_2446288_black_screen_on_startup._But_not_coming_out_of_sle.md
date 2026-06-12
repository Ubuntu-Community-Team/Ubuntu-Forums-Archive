---
title: "black screen on startup. But not coming out of sleep mode."
date: 2020-06-27
forum: New to Ubuntu
---

### Post by Tach on 2020-06-27
Hi, I tried installing Ubuntu 20.04 and I have an issue where the screen just goes black. Then if I press the power button to put the computer into sleep mode, it goes into sleep mode; and upon waking the computer from sleep mode my screen appears just fine and I can then use Ubuntu. I also have this problem with Clear Linux. I'm thinking it's hardware related.

Hardware
GA-B85N-WIFI motherboard (with intel integrated graphics disabled)
Intel 4790K CPU
Nvidia 1080 gtx Ti
Broadcom wifi that need proprietary drivers

That's basically it. Anyone have any idea what's going on?

edit: Oh I'm also using a 4k TV, a Samsung MU6300, but this also shows up on my Vizio 655-G9.

---

### Post by MoebusNet on 2020-06-27
Have you tried using the proprietary Nvidia driver for your video card? Look in the Menu for 'Additional Drivers' to see whether or not you are using the open-source video driver or the proprietary Nvidia driver.

---

### Post by Tach on 2020-06-27
Ohh, no I'm not. 
But unfortunately I can't install it, since I don't have the Broadcom driver installed to access the internet. I tried this -> [https://askubuntu.com/questions/523458/unable-to-connect-to-any-wifi-in-ubuntu-14-04/523568#523568](https://askubuntu.com/questions/523458/unable-to-connect-to-any-wifi-in-ubuntu-14-04/523568#523568), but then I have a bunch of dependencies I can't install...and I don't understand why the driver isn't installed to begin with, since it was working during installation. This is pretty stupidly frustrating, whoever designed it like this. I get that people want Linux to be open source, but if the open source drivers don't work or are non-existent, install the bloody proprietary drivers by default Canonical!!

---

### Post by Tach on 2020-06-27
Maybe I'll come back to this when I'm not seriously annoyed.

But thanks for the help.

---

### Post by Tach on 2020-06-27
Oh, I'm an idiot. So I reinstalled and noticed an option to install third party drivers. Now everything works great. :)

---

