---
title: "My Installation keeps falling over help!"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by Freakiwombatman on 2008-08-28
I have just installed 8.04. 

On booting, after about 15 minutes it falls over and the screen freezes - I still have keyboard and mouse function but they don't effect anything. The only way I can get out of it is to restart the machine.

I have 512mb RAM and an AMD Athlon XP 2800 processor, dual ATI 128mb video card. 

any help would be gratefully received!!:confused::confused::confused:

---

### Post by nicedude on 2008-08-28
Ok you are going to have to describe this better for someone to help you out. For starters does it start up and work for 15 minutes and then crash? Have you tried updating the system in case it is a problem that is already fixed and you just don't have the newest versions of stuff. Please try updating and also giving a little better description of everything that is occuring, also let us know what brand and model your PC is or what mobo you are using if you built it yourself.

---

### Post by Freakiwombatman on 2008-08-28
This may sound like a stupid question but what is a mobo? I did build the system myself. 

I can boot the system login to ubuntu and then do things for 15mins or so then the screen freezes.

Anyway I shall go away any get some updates, I thought I needed to do that!! Thanks for your reply!

---

### Post by nicedude on 2008-08-28
mobo is geek speak shorthand for your motherboard. Since you say it runs for 15 minutes and then freezes that is pretty strange and one thing that it makes me think is maybe this is graphics card driver related so I would recommend you install envyng-gtk and use it to download a new driver and install it for you and see if that solves the problem.

command to install envyng-gtk

sudo apt-get install envyng-gtk

and then this command to start it up

sudo envyng-gtk

Then just select to install ATI driver and let it do everything for you.

---

### Post by Crafty Kisses on 2008-08-28
Post results of > top

Could be a resource issue.

---

### Post by Cheesehead on 2008-08-28
Have you checked for overheating in the CPU and video card?
Is your fan working?
Does your system have good airflow? Heatsinks? Heatpipes?
Is anything exceptionally hot to the touch (be careful)?

---

### Post by Freakiwombatman on 2008-08-28
Mobo is a Soltek SL-KT600-C1L if that is any use.

The heatsinks/fans on both my cpu and graphics card are running fine and blowing nice cold air.

So I shall try updates and installing graphics cards. I shall let you know the outcome but it will be next week, thanks for all your help!

---

### Post by halitech on 2008-08-28
they may be blowing cold air but if the CPU heatsink isn't making good contact with the CPU it could still be heating up slowly to the point of locking up. You say you built the system yourself, did you apply anything like artic silver CPU paste to the CPU before you installed the heatsink?

---

### Post by nicedude on 2008-08-28
I thought of heat as well but wouldn't he get a thermal shutdown message ( my laptop does when it does this ) and wouldn't he not be able to move his mouse around the screen as I took it he can since he said mouse & keyboard still function but do not effect anything.

Just made it seem to me like this isn't temp, but since he built it himself that is defiantly a much greater chance of a incorrect CPU install and therefore thermal shutdown to be the culprit.

---

### Post by halitech on 2008-08-28
I don't on my desktop nor on my laptop (granted not sure a 10 year old laptop would have that ability anyway) and I know I've run my desktop to the point of overheating (darn small apartment and no a/c during the summer) and it simply locked up but I think I could still use the mouse but it was jerky if I remember right

---

### Post by nicedude on 2008-08-28
Then it may be thermal related, I can just say with 100% certainty that my Acer laptop gives a thermal shutdown warning ( its a Linux system shutdown message ) when it overheats as I have been working recently on power saving script and have had it do it quite a few times lately while experimenting.

---

### Post by halitech on 2008-08-28
I wouldn't rule it out as a possibility until they tell us if they used thermal paste or not

---

### Post by nicedude on 2008-08-28
Yeah I hope he did as if not then that is a guarantee of a non working system, usually  they provide some cheap thermal grease with CPU's but the instructions to install it are usually pretty bad. I do know that at the arctic silver website they have PDF files for thermal paste installation based on processor model which are pretty good and apply to using any brand thermal grease.

When building a new PC the 6$ for arctic silver is probably the best investment you can make followed closely by the 20$ to buy a better CPU fan than the cheesy ones CPU manufacturers give you.

---

### Post by halitech on 2008-08-28
I agree, I had to go buy some recently and everytime I take a heatsink off, I clean the cpu and the heatsink and then put on a thin coat of paste and then put everything back together. those thermal pads they give these days are worthless

---

### Post by nicedude on 2008-08-28
Yep those pads are junk and actually can be a pain to get off :-) but I always use Arctic silver on all CPU's I install as I have had good success with it and it is pretty inexpensive especially if you order it online when buying system components. It is sad that Intel & AMD can't provide a few bucks of good thermal compound with an expensive purchase such as a CPU since it is probably the most important thing to get right when building a system.

---

### Post by kansasnoob on 2008-08-28
Beyond heat sink thermal compound I wonder when the OP says it's "blowing cold air" if the fans are installed backwards:confused:

It could be many things!

---

### Post by kansasnoob on 2008-08-28
Another thought, something I've run across quite often is crappy power supplies! Quite often people spend megabucks on components and buy a cheap case with a cheap overrated power supply.

I've even seen failures where someone upgraded their RAM and it exceeded the capabilities of the power supply under demand!

---

