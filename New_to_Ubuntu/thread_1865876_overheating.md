---
title: "overheating?"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by Jmob on 2011-10-20
I'm having an issue with my T500 overheating when the CPU scales up.  Generally, this will be something graphical, and it causes, of course, ubuntu to shut down.  

At idle, it will run 45-55 degrees C.  However, load will quickly push it up over 80+.  Some forms of graphical load will very quickly push it to the shutdown threshold (though not all--most flash stuff doesn't do this, though I've found a few.  However, I put on an old game boy emulator just for kicks, and the few inches square of graphics knocked out the box in a matter of maybe 10-20 minutes or so.)

So, I'm not getting a clear sense of the problem.  I'm running xsensors right now, with one tab open (this one) in firefox, and deja dup doing a backup.  With this load, xsensors is hovering at 85 c for the first item.  Fan is hovering at 3039 rpm.  The bar beneath the fan sensor seems to indicate it could go faster, but it never does much more than that.  I don't know if that's the fan or the gauge.

Notably, the only item that increases is temp1, which appears to be the cpu.

I have an ATI video card, but I'm currently running only integrated graphics in the bios.  This problem was worse when discrete was turned on.

I did a quick spot check on the fan region by lifting the keyboard and blowing it out with some spray duster.  Didn't get much out, and the fan area didn't look clogged, nor did the rest of the inside, though I didn't dig all the way down to the fan spindle.

Can anyone offer me some direction on this?

---

### Post by LinuxFan999 on 2011-10-20
Open the laptop, remove the CPU heatsink, spread some new thermal paste on the CPU (a thin layer), then place the Heatsink back on the CPU and close up the laptop.

I reccomend Arctic silver 5 thermal paste, which you can find online at sites like newegg.

You should also use a thermal paste remover to remove the old thermal paste.
Thermal paste removers can also be found online.
Make sure that the heatsink is secure when you're finished.

---

### Post by LinuxFan999 on 2011-10-20
Don't forget to apply thermal paste to the GPU too.

---

### Post by Jmob on 2011-10-20
Thanks.  I'd wondered about that.  

Just curious: are you proposing that as the likely solution, or just the most sensible first troubleshooting step?

Also, do you know if this is a Lenovo/Thinkpad/T500 thing, or was I just unlucky?

Edit: and one other thing.  Should my fan be picking up more slack, or is topping out just above 3k rpm normal?  I've had fans with much higher top speeds than that on older laptops.

---

### Post by LinuxFan999 on 2011-10-20
This could be a possible solution.
I think this is an issue with Linux, since others with this same laptop are experiencing this issue under Linux, but not under Windows.
I think that the fan could go over 3000 rpm, but I am not sure.

---

### Post by Jmob on 2011-10-20
I'm almost exclusively running Linux, so I don't have much to compare.  I thought it might be a linux problem.   But it did happen to me once in w7.  I had plugged in a second monitor and was doing some light photo editing at the time, but it was nothing this computer shouldn't have been able to handle.  We're talking brighness/contrast kind of adjusts on single photos.  So, I think it's a broader problem.

I just found out that I'm still covered under an extended warranty (hooray for school purchases), so I'm just going to take it back to the school and see what they say.  But I'll keep an order for that arctic silver 5 at the ready, just in case.  

Thanks a lot.

---

### Post by d4m1r on 2011-10-20
> **LinuxFan999 said:**
> Open the laptop, remove the CPU heatsink, spread some new thermal paste on the CPU (a thin layer), then place the Heatsink back on the CPU and close up the laptop.

I reccomend Arctic silver 5 thermal paste, which you can find online at sites like newegg.

You should also use a thermal paste remover to remove the old thermal paste.
Thermal paste removers can also be found online.
Make sure that the heatsink is secure when you're finished.


That is a lot of work. What I'd try:

1)Check your BIOS, set your CPU fan to run at full speed 100% of the time

2)Look into a Ubuntu app that lets you adjust your CPU fan from within Ubuntu (don't know if 1 exists but)

3)80c is not normal regardless, call up the manufacturer and report it if its still under warranty...cpu fan might be busted or has been gapped as a result of thermal paste becoming undone (which it tends to do @ extremely high temps).

---

