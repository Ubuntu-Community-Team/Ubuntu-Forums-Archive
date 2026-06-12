---
title: "Arduino and Ubuntu 11.10"
date: 2011-11-26
forum: New to Ubuntu
---

### Post by WinzenFlyer on 2011-11-26
Hello everybody,

when I saw that the Software Center has the Arduino 0022 IDE now, I was hoping that installation of my Arduino Uno would be as easy as on Windows.

Unfortunately, this was not the case. I installed from the Software Center and when I connected the Arduino by USB, it was flashing the Pin 13 LED and the TX LED was on constantly. The IDE was very slow and when I clicked on "Tools" to set the serial port, it took several seconds until something happened! Then I found only the port "tty0", while when I followed the "Complete Numpties Guide to Arduino on Ubuntu" I could see with dmesg that the Uno was recognized as ttyACM0. (And this option occasionally appeared in the Software, only to disappear again immediately)

I uninstalled the IDE and went according to this blog post: [http://mattgreensmith.wordpress.com/2011/11/24/installing-arduino-0023-on-ubuntu-11-10-oneiric-ocelot/](http://mattgreensmith.wordpress.com/2011/11/24/installing-arduino-0023-on-ubuntu-11-10-oneiric-ocelot/) . Still no success. I then tried what is given in the Arduino Playground:

> - download and install the latest release

- install the compiler (gcc-avr) and the libraries (avr-libc) packages:* sudo apt-get install gcc-avr avr-libc*
- if you use the USB port to dialog, you should add yourself to the group 'dialout' in order to have write permissions on that port: *sudo usermod -aG dialout <myuser>* That also didn't work. What can I do now?

---

### Post by mgreensmith on 2011-11-26
I found a thread where people are complaining of similar issues ([http://www.arduino.cc/cgi-bin/yabb2/YaBB.pl?num=1286088093/34]("http://www.arduino.cc/cgi-bin/yabb2/YaBB.pl?num=1286088093/34")), and it seems that this issue is caused by older (and broken) firmware on the Uno's USB chip.

Looks like the Arduino folks have posted a fix, though.  It requires updating the firmware on the USB chip.  [http://arduino.cc/blog/2011/02/15/fix-to-uno-and-mega-2560-linux-serial-problems/]("http://arduino.cc/blog/2011/02/15/fix-to-uno-and-mega-2560-linux-serial-problems/")

---

### Post by WinzenFlyer on 2011-12-01
Thank you Matt, that seems to be logical and I could try if that works!

---

