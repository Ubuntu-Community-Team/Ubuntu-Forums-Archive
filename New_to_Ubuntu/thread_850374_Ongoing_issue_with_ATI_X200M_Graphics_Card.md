---
title: "Ongoing issue with ATI X200M Graphics Card"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by davesalyers on 2008-07-05
Thanks! I finally got the wireless up and running (had to use wicd).
Now I want to work on the graphics for the 3-D and rendering and such.
This is what I have:

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS
200M 5955 (PCIE) (prog-if 00 [VGA controller])
Subsystem: Hewlett-Packard Company Unknown device 3091
Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 16
Memory at c8000000 (32-bit, prefetchable) [size=128M]
I/O ports at 9000 [size=256]
Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
[virtual] Expansion ROM at c0120000 [disabled] [size=128K]
Capabilities: <access denied>

I tried the things on the Ubuntu wiki but have the "MESA" error. I
guess I could "start over". Basic graphics and online are no problem.
Any suggestions?

Dave

---

### Post by NT4usB on 2008-07-05
You don't say what release you're using. If it's Hardy, enable the restricted drivers manager. I've heard it does all the graphics for you.
I use [Envy]("http://albertomilone.com/nvidia_scripts1.html") for all my graphics. Works a treat!
If you try it, read the FAQs first. I'd also recommend using the removal options in Envy to clean up any residual driver stuff before installing.

---

