---
title: "Broadcom B43 Wireless Problem"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by 7Seas on 2008-04-26
Lost my wireless internet connection after the 8.04 upgrade.

When I select System>Admin>Hardware Drivers
I get: "No proprietary drivers are in use on this system"
The Broadcom B43 wireless driver status is "In use" but
the Enabled box is greyed out.

When I try to enable it, I get the "Failed to fetch..." error because of no wired (or wireless) connection.

Are there any work arounds for this?

Thanks in advance for any help with this.

Jones'n in Texas...

---

### Post by nullmind on 2008-04-26
See my signature for how I fixed this via ndiswrapper in Hardy. I don't know if all the bugs that existed in Beta that caused me to write that article are still open, but I have ndiswrapper working and explain how b43 is most likely not going to work!

Cheers,
Kris

---

### Post by vidus on 2008-04-26
dont bother with ndiswrapper its not neccesary.

do you have 3rt parts etc.. repos boxes checked in synaptic?

---

### Post by 7Seas on 2008-04-26
Thanks Kris,

Looks like you're on to something. Gotta grab some lunch then I'll try your fix.

Rudy

---

### Post by 7Seas on 2008-04-26
I'm sorry but what is the 3rt, etc.. you mention?

---

### Post by vidus on 2008-04-26
sorry. i meant 3rd party repos. 
i had the same prob as you, i just enabled all the repos and then the hardware manager had my enabled box availbale.. checked it off and i was wireless!

---

### Post by 7Seas on 2008-04-26
Thanks to nullmind & vidus for helping me with this issue.  Got the wireless going and it's great!.

---

