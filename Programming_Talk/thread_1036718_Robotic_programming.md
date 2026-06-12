---
title: "Robotic programming"
date: 2009-01-11
forum: Programming Talk
---

### Post by hoboy on 2009-01-11
what is the best language for robotic programming ?

---

### Post by TheOrangePeanut on 2009-01-11
Basically, whatever language you want to use that also works with the robot.  In my schools CS department, we have a Java robots, Robo-C robots, and a couple robots that can run any language that can import C functions.  I ended up writing my AI project with the Java robot since I already knew Java.

---

### Post by Kilon on 2009-01-12
I was searching for python 3d APIS and I found this by accident. It may interest you. 

[http://pyrorobotics.org/?page=Pyro](http://pyrorobotics.org/?page=Pyro)

---

### Post by slavik on 2009-01-12
LISP was invented for AI programming. :)
But any code that can alter itself is good.

---

### Post by cszikszoy on 2009-01-12
Most microcontrollers have some type of C compiler.  Don't waste your time with python if you want to do robotics programming.  If you're looking to do AI programming, then python may be the correct route.  In the world of microcontrollers, however, there are pretty much two useful languages, C and ASM.

Get yourself a good Atmel development board and start learning how to control the hardware of a microcontroller.  You'd be pretty surprised what you can do with the ADC and PWM circuitry that's built into the Atmega and Attiny uCs.

Atmel also provides a very, very nice IDE for embedded development.  It's windows only, but it works very well in a VM.  It's a great learning tool because it actually has a built in simularot for 90% of the atmel uCs.  You could actually learn how to program a uC without ever buying anything.  But that's not quite as fun... :p

---

