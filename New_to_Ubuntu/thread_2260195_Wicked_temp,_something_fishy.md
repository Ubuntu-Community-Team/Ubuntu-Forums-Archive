---
title: "Wicked temp, something fishy?"
date: 2015-01-09
forum: New to Ubuntu
---

### Post by haxerius on 2015-01-09
Hi, sorted out my usb install problem of lubuntu, noticed that i had wicked high temp on my laptop. Is there anything i should check out to get a lower temp on my laptop?
Seen that high temp has something to do with the gpu since when i watch movies the temp and fan goes to max. Noticed that intel graphic installer downloaded a bit more than the last time hope it will give me lower heat.

Tries restarting my laptop since ive had not done it since i installed lubuntu, everything runs smoother, but temp is a bit high still. Anyone?

---

### Post by sandyd on 2015-01-09
Hi,

How are you viewing the temperatures? (lm-sensors, widgets, conky, etc)

---

### Post by haxerius on 2015-01-10
No viewing other than feeling to outlet of the air and its burning, cant put my finger near for more than secunds, have conky installed but not showing any temp.

Just installed psensor ... 81c + is it too much? :) How do i put the temp down. Im just streaming film.

Although im on a HP lol

---

### Post by QIII on 2015-01-10
Hello!

Can you give us your machine specs, such as the CPU, GPU, hybrid graphics or not, etc?

---

### Post by haxerius on 2015-01-10
[TABLE="class: shop_attributes"]
[TR]
[TD]Elitebook 2530p
[/TD]
[/TR]
[TR="class: alt"]
[TH]Cpu:[/TH]
[TD]Intel Core 2 Duo L9400 &#8211; 1,86GHz[/TD]
[/TR]
[TR]
[TH]Mem:[/TH]
[TD]4096MB DDR2-800MHz[/TD]
[/TR]
[TR="class: alt"]
[TH]Hd[/TH]
[TD]120GB[/TD]
[/TR]
[TR]
[TH]gpu:[/TH]
[TD]Intel GMA 4500MHD
[/TD]
[/TR]
[/TABLE]

Integrated graphics 
loading about 800mb mem RAM right now seen on conky

---

### Post by nerdtron on 2015-01-10
Are your internal fan/grill heatsink cleaned?

---

### Post by haxerius on 2015-01-10
No but nothing showing from the outside though.

---

### Post by QIII on 2015-01-10
You may not see anything from the outside.

That's a pretty old machine.  A lot of time for dust bunnies to have grown in the HSF.  Buy a can of compressed air and blow up through the intake to see if you get a cloud of dust and lint out of it.

---

### Post by haxerius on 2015-01-10
Anything else i might try?

Will try the air in a can trick tomorrow when the stores open, but is there anything else i can try?

---

### Post by QIII on 2015-01-10
This is such a common cause of overheating in laptops that it is really the very first thing you should do before getting too bound up in checking anything else.

Something easy you might try is to put a pencil or pen under the rear of the laptop when it is on your desk to see if it will allow greater air flow.  But a dirty heat sink is the most common cause of this.

---

### Post by haxerius on 2015-01-10
Thanks Ill open my laptop open someday and give it a shake. Thanks for fast responding!

---

### Post by haxerius on 2015-01-10
Something more fishy .. when goofing around changing my mac adress... it stopped and dropped to 49c+ ... WTF?

---

### Post by nerdtron on 2015-01-10
If you are not doing anything that puts load on the cpu, say just "goofing around", the temp will be lowered. But if you start playing an HD video, and browsing youtube video, and feels the temp is higher again, then you really need to check the hardware first since the fans can't keep the temp cool.

If your fans are clean, and temps are still high then we can proceed troubleshooting.

---

### Post by haxerius on 2015-01-10
Nothing is wrong now. Watching HD movies, playing games with eaze... just changed my mac adress :(


Really nice if anyone of you know "temp3" in Psensor what does it measure? Becuse mine temp3 is stuck at 74... but temp1 was at 84c+ but now calmy at 45+c

---

### Post by nerdtron on 2015-01-10
For how long are they playing? Why and how did you changed your mac address?
Anyway, just watch for it to happen again and note things like what changes you did, what programs are running, and open the system monitor, look at the processes and post the screenshot here.

---

### Post by haxerius on 2015-01-10
Temp3 is for acpi :P 

Just goofing around with 
ifconfig -a | grep HWaddr who cares why?

Still doing the same things that i was doing before...

---

### Post by Impavidus on 2015-01-10
> **haxerius said:**
> No viewing other than feeling to outlet of the air and its burning, cant put my finger near for more than secunds, have conky installed but not showing any temp.

Just installed psensor ... 81c + is it too much? :) How do i put the temp down. Im just streaming film.

Although im on a HP lol
If there is a problem with the fan or the heatsink, the CPU gets hot because the heat is not moved out of the box. As the heat doesn't get out, there cannot come a lot of hot air out of the ventilation openings. The fact that you nearly burnt your hand tells us the heatsink and fan are fine.

---

### Post by Mike_Walsh on 2015-01-10
> **QIII said:**
> This is such a common cause of overheating in laptops that it is really the very first thing you should do before getting too bound up in checking anything else.

Something easy you might try is to put a pencil or pen under the rear of the laptop when it is on your desk to see if it will allow greater air flow.  But a dirty heat sink is the most common cause of this.

A BIG +1 to this.

QIII's on the button, as usual. The only real long-term answer to this is to strip the laptop in question down, and have a thorough 'spring-cleaning' session. I've just recently done this for the first time on an eleven-year-old Dell Inspiron laptop; admittedly, it was probably easier to perform this on an old laptop, rather than a modern one, due to the fact there's more room 'under the hood' in the old machines.

The amount of dust, fluff, and general assorted crap around the heat-sink was quite astonishing.....although our house has hot-air heating, so it tends to move the dust around the place all the time..! That, combined with removing the CPU and re-seating it with fresh thermal paste, has resulted in a temperature drop in the region of over 25 degrees...

On top of all that, I no longer rely on the clearance provided by the supplied rubber feet. I've outfitted my old girl with some commercially-available, self-adhesive 'bumper stops' (quite cheap), which give me nearly three times the 'ground clearance' it had before.....and I ALWAYS use it on a hard surface, to maximise the airflow.

It works.

Regards,

Mike. ;)

---

