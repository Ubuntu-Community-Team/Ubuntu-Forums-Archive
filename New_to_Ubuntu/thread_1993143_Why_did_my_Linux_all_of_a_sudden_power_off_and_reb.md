---
title: "Why did my Linux all of a sudden power off and reboot?"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by hanzj on 2012-06-01
Without any notice, my computer rebooted itself. Why did it do that?

---

### Post by 3177 on 2012-06-01
most likely and without further information, your computer overheated.

---

### Post by hanzj on 2012-06-01
1. How can we confirm your hypothesis?
2. What information would you need in order to come to an evidence-supported conclusion?

---

### Post by Paqman on 2012-06-01
Overheating, power supply problem, component about to fail, etc, etc. Could be anything really.

---

### Post by hanzj on 2012-06-01
It could be any thing, you say. No argument there. 
My question is: What is it, of many a thing, that caused this particular reboot?

---

### Post by deadflowr on 2012-06-01
Was it a one shot, or is it a recurring issue?
If it was a one shot, then most likely it is a power issue(and depending on your source of power, not anything you can deal with).
If it is repeating over and over again, most likely it is an overheating, or component failure.
For power issues, if you happened to be plugged in, as opposed to running on a battery, it might have been affected by a power utility glitch.(something, somewhere on your local power grid suffered a break which can cause very quick and dramatic spikes, and drops across the entire grid)
In my experience with overheating issues, systems I've used which overheat usually give me a brief warning message on the intial reboot that the system had to shutdown for stated reason.

---

### Post by Paqman on 2012-06-01
> **hanzj said:**
> 
My question is: What is it, of many a thing, that caused this particular reboot?

Well, we aren't psychic, you'll need to do some investigation and start ruling things out.

First thing I would do would be open the machine up. Look for fluff in your heat sink and vents, check the security of all the power cables, etc. Stress test your machine and watch the temperature. See if you can recreate the fault.

---

### Post by hanzj on 2012-06-01
It was a one-shot. Laptop is plugged in, and I don't have a battery in the laptop.

I don't recall the ceiling light going off.

---

### Post by Cheesemill on 2012-06-01
A glitch in the power could cause your machine to reboot without affecting the lights.
This sounds like the most likely cause to me.

---

### Post by Paqman on 2012-06-01
> **hanzj said:**
> 
I don't recall the ceiling light going off.

Doesn't necessarily have to have been a total loss of power. A short spike or drop in voltage might not show in a light bulb, but might upset electronics. Transient spikes can come from anywhere, appliances like your fridge or lightning strikes miles away. That's why you should use a good surge protector.

It's only one of several options though. Just as likely to be something like a wobbly power plug inside the machine or a knackered solder joint.

---

### Post by Bluenoser81 on 2012-06-01
> **Cheesemill said:**
> A glitch in the power could cause your machine to reboot without affecting the lights. This sounds like the most likely cause to me.

Do you know how this would work? I'm wondering because I thought the power going off/dipping/spiking would be essentially the same as just unplugging your laptop and running on battery. I've had the power go off/flicker many times in winter storms, and the laptop just switches to battery--it doesn't reboot or turn off suddenly.

---

### Post by Cheesemill on 2012-06-01
> **Bluenoser81 said:**
> Do you know how this would work? I'm wondering because I thought the power going off/dipping/spiking would be essentially the same as just unplugging your laptop and running on battery. I've had the power go off/flicker many times in winter storms, and the laptop just switches to battery--it doesn't reboot or turn off suddenly.

From the OP:
> and I don't have a battery in the laptop.

---

### Post by deadflowr on 2012-06-01
> **Cheesemill said:**
> From the OP:

Exactly, having no battery in a laptop can make it even more prone to this, and power glitches can be even shorter in length. Laptops are usually built to use lower resources than say a desktop, but they are usually taxed at a higher rate(ie a laptop runs on, lets say, 19 volts and can consume 100 watts, it'll consume near its capacity, where as a desktop might run on 110 volt and a 400 watt but only utilize 200 watts.) Because the laptop uses lighter resources higher capacity levels it will dissipate faster and in less time and we're talking microseconds.
I also agree with pagman that this is only one of several scenarios, though the one with the highest probability. 

Does that make sense?

---

### Post by haqking on 2012-06-01
> **hanzj said:**
> Without any notice, my computer rebooted itself. Why did it do that?

Cos it lost power ?

cos it powered off ?

Cos you hit the switch with your knee ?

cos your drinking ?

cos your not drinking enough ?

---

### Post by mijdrawoh on 2012-06-01
Good joke. Proves Ubuntu users are so helpful they'll try to answer questions which are impossible to answer.

---

### Post by roton on 2012-06-01
You could try making it happen again by running something like prime95.

---

### Post by inashdeen on 2012-06-01
Wait, which version of ubuntu are U using. if U r using 11.10, chance are this issue is a probable bug. It happens to me few times when I used 11.04 and 11.10, but the problem is totally fix for me on 12.04

---

