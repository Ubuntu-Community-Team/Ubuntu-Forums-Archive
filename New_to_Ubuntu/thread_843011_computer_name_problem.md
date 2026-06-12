---
title: "computer name problem"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Matt26 on 2008-06-27
for some reason when i look at the Network Magic program (network scanning utility) under my Windows XP computer, i am seeing an entry that was just recently detected on my network for a computer called 'MININT-FQFR1Y', and after a little investigation i discovered that this appears to be my ubuntu system (same IP address and MAC address) but i have a different name (Central) for my ubuntu system, and it shows up as a separate system in Network Magic with the proper name as well- what could be the cause of this?  does this computer name have any significance that anyone is aware of?  i'm wondering if it is possibly an intruding system on my wireless network or something malicious.

any help would be greatly appreciated.

thanks.

---

### Post by defrex on 2008-06-27
Hmm, ya, my first thought is mac address spoofing by an intruder. Are you using mac filtering?

Though, someone else may have a better explanation.

---

### Post by st33med on 2008-06-27
> **defrex said:**
> Hmm, ya, my first thought is mac address spoofing by an intruder. Are you using mac filtering?

Though, someone else may have a better explanation.

My explanation: It's Windows :D

Try turning off the Ubuntu PC and see if it goes away. If it does not, I would HIGHLY recommend disconnecting your router and make a new password.

You do have a wireless encryption (WEP, WPA, etc.) right? If you do not (or use WEP), best use WPA or WPA2, if it can be enabled on your router.

---

### Post by Matt26 on 2008-06-27
yes, i do use WPA2 + MAC filtering... the Windows computer i am viewing the Network Magic utility on is actually a virtual machine that is running on the ubuntu system, so i can't turn the ubuntu system off to see what happens ;)  the proper entry that is showing up in Network Magic for my ubuntu is actually showing the system as Offline, and showing the new computer as Online?  not sure what this means...

---

### Post by st33med on 2008-06-27
Not too sure how Network Magic works, but, it sounds as if Virtual Box has a hard time detecting the same computer.

Try focusing on the Ubuntu desktop and surfing the internet and see what Network Magic says...

(I have no experience with VM's, if you have not noticed :))

---

### Post by Matt26 on 2008-06-27
i'm actually using vmware server for the virtual machine- and i have been posting to the ubuntu forums on the ubuntu system since this issue began and Network Magic hasn't updated anything yet.

---

### Post by Matt26 on 2008-07-01
i tried changing the IP address of my ubuntu host machine, and the network magic program updated the new computer it has detected with the new IP address- i also powered off my wireless router to see if the new computer would get disconnected but it stayed online.  i was able to turn off my ubuntu host machine and view the network magic program from a separate physical windows XP PC and it showed the new computer as being offline, then when i tuned the ubuntu machine back on, network magic showed the new computer as being online again- so for the most part it looks like this new computer that is being detected is in fact my ubuntu system- but it shows up with this weird computer name and detects windows XP as the OS- i don't know why this is happening- does anyone have any ideas?

thanks.

---

