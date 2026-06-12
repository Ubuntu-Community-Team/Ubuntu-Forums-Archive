---
title: "Lenovo Yoga 310"
date: 2018-02-17
forum: New to Ubuntu
---

### Post by imaginary.duck on 2018-02-17
I just bought a new Lenovo Yoga 310 with Windows 10 and I decide to install Ubuntu 16.04 on it.
In order to install Ubuntu on it, I had to get a Live USB stick and boot the computer up in legacy mode.
Ubuntu is now installed on the computer. 
Touch screen display is working, however, the touch pad isn't working. 
I can see the pointer, but it ain't moving.
It does move with touch screen and with external mouse.
Do anyone have an idea how to get touch pad working?

Also I can't boot to Windows 10 anymore.
Thanks in advance!

---

### Post by krusty8 on 2018-02-19
You could try with a new version. 17.10

---

### Post by m*&amp;rTb$l)@ on 2018-02-19
Make sure you have the Synaptics package installed. This once fixed it for me on 16.04 on my laptop.

```
sudo apt-get install xserver-xorg-input-synaptics
```

---

### Post by imaginary.duck on 2018-02-19
> **julian2000nl said:**
> Make sure you have the Synaptics package installed. This once fixed it for me on 16.04 on my laptop.

```
sudo apt-get install xserver-xorg-input-synaptics
```


That didn't work for me, however, when I was searching for more information I found a forum that recommended this command:

```
sudo apt-get install xserver-xorg-input-libinput-hwe-16.04

```

That turned out to solve the problem!
Thank you guys! Really nice of you.

---

