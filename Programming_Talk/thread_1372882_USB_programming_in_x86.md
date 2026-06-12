---
title: "USB programming in x86"
date: 2010-01-05
forum: Programming Talk
---

### Post by JohnnySage50307 on 2010-01-05
Hello All!

So, I searched the internet for hours and I couldn't find any real information.  The university I belong to teaches the low-level mechanics of RS232 serial communications, however to be a lil more valuable in the marketplace, I'd like to learn the x86 assembly mechanics of USB interactions.  For instance, I know USB 2.0 supports an array of speeds, therefore I assume there must be some value which must be set on the port which indicates the mode of operation (correlates to having to set the baud for a RS232 port).

Any sample code is highly appreciated!

---

### Post by chewearn on 2010-01-05
You can find a lot of info here:
[http://www.usb.org/developers](http://www.usb.org/developers)

Beware: you will quickly find that the USB interface is significantly more complicated compared to RS232.

---

### Post by JohnnySage50307 on 2010-01-05
I checked there first, but USB.org has a lil too heavy on the electrical engineering focus and it's difficult to find any sample code without pouring through the mountains of documentation beforehand.

Thank you for the help though!  Anyone else?

---

### Post by akashiraffee on 2010-01-05
Presumably you want to work with** the device drivers for the USB hub**, which is kernel space programming.

Here's a short guide to give you an idea about kernel modules, it is slightly out of date tho:
[http://www.linuxtopia.org/online_books/Linux_Kernel_Module_Programming_Guide/index.html](http://www.linuxtopia.org/online_books/Linux_Kernel_Module_Programming_Guide/index.html)

I know the 2nd Edition of "Linux Device Drivers" is also free on line.

Just be warned, this is not a trivial task and the online resources are limited.

---

### Post by WitchCraft on 2010-01-05
How can I develop my first USB application without having some sort of easy USB device?

---

### Post by not_a_phd on 2010-01-05
For some relatively up to date info on USB programming in Linux: Linux Device Drivers 3rd edition is available online at: [http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/)

Chapter 13 addresses USB devices and how they are dealt with in the kernel.

For a sample device, I would recommend studying the kernel drivers written for your favorite mouse or joystick.

---

### Post by chewearn on 2010-01-06
> **not_a_phd said:**
> For some relatively up to date info on USB programming in Linux: Linux Device Drivers 3rd edition is available online at: [http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/)

Chapter 13 addresses USB devices and how they are dealt with in the kernel.

For a sample device, I would recommend studying the kernel drivers written for your favorite mouse or joystick.

Thanks for the tip! ):P I didn't know the book has been updated to Ed 3. :mrgreen:

---

### Post by JohnnySage50307 on 2010-01-06
Again, I'd like to thank everyone for your help!

Saddly, no, I'm not looking for design of a device driver per se...

The reason is that my university teaches a Computer Interfacing course that only focuses on RS 232 Serial Communications--ancient stuff compared to the market demand.  The class was recently canceled because of the untimely passing of the lecturer.  As a new graduate student, I'm talking to the head of my department about reopening the course, but structuring it to fit current technological trends.  The only thing that I know is an absolute requirement is that there has to be a great exposure to x86 assembly for atleast that portion of the course (I also intend on instructing about network interfacing and GUI design).

As for kernel space device drivers, I know about the layering of drivers and how to simply design a driver which communicates with the corresponding /dev port.  Ultimately, in the end, the students MUST know what are the operations the processor must accomplish in order to initialize, open, and close a USB communication on an x86 architecture.

Again, thank you all for your help!!  I'll continue to look a little deeper into USB.org's documentation, however any sample code is highly appreciated!

P.S. Yes, I know in my first post I mentioned a desire to "be more valuable in the marketplace".  While this is still very true, I also want to extend this added knowledge to other students.

---

### Post by leblancmeneses on 2010-01-06
I think learning about compilers work by building mono on arm would be real world experience also.  Besides interfacing with real world on arm device. (DIO/ADC/TPU/SPI/EEPROM/...ect)

there is a book on amazon.com that builds a computer start to end they have a java simulator for a graphic display. (examin stack/registers ect) - read partial of the book (google reviewed it in a video)

for usb drivers:
[http://osrfx2.sourceforge.net/](http://osrfx2.sourceforge.net/)

---

### Post by JohnnySage50307 on 2010-01-06
> **leblancmeneses said:**
> I think learning about compilers work by building mono on arm would be real world experience also.  Besides interfacing with real world on arm device. (DIO/ADC/TPU/SPI/EEPROM/...ect)]

The University of Pittsburgh's Computer Engineering curriculum is all about designing systems from start to finish.  The class I'm trying to update is supposed to focus on these communication protocols.  For example, ultimately, each of your USB devices contains an embedded computer of some sort.  It is through this computer we communicate to another "host" computer (for lack of better terminology).

The primary interests of this course are the exact x86 processor interactions with the system bus and USB controller block.

---

### Post by NathanB on 2010-01-07
You should consult the Operating System development wiki:

[http://wiki.osdev.org/Main_Page](http://wiki.osdev.org/Main_Page)

...and ask your questions in the OS-Dev newsgroup:

[http://groups.google.com/group/alt.os.development/topics?hl=en&lnk=rgh](http://groups.google.com/group/alt.os.development/topics?hl=en&lnk=rgh)

---

