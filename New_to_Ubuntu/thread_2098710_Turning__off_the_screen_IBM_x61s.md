---
title: "Turning  off the screen IBM x61s"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by blake7 on 2012-12-27
Can I close the lid of my lap top and only turn off the screen?


I once could do this in Ubuntu very easily

---

### Post by audiomick on 2012-12-27
You can do this. Which version of Ubuntu is it? You'll need to mention that so that people can tell you where to look for the setting. It is different depending on which version you are using.

---

### Post by blake7 on 2012-12-29
its 12.10
thank you

and i like is to for the screen to shut down and thats it
when i close the lid


this on the older versions of ubuntu was very simple done in settings 

i can not see it there any more
can you help 
thank you

---

### Post by audiomick on 2012-12-29
I haven't got Unity on a laptop, so I am not sure, but I think it should be 
in system settings: click on the icon to shut down and choose "system settings", and in the "hardware" part there is a thing about power management. Not sure what the english is, it is "Leistung" in German. It should be somewhere in there, anyway.

---

### Post by blake7 on 2012-12-29
yeaaaa
that where it should be 
be looks like some fool some where had the bright idea of getting rid of it

whyyyyyyyyyyyyyyy

any way one step back etc

is there any other way
thank you

---

### Post by steeldriver on 2012-12-29
On my T61p with 12.04 I can do it via System Settings --> Power and then change the "When the lid is closed" dropdown from "Suspend" to "Do nothing" (it turns off the LCD - but audio content keeps streaming)

---

### Post by blake7 on 2012-12-29
saddly that does not work on my laptop

but it makes a lot of sense that
and would explain why they would remove it from the menu

but does not help me saddly

cheers

---

### Post by steeldriver on 2012-12-29
My guess is it's a reflection of what acpi modes are available (or enabled) at the hardware / BIOS level - rather than what "they" have or have not removed

---

### Post by audiomick on 2012-12-29
I booted into 12.04 live USB on my desktop to have a look. There was nothing there, but I half expected that. I believe that the OS somehow "knows" if the machine is a laptop or not, and offers options accordingly. 

I then had a bit of a look in the Ubuntu documentation, and found this.
[http://askubuntu.com/questions/15520/how-can-i-tell-ubuntu-to-do-nothing-when-i-close-my-laptop-lid/15531#15531]("http://askubuntu.com/questions/15520/how-can-i-tell-ubuntu-to-do-nothing-when-i-close-my-laptop-lid/15531#15531")

A little way down, the method for the unity desktop is shown. It is supposed to be where we think, i.e. in system settings> power.

So it seems that the option has theoretically not been removed, but your machine is not offering it for some reason.

---

