---
title: "Normal CPU temperature."
date: 2008-05-27
forum: New to Ubuntu
---

### Post by sharks on 2008-05-27
What is the Normal CPU temperature? mine it is 60*C . is it normal?

---

### Post by forestpixie on 2008-05-27
There isn't afaik a normal cpu temperature because most have slightly different temp ranges - you can find out from your cpu manufacturer - sounds a bit warm though

---

### Post by kpkeerthi on 2008-05-27
What CPU do you have? Is it a desktop?

Considering you and me living in the same city and our ambient temperature is usually 40 degrees C, 60 sounds pretty normal for a desktop.

My laptop's (Pentium M centrino) usually idles at 44 degrees.

---

### Post by sayakb on 2008-05-27
I always have a 60 degrees on a laptop, while normal temp for desktop ranges from 50-60 degrees which also depends upon how may ACPI fans you have. This all depends on your processor (Core Solo has lower temp than Core and Core2 Duos or further).

---

### Post by cheesypoof on 2008-05-27
60*C is a bit high for idle no matter what CPU you are running.
<-- Intel Quad Core @ Idle = 50*C Load = 62*C

---

### Post by sharks on 2008-05-27
intel p4 519 at 3.06ghz

---

### Post by sayakb on 2008-05-27
> **cheesypoof said:**
> 60*C is a bit high for idle no matter what CPU you are running.
<-- Intel Quad Core @ Idle = 50*C Load = 62*C

Which quad do you have.. :confused:
My Q6600 rises till 70 and 55-60 is idle. I have 12 ACPI fans on the cabinet.

---

### Post by sayakb on 2008-05-27
> **sharks said:**
> intel p4 519 at 3.06ghz

For a P4 Desktop, 60 is quite high.

---

### Post by soxs on 2008-05-27
Phenom seems to be another world: 35°C idle, 50°C load; 55°C heavyload
But this higly depends on our environemt temperature.
Note: I own a 400g Alu Cooler 8)

---

### Post by reeseslover531 on 2008-05-27
Ya 60 is high for idling my q6600 overclocked to 3.4 ghz only hits 60 under pretty extreme load. What cpu do you have?

---

### Post by sayakb on 2008-05-27
I guess it also depends on the country you live in 8)
India has about 40*C to 42*C during the noon-afternoon period, so that might be the cause.. :(

---

### Post by cheesypoof on 2008-05-27
> **LinuxIsInnovation said:**
> Which quad do you have.. :confused:
My Q6600 rises till 70 and 55-60 is idle. I have 12 ACPI fans on the cabinet.

I also have the Q6600, the B3 revision. Make sure you have not disabled stepping. That would mean your CPU would be running at 2.4ghz while idle instead of 1.6ghz. I have a Thermaltake CL-P0310 CPU Cooler + 4 case fans by the way in the western USA. If those temperatures are correct for your region, then I would definitely look at those as a significant factor why yours are higher. Hopefully this provides you with reasons why your temperatures differ from mine. :)

[http://www.thermaltakeusa.com/product/cooler/retail/cl-p0310/cl-p0310.asp](http://www.thermaltakeusa.com/product/cooler/retail/cl-p0310/cl-p0310.asp)

---

### Post by sayakb on 2008-05-27
What I did is that I changed the power manager CPU settings from gconf (/apps/gnome-power-manager/cpufreq). I set the AC fre to 80. It already has started showing 50*C :D 
How much is this supposed to affect my speed (no notable differences)

---

