---
title: "Can't find an answer to my external hard drive problem"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by Visrite on 2013-02-25
I've been googling and searching the forums here for about 2 days now and still no access to my external hard drive. I'll try some commands I find and either I'll get an error message somewhere or I'll see the terminal just turn into a bunch of blue ~ and no idea what I did and how I don't damage my system.

The external is windows formatted, plugs in with 2 usb ports and beeps continually at me every time I plug it into my machine but not my room mates. Their computer can see and interact with the drive and it doesn't beep.

I'm not sure what information y'all need to please help me trouble shoot this problem. Thanks for your time.

---

### Post by carl4926 on 2013-02-25
If I were to Google external Hard Drive, I wonder which one would be yours?

Can you tell us what Make/Model/Size etc....

---

### Post by DuckHook on 2013-02-25
It is almost 100% certain that you have a HW issue. The USB standard requires USB ports to output 500mA at 5 volts. Your drive requires 1A, therefore, the 2 USB ports. The second port is tapped only for power. No data is transferred through it.

Your USB ports are likely not sending out sufficient wattage to power the drive properly, whereas your roommates' computers are. The drive is telling you that you have insufficient power. You can either:

1. Try different USB ports on your computer to see if another two provide sufficient power, or
2. Buy a ***powered*** USB 4 port hub that supplies a total of ***at least*** 2 amps. The hub ***must*** be powered. Otherwise you are in even worse shape than without it.

---

### Post by Visrite on 2013-02-25
Seagate FreeAgent Go 160 GB

I'm really hoping its not the hardware. Is there a way I can check/change the power being outputted to the unit?

---

### Post by Visrite on 2013-02-25
DuckHook you hit it on the nose. I didn't think to try the other usb port because its by its self on the other side of the pc and after plugging one end into that usb it popped right up.

Thanks guys, I feel a facepalm moment.

---

### Post by DuckHook on 2013-02-25
Some manufacturers chintz out on their USB ports by splitting one bus into two or more ports (which is fine) without upping the power supply (which is not fine). In essence, they turn a portion of their ports into unpowered hubs. Saves them a few bucks at the expense of legions of users who have no idea why their peripherals don't work. They don't get complaints or returns because few can even conceive of such problems much less figure them out, so no incentive to change.

To be fair, I find that the cheaper the laptop, the more such shortcuts. But have seen it in pricey models too.

<edit>
btw, probably obvious, but it bears noting that if you hitch any further USB peripheral up to your laptop, your ext HDD will die. You have a very fragile ecosystem right now. You may still wish to invest in that powered hub.
</edit>

<edit_2>
...and please mark thread solved.
</edit>

---

