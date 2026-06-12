---
title: "USB - any way to write raw bits?"
date: 2009-02-13
forum: Programming Talk
---

### Post by Senesence on 2009-02-13
In other words: is it possible to directly set the 4 pins found on a usb port to either a high(1) or a low(0)?

I just want to control a single LED (Light Emitting Diode) with a program, and I don't want to buy another piece of hardware to act as a "middleman" for something so (seemingly) trivial.

PS: I would use the serial port, but my computer doesn't have one.

---

### Post by u497 on 2009-02-13
> **Senesence said:**
> In other words: is it possible to directly set the 4 pins found on a usb port to either a high(1) or a low(0)?

I just want to control a single LED (Light Emitting Diode) with a program, and I don't want to buy another piece of hardware to act as a "middleman" for something so (seemingly) trivial.

PS: I would use the serial port, but my computer doesn't have one.

usbs has 2 data ports ..
and 2 power pins.
so you can use only 1 pins because another pin too is for receiving data. so 1 pin for data transmitting.

---

### Post by Zugzwang on 2009-02-13
> **Senesence said:**
> In other words: is it possible to directly set the 4 pins found on a usb port to either a high(1) or a low(0)?

I just want to control a single LED (Light Emitting Diode) with a program, and I don't want to buy another piece of hardware to act as a "middleman" for something so (seemingly) trivial.


This depends on whether your USB controller supports this. You can only be sure about that by reading its technical documentation. However, the answer is very likely to be "no" - Modern hardware normally doesn't allow such direct access. Even for later versions of the parallel port, this was hardly possible.

---

### Post by Ferrat on 2009-02-13
Well since what you want to control is a singel LED it's really just skipping the dataport and connecting the light to the + and - and the having a program activate/deactivate (turn the light on and off) the USB I would reccon, but you will need to regulate the current with hardware since USB ports (AFAIK) all follow the industrial standard 5V at 500mA but that shouldn't be to hard.

---

### Post by NathanB on 2009-02-13
Do you happen to have an old 80's computer in the attic?  Like a Commodore 64 which contains a TTL port?

[http://en.wikipedia.org/wiki/Commodore_64](http://en.wikipedia.org/wiki/Commodore_64)

[http://en.wikipedia.org/wiki/Transistor%E2%80%93transistor_logic](http://en.wikipedia.org/wiki/Transistor%E2%80%93transistor_logic)

The USB port uses its twisted-pair wires as a conduit to carry a broadcasted signal similar to a radio transmission.  This signal is serial data -- therefore, it will never hold a continuous state.

Hardware is required to intercept a USB transmission and translate the data into some sort of representation via pin voltage status.

---

### Post by Senesence on 2009-02-14
> **Ferrat]Well since what you want to control is a singel LED it's really just skipping the dataport and connecting the light to the + and - and the having a program activate/deactivate (turn the light on and off) the USB I would reccon, but you will need to regulate the current with hardware since USB ports (AFAIK) all follow the industrial standard 5V at 500mA but that shouldn't be to hard.[/QUOTE]

Ah, now that's clever. Is there a special command that can shut down specific usb ports, or will I have to write a C program to do it?

[QUOTE=NathanB said:**
> Do you happen to have an old 80's computer in the attic?  Like a Commodore 64 which contains a TTL port?

Heh, I don't even have an old "90's" computer.

> The USB port uses its twisted-pair wires as a conduit to carry a broadcasted signal similar to a radio transmission.  This signal is serial data -- therefore, it will never hold a continuous state.

Right, but that "radio transmission" is still digital, so on a wire it would have to be represented via distinct voltage levels; I'm thinking that the ability to send a series of predominant lows/highs would be one way to change the state of the LED in some noticeable fashion.

[QUOTE=Zugzwang]Modern hardware normally doesn't allow such direct access.[/QUOTE]

[QUOTE=NathanB]Hardware is required to intercept a USB transmission and translate the data into some sort of representation via pin voltage status.[/QUOTE]

Ok, so let's say that I have a micro-controller that can buffer this transmission: how can I program the usb port on my computer to just send an arbitrary byte (like [11110000], for example)?

Also, what would the micro-controller have to do in order to receive that byte?

I've googled around for documentation regarding these matters, but all I found is some very, very old FAQs and general overviews of the usb system; nothing that explains how one would actually set up the necessary software/hardware to enable transmission of arbitrary bytes on a Linux system.

So, if anyone here can point me to some other sources that go into such practical details, I would appreciate it.

---

### Post by pp. on 2009-02-14
You might consider just sending a continuous stream of all 1s or 0xAAs when you want your LED lit and not sending anything when not. The LED might not be at its brightest, but given that you do not want to use any additional hardware, you might be able to live with that.

---

### Post by u497 on 2009-02-14
there is also some usb to paralel port adapters on current markets.
they are not that expensive neither cheap..
afaik they are arround 15$~ so you can buy one and use it for that stuff.as paralel ports which is good enoug for working with that things.

---

### Post by Ferrat on 2009-02-14
> **Senesence said:**
> Ah, now that's clever. Is there a special command that can shut down specific usb ports, or will I have to write a C program to do it?


Well there should be some program or not very hard to create one, should be a simple way of asking Ubuntu just to turn it off/unmount the usb or something, my usb-webcams LED turns-on/off if used/mounted or not.

---

### Post by Senesence on 2009-02-15
> **pp. said:**
> You might consider just sending a continuous stream of all 1s

How would I do that? That's what I want to know.

[QUOTE=u497]there is also some usb to paralel port adapters on current markets.[/QUOTE]

I know, but I want to know how to use the usb system directly, or at least as directly as possible.

My real goal is to learn by doing a minimal project (like controlling a single LED) from the ground up, and then hopefully move to more complex things from there.

Now, given that I would indeed require additional hardware on the outside to control the LED; would I need to buy some kind of special purpose chip that knows how to "speak" usb, or is this something that I could program myself on a micro-controller (which I would prefer, because then I wouldn't have to buy anything)?

If the latter is true: where is the documentation that describes the minimal software required on both the sender (PC) and receiver (my micro-controller) to send an arbitrary byte?

**@Ferrat**

Yea, I'll look into that, but I would much rather use the data lines.

Thanks.

---

### Post by NathanB on 2009-02-15
You should start your research here:

[http://www.create.ucsb.edu/~dano/CUI/](http://www.create.ucsb.edu/~dano/CUI/)

You may also find these useful:

[http://hackaday.com/category/peripherals-hacks/](http://hackaday.com/category/peripherals-hacks/)

[http://www.parallax.com/Store/Microcontrollers/BASICStampModules/tabid/134/ProductID/300/List/1/Default.aspx?SortField=ProductName,ProductName](http://www.parallax.com/Store/Microcontrollers/BASICStampModules/tabid/134/ProductID/300/List/1/Default.aspx?SortField=ProductName,ProductName)

---

