---
title: "Live USB Ubuntu (screen?) fails to restart after suspend"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by wigout on 2012-09-08
Hello All-
I have a laptop that I can't install a hard drive in - a connector is broken of some sort.

All else works well & has a great battery life, so I am using a live usb with persistence with the laptop.

All is good enough except for suspend.

Here's the scenario:
Choose suspend
Laptop suspends
Press a button
Things happen (fan whirs, some lights come on- looks/sounds/smells as if it is on
Screen is black/not on
I try 8000 keystroke combinations to wake it
Nothing works
I press and hold power button to shut it off

To clarify about the screen being "black/not on"- 
it's black- definitely not back lit
I have left it alone in that state for over 20 minutes with no change

I have searched the forums and tried a couple of solutions proffered for others in similar situations with no love (stuff about killing the xserver and a couple of esoteric to me bits with startup scripts- it was a scattershot attempt that I've lost the references too (I apologize for that))

One detail that seemed different in my case is that I am running a live usb with persistence- pretty much all the other cases involved regular old hardrive installed ubuntu.

So, one question for experts I have is- is a live usb ubuntu with persistence (running on a laptop) capable of suspending? Does the usb nature or persistence mess stuff up?

All other input welcome.

---

### Post by anewguy on 2012-09-08
I honestly don't know if a persitent USB installation has a swap file or not, and I think the type of suspend or hibernate you are talking probably requires a swap file larger than the physical memory size.

---

