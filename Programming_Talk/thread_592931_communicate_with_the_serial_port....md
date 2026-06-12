---
title: "communicate with the serial port..."
date: 2007-10-26
forum: Programming Talk
---

### Post by dottedquad on 2007-10-26
Hello all, In my free time I started a project that utilizes a sensor electronics project and a PC to work together.

Here's some background info on what I'm doing. The electronics project calculates the sensors and passes it along to the computer VIA serial port. From there, the computer's software manipulates the data and also sends information to the electronics project to do various processes.

What language will allow me to effectively communicate back and forth VIA serial port on Linux and windows?

-Thanks,
Rich

---

### Post by gradedcheese on 2007-10-26
The easiest/nicest interface I've used (and use regularly) is pyserial, for python.  The Serial module makes this pretty painless and comes with all the examples you need to make things work.  Check it out:

```

sudo apt-get install python-serial

```

[http://pyserial.sourceforge.net/](http://pyserial.sourceforge.net/)
(with examples)

Also your scripts can be cross-platform in that case (I usually don't care, but it's sometimes helpful).

---

### Post by dumbsnake on 2007-10-27
Python?  I guess I haven't really used Python much, but I would think that all the low level libraries for doing that would be written with C in mind.  It seems I ought to learn python one of these days...

---

### Post by gradedcheese on 2007-10-27
most of what's behind python-serial is written in C.  If you do want to do it in C, it's fine, but you will have to manually issue all of the ioctl() calls to the serial port char driver and manage all of the settings, set up the poll/select calls manually, etc.  I've done it, and it's quiet a lot of rather mundane code and very inconvenient,  You can find many examples via google, though I don't think there are any 'libraries' of the python-serial sort to use.  

Anyhow, python-serial is what I always tend to use to talk to embedded systems (data acquisition, communication/control, firmware download, etc) and it works quite well for me.

---

### Post by DavidBell on 2007-10-27
I know you can just open a file called "/dev/tty0" and print to it for serail port, I think you can read from it as well.

Won't get you voltages or anything, just ascii.

DB

---

### Post by dottedquad on 2007-10-27
> **gradedcheese said:**
> The easiest/nicest interface I've used (and use regularly) is pyserial, for python.  The Serial module makes this pretty painless and comes with all the examples you need to make things work.  Check it out:

```

sudo apt-get install python-serial

```

[http://pyserial.sourceforge.net/](http://pyserial.sourceforge.net/)
(with examples)

Also your scripts can be cross-platform in that case (I usually don't care, but it's sometimes helpful).

It's amazing how simple this can be.  Writing text to the serial is all I really need for this project.  I currently work with php and php-gtk and never touched base with python at all.  Will it be a hard transition? Also, can I use this module with pygtk(spelling?)

-Thanks,
     Rich

---

### Post by dptxp on 2007-10-27
I used Visual Basic in Windows for serial communications. If you are not using hardware control and using Tx and Rx only, short pins 6 to 9 of the 9-pin D connector to avoid unnecessary interrupts.

I guess that Gambas can be used in Linux, it is not exactly like VB, but it is sort of similar. I am yet to use it, but it has serial communications.

Gambas is in Add/Remove, so easy to install.

---

### Post by dottedquad on 2007-10-27
> **dptxp said:**
> Gambas is in Add/Remove, so easy to install.

Indeed, that was one of the languages I installed first.  I played around with it for a bit. Although simple, I ended up uninstalling it since I don't care for basic syntax. Even though the microprocessor I'm using utilizes the basic language, I guess I'm still stuck with the basic language for 50% of the project.

I come to realize the languages I prefer are based off the c syntax considering I'm used to the layout, such as pyGTK and/or php-gtk.

-Rich

---

### Post by moma on 2007-10-27
If you choose C/C++ then check the I/O programming guides [here...]("http://www.futuredesktop.org/opportunities.html")
"Serial lib" and "Going Serial" and "s"...

---

### Post by gradedcheese on 2007-10-28
> **dottedquad said:**
> It's amazing how simple this can be.  Writing text to the serial is all I really need for this project.  I currently work with php and php-gtk and never touched base with python at all.  Will it be a hard transition? Also, can I use this module with pygtk(spelling?)

-Thanks,
     Rich

Yes, you can use it with pygtk, I've done that many times for various projects.  Try it.  You'll like python a lot better than PHP ;)

Yes, you can open /dev/ttyS0 and read/write, but it's nice to be able to set at least the baudrate (setserial style), for which it's nasty to manually issue the ioctls, it's nice to read event-style via select() (and py-serial handles it), etc.

---

### Post by duuchung on 2007-10-28
Hi,
I just want to know whether there is any perl equivalent in CPAN to do the same job.

regards,
duuchung

---

### Post by tux21 on 2008-03-08
i would like to use gambas instead of vb for my final year engg. project. so i requiire ur help

its a cardiac monitor with multiple waveforms displayed on one screen from 6 patients . how to use gambas to access serial port like mscomm control in vb and also plot multiple waveforms. plz point in some examples for this. i am using pic controller based hardware for a/d and uart.

---

### Post by SnuShogge on 2008-08-29
me and my friend are trying to send data between computers using laser. 
We don't know much about controlling serial or parallel ports. 

Is it possible to control each pin in the port? For example if i'd want to send a voltage through pin 2-4 and keeping the rest inactive.

any suggestions on how to connect the laser if i'd wish to send large files?
the laser is supposed to twinkle from the voltage in the pins and can therefore only send one bit at a time, which is way to slow and requires more advanced chip sets to store each byte until it is completely sent.

thanks

---

### Post by mujambee on 2008-08-29
> **dottedquad said:**
> Hello all, In my free time I started a project that utilizes a sensor electronics project and a PC to work together.

Here's some background info on what I'm doing. The electronics project calculates the sensors and passes it along to the computer VIA serial port. From there, the computer's software manipulates the data and also sends information to the electronics project to do various processes.

What language will allow me to effectively communicate back and forth VIA serial port on Linux and windows?

-Thanks,
Rich

I've done a lot of this, connecting all sort of laboratory instruments, and we always used C, opening ports as files both in Windows and in Ux (names differ). It was quite straightforward.


Also, you could have a look here: [http://ubuntuforums.org/showthread.php?t=896869](http://ubuntuforums.org/showthread.php?t=896869)

---

### Post by signifer123 on 2008-08-29
> **duuchung said:**
> Hi,
I just want to know whether there is any perl equivalent in CPAN to do the same job.

regards,
duuchung

Device::SerialPort

[http://search.cpan.org/~cook/Device-SerialPort-1.002/SerialPort.pm](http://search.cpan.org/~cook/Device-SerialPort-1.002/SerialPort.pm)

---

