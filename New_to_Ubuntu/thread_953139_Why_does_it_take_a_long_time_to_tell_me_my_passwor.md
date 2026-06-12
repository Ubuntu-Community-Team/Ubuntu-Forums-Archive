---
title: "Why does it take a long time to tell me my password is wrong?"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by NoSmokingBandit on 2008-10-19
I've always wondered this and i was logging in and misspelled my name and it reminded me. Whenever i misstype a password or username it takes about 5 seconds for any linux distro to tell me it was wring, yet in windows and osx it tells me instantly. Is there some method to the madness that i dont grasp.

---

### Post by Pro-reason on 2008-10-19
> **NoSmokingBandit said:**
> I've always wondered this and i was logging in and misspelled my name and it reminded me. Whenever i misstype a password or username it takes about 5 seconds for any linux distro to tell me it was wring, yet in windows and osx it tells me instantly. Is there some method to the madness that i dont grasp.

The madness is in letting the person try another password immediately.  It means they can brute-force it by guessing lots of possibilities very quickly.

The Linux way is much more secure.  The guesser can't even be sure it's wrong until he waits a bit (it could just be starting the logging-in process).

Does your bank's cash dispenser allow you key in several PINs in quick succession?

---

### Post by forger on 2008-10-19
If you ask me, they should delay that exponentially or +1 second for each bad try :)
However, you can log in automatically or set it to '0 seconds' if you want to: System > Administration > Login Window

---

### Post by NoSmokingBandit on 2008-10-20
> **forger said:**
> If you ask me, they should delay that exponentially or +1 second for each bad try :)


That sounds like a good idea. One typo and you only have to wait 1 second and you can log in right away. 2nd fail is 2 seconds, 3rd is 4, 8, 16, 32, 64...
Not only is that more convenient but it would, in theory, be more secure against brute force attacks.

---

