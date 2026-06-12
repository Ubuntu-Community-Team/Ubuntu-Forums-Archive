---
title: "Adding RAM"
date: 2012-04-02
forum: New to Ubuntu
---

### Post by Foobarz on 2012-04-02
Ok so this is what happened:

I have a laptop with 2gb ram. I put another 2gb ram chip in the second slot on my laptop. My laptop would not go into bios. I turned it off, and put a 512 mb ram chip in the second slot. My laptop turned on, and everything went smoothly, but GNOME's system monitor says that I only have 2 gb ram. Is 2gb the limit for 32bit systems?

---

### Post by zandman on 2012-04-02
Usually there are special keys you need to press before/during/after pressing the "On" key on laptops.. Did you try that?
As an example: i have a Dell D830 and to go into bios for that you have to follow the steps below.
Viewing the System Setup Screens

    Turn on (or restart) your computer.

    When the DELL&#8482; logo appears, press <F2> immediately.

---

### Post by Foobarz on 2012-04-02
nonon i think you've misunderstood what i was saying. Is there a limit to the amount of ram you can add to a 32 bit machine?

---

### Post by rattskjelke on 2012-04-02
I think it depends more on what type of processor, motherboard, how many memory slots you have, and what capacity size of memory sticks are manufactured in the pysical size that the motherboard takes.
I would not think it would be less than 4GB on anything recent.

See [http://en.wikipedia.org/wiki/RAM_limit](http://en.wikipedia.org/wiki/RAM_limit)

---

### Post by zandman on 2012-04-02
Good, so what type of laptop do you have? Usually you should be able to find maximum ram for it in the documentation. Coming back to the Dell D830 i have: i've put in 2x2GB ram, it only reports 3.2 GB as memory. Still 50% more then i had and good enough for 11.10

---

### Post by rattskjelke on 2012-04-02
You can also run Memtest86+ (I think that's what it's called) on the grub boot menu or any Ubuntu live CD. It is a diagnostic tool that tests for memory problems.

---

### Post by Ms. Daisy on 2012-04-02
> **zandman said:**
> Good, so what type of laptop do you have? Usually you should be able to find maximum ram for it in the documentation. 
+1

You need to check the documentation for your specific computer.  There is a maximum amount of ram it will take and there is a specific type it will take.

---

### Post by westie457 on 2012-04-02
You could also go to the crucial.com website for your country and use their memory advisory tool to find the limits for your machine.

---

### Post by JKyleOKC on 2012-04-02
> **Foobarz said:**
> nonon i think you've misunderstood what i was saying. Is there a limit to the amount of ram you can add to a 32 bit machine?Yes, there is, but it's 4 GB. Actually it will only use 3.4 GB when you put in 4, but it ought to accept the second 2 GB chip. Have you made certain that the new chip was good? RAM chips can easily be destroyed by static electricity when you are handling them.

---

### Post by sammiev on 2012-04-02
> **Ms. Daisy said:**
> +1

You need to check the documentation for your specific computer.  There is a maximum amount of ram it will take and there is a specific type it will take.

+1 again and also note that some ram must be matched with the ram on board.

---

### Post by jerome1232 on 2012-04-02
I've had occasions where rearranging the ram sticks caused it to magically work, I'm not sure if it was simply the act of reseating them or if it really liked the new one in slot 0.

Just driving home even further that this is a harware thing, not a software thing, as suggested reseat the ram, rearrange the ram, double check that it's the correct speed, type, and that your motherboard can handle that much ram. IF all this checks out, it's probably a bad stick, give the manufacturer a call, I'm sure they'll replace it.

---

### Post by RJARRRPCGP on 2012-04-02
> **Foobarz said:**
> Ok so this is what happened:

I have a laptop with 2gb ram. I put another 2gb ram chip in the second slot on my laptop. 

4 GB is the limit for 32-bit systems.  

And 3 GB seems to be a limit for many motherboards (At least with Asus socket 462) made before 2005. 
(Possibly a chipset limitation of Via KT400 and Nvidia nForce2)

2005 and later systems should be able to use 4 GB. And when 4 GB is being used, the OS typically reports a little less, such as 3.2 GB. (Especially 32-bit Windows.)

-> It will definitely show less when using Intel graphics.

---

