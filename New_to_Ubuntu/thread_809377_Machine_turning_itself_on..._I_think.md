---
title: "Machine turning itself on... I think"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by watson524 on 2008-05-27
hi all - new user here.

I am running ubuntu as a standalone on a machine with only one HD. I shut the machine down at nite and I notice that in the morning, it seems to be "on" but not really. Fan is going, and HD I light is blinking rapidly on the front of the tower. I have "suspend" set to never and turn off monitor after 40 minutes but that's all I know about for power settings. Any ideas how I can stop the machine from coming on? I'm not sure what's causing this.

thanks!

---

### Post by Cypher on 2008-05-27
Are you sure the machine properly shutdown at night? The fans have stopped and there are no lights on? Perhaps the machine didn't really shutdown?

You might want to check in the BIOS and see if you have Wake On Lan enabled or any other thing..some BIOS' allow you to start the PC by hitting any key on the keyboard as well..so check on those settings..

---

### Post by watson524 on 2008-05-27
yep, fans are stopped, all lights are off. it's running some updates now so i'll check the bios on next reboot. this is my husband's old windoze machine so i'm not as up on his bios settings as i would be if it were my old machine.

thanks!

---

### Post by watson524 on 2008-05-27
looked in the bios, nothing that tells me it'd wake the machine up so i'll have to see if i can shut it down during the day while i'm sitting here and see if it does it. maybe it does it just to spite me overnite :-)

---

### Post by alienexplorers on 2008-05-27
Might be a power supply problem.  I had one going bad and it did this.

---

### Post by watson524 on 2008-05-27
ok it's something with the LAN. i have this machine plus my windoze machine running through a wired switch. i though ok let me try this... i did a send/receive on my windoze machine in outlook, and sure enough, the HD light started blinking on the linux machine. so it must be a bios setting, i just can't find it. huh. what's also interesting is that when the HD light starts flickering, it's not as bright as when the machine is on and the HD is really flickering because it's doing something.

---

### Post by watson524 on 2008-05-27
well now i'm not convinced it's the LAN since now it's doing it when the lan isn't being accessed. maybe it just is a fluky PSU but my husband said he never saw this happened when it was a windoze machine and he sat in the dark a lot with it so he'd noticed a blinking light.

---

### Post by Cypher on 2008-05-27
Depending on the age of the BIOS and PC, some did support the Wake On Lan. So if you were to try to ping the machine while it was off, it would actually turn on..

I would think that if the PSU was flaky you would see random shutdown/restart while you were using the machine. Just powering up without any provocation seems like a very unique symptom of PSU failure..

---

### Post by watson524 on 2008-05-27
it's weird because it's not like the machine is actually on, it's just the HD light blinking REALLY fast dimly. i still have to hit the power button where it then POSTs and boots up.

---

### Post by Paqman on 2008-05-27
If it is Wake On LAN you should be able to disable that in your BIOS.

Sounds a bit odd though. To turn on the machine has to receive a special packet sent directly to it. What could be sending the magic packet?

---

### Post by Duck2006 on 2008-05-27
> **watson524 said:**
> it's weird because it's not like the machine is actually on, it's just the HD light blinking REALLY fast dimly. i still have to hit the power button where it then POSTs and boots up.

Power supply problem, is what it sounds like.

---

### Post by watson524 on 2008-05-27
nothing is sending any thing to the machine. i thought it was when i caused internet traffic on the windoze machine that's on the same switch (and then down into the same router in the basement) but that test has proven unreliable. and since it's not fully on (i.e. not in the OS, just at a blank screen with HD light flashing) i'm totally lost on what this could be. not a show stopper, just an annoyance because i can't make it stop and behave.

---

