---
title: "What are hardware drivers? How to make them?"
date: 2009-01-28
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-01-28
I have heard, that long time ago people made their hardware drivers themself.

What are they? What do they do? How to make them? Is it difficult?


I know C and Python, and I want to learn making the drivers.

---

### Post by jimi_hendrix on 2009-01-28
> **crazyfuturamanoob said:**
> 
I know C and Python, and I want to learn making the drivers.

C, ASM, and Forth are the common driver languages i believe...

same question...i want to know how crazy i would be to write my own network card driver...thanks for this post OP

---

### Post by Zugzwang on 2009-01-28
@OP: Go to your local university library and grab a book like "Essential Linux Device Drivers (Prentice Hall Open Source Software Development)" - That topic is quite advanced.

---

### Post by Simian Man on 2009-01-28
It is difficult to write good drivers even for professionals who have all of the specs and have access to the engineers who designed the hardware.  Reverse engineering the hardware and trying to write drivers from that is going to be prohibitively difficult for even very good programmers.

---

### Post by NathanB on 2009-01-28
The hardware manufactures themselves are the people who are in the best position to write Linux ports of their drivers.  If you want a Linux driver for your favorite peripheral, join the chorus to put pressure on the vendor to produce these.

---

### Post by crazyfuturamanoob on 2009-01-28
ATM there isn't any devices I have that lack drivers for Ubuntu.

And I'm not reverse-engineering anything. I just want to learn the basics of writing drivers.

---

### Post by NathanB on 2009-01-28
I recommend joining the **sane** and **libsane** projects.  They have absorbed the old "parallel port library" projects to provide better support for older flatbed scanners.  Currently, there is support for a majority of devices, but there is **always** room for improvement.

**libusb** is another project in need of attention:

[http://www.linux-usb.org/](http://www.linux-usb.org/)

---

### Post by crazyfuturamanoob on 2009-01-28
But I can't help without **any** knowledge of drivers. I just know they are needed to make devices working.

---

### Post by doojsdad on 2009-01-28
A pretty advanced topic. You need the specs to the hardware that you are writing the drivers for, for one thing. An example would be to get a cheap microcontroller [[COLOR="Blue"]development board[/COLOR]]("http://www.futurlec.com/CP68HC11DevBrd.shtml") and then get a simple 12-key keypad, like this one [http://parts.digikey.com/1/parts/961005-keypad-12-key-blk-front-pnl-mnt-96ab2-152-f.html](http://parts.digikey.com/1/parts/961005-keypad-12-key-blk-front-pnl-mnt-96ab2-152-f.html)

Just connecting the keypad to the microcontroller's interfaces isn't going to do anything. You need to write software, ie drivers, that you load onto the microcontroller that looks for the keypad interrupts/signals and does something with them. This is taught at the senior level in electical engineering curriculums.

---

### Post by jimi_hendrix on 2009-01-28
> **doojsdad said:**
> This is taught at the senior level in electical engineering curriculums.

i thought i was insane

---

### Post by crazyfuturamanoob on 2009-01-28
> **doojsdad said:**
> A pretty advanced topic. You need the specs to the hardware that you are writing the drivers for, for one thing. An example would be to get a cheap microcontroller [[COLOR="Blue"]development board[/COLOR]]("http://www.futurlec.com/CP68HC11DevBrd.shtml") and then get a simple 12-key keypad, like this one [http://parts.digikey.com/1/parts/961005-keypad-12-key-blk-front-pnl-mnt-96ab2-152-f.html](http://parts.digikey.com/1/parts/961005-keypad-12-key-blk-front-pnl-mnt-96ab2-152-f.html)

Just connecting the keypad to the microcontroller's interfaces isn't going to do anything. You need to write software, ie drivers, that you load onto the microcontroller that looks for the keypad interrupts/signals and does something with them. This is taught at the senior level in electical engineering curriculums.

Why do I need a 80$ devboard just to run some software? Can't I run the software on my laptop?

---

### Post by doojsdad on 2009-01-28
I was giving the simplest example that crossed my mind. You sounded like you weren't sure what you wanted to do so I wanted to give you an example. What did you have in mind?

---

### Post by crazyfuturamanoob on 2009-01-28
I want to learn making drivers for different devices, like that keyboard with 12 keys.

But if making drivers needs some 80$ devboards, I'm not interested.

---

### Post by kavon89 on 2009-01-28
Hardest part is knowing absolutely everything about the piece of hardware, what it connects to and how it will communicate, and the devices it will interact with. Then a couple very low level programming languages to wrap it all together.

Pretty hard.

---

### Post by NathanB on 2009-01-28
>  Originally Posted by doojsdad:
This is taught at the senior level in electical engineering curriculums.
> **jimi_hendrix said:**
> i thought i was insane

Those students tend to earn a pretty decent salary after graduation.  Being a "detail-oriented" person has its plus side!  :)

I don't say "No" to those projects that recruit at $2,000 USD per hour.

---

### Post by NathanB on 2009-01-28
> **crazyfuturamanoob said:**
> But if making drivers needs some 80$ devboards, I'm not interested.

That actually sounds like a reasonable price for an education.

Have you priced university tuition lately??  Be sure to include room & board, student fees, books, lab fees, etc. into your calculations.

"Young people these days... I'll never understand them!"  :)

---

### Post by fiddler616 on 2009-01-28
> **jimi_hendrix said:**
> i thought i was insane
Yeah. My thoughts while reading this went "Cool...sweet...DARNIT...whoa, money..."
--
So I take it that Linus's comment about "Back when men were men and wrote their own device drivers" was grossly hyperbolized?

---

### Post by Sorivenul on 2009-01-28
Quite an advanced topic. If you are looking for some information on Linux device drivers, along with some code to compare your knowledge to I believe some of the following may be decent starting places:
[Writing a Simple USB Driver]("http://www.linuxjournal.com/article/7353")
[Writing device drivers in Linux: A brief tutorial]("http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0%2C0") (PDF available)
[Introduction to Linux Device Drivers]("http://www.mulix.org/lectures/intro_to_linux_device_drivers/intro_linux_device_drivers.pdf") (PDF)

Happy hacking!

---

### Post by crazyfuturamanoob on 2009-01-29
Some people thought I was student.
But no, I'm not a student, I haven't went to university yet. I'm much younger. 
I taught myself C and Python, with no teachers, but this forum.
So I guess I can learn doing drivers myself as well.
> **Sorivenul said:**
> Quite an advanced topic. If you are looking for some information on Linux device drivers, along with some code to compare your knowledge to I believe some of the following may be decent starting places:
[Writing a Simple USB Driver]("http://www.linuxjournal.com/article/7353")
[Writing device drivers in Linux: A brief tutorial]("http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0%2C0") (PDF available)
[Introduction to Linux Device Drivers]("http://www.mulix.org/lectures/intro_to_linux_device_drivers/intro_linux_device_drivers.pdf") (PDF)

Happy hacking!

Thanks! I'll be back on this topic when I have read those.

---

### Post by cmay on 2009-01-29
> **crazyfuturamanoob said:**
> Some people thought I was student.
But no, I'm not a student, I haven't went to university yet. I'm much younger. 
I taught myself C and Python, with no teachers, but this forum.
So I guess I can learn doing drivers myself as well.


Thanks! I'll be back on this topic when I have read those.

yes you did. thats cool . actually for some reason i think you can learn this as well . 
keep up the spirit :)

---

### Post by crazyfuturamanoob on 2009-01-29
Is there any software like usbsnoop for Linux which would listen to USB ports and print the data?

---

### Post by jpkotta on 2009-01-29
> **crazyfuturamanoob said:**
> Is there any software like usbsnoop for Linux which would listen to USB ports and print the data?

Maybe usbmon is what you want?  [http://www.mjmwired.net/kernel/Documentation/usb/usbmon.txt](http://www.mjmwired.net/kernel/Documentation/usb/usbmon.txt)

I didn't see [Linux Device Drivers (3rd ed.)]("http://lwn.net/Kernel/LDD3/") mentioned yet.  I found this book immensely helpful.  There are examples that use common PC hardware (memory, parallel port).  

I've worked on a few dev boards, (at91sam9260ek, omap5912osk, bf-548-ez), but the at91 was my favorite, mainly because the documentation was good.  All of those are rather expensive.

---

