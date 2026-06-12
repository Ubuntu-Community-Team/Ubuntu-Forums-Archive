---
title: "When I use ubuntu, My laptop emits strange sounds. Why?"
date: 2015-12-11
forum: New to Ubuntu
---

### Post by Sky_Byte on 2015-12-11
When I use Ubuntu, My laptop emits strange sounds. I can't describe it. 
Can you help me? Thank you very much!

---

### Post by matt_symes on 2015-12-11
Hi

Welcome to the forums :)

> When I use Ubuntu, My laptop emits strange sounds. I can't describe it.
Can you help me?

With a description like that, no-one can help you without the most profound piece of luck. You'll have to supply far, far more information.

> Thank you very much!

You're welcome.

Kind regards

---

### Post by Sky_Byte on 2015-12-11
I can't describe it. But i think that emits strange sounds from hard disk.

---

### Post by matt_symes on 2015-12-11
Hi

Consider this question:

> When I use my car, My my car emits strange sounds. I can't describe it.
Can you help me? Thank you very much! 


How would you help that person ? There are plenty of people who would like to help you on these forums but you'll have to describe the problem in more detail.

> **Sky_Byte said:**
> I can't describe it.

Give it a try. Is it a clicking sound ? A whining sound ?

> But i think that emits strange sounds from hard disk.

Have you taken off the back hard drive plate cover and checked ? Is it the fan ? is it coming from the speakers ?

When exactly does it happen ? As soon as you boot up the laptop ? When the laptop has been running for a while ?

Kind regards

---

### Post by Geoffrey_Arndt on 2015-12-11
Does it sound like Watusi drums . . . . . ??

---

### Post by maglin2 on 2015-12-12
> **Sky_Byte said:**
> When I use Ubuntu, My laptop emits strange sounds. I can't describe it. 
Can you help me? Thank you very much!

If by this you mean to imply that it makes these noises when you use ubuntu, but not when you use windows it may be related to diffrences in hdd power management.

Is the sound a repeated click and whirr (hdd spinning up and down)?

You could try entering into a terminal

```
[COLOR=#0000FF]sudo hdparm -B 254 /dev/sda

[/COLOR]
```[COLOR=#000000] to see if it fixes it. This change is only temporary, and will be lost at next suspend/power off.[/COLOR][COLOR=#0000FF]
[/COLOR]

---

### Post by buzzingrobot on 2015-12-12
I used to hear text scrolling on green phospor screens, back when. Turned out to be a real thing.

When do you hear this noise? Continuous? Intermittent? Is it associated with any specific activity?

How much RAM?  How much swap space? What's your typical mix of running applications?

---

