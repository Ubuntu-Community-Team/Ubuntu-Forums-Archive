---
title: "OS development"
date: 2014-11-25
forum: Programming Talk
---

### Post by Matthew_Harrop on 2014-11-25
I am currently taking a University course (after work) on how to manipulate assembly code and write an OS. 
Its very interesting (If not a little confusing, especially with the Pin calls to the GPIO...) 

Because I am writing just the Kernel of the OS, I was hoping you would all be able to tell me if its possible to run JUST a kernel. Nothing else but the Kernel (Except, of course, the boot loader and BIOS) and what the dependencies of a kernel are. My kernel is written in machine code, so it should have just the dependency of the chip, but I just wanted to check.

Also, how would/should I go about distributing it when I get it to a working stage? 
And would anybody like to try it when I'm there?

I'm writing it on an ARMv6 (The course stipulates use of a Raspberry Pi, because its cheap and the chip is simple)

---

### Post by ofnuts on 2014-11-25
[LIST]
[*]The only purpose of a kernel is to run other programs... you can only demonstrate it works by making it run programs (perhaps  trivial ones: blink led, write to disk...). You can have an inkling that it is not completely dead by making it display a "heartbeat" (another blinking led). 
[*]Distribute via GitHub or else 
[*]Wet blanket time: be realistic, before your kernel is usable by others it will take a long while. Writing a kernel all by yourself is a lifetime project. People will want to run programs so your kernel will have to be associated with development tools. Either you write them too or you make your kernel compatible with existing ones (which means for instance being able to run the executables they produce...). But doing so will take time and why would people use your kernel when they can run the same things on a more proven operating system? To be adopted your kernel will need to have very compelling benefits (memory footprint, speed, real-time capability, hardware support... ). This doesn't mean you shouldn't try. This is something very nice to demo to a potential employer... 
[/LIST]

---

### Post by Matthew_Harrop on 2014-11-26
Well, you've successfully thrown a wet blanket on my dreams there... ;)

So what would you want to see in an OS? 
What are the most desirable features in an OS that are not currently catered for?

---

### Post by SagaciousKJB on 2014-11-26
Didn't Linus start Linux off as a clone of Minix?  Then people on mailing lists wanted it because they couldn't run Minix and then it just ran from there?

---

### Post by ofnuts on 2014-11-26
> **SagaciousKJB said:**
> Didn't Linus start Linux off as a clone of Minix?  Then people on mailing lists wanted it because they couldn't run Minix and then it just ran from there?

Yes, but a the time there was nothing else, while now there are several Linux distros for the Raspberry alone.

---

### Post by ofnuts on 2014-11-26
> **Matthew_Harrop said:**
> Well, you've successfully thrown a wet blanket on my dreams there... ;)

So what would you want to see in an OS? 
What are the most desirable features in an OS that are not currently catered for?

Given the availability of several Linux distros, I would aim for something that standard Linux doesn't do well: real-time. The Raspberry could then become a super-Arduino.

---

### Post by Matthew_Harrop on 2014-11-26
> Given the availability of several Linux distros, I would aim for  something that standard Linux doesn't do well: real-time. The Raspberry  could then become a super-Arduino.

By real time I am assuming you mean real time data processing? 

What other features would you want in an OS?

---

### Post by ofnuts on 2014-11-26
Actually real-time event processing. If something happens (even to which user code subscribes/waits) the user code will be called within X microseconds. This has implications on task switching, memory swapping, etc...

---

### Post by Matthew_Harrop on 2014-11-26
Why is that not handled very well in Linux/Windows?

---

### Post by flaymond on 2014-12-06
Well, for me. I will say it straight forward. We want an OS that not like others, but more improvement. Not like vulnerable to malware, Closed-Software and expensive OS like Windows. Nor, like lack of compatibility and lack of very good softwares like Linux. Just create something that not exist...***yet.***
That would be the best attraction to everybody. That's a human nature. Humans love something new and something better. ;)

---

