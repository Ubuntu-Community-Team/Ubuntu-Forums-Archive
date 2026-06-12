---
title: "Programming serial port to output specific voltage"
date: 2011-08-13
forum: Programming Talk
---

### Post by wannabegeek on 2011-08-13
Hi all,

I'm working on a personal side project, to make an LED light turn on for about 0.5 sec,  using a script and a serial port. The computer doing this is expendable so I'm not overly paranoid about blowing out internal electronics. I know not to use the +- 15 V  or the 15 V supply pins to power the LEDs.

For now, assume that the output from pin 3 (trans data) has been inverted by a follower so that it is logical 1 at +15 V. 

My current analog circuit idea is to use a sample and hold circuit to maintain the logical 1 signal for ~0.5 seconds or less, which will operate the base of a  transistor that completes a circuit to a bank of D batteries to turn on the LEDs.

I don't know what resource to use to interface the serial port. I found minicom for modems, not sure if that will work. This area of computers is totally new to me.

If you're wondering why I need the short burst of light, it's for a webcam set up to take time lapse pictures,
once every hour, for a week or longer.

TIA !!

wbg

---

### Post by Bachstelze on 2011-08-13
Google gives me this:

[http://yengal-marumugam.blogspot.com/2011/07/serial-port-manipulation-in-c-linux.html](http://yengal-marumugam.blogspot.com/2011/07/serial-port-manipulation-in-c-linux.html)

I haven't read it in detail but it looks good.

---

### Post by wannabegeek on 2011-08-13
Thank you Bachstelz...! Looks like a great start for me...

I was just working on analog circuit and finally got it mostly working...that feels good since I am not an expert.

UPDATE:  I compiled the C program the author gives just to see what happens. It compiled with out a problem.

---

