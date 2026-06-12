---
title: "Is Java or Mono suitable for writing a Linux daemon?"
date: 2010-10-19
forum: Programming Talk
---

### Post by samalex on 2010-10-19
I have a few projects I'd like to tackle, namely a home brew NNTP and Telnet daemon that can run in the background on Linux.  Given I want to do more GUI programming down the road, would using Mono or Java be a decent language for a CLI application that would run in the background for NNTP or Telnet?  I know Java has the overhead of the VM, but what about Mono? 

Thanks.

---

### Post by directhex on 2010-10-19
I know SUSE has some Mono-based daemons, so it should be doable. You can even use the mono-service app to spawn a service using System.ServiceProcess, allowing the same daemon to integrate into Windows' "services" control panel & onto Ubuntu without modifications.

---

### Post by PaulM1985 on 2010-10-19
Mono is the .NET version of a virtual machine.  Similar in the way that Java has the JVM.  So either way you would have a virtual machine running, although I don't know which would be the quickest.

I would recommend using the tool which is best at solving the problem.

Paul

---

### Post by worseisworser on 2010-10-19
> **samalex said:**
> I have a few projects I'd like to tackle, namely a home brew NNTP and Telnet daemon that can run in the background on Linux.

Either would be fine.


> **samalex said:**
> Given I want to do more GUI programming down the road, would using Mono or Java be a decent language for a CLI application that would run in the background for NNTP or Telnet?  I know Java has the overhead of the VM, but what about Mono? 

Thanks.

Still the same; either would be fine; both have run-times or VMs. If that was a problem (FWIW I generally don't think it is) you could write just the UI part of your software in some other run-time/language combination.

---

### Post by directhex on 2010-10-19
If memory footprint is a concern, the Java version would likely be much heavier (since it needs to load the whole classlib into RAM)

---

### Post by Dragonbite on 2010-10-19
It probably will come down to what you are more familiar or comfortable with (Java or C#), though they are similar (but not the same).

---

### Post by worseisworser on 2010-10-19
> **Dragonbite said:**
> It probably will come down to what you are more familiar or comfortable with (Java or C#), though they are similar (but not the same).

Don't forget that the JVM and the Mono run-time supports several languages; not just Java and C#.

---

### Post by Dragonbite on 2010-10-19
> **worseisworser said:**
> Don't forget that the JVM and the Mono run-time supports several languages; not just Java and C#.

I didn't know about JVM, but I know Mono supports additional languages, they just focus on C# (using VB.NET in Mono isn't as much fun.. doable, but not as much fun ;) )

---

### Post by ChurroLoco on 2010-10-19
They will both work great.  I love my my mono though. ;)

---

