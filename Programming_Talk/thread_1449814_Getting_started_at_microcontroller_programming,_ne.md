---
title: "Getting started at microcontroller programming, need help"
date: 2010-04-08
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2010-04-08
I know absolutely nothing about microcontrollers, but I can write software in C, Python and Java. I want to learn about microcontrollers, electronics and assembly.

It seems to be that there are free open-source C compilers (and emulators) for only few chips. I don't want to buy a random chip because I might need wine/windows to be able to program it.

I have read that AVR is the best. Free C compiler for Linux, lots of memory and smart architechure. So I will buy an AVR chip. What microcontroller, components and devices should I buy to get started?

Also, my laptop doesn't have JTAG, SPI, TWI, UART, USART or USI connectors. Just USB, bluetooth and infrared. But no drivers for infrared so it's useless. How to build a thing that lets me use USB for programming?

I can get anything listed on these pages: _[www.farnell.com](www.farnell.com)_ and _[www.elfa.se](www.elfa.se)_. And also all kinds of resistors, transistors, LEDs, and the basic stuff.

---

### Post by MindSz on 2010-04-08
Usually when you buy a micro IC you can get the programming suite from the same people. This suite can be connected to your PC through parallel, serial, and/or USB port.

First, you need to know what kind of IC you want. How many input/output pins, if you want internal/external crystal for the CLK signal, serial communication, etc.

At work, I use a PIC18F252 from Microchip Technology Inc. and I had to buy its programming suite (software + hardware) to be able to program it.

---

### Post by gvoima on 2010-04-08
I'd suggest that you start with AVR 8-bit RISC microcontrollers, a basic atmega32 (or 16), as these and the boards for those are fairly cheap and common.
e.g. this one [ATMega Control Board]("http://www.avrfreaks.net/index.php?module=Freaks%20Tools&func=viewItem&item_id=482")
(btw. that site will be your best friend in the future, so bookmark it ;))

A test board like this has all the things you need to get started.
I wont get into detail what properties it has. But it's highly recommended that you get a book for starting programming with micorcontrollers, because they often cover the hardware part very well and more important the terminology.
For example how to set up a basic switch and make the code recognize it, they go through what different scenarios are eligible, using a pull-up resistor or not, and does the controller have a built-in resistor etc. (just for reference)

Then what you need is a programmer. A programmer is the device that then sends/writes the compiled binary to the controller.
There are many of these supporting many different devices, but for you i suggest a basic usb programmer to get started.
I use a noname usb programmer which works with the avr910 config, they often are very much alike.

Here's one for starters [AVR910 USB ISP Programmer]("http://www.avrfreaks.net/index.php?module=Freaks%20Tools&func=viewItem&item_id=941")

Linux has very good tools for avr.
The GNU compiler has a derivant avr-gcc which is the mostly used one these days, likely the only one if we exclude some proprietary compilers.
Then there's avrdude that uses your programmer to write the data to the avr (uisp is a derivant from dude and not so often updated these days, so I strongly suggest you use avrdude.)
And then you need the standard C library for Atmel AVR 8-bit RISC microcontrollers.

These are the basic three things you need to get started.

And to get acquainted with avr c-librarys there's a online manual here [AVR Libc]("http://www.nongnu.org/avr-libc/")


And the tools you need to get started with all of this, is in the repositories.
```
apt-get install gcc-avr gdb-avr avr-libc binutils-avr avrdude
```


And now when you learn the basics and go through all the forums etc. you get to know what kind of other controllers are out there. But starting with avr atmega family is a safe bet, because it is so widely used by amateurs out there.

This is a wonderful hobby and I hope you have fun learning :)

---

### Post by DrMelon on 2010-04-08
Buy an Arduino kit. You can get kits that include breadboards and a ton of wires. The Arduino is fully self-contained, comes with its own IDE and connects to the PC via USB. I've seen literally hundreds of projects use these, and they're fairly cheap. You can get beginner kits, and I strongly advise you to get one.

---

### Post by gvoima on 2010-04-08
Oh and forgot to mention.

You don't need an IDE for this, just use your favorite editor.
But, a good one that I started to like the most, is Eclipse with the AVR Eclipse Plugin.
Then there's code::blocks, I personally didn't like it.
AVR Studio is an IDE form Atmel, but it's windows only afaik. But there's a pdf at avrfreaks that uses wine to get it working.


And if anyone has some good beginners tutorials, or something to add or correct, please do so :)

---

### Post by crazyfuturamanoob on 2010-04-08
Thanks for the replies.


I want to generate a vector image on my PC with a script, then build a robot to draw that image on A4 paper, and write some software to command that robot.

The robot is going to have 2 motors for moving around, a pencil, one motor to raise/lower the pencil, and a cable to PC, where the instructions come from.

[SIZE="1"][COLOR="Gray"](Or I could use bluetooth instead of a cable, so I could write the PC-side software in Java and port it to JavaME and control the robot using my mobile phone, but that might make it way too difficult)[/COLOR][/SIZE]

Is it very difficult to make a such robot? If so, maybe the first project will be just a LED-show or something like that.


Arduino uses "Arduino programming language", according to the Arduino front page. I don't want to spend time on learning a language that works on only one platform!

ATMega32 looks total overkill, in both features and size. I was thinking of this: _[http://fi.farnell.com/atmel/attiny13v-10pu/8bit-1k-flash-mcu-dip8/dp/9171576](http://fi.farnell.com/atmel/attiny13v-10pu/8bit-1k-flash-mcu-dip8/dp/9171576)_ (it costs just 2,83 &#8364;)
[img]http://fi.farnell.com/productimages/farnell/standard/42268235.jpg[/img]

There are hundreds of AVR chips with 8 pins. They look exactly the same. I don't see a difference. Can you tell me why this one is good or bad?

If I need only one pin per motor, I have 5 pins for the cable. USB has data +/-, 5V and ground. So a 8-pin chip should be enough, right?

But if 64 bytes of RAM is not enough for USB driver, I might get the ATMega32 instead (external LCD from old phone would be so cool).

[SIZE="1"]BTW I don't use IDEs. They tend to have lots of useless junk, which makes them sluggish. I use *Scite + Terminal + File browser*.[/SIZE]


Edit: V-USB needs 128 bytes RAM, that one is not good.

But this one looks the same and has 256 bytes of RAM: [http://fi.farnell.com/atmel/attiny45-20su/8bit-mcu-4k-flash-5v-smd-soic8/dp/1288353](http://fi.farnell.com/atmel/attiny45-20su/8bit-mcu-4k-flash-5v-smd-soic8/dp/1288353)

---

