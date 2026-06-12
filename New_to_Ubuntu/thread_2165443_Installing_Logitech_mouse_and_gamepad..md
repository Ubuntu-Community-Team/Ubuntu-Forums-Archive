---
title: "Installing Logitech mouse and gamepad."
date: 2013-08-05
forum: New to Ubuntu
---

### Post by jody2 on 2013-08-05
I just recently completely switched over from windows 8 to ubuntu 12.04.2, and I really need to know how I can go about using my logitech M510 wireless mouse and my logitech gamepad F310.
I am a complete noob to ubuntu and anything linux. I have tried my best to search for a solution on the internet but I can't find a straightforward answer for the life of me.
Please help! I need someone to guide me through this as soon as possible! I need to play my emulators! :mad: 
If anyone can also point me in the direction of a halfway decent guide on understanding ubuntu that would make my week.
I really want to enjoy this OS, but so far i'm having a really difficult time doing so. :( HELP!

---

### Post by fantab on 2013-08-05
Generally most of the Logitech devices are supported out of the box on GNU/Linux or Ubuntu. However, if you are looking to pair different Logitech devices to single reciever then it can only be done with its own software which only works on Windows. You use a Windows machine to pair 'em up then connect to Ubuntu and they work. Sometimes you need to unplug/plug the reciever to get it going. I don't know about gamepads.. as I don't use 'em but I do use a Logitech paired Keyboard and Mouse, and it works great.

If you still have any problems then use the following command to see if your devices are being detected...

```
lsusb
```

If you are not sure then post the output here. Remember to keep the devices connected while you run the above command.

---

### Post by jody2 on 2013-08-05
My mouse just started to work shortly after I posted this. I am still unsure about the gamepad. I entered lsusb into the terminal and this was the output. 

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0c45:644b Microdia 
Bus 002 Device 003: ID 8087:07da Intel Corp.

The only way I could think of testing the gamepad would be to play an emulator, but I can't seem to get that to install correctly either. :(

---

