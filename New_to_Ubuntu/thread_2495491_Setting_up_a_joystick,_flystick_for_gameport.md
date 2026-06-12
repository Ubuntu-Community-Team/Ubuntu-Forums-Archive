---
title: "Setting up a joystick, flystick for gameport"
date: 2024-02-21
forum: New to Ubuntu
---

### Post by Diablero on 2024-02-21
Hi all! Ubuntu 22.04, I connect to the sound system via gameport. I decided to fly here a little and connected an old joystick - Quickshot Srato Warrior QS-216. I added the analog parameter to /etc/modules, it worked, but the buttons do not work. In jstes-gtk they are not active, they are not clickable. 
jstest /dev/input/js0 produces the following:
```
Driver version is 2.1.0.
Joystick (Analog 4-axis 4-button joystick) has 4 axes (X, Y, Throttle, Rudder)
and 4 buttons (Trigger, ThumbBtn, TopBtn, TopBtn2).
Testing ... (interrupt to exit)
Axes:  0:     0  1:     0  2: 32767  3:-32767 Buttons:  0:off  1:off  2:off  3:off
```
The buttons are off, but how to make them on?  I googled about analog.map=, but in principle it automatically determines it correctly, 4 axes, 4 buttons. So I think this is not the problem, but something simple, you just need to turn it on. You can set options using modeprobe, but where can you find out what to write there, where can you see the list of commands? Help please, I’ve been trying to set it up for four days)

---

