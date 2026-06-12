---
title: "How could I create a Python Program to control a fan (without any mircocontrollers)."
date: 2011-04-18
forum: Programming Talk
---

### Post by Zanderist on 2011-04-18
I've come up with a project where I would make a program with Python, to monitor my CPU temp; which will then send a High signal when the temperature high set point is reached, through a USB cable (from the laptop) to the following circuit diagram attached.

 (The inductor attached to the relay is supposed to be the fan). 

It will then loop until the CPU temp has returned to the temperature low point is reached to avoid 'hunting'.

The only problem is that since I'm not going to use any programmable chips, just a logic gate. I would need to tell the program which USB to send the signal too, so I would need to identify the address of the USB port I want to use.  In addition to that I would need to have a real time CPU temp update looping.

Lastly; Which wire from the  USB would I use? Data(-) or Data(+)

So how would I go about doing this?

---

### Post by mdurham on 2011-04-18
I think you should use a parallel port and not USB. A parallel printer port could easily be used for this.

---

### Post by Zanderist on 2011-04-18
> **mdurham said:**
> I think you should use a parallel port and not USB. A parallel printer port could easily be used for this.
Well the thing is, I don't have a parallel port on this laptop. I also don't know (at the moment at least) the holes of a parallel port.

I figure, I could just send a single high signal through the USB.

---

### Post by cgroza on 2011-04-18
Well, in this case, you will need an usb library. Take a look at pyusb. Hope it helped.

---

### Post by mdurham on 2011-04-18
I don't think it's possible to use the direct USB output. Even if it were possible it wouldn't be a good idea as you could damage the laptops internals if you make an mistake with the hardware.
You could get a USB to RS232 converter on ebay for 2 or 3 $$'ss They have settable output lines, maybe there is a USB to parallel converter, I haven't looked.

---

### Post by Zanderist on 2011-04-18
> **mdurham said:**
> I don't think it's possible to use the direct USB output. Even if it were possible it wouldn't be a good idea as you could damage the laptops internals if you make an mistake with the hardware.

Well the only thing I could see damaging the Laptop's internals is that somehow the separate power source for the fan feeds back through the control circuit.

I plan on using the +5v and ground wires to power the control side of circuit, all of which will pass through diodes.

---

### Post by ssam on 2011-04-19
not sure you can just set a pin on a usb port to high. its a serial system so you need to send bytes though it. I guess you could send a continuous stream of 0xFF. also a usb device needs to identify its self to the host by sending its device ID, and needs to be able to acknowledge packets. have a good read of  [http://en.wikipedia.org/wiki/Universal_Serial_Bus](http://en.wikipedia.org/wiki/Universal_Serial_Bus) . really does not look like the sort of think you can do without a micro controller.

plain serial and parallel ports are much simpler. with serial you could just keep sending 0xFF, without worrying about replies. with parallel you can just set a pin high.

a USB to parallel port is there for probably the simplest thing you can use.

next up, if you are interested in electronics, would be to get an arduino, or similar. maybe overkill for this project, but it would let you do fun things like hook up a row of LEDs and you these to display the temperature.

---

### Post by mdurham on 2011-04-19
I've just looked up "usb parallel" on ebay, you can buy a converter for $2

---

### Post by Zanderist on 2011-04-19
> **ssam said:**
> 

next up, if you are interested in electronics, would be to get an arduino, or similar. maybe overkill for this project, but it would let you do fun things like hook up a row of LEDs and you these to display the temperature.

I'm actually thinking about getting the TI launch pad instead of the arduino, it's $4.80, and the Arduino is around $30.
> 
also a usb device needs to identify its self to the host by sending its device ID, and needs to be able to acknowledge packets.
I can't force it to send away?

> a USB to parallel port is there for probably the simplest thing you can use.
 
What I don't like about using parallel for this is that I have a bunch of unused pins, part of my objective is to have everything used (for example:you see 3 nor gates because the CMOS I have, have 3 nor gates within them.)

---

### Post by olddouane on 2011-07-28
> **mdurham said:**
> I think you should use a parallel port and not USB. A parallel printer port could easily be used for this.
:) Easily? Where can I find a decription of this? In Python! Please:P

---

