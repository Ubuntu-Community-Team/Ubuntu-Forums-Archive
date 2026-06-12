---
title: "Recommended Version for Dell Latitude D600 Laptop"
date: 2015-09-03
forum: New to Ubuntu
---

### Post by Infyrin on 2015-09-03
I'm trying to get my friend a Ubuntu version installed and my immediate resolve was to go to 15.04, because it's recent and new.

Unfortunately, I think this laptop has finally met it's limitations and is unable to function the entirety of this version. Notably how the windows take a minute each fading in and out as well as notable chugs in performance. So, I'm trying to wonder what's a suitable version of ubuntu that will make due on this laptop.

Specs:

2GB DDR (266-MHZ, maxed out)
1.63GHz Pentium Centrino CPU
ATI 32MB of Video RAM

Also, as a side question. I know this laptop has bluetooth, because it has the symbol next to the battery charge. I'm trying to get my LG440G Tracfone phone to pair with the laptop because apparently bluetooth is the only way to transfer files to and from the phone. How can I get this to function in an Ubuntu environment?

Thanks.

---

### Post by sudodus on 2015-09-03
Welcome to the Ubuntu Forums :-)

I would try Lubuntu or Xubuntu or a combination.

If you can download a couple of iso files, I would recommend

**lubuntu-14.04.2-desktop-i386.iso** and **xubuntu-14.04.1-desktop-i386.iso**

14.04.1 LTS is supported until April 2017. Yet I recommend **lubuntu-14.04.2-desktop-i386.iso** or **lubuntu-14.04.3-desktop-i386.iso**, because they are better debugged than **lubuntu-14.04.1-desktop-i386.iso**.

You may need the boot option **forcepae**. See this link [https://wiki.ubuntu.com/Lubuntu/AdvancedMethods](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods)

You can get the best of both flavours if you install ***Xubuntu 14.04.1 LTS ***and update/upgrade it to be up to date. After that you can install lubuntu-core, reboot and clean the system:

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo reboot
sudo apt-get install lubuntu-core
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```

This way you can switch between Xubuntu for most applications and Lubuntu when you need a faster desktop, for example to play video.

-o-

If there are problems with drivers for the graphics chip, I would recommend a community 're-spin' based on Ubuntu 12.04 LTS:

Try ***Bento, Bodhi, LXLE and ToriOS***. Try live before installing!

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

