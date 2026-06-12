---
title: "Ubuntu Internet Problems!"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by IBUA on 2008-11-12
I know i should do this in the Networking forum but they were all too complicated :P

Well today i finally got round to installing Ubuntu via Wubi.

And it installed fine, and everything worked without a hitch (Had dual-booted it)

I was then going to update/upgrade it to Ubuntu Studio... but then it said i had to be connected to the internet (obviously). So then i went to see if i could add my wireless connection.
As for somereason it didn't detect it automatically.

(The router is on a different computer and i get linked to the internet on the computer with Ubuntu on it with one of those dell USB wireless adaptor thingys that you get with it)

But it was way too complicated for my liking even after attempting to find it... (The networking thingy) and there was no option to "Search" for the other wireless networks that i could see.

So then i went back to the windows OS where i still had internet. 

So i went and looked at all the help and things and various forums/threads with the same problem. but none of them helped. Because either it didn't make sense or the way i did it i could do(for ecample it'd tell me to go go SYSTEM>APPLICATIONS>NETWORK, but i wouldn't have that... i'd only have NETWORK TOOLS)

I don't know but is this a problem to do with the new Ubuntu 8.10? and has Wubi installed that version? ( I downloaded Wubi today)

SO OVERALL Here are my questions:

1. How do i connect to the internet in 8.10
2. If i still can't do this, should i go back to 8.04
3. How would i do this as none of the old Wubi Installers exist anymore
4. ALSO I installed Ubuntu onto my external hard disc drive (E:/) and i was told previously i'd be able to accsess my music... but for somereason i could only look into the files like documents and programs on the computers C:/ drive and not the External HDD (wehre all my music was) How can i accsess my files on the E:/???

I have looked at lots of other threads and people say oh just go to this thread and so on, but this never helps as it never sorts the problems i have.

PLEASE HELP!

Thanks in advance!

(BTW As i only installed Ubuntu today i'm a complete noob so you'll have to explain everything the "simple" way haha)

---

### Post by Kaspersky_ on 2008-11-12
The drivers for the USB adapter are probably not installed. Ubuntu should automatically try to install them upon detecting the adapter. From there you can just connect to any wifi connection you have access to.

---

### Post by IBUA on 2008-11-12
> **Kaspersky_ said:**
> The drivers for the USB adapter are probably not installed. Ubuntu should automatically try to install them upon detecting the adapter. From there you can just connect to any wifi connection you have access to.

Ok. But obviously this hasnt happened as i have no connections at all in the Network Manager?

So how would i do this?

---

### Post by saru411 on 2008-11-12
Your problem is you need the packages(drivers) for the wireless card. If you were connected to the internet(via an ethernet wire) Ubuntu would recognize the adapter and you could install the drivers(via System>Administration>Hardware Drivers). It is always very difficult to install a base Operating System with only WiFi.

---

