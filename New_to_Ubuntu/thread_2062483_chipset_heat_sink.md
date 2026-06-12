---
title: "chipset heat sink"
date: 2012-09-25
forum: New to Ubuntu
---

### Post by SummerT on 2012-09-25
Can anyone tell me what this means.  I was trying to boot another computer and the screen came up with something like chipset heat sink and then turned off.  Can't get it to stay on past that.

---

### Post by mcduck on 2012-09-25
Chipset heat sink is thge piece of metal placed on top of the chipset on your motherboard, used to radiate away the heat the chipset generates.

Without knowing the exact error you got it's of course impossible to say for sure, but based on what you said it sounds like the heatsink is not properly fixed in it's place, is too dusty to work, or it has a fan attached the fan has failed. So the chipset is overheating and the system turns itself off to avoid any damage.

While it's not too complicated thing to fix yourself, based on the fact that you asked what chipset heat sink is I'd recommend taking the computer to some repairs shop... :)

---

### Post by newb85 on 2012-09-25
+1 on McDuck's advice.

---

### Post by SummerT on 2012-09-25
Thanks.  If you can describe what part to get and if you know how to do it, I think I can figure it out with your help.  I remember the error said that it wasn't detected. And it shut the system down.
 
I'm not as slow a learner as I may appear to be. :)

---

### Post by Wim Sturkenboom on 2012-09-26
Have a look at your motherboard; do you see any fans? If so, you will probably see one that's not turning when you power the system up.

Else look at the heat sinks. They usually are pieces of metal with some fins. See e.g. the image at [http://en.wikipedia.org/wiki/Heat_sink](http://en.wikipedia.org/wiki/Heat_sink)

Note that the passive one is still relatively big; you might find ones that are only 5mm thick like the one next to the sata connectors (right top) on [this board](http://www.asrock.com/mb/photo/Angle/H61M-VS%28m%29.jpg). They're also often 'painted' in fancy colors.

---

### Post by SummerT on 2012-09-26
Thanks wim.
 
so what am I buying and where am I putting it?
 
the pic links are very helpful

---

### Post by shreepads on 2012-09-26
What motherboard are you using and does the message say the chipset or the chipset fan is 'not detected'? Is there an error code displayed?

Can you look at your motherboard manual, locate the chipset on the board and figure out if there is a fan on the chipset or not? If yes, does it start spinning the moment you power on the computer?

Most likely explanation is that the chipset is overheating because of a non functional fan or the heatsink may be unseated (if there is no fan on the chipset)? If the former then a new fan should do the trick, if the latter than you need rubbing alcohol, cotton buds and something like Arctic Silver 5...

If the chipset itself is not detected then you may have bigger problems and a trip to a repair shop is indicated...

---

### Post by SummerT on 2012-09-26
not sure of the motherboard.  the message says Heatset chip not detected.  system shutting down or something.  it does start spinning immediately and fairly loud.

---

### Post by SummerT on 2012-09-26
The exact error states:
 
Alert! Chipset heat sink not detected. System failed.

---

### Post by shreepads on 2012-09-27
> **SummerT said:**
> The exact error states:
 
Alert! Chipset heat sink not detected. System failed.

A quick google search on the error message gives:

[http://news.sequimpc.com/dell/dell-dimension-4600c-heatsink-alert-chipset-heatsink-not-detected-system-halted/](http://news.sequimpc.com/dell/dell-dimension-4600c-heatsink-alert-chipset-heatsink-not-detected-system-halted/)

And from the Dell support site:

[http://support.dell.com/support/edocs/systems/ws530/en/ug/html/2codes.htm](http://support.dell.com/support/edocs/systems/ws530/en/ug/html/2codes.htm)

Suggest you go to a repair shop...

---

### Post by SummerT on 2012-09-27
it's not something I can do myself, you feel?

---

### Post by shreepads on 2012-09-27
> **SummerT said:**
> it's not something I can do myself, you feel?

I guess you could if you wanted, but have a look at the first link, didn't seem straightforward to me...

Simply put, the heatsink has a clasp which is also an electrical contact that informs the motherboard whether it is closed.

See if you can spot the clasp and check if it is open. If yes, close it and see if the error goes away. Even then a bigger question is why did the clasp open and has the thermal compound between the chipset and heatsink been compromised. If yes, you'll need to remove the heatsink, clean the heatsink-chipset surfaces (e.g. using cotton bud wetted with rubbing alcohol), apply a new layer of thermal compound (e.g. Arctic Silver 5) and close it down (look at the Arctic Silver website for how-tos)..

If the clasp is not open or if closing it doesn't make the error go away you may have bigger problems. I assume it's a Dell desktop, best take it to them for repair in that case...

---

### Post by SummerT on 2012-10-01
Hey everyone.  Ok, so I went out and bought artic silver and placed it on the heatsink after cleaning properly etc.
 
I just got the same error message about heatsink not being detected, shutting down.
 
any ideas?

---

