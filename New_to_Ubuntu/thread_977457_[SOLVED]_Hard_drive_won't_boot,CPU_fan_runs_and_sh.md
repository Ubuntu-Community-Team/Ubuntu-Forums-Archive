---
title: "[SOLVED] Hard drive won't boot,CPU fan runs and shuts down"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by meindian523 on 2008-11-10
Well,this was the first time I removed my internal HDD to get the alternate ISOs of Ubuntu and Kubuntu 8.10 from a friend.When I got there,my friend's PC refused to boot while my HDD was connected.There were NO shocks when traveling.As I left,the bag containing the HDD slightly bumped against the elevator's wall.
Alarmed by these,I plugged in the HDD first thing when I got home and the symptoms are the same,the CPU fan runs for a second and dies.The PC won't boot.
Can someone help me please?:(
Many TIA.

PS:Posting from Live CD 8.04.

---

### Post by Peter09 on 2008-11-10
Have a look in your BIOS, see if the drive is recognized there. Also check that all the external links a still seated correctly. i presume the drive is linked as master?

---

### Post by meindian523 on 2008-11-10
Primary Master,yes.What do you mean by external links?Please explain in n00b language.Those bean counts count for nothing when it comes to hardware.

---

### Post by Peter09 on 2008-11-10
There is normally a link on the back of the drive wich you can move to define wether the drive is a master or slave. It may not work if its defined as slave and there is no master on the bus.

Also try booting with the LIVECD, you should then be able to examine your disk

---

### Post by meindian523 on 2008-11-10
The HDD is still set as master.I will reboot and get back if I'm able to boot into LiveCD with the HDD connected.

---

### Post by meindian523 on 2008-11-10
The PC doesn't boot whenever the HDD power cable is connected,even from LiveCD.The CPU fan just runs for a second or so and dies.Since the HDD doesn't have power,the HDD is not recognized either.

EDIT:The HDD is a PATA,Samsung SP0842N.

---

### Post by DGortze380 on 2008-11-10
> **meindian523 said:**
> The PC doesn't boot whenever the HDD power cable is connected,even from LiveCD.The CPU fan just runs for a second or so and dies.Since the HDD doesn't have power,the HDD is not recognized either.

EDIT:The HDD is a PATA,Samsung SP0842N.

Carefully remove the ribbon cable from the drive and mother board.

Remove the drive from the case.

Check the back of the drive for bent or missing pins. There should be 39 pins on a 40-pin IDE Ribbon Cable.

Your drive should be set to Master if it's the only HDD you have. You can also try CS (Cable Select) if it's supported.

Plug the cable back into the drive, press firmly, make sure it's all the way in. 
Use the master connector (if there are three connectors on the cable, use the one closest to the end and nearest the second connector). If there are two connectors, it shouldn't matter.

Plug the cable back into the board. Make sure you press firmly and push the cable all the way in. Make sure you've connected the drive to the first IDE Channel.

---

### Post by JohnLM_the_Ghost on 2008-11-10
> **meindian523 said:**
> The PC doesn't boot whenever the HDD power cable is connected,even from LiveCD.The CPU fan just runs for a second or so and dies.Since the HDD doesn't have power,the HDD is not recognized either.

EDIT:The HDD is a PATA,Samsung SP0842N.
Obviously you suspect you HDD is dead. So that's probably true.
However You shouldn't give up!
Try different Data cables and power connectors.
Try making it slave.
Try putting in different PC.
Try leaving HDD for a few days.

And always remember when carrying sensitive hardware outdoors, it shouldn't be powered for at least 15 minutes when carried back to PC (or other device).

EDIT: Ouch, Samsung! I never put money into Samsung HDDs or other devices (unless I'm short on money)
If it makes funny noises it usually doesn't... it doesn't suggest anything "healthy".

---

### Post by meindian523 on 2008-11-10
> **DGortze380 said:**
> Carefully remove the ribbon cable from the drive and mother board.
The end attached to the motherboard doesn't come out,and I'm not sure I should use brute force.
> **DGortze380 said:**
> 
Check the back of the drive for bent or missing pins. There should be 39 pins on a 40-pin IDE Ribbon Cable.
No missing pins,and as far as I can see,none are bent.
> **DGortze380 said:**
> 
Your drive should be set to Master if it's the only HDD you have. You can also try CS (Cable Select) if it's supported.
I have only one HDD.
> **DGortze380 said:**
> 
Plug the cable back into the drive, press firmly, make sure it's all the way in. 
Use the master connector (if there are three connectors on the cable, use the one closest to the end and nearest the second connector). If there are two connectors, it shouldn't matter.

Plug the cable back into the board. Make sure you press firmly and push the cable all the way in. Make sure you've connected the drive to the first IDE Channel.

What master connector?Before I removed the HDD,there were only two connectors connected in it.One was the ribbon(data) cable and the other was the 4 pin,female power connector.Since,I couldn't remove the cable from the motherboard,I haven't connected it back either.

---

### Post by meindian523 on 2008-11-10
DGortze380:
Reboot after above steps didn't resolve the problem.

---

### Post by meindian523 on 2008-11-10
> **JohnLM_the_Ghost said:**
> Obviously you suspect you HDD is dead. So that's probably true.
I'm not thinking that and hopefully,it's not dead.> **JohnLM_the_Ghost said:**
> 
However You shouldn't give up!
Try different Data cables and power connectors.
Try making it slave.
Try putting in different PC.
Try leaving HDD for a few days.
We already tried it in my friend's PC which exhibited the same symptoms despite totally different hardware and one more HDD which could be booted from.That PC had a different data cable,a different SMPS too.So,only last option is available.:(
> **JohnLM_the_Ghost said:**
> 
And always remember when carrying sensitive hardware outdoors, it shouldn't be powered for at least 15 minutes when carried back to PC (or other device).
Could you explain please?
> **JohnLM_the_Ghost said:**
> 
EDIT: Ouch, Samsung! I never put money into Samsung HDDs or other devices (unless I'm short on money)
If it makes funny noises it usually doesn't... it doesn't suggest anything "healthy".
It's not making any funny noise,in fact it's not making noise at all.

---

### Post by DGortze380 on 2008-11-10
> **meindian523 said:**
> DGortze380:
Reboot after above steps didn't resolve the problem.

Ok, have we found out if the drive is showing up in the BIOS?
Are there any POST Beeps when you turn on the machine?

---

### Post by meindian523 on 2008-11-10
The drive does not show up in BIOS because it doesn't have power(AFAIK)If I give power,the machine doesn't boot,the CPU fans runs for a few seconds and then dies.And no,there are no POST beeps when the HDD is given power(apparently because the machine won't boot at all)

---

### Post by DGortze380 on 2008-11-10
> **meindian523 said:**
> The drive does not show up in BIOS because it doesn't have power(AFAIK)If I give power,the machine doesn't boot,the CPU fans runs for a few seconds and then dies.And no,there are no POST beeps when the HDD is given power(apparently because the machine won't boot at all)

We haven't reached the boot stage yet. We're at POST.

Does anything come on the screen when you try to boot with the dive attached and powered up? Are there any indicate lights or hex displays on your board that would output a POST error? Do you have a model number for you mother board?  

No POST beeps could be clue by itself, typically normal POST would be one beep, then you get to start bootstrap and can access the BIOS.

EDIT: Can you boot a LiveCD with the HDD unplugged?

---

### Post by meindian523 on 2008-11-10
> **DGortze380 said:**
> We haven't reached the boot stage yet. We're at POST.
Ok.mea culpa.
> **DGortze380 said:**
> 
Does anything come on the screen when you try to boot with the drive attached and powered up?
Nopes,as I said,if the HDD is attached and powered up,CPU fans rotate for a second or so and stop.Nothing else happens after that.

> **DGortze380 said:**
> 
Are there any indicate lights or hex displays on your board that would output a POST error? Do you have a model number for you mother board?
I wouldn't know.My motherboard is the Intel D101GGC.

> **DGortze380 said:**
> 
No POST beeps could be clue by itself, typically normal POST would be one beep, then you get to start bootstrap and can access the BIOS.
That single POST beep and booting happens only when the HDD is NOT powered up.

---

### Post by DGortze380 on 2008-11-10
ok. what about the live cd? can you boot a live cd with the HDD unplugged?

---

### Post by meindian523 on 2008-11-10
Yes,that's where I'm posting from.

---

### Post by Peter09 on 2008-11-10
These systems are similar to what I had when there was a power fault. The device I was plugging in had a fault which took down the motherboard power line. Unplug and all was O.K. 

It may be the power supply on your HD has gone. Also look at any unprotected electronics on your HD, see if there is a possible place where a short may have happened.

---

### Post by meindian523 on 2008-11-10
Well,the exposed electronics are on a PCB,and it's very complex.I'm unsure whether there could be a short.I blew on it,to remove any dust,just in case.

EDIT: Does that mean I will have to replace the HDD?

---

### Post by DGortze380 on 2008-11-10
> **meindian523 said:**
> Yes,that's where I'm posting from.

Ok, that rules out a lot on the board.

It looks like your problem is going to be somewhere from the IDE Bus to the HDD. 

Start cheap. Try a new ribbon cable. 

Try and borrow a HDD to test in the machine. If a known good drive works, then your drive is dead or dying, start looking at data recovery. 

If the known good drive and known good cable don't work, you've got a problem with the IDE Bus on the board. You can by an PCI to IDE card, or just look at upgrading the computer.

---

### Post by jerome1232 on 2008-11-10
It's gotta be the hard drive, you plugged it into another machine and that machine refused to boot as well. Is it possible for you to test another known good working hard drive? 

A slight bump while a hard drive is powered off and not in use shouldn't do anything to it, takes a good shock to knock the heads about. (I've dropped my current one two feet onto a tile floor once, that worried me but it was fine)

At first I was thinking power supply (when you plug the hard drive into the system the power supplies max wattage is exceeded and the system doesn't boot). After all over time power supplies tend to deliver less and less power.

---

### Post by meindian523 on 2008-11-10
> **DGortze380 said:**
> Ok, that rules out a lot on the board.
It looks like your problem is going to be somewhere from the IDE Bus to the HDD. 
Start cheap. Try a new ribbon cable. 

Are you sure about that?We tried,as mentioned above,in a separate PC,which had a separate data cable and power supply.In short,I had taken the naked HDD,no cables attached.

> **DGortze380 said:**
> 
Try and borrow a HDD to test in the machine. If a known good drive works, then your drive is dead or dying, start looking at data recovery. 
If the known good drive and known good cable don't work, you've got a problem with the IDE Bus on the board. You can buy an PCI to IDE card, or just look at upgrading the computer.

Ok.I think the only possibility as a summary is that either the HDD is going bad or the power circuits on the HDD are shorting out somewhere.

Thing is how does the HDD start dying all of a sudden?I booted into it this morning,at 1400 hours.There was no problem then,no corrupt files,etc.
And how again,do circuits short out all of a sudden?

---

### Post by meindian523 on 2008-11-10
I think I should mark this thread solved seeing as what can be done is only hardware issue,and no problems with the motherboard,etc.

---

### Post by JohnLM_the_Ghost on 2008-11-10
> And always remember when carrying sensitive hardware outdoors, it shouldn't be powered for at least 15 minutes when carried back to PC (or other device).
> **meindian523 said:**
> Could you explain please?
That one is not for this case but an advice in general. If you carry hardware through humid and/or cold air the device (HDD in this case) is prone for condensate build-up. If you hook up this device to power it can short-circuit. (From my experience I've had a PC's PSU literally exploding when turned on right after carried back indoors)

> **meindian523 said:**
> It's not making any funny noise,in fact it's not making noise at all.
No noise at all is also not good sign.
Make sure it spins up and does head-seek (eg. makes subtle spinning sound and few clicks).

---

