---
title: "How to revert to my previous setup please?"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by ntu on 2012-04-27
I have Ubuntu 10.4 istalled on one hdd and xp on the other and switch from one to the other using bios. Normally the xp hdd is uninstalled as I rarely use it. However last update was done with it installed and now I cannot run 10.4 without the xp hdd being installed. How to revert to my previous setup so that I can run the 10.4 hdd on its own?

I am an old timer and particularly like having xp and ubuntu on completely separate hdds that I can remove at will as I have got into a horrible muckup before with Grub.

---

### Post by haqking on 2012-04-27
> **ntu said:**
> I have Ubuntu 10.4 istalled on one hdd and xp on the other and switch from one to the other using bios. Normally the xp hdd is uninstalled as I rarely use it. However last update was done with it installed and now I cannot run 10.4 without the xp hdd being installed. How to revert to my previous setup so that I can run the 10.4 hdd on its own?

I am an old timer and particularly like having xp and ubuntu on completely separate hdds that I can remove at will as I have got into a horrible muckup before with Grub.

OK so grub is on your MBR on the first drive which you dont have connected is this correct ?

And you want to boot as you did previously by choosing in the BIOS ?

---

### Post by ntu on 2012-04-27
I imagine that is where mbr has been put. I can easily disconnect the xp drive and want to do this.

---

### Post by ntu on 2012-04-27
And yes when I put the xp drive back in I want to boot using bios.

---

### Post by haqking on 2012-04-27
> **ntu said:**
> I imagine that is where mbr has been put. I can easily disconnect the xp drive and want to do this.

out of interest, it works when both drives are connected right ? so why do you need to have one disconnected ?

---

### Post by ntu on 2012-04-27
It gives me flexibility with other hdds I have here - for copying ubuntu to another hdd for backup and trying out other disros. I know this is unusual but it is what I like.

---

### Post by gordintoronto on 2012-04-27
Can you boot Ubuntu, disconnect the XP drive, then in Terminal run: sudo update-grub

---

### Post by ntu on 2012-04-28
Thanks for the advice gordintoronto. Tried what you said and it sounded like something was happening when I gave the command, but 10.4 hdd will still not boot when installed without the xp hdd.

Edit: And I made sure the jumper was in the master position on the hdd.

---

### Post by gordintoronto on 2012-04-28
"hdd will still not boot" -- what happens?

I hope you know that leaning on the shift key might help Grub appear.

Do you know which version of Grub is on the computer?

---

### Post by ntu on 2012-05-04
Thank you for your efforts gordintoronto. I have decided to use 10.04 as it is here and install 12.04 on a spare hdd I have here and move onto that. Thanks again.

---

