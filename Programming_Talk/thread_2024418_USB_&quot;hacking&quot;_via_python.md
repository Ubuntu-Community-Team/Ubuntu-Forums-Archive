---
title: "USB &quot;hacking&quot; via python"
date: 2012-07-13
forum: Programming Talk
---

### Post by shinkstor on 2012-07-13
I wish to do something along the lines of connecting a linux PC to something like an XBOX 360 via usb, and running a python script that will loop some code to emulate a USB mass storage device. Is this possible with any language in the first place?

I want to be able to change the contents of a flash drive that is being read by the Xbox without disconnecting it. 
This also wouldn't be limited to software, if anyone has any hardware insight or anything.

---

### Post by snip3r8 on 2012-07-15
Im not sure such a thing is possible with python ,I wouldn't say its Impossible but I would think you would need direct access to certain memory locations.

---

### Post by cgroza on 2012-07-16
Take a look at pyusb. It is a library that will allow you to manipulate USB ports and connections, and I am pretty sure that what you want to do is possible even if it could be more complicated.

---

### Post by trent.josephsen on 2012-07-16
You're going to need some specialized, and maybe self-designed, hardware.

For starters, USBish gender changers, like you would need to use in order to connect the Xbox directly to a PC, are in violation of the USB spec and you might burn something up just plugging one into the other. At least, you need to isolate the power supplies and put some logic in the middle so both controllers don't fight over the bus when it's first connected. (There are gender changers out there that do this, but those probably won't work for you -- hang on and maybe it will be more clear in a minute.)

Second, that logic in the middle is non-trivial. Both the PC and the Xbox have USB *host controllers*, which cannot connect to each other in a peer-to-peer fashion. There is no way to make a *host* controller act like a *slave* controller unless the system is designed, in hardware, to allow it (which is not going to happen with a PC). So the logic in the middle has to behave as if it were *two* slave controllers, slave X talking to the Xbox and pretending to be a mass storage device and slave Y talking to the PC. [Here]("http://stackoverflow.com/questions/682193/windows-pc-as-a-usb-slave-to-emulate-a-thumbdrive") [are]("http://bytes.com/topic/windows/answers/861697-howto-make-you-windows-pc-act-usb-mass-storage-device") some similar questions with more variety in answers.

I could go on -- there are also potential difficulties in making the content available to slave Y and further difficulties in handling startup so that slave X doesn't start emulating a mass storage device before slave Y is paired with the PC, just off the top of my head. But the bottom line is, You Can't Do That In Software(TM).

There might already be USB devices on the market that do more or less what you want. I don't know of any, though. There are USB devices that connect PC-to-PC over a networking protocol, but those wouldn't help you emulate a mass storage device.

The easiest route I can think of, unless you can find a pre-made USB device to simplify matters, is to find a prototyping platform like an Arduino or something that can act as two USB slaves, and program it to act like a mass storage device to both hosts -- i.e., store the actual data on the device itself but allow access to it from both hosts at once.

I'd first think about what problem it is you're actually trying to solve, and see if you can think of other, simpler ways to solve it.

---

### Post by blortuga on 2012-07-20
This was one of the highly touted "great" features of ieee 1394 (aka "firewire" or Sony's "i-link").  You could put a host into "target disk mode", and treat it like a mass sotrage device.  

Like @trent.josephson said - the USB spec is not designed or intended to do this, and that's at the hardware level.  I wouldn't expect something like that to be easy to hack, but I could be wrong. Two of the 4 conductors are for 5v DC power, (and the other two are for signal), so you'll definitely want to take that into account when you wire your gender-bender. (ie. don't connect +5 DC to +5 DC. . . ).

---

### Post by shinkstor on 2012-07-20
Thanks for all of this info guys! 
I am particularly trying to find some exploits in USB drivers in consumer electronics in order to do a presentation at a small security convention. 
I don't normally dwell in hardware, so I am just trying to broaden my horizon.

Thanks again guys!

---

### Post by taggalucci on 2012-10-16
Hi there,

Have you seen this?

[http://travisgoodspeed.blogspot.com.au/2012/07/emulating-usb-devices-with-python.html](http://travisgoodspeed.blogspot.com.au/2012/07/emulating-usb-devices-with-python.html)

---

### Post by ssam on 2012-10-16
USB OTG sockets can act either as a host or device. these are common on phones and embedded devices, so that a phone can act as a mass storage device, or can have a mass storage device plugged in.

the simplest hardware to get you started might be something like a beagleboard [http://elinux.org/BeagleBoard#OTG](http://elinux.org/BeagleBoard#OTG) . Then you will need to look at the USB gadget drivers in the kernel [http://www.linux-usb.org/gadget/](http://www.linux-usb.org/gadget/)

---

