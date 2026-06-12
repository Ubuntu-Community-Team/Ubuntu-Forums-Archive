---
title: "Change &quot;mouse&quot; device to &quot;js&quot;"
date: 2015-01-24
forum: New to Ubuntu
---

### Post by chris_shaw2 on 2015-01-24
Hi all! (My first post here! ):P).

I have made an Arduino-based joystick using some firmware (UnoJoy! [https://code.google.com/p/unojoy/](https://code.google.com/p/unojoy/)) that basically turns the Arduino into a USB HID device. It all works fine on Mac & Windows but on Ubuntu I'm having the following problem:

The device gets recognised as /dev/input/mouseX, it moves the mouse on-screen, and I've checked that other data is also coming through, but I really need it to be recognised in Ubuntu as a joystick!

I've tried various instructions, from UnoJoy! & other related forum posts & google-searches, but nothing is working. I've played around with using joystick, jstest and some other packages/commands but I'm not at all familiar with Linux and I simply don't know how I can change the device recognition (or drivers if that is the problem)  on Ubuntu.

Any help anyone can give to solve this is much appreciated!

---

### Post by chris_shaw2 on 2015-04-23
Bump... No-one have any ideas for a solution to this??

---

### Post by Geoffrey_Arndt on 2015-04-23
Don't know about that software & linux compatibility but I saw this on Amazon for not too much $$:

[http://www.amazon.com/Logitech-940-000110-Gamepad-F310/dp/B003VAHYQY/ref=sr_1_2?ie=UTF8&qid=1429825879&sr=8-2&keywords=linux+joystick#Ask]("http://www.amazon.com/Logitech-940-000110-Gamepad-F310/dp/B003VAHYQY/ref=sr_1_2?ie=UTF8&qid=1429825879&sr=8-2&keywords=linux+joystick#Ask")

Mayhaps this paragraph provides a clue:

Should  be a switch on the back for Xinput and DirectX input. Make sure it's on  Xinput and it should work. "jstest-gtk" (sudo apt-get install  jstest-gtk) is a program that will allow you to calibrate a Game pad,  it's pretty much a must have for all Game pads and can be acquired from  the Ubuntu software center also

---

