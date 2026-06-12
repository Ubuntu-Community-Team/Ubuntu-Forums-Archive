---
title: "Really bad lag"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by Fritooo on 2008-06-25
I'm getting horrible amounts of both computer and internet lag. All I'm running are amarok, pidgin, and firefox, yet the system monitor says that 100% of the processor is being used almost all of the time.
I have 2 gigs of ram, 3 gigs of swap, and an 80 gig hard drive, of which I'm using less than 10 gigs. This makes no sense, I thought Ubuntu was supposed to run faster than Windows, yet it's running at least 10 times slower on average.

---

### Post by Afkpuz on 2008-06-25
This is not a sure fire fix, but if you're not too far along, a re-install might be good.

---

### Post by Fritooo on 2008-06-25
Yeah, I've had this install going for about 2 days. 
The one before that had a 30 gb hard drive and still ran way slow.
I just don't get it.

---

### Post by avtolle on 2008-06-25
At the terminal (Applications>>Accessories>>Terminal)```
top
```to get a list of the various processes running and the cpu % each is using, It could be that there's something running that is a hog (tracker? in earlier versions of Ubuntu, Network Manager was problematic). If you find something running that is hogging the cpu, hit "k" and enter the PID to kill it. HTH.

---

### Post by kestrel1 on 2008-06-25
What speed is your processor?
I assume its if a reasonable speed, as you have 2gb RAM installed.
What processes are running?

---

### Post by Fritooo on 2008-06-25
2.66ghz
My computer is a bit outdated, but I didn't think it was THAT bad.
gnome-system-monitor
firefox-bin
amarokapp
metacity
pidgin
those are the only ones using any %CPU constantly

---

### Post by shae on 2008-06-25
Perhaps your cpu is using frequency scaling slowing that way down?

---

### Post by Fritooo on 2008-06-25
Is there any way I can fix that?

---

