---
title: "Atmel AVR programming"
date: 2012-07-29
forum: Programming Talk
---

### Post by Media Boot on 2012-07-29
I have two ( for now ) questions:


[LIST]
[*]does Ubuntu support AVRISP mkII ( saw a few quite old threads stating it is a nightmare to get it up and running ) ?
[/LIST]

[LIST]
[*]what is the best ( in terms of functionality ) replacement for AVR Studio ?
[/LIST]

---

### Post by DarkAmbient on 2012-07-30
For question #1, a quick search gave me this, it's old but ***should*** still be valid.

[http://steve.kargs.net/bacnet/avr-isp-mkii-on-ubuntu-hardy/](http://steve.kargs.net/bacnet/avr-isp-mkii-on-ubuntu-hardy/)

---

### Post by MicahCarrick on 2012-08-12
You are not going to find a replacement for AVR Studio. Like many things in Linux, multiple projects comprise the functionality you would often find in many Windows all-in-one applications. 

Most folks write their code in C (with the help of avr-libc) using their favorite text editor or IDE (I use Gedit, the default text editor), compile that code with `avr-gcc`, debug and simulate it with `avr-gdb` and `simulavr`, and program it to the chip with `avrdude`. All of these packages are available in the repos (I think avr-gcc is in there as gcc-avr). This is the same as WinAVR on Windows.

Makefiles are typically used to manage complex AVR projects.

---

### Post by the_unforgiven on 2012-08-13
You may want to take a look at the [Wiring]("http://en.wikipedia.org/wiki/Wiring_(development_platform)") development platform.

---

### Post by studyembedded on 2013-02-24
Hi Guys new to this forum, i wonder if there is an development environment for AVR on UBUNTU platform. If there is one, please suggest me. In case if this is a wrong place to ask this question, please guide me to right forum....thanks!

---

### Post by larytet on 2013-03-19
Just in case if anybody works with Olimex
Ubuntu 12.04 you need only avrdude
and you do something like this
```
avrdude -V -p m64 -c stk500v2 -P /dev/ttyACM0 -U ~/mbvideo/icard/mk/icard.prog.hex -v 
# Fuse bytes shall be programmed only once on the new card. Be careful about actual values for FUSE. It is better no to touch them at all
# avrdude -V -p m64 -c stk500v2 -P /dev/ttyACM0 -U lfuse:w:0xFF:m -v  
# avrdude -V -p m64 -c stk500v2 -P /dev/ttyACM0 -U hfuse:w:0xD8:m -v  
# avrdude -V -p m64 -c stk500v2 -P /dev/ttyACM0 -U efuse:w:0xFF:m -v 
```
In Windows 

[LIST]
[*]Install driver [https://www.olimex.com/Products/AVR/Programmers/AVR-ISP500/](https://www.olimex.com/Products/AVR/Programmers/AVR-ISP500/)
[*]Install WinAVR [http://www.ladyada.net/learn/avr/setup-win.html](http://www.ladyada.net/learn/avr/setup-win.html)
[*] Command  ```
avrdude -V -p m64 -c stk500v2 -P COM112 -U ecard.prog.hex 
```
[/LIST]

---

### Post by slickymaster on 2013-03-19
> **studyembedded said:**
> Hi Guys new to this forum, i wonder if there is an development environment for AVR on UBUNTU platform. If there is one, please suggest me. In case if this is a wrong place to ask this question, please guide me to right forum....thanks!

[AVR Setup]("http://www.ladyada.net/learn/avr/setup-unix.html")

---

