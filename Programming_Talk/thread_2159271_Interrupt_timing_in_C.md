---
title: "Interrupt timing in C"
date: 2013-07-02
forum: Programming Talk
---

### Post by timvanhees on 2013-07-02
I am working on a project where I have to measure time between 2 interrupts on the same interrupt. does anyone have a clue how to do that. I am completely stuck at this point. it is used for speedmeasurement.

---

### Post by Dirich on 2013-07-02
Nevermind, I thought I read C++

---

### Post by dwhitney67 on 2013-07-02
> **timvanhees said:**
> I am working on a project where I have to measure time between 2 interrupts on the same interrupt. does anyone have a clue how to do that. I am completely stuck at this point. it is used for speedmeasurement.

Ask yourself, how does one compute the time delta between two events?

Answer... capture the time of the first event, and then capture the time of the second event.  The delta time between events is time_second - time_first.

How do you know an interrupt has occurred?  Do you have an event (interrupt) handler defined?  If so, capture the time when the handler is called.  I tend to use gettimeofday() when I require lots of precision (microseconds), but unfortunately not all systems offer this level of precision.  What system are you using?

---

### Post by timvanhees on 2013-07-04
I am using a Atmega16-16PU where i am trying to run this program on

---

### Post by trent.josephsen on 2013-07-04
If the system you're working in allows telling time, you'll need to do so using toolchain-specific information. For example, if you're using avr-gcc, I'd expect to find information about accessing the RTC (if the hardware is set up to do so) in its documentation. If not you may need to resort to assembly language.

May I ask why? If you're collecting data, that's one thing, but if you are using the time between interrupts as a concurrency measure (e.g. to avoid doing something twice in a short period of time), you might want to consider using a lock instead.

---

### Post by timvanhees on 2013-07-04
it is used to do speed measurement. the closer those peaks are the faster the vehicle moves. With that calculation I need to controlle a 8bit DAC.

---

### Post by trent.josephsen on 2013-07-04
Real men do controls in analog. :P

I don't have personal experience with ATmega units -- at least, not since my freshman year of college. The datasheet suggests it should be possible (look at page 71, if you haven't already) but that doesn't guarantee you can do it in C (i.e., without dropping to assembly language). Looks like there's no built-in support for a counter of more than 8 bits, so be aware that will limit both your precision and the maximum length of time you can tolerate between interrupts.

Are there any toolchains besides avr-gcc? Is that what you're using?

---

