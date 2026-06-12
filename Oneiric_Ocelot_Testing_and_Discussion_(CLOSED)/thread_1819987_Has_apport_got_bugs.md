---
title: "Has apport got bugs?"
date: 2011-08-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by CaptainMark on 2011-08-07
I keep getting apport messages to say various processes have crashed even though i dont notice any difference to the process running, some likely culprits are chromium browser, indicator applet, banshee and software centre.  is it possible apport is at fault,

its weird its kind of like if you break down in your car and your insurance company send a recovery van to you, but then you find out that the van has broken down

---

### Post by ~!geek!~ on 2011-08-07
There is a possibility that the applications you got apport error with are actually not starting and shutting down correctly. Apport does react this way to the situations like that. You may disable the apport showing up by changing a setting from 1 to 0 in a file which I m not able to recall (use google to find the file).
You may also try looking for some controls for apport. (I don't know if it even exists, although you may stop apport from showing up as mentioned above)

---

### Post by sgage on 2011-08-07
> **~!geek!~ said:**
> There is a possibility that the applications you got apport error with are actually not starting and shutting down correctly. Apport does react this way to the situations like that. You may disable the apport showing up by changing a setting from 1 to 0 in a file which I m not able to recall (use google to find the file).
You may also try looking for some controls for apport. (I don't know if it even exists, although you may stop apport from showing up as mentioned above)

The file you want is /etc/defaults/apport

---

