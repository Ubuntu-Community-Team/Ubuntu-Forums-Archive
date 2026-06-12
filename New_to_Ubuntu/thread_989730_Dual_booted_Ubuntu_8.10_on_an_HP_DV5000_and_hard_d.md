---
title: "Dual booted Ubuntu 8.10 on an HP DV5000 and hard drive light stays on while idle."
date: 2008-11-21
forum: New to Ubuntu
---

### Post by Crow550 on 2008-11-21
My friend has had major issues with his laptop getting viruses and spyware allot. I dunno what he does lol.

Anyways.....
I figured I would let him try Ubuntu as well as partition and dual boot XP and secure it.

When the laptop is idling the hard drive light stays on. I don't know what it's doing. In XP it doesn't do this and will go off when idle. In Ubuntu when a program is loaded it will go off but then when idle it will stay on. Even if Ubuntu just starts up and not even logged in, it will do it.

Is this something to worry about or what? I am gonna give it a battery test and see how long the battery lasts. It usually lasts 2 hours, so if it goes out quicker then I assume the hard drive is getting accessed more? Right?

Update:  Laptop battery lasted about two hours.

---

### Post by Crow550 on 2008-11-23
Help?

---

### Post by Crow550 on 2008-11-24
Problem fixed.... Laptop mode wasn't enabled. I just opened the terminal and typed sudo /etc/default/acpi-support then went to search and laptop and found ENABLE_LAPTOP_MODE and set it from false to true. I figured this out after doing some research and decided to check if it was on.

I don't know why Ubuntu didn't figure out it was a laptop in the first place. I also heard when installing Ubuntu to go into other options and select laptop mode? Why can't it detect a laptop or ask you if your installing it on a desktop or laptop?

---

### Post by chuckyp on 2008-11-24
Did you get longer battery life enabling this mode?

---

### Post by Crow550 on 2008-11-24
Battery seemed to last around 2 hours and 30 minutes.

---

