---
title: "System Freezes When Changing Monitor"
date: 2013-10-01
forum: New to Ubuntu
---

### Post by Prime624 on 2013-10-01
I have Ubuntu 12.04 installed dual-boot with Win7 on my Sony VAIO laptop. I usually have it hooked up to a monitor, and I have it set to not do anything when I close the screen. When in Windows, it automatically checks if there is a monitor to use when I shut the screen, and uses it. In Ubuntu, it freezes the computer, where only the mouse moves, but doesn't do anything. Why is this happening, and how can I fix it?

---

### Post by Prime624 on 2013-10-03
Bump.

---

### Post by DuckHook on 2013-10-03
Ubuntu may sense the act of closing the laptop lid as the signal to either go into sleep mode or even to suspend. What happens when you open the lid back up? What are your power settings? Go into System Settings>Power and make sure that "When the lid is closed" option is set to "Do nothing".

---

### Post by Prime624 on 2013-10-03
> **DuckHook said:**
> Ubuntu may sense the act of closing the laptop lid as the signal to either go into sleep mode or even to suspend. What happens when you open the lid back up? What are your power settings? Go into System Settings>Power and make sure that "When the lid is closed" option is set to "Do nothing".

Thank you for the reply, but, as I said, [COLOR=#000000]I have it set to not do anything when I close the screen. Re-opening/closing the lid does nothing. I have tried switching workspaces: nothing. I get around it by putting it in sleep, then (un)hooking up to monitor, then waking it up. This does not freeze it.[/COLOR]

---

### Post by DuckHook on 2013-10-03
Ah. I see where I did not entirely understand your initial posting, but understand it better now. Are you trying to "Hot Dock" the monitor? I have never tried this, but would not be surprised if this is either not possible or very unreliable in Ubuntu. I'm no programmer, but I imagine that the act of just un/plugging a central HW component while system is running can only be done with lots of fancy kludges and workarounds. I suspect that such routines either don't exist in Linux, or are in a very rudimentary state. I admit that it's just a guess on my part.

I'm afraid that I'm out of my depth on this one. If you've already found a workaround, is this sufficient?

---

### Post by Prime624 on 2013-10-03
> **DuckHook said:**
> Ah. I see where I did not entirely understand your initial posting, but understand it better now. Are you trying to "Hot Dock" the monitor? I have never tried this, but would not be surprised if this is either not possible or very unreliable in Ubuntu. I'm no programmer, but I imagine that the act of just un/plugging a central HW component while system is running can only be done with lots of fancy kludges and workarounds. I suspect that such routines either don't exist in Linux, or are in a very rudimentary state. I admit that it's just a guess on my part.

I'm afraid that I'm out of my depth on this one. If you've already found a workaround, is this sufficient?

I am trying to "hot dock". It shouldn't be a problem because I have a laptop, and if Windows can do it, then why can't Ubuntu? Just to find out how.

I did kinda find a workaround, but it's very specific and not adequate for me. When I try, I sometimes plug in a USB keyboard before connecting to the monitor, which for some reason waked the computer.

---

### Post by Prime624 on 2013-10-03
Just found out: I can disconnect from monitor while in sleep. Cannot connect to monitor while on at all.

---

### Post by DuckHook on 2013-10-03
> **Prime624 said:**
> It shouldn't be a problem because I have a laptop, and if Windows can do it, then why can't Ubuntu?This does not follow at all. Linux is a completely different OS than Windows and it is a mistake to think of it as just a "free" or a "better" Windows. You may wish to read [this]("http://linux.oneandoneis2.org/LNW.htm") article for the right expectations and perspectives.

I doubt that you can hot-dock Ubuntu the way you can Windows. Some guru might jump in here to correct me, but my expectation would be that Linux's focus on system stability would preclude it from easily implementing measures that allow connecting/disconnecting of monitors, NICs, etc on the fly. Even if you can do it, this would be fortuitous and not by design. However, I admit that I am only guessing and have no real expertise in this area.

You can try Googling for a solution, or waiting to see if a guru notices this thread and gives you a more informed answer.

---

### Post by Prime624 on 2013-10-03
Mac OS supports "Hot Docking" as well. It shouldn't be very difficult, or at the very least shouldn't crash the whole computer. I don't want Ubuntu to be a free/better Windows, but some features should be present in all modern operating systems. Just because I'm on Linux doesn't mean I should have to restart my computer just to present a PowerPoint presentation.

I've been using Ubuntu for over a year, although I've just started to try to make it my main OS. It's proving very difficult. Expecting Ubuntu to connect to a monitor without restarting is not a lot to ask. It's not a Windows thing, it's a laptop thing. If you're saying Ubuntu isn't made for laptops, fine. Otherwise, I have every reason to expect it to work.

---

### Post by shaone on 2014-04-16
I'm having a similar problem with my Lenovo B570: unplugging external monitor whilst running freezes the entire system and I have to do a hard reboot, nothing else gets it running again, which is a real pain in terms of workflow and not very hardware/software friendly.

I also tend to agree with prime624, this seems such a basic laptop 'thing to do' a natural part of daily workflow and in line the nature and use of these machines, not sure why it would not be standard setup?

By no means sending me back on the windows path but probably onwards into mac as my next computer move, unless of course this kind of niggle can be solved.

Best wishes
Sean

---

### Post by shaone on 2014-06-10
Any advances on a solution to this?

Surely it can be done!?

Still experiencing the same issue with Ubuntu 14 on a Lenovo laptop, makes the OS somewhat unviable for use with laptops does it not?

 Is the final answer categorically that 'hot docking' cannot be done whatsoever in Ubuntu?

If some one could explain simply the reason why not it would be very helpful for many I'm sure.


Many thanks
ShaOne

---

