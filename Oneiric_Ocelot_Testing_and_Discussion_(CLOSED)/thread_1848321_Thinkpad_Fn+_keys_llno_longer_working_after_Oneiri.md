---
title: "Thinkpad Fn+ keys llno longer working after Oneiric insta"
date: 2011-09-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by maxxfell on 2011-09-22
Key combinations such as fn+f5 to toggle wireless and fn+f8 to toggle the trackpad worked ootb in Natty. Since I've upgraded to Oneiric they are not working at all. Checking with xev, they seem not to be registering as events.

Not only have these keys stopped working in Ubuntu, they're now not working in the other OS'es on the machine, Win 7 and Arch.

Any ideas for what might be going on and how to fix gratefully considered!

---

### Post by cariboo on 2011-09-22
It sounds like you have a defective keyboard, if the keys don't work in other OSs too.

---

### Post by lucazade on 2011-09-22
yep, if don't work in other os it is probably an hw issue.

anyway try to see if it is acpi related in oneiric.. start 'acpi_listen' in terminal and press Fn combinations.

---

### Post by maxxfell on 2011-09-23
Thanks for the responses. I might have thought the keyboard was defective too, at first, but it clearly wasn't. Was working fine prior to 11.10 install, the Fx keys were working fine without the [Fn mod] after install, and the [Fn mod] was working with the multimedia keys.

After 11.10 upgrade [Fn mod]+Fx key combinations were showing no response in xev or acpi_listen.

I eventually solved the problem without really tracking down what was going on. I booted a SystemRescueCD session from a USB stick. In that session, the Fn+F5 key combo was successfully toggling wireless. When I booted back into Arch and then Windows and then Ubuntu from the HDD, the [Fn mod]+Fx key combo function was restored. I didn't do anything with the SystemRescueCD session other than boot into it. Possibly any other live boot would have worked as well. I tried the boot based on a thread I found in the Arch forum.

So all is working OK now, but I have no clue as to why it stopped working for a while.

Sorry about the thread title, by the way. Typo because I couldn't turn the touchpad off!

---

### Post by lucazade on 2011-09-23
> **maxxfell said:**
> Thanks for the responses. I might have thought the keyboard was defective too, at first, but it clearly wasn't. Was working fine prior to 11.10 install, the Fx keys were working fine without the [Fn mod] after install, and the [Fn mod] was working with the multimedia keys.

After 11.10 upgrade [Fn mod]+Fx key combinations were showing no response in xev or acpi_listen.

I eventually solved the problem without really tracking down what was going on. I booted a SystemRescueCD session from a USB stick. In that session, the Fn+F5 key combo was successfully toggling wireless. When I booted back into Arch and then Windows and then Ubuntu from the HDD, the [Fn mod]+Fx key combo function was restored. I didn't do anything with the SystemRescueCD session other than boot into it. Possibly any other live boot would have worked as well. I tried the boot based on a thread I found in the Arch forum.

So all is working OK now, but I have no clue as to why it stopped working for a while.

Sorry about the thread title, by the way. Typo because I couldn't turn the touchpad off!

glad you solved.. don't worry about typos in thread title.
(there are other threads where I need a Rosetta Stone to decrypt! uh oh)

---

