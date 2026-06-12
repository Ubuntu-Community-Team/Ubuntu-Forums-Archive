---
title: "Different updates"
date: 2015-07-13
forum: New to Ubuntu
---

### Post by MGrowl on 2015-07-13
I have two instances of 14.04 installed on two different pc's. My question is, when updating one of the pc's shows updates the other doesn't. What gives? I already checked */etc/apt/sources.list*, and double-checked the GUI for software updates, the same sources have been checked. Why is this happening? And should I be worried?


BTW, when using *apt-get update* on one of the computers it shows there are updates available, but when I check with the GUI for updates it says "software up-to-date".

---

### Post by Bucky Ball on 2015-07-13
Are the two machines identical as far as hardware and software? Identical? I'd probably wait for a week, upgrade both so you know they have been updated at exactly the same time, wait for another week and go for the updates and check the size of the update on both prior to doing it (under the list of what is going to be updated it tells you how much will be downloaded). This is still probably not going to give total accuracy as, well, it is doubtful the machines have exactly the same software installed and its running on the same hardware.

---

### Post by deadflowr on 2015-07-13
The difference is how you are applying the updates.

Ubuntu introduces an update feature known as phased-updates.
It is used through the gui approach.
what it does is set a number of users to get updates first, then if the error reporting of those updates is below a given threshold those updates get expanded to more users, until all users get them.
It was put in place so that if a regressive or corrupt update came, they could stop it before everyone got it.

This, however, only applies to the gui method.

The command line approach is not affected, so those updates will come without being blocked by the phased-updates system.

Reference here:
[https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

Hope this helps.

And, yes, you are doing nothing wrong.

---

### Post by MGrowl on 2015-07-13
@Bucky Ball They aren't identical. I do update them minutes apart though. The software is mostly identical, only a couple aren't installed on both machines. Although, shouldn't they be sharing the same security updates? For instance, the other week, one of the machines needed GRUB to be updated, so I did. After the update I immediately checked the other PC, but no updates for GRUB showed. Does this mean that security updates differ machine-to-machine?

---

### Post by Bucky Ball on 2015-07-13
Interesting deadflowr. Never knew that. Neat. Perhaps I'll start updating using the Software Updater again rather than the terminal. :)

---

### Post by MGrowl on 2015-07-13
@Bucky Ball, @deadflowr Thanks guys. 

@deadflowr, Thanks for the link and explanation. Phased updates really makes a lot of sense.

---

