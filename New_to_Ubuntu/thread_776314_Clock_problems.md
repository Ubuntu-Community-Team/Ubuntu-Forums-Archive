---
title: "Clock problems"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by almabeck on 2008-04-30
My computer clock insists on reading an hour ahead. I'm currently using Vincennes, IN (I'm in Central time zone). I've tried to go to manual setting, but when I restart, it reverts to the hour-fast time. I've tried to change the time zone, but that has no effect, either. 

Is my computer bewitched? Any ideas how I can heal it?

I hoped this problem would go away when I upgraded to 8.04, but no such luck. (Instead, I lost sound!)

---

### Post by it.henrik on 2008-04-30
are you synchronizing your clock against the internet servers?

right click on the clock in upper right corner -> preferences -> unlock 

make sure you have the right timezone and "configuration" is set to "Keep synchronized with internet servers".

Hope it helps

---

### Post by almabeck on 2008-05-01
> **it.henrik said:**
> are you synchronizing your clock against the internet servers?

right click on the clock in upper right corner -> preferences -> unlock 

make sure you have the right timezone and "configuration" is set to "Keep synchronized with internet servers".

Hope it helps

Thanks for the suggestions. I've tried all that. The clock still reverts to the hour-ahead time when I restart. Sometimes it reverts w/out the restart, even.

---

### Post by Paqman on 2008-05-01
Can you get into your BIOS and see what time you're set to there?

---

### Post by avtolle on 2008-05-01
> **almabeck said:**
> My computer clock insists on reading an hour ahead. I'm currently using Vincennes, IN (I'm in Central time zone). I've tried to go to manual setting, but when I restart, it reverts to the hour-fast time. I've tried to change the time zone, but that has no effect, either. 

Is my computer bewitched? Any ideas how I can heal it?

I hoped this problem would go away when I upgraded to 8.04, but no such luck. (Instead, I lost sound!)

I believe the entire state of Indiana is in the Eastern time zone. Reset your zone to America/Chicago, this should correct your problem. To do: System-->Administration-->Time and Date, unlock, and select America/Chicago. I'm in the Central time zone, too, and that is what my configuration shows when I checked it. HTH.

---

### Post by Kevbert on 2008-05-01
> **it.henrik said:**
> are you synchronizing your clock against the internet servers?

right click on the clock in upper right corner -> preferences -> unlock 

make sure you have the right timezone and "configuration" is set to "Keep synchronized with internet servers".

Hope it helps

Thanks it.henrik.  What's with the weather tab ?  I'm running Hardy X64. :confused:

---

### Post by almabeck on 2008-05-23
Clock problems (as well as sound problems) were magically fixed by a clean install of 8.04. Yeah!

---

