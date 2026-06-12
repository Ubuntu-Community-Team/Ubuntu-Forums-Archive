---
title: "synaptic will not start"
date: 2011-08-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sammiev on 2011-08-26
Synaptic once selected will ask for the password, I enter the password to open and then synaptic flashes on the screen and closes. I removed it completely, rebooted and installed again will no change. :( Any ideas I may try? I searched everywhere. TY :)

---

### Post by Harry33 on 2011-08-27
> **sammiev said:**
> Synaptic once selected will ask for the password, I enter the password to open and then synaptic flashes on the screen and closes. I removed it completely, rebooted and installed again will no change. :( Any ideas I may try? I searched everywhere. TY :)

Does it open from terminal with the command:
```
pkexec synaptic
```

---

### Post by sammiev on 2011-08-27
This is what I see when I try it from terminal. Synaptic asked for my password and close as soon as it opened on the screen. 
Thanks

sam@sam-Satellite-L650:~$ pkexec synaptic
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
Aborted (core dumped)
sam@sam-Satellite-L650:~$

---

### Post by rapiertg on 2011-08-27
This is something i had faced too on two computers. Some updates to gcc or some libraries fixed them lately.

---

### Post by sammiev on 2011-08-27
> **rapiertg said:**
> This is something i had faced too on two computers. Some updates to gcc or some libraries fixed them lately.

Thanks, It broke on an update and I hope it will be repaired on an update. :)

---

