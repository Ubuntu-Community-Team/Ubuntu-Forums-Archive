---
title: "Live CD won't boot and ends at comand prompt"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by johntuck on 2008-11-01
When I try to install/or run the Live CD of Ubuntu 8.10 on my Dell Computer Q8600 Quad Core 2.9 Dual Nvidia 8800 4 Gig ram I get the following problem.
I select the language then Try ubuntu without installing. The bar keeps going back and forth and finally I end up with a black screen and the following messages appear. 

A notification that Ubuntu is free software and that it comes free of charge.

Another notification that it comes with no Warranty 

Another webpage notice on where to find the manual and a notice on how to run a command as root or administrator user.
then comes the following command prompt:

ubuntu@ubuntu:`$

No error message or anything else. Please help I am a complete newbie and would appreciate any help.

---

### Post by Cypher on 2008-11-01
Just as a hunch..can you edit the boot options and add "MEM=2048MB" to limit Linux to just 2 GB of RAM and see if that works any better..

Also have you tried a previous version of Ubuntu (8.04 Hardy Heron) to see if that works?

---

### Post by johntuck on 2008-11-01
I tried the memory change - nothing changed.
Ubuntu Live CD 8.04 boots with no problems but without sounds since I have a X-F1 soundcard and that at the time so far as I can tell was too new at the time. Thanks for the help anyway. Any more ideas?

---

### Post by Bölvaður on 2008-11-01
when you are in boot options, press f4 and pick safe graphics mode. Þat should do it for you.

---

### Post by johntuck on 2008-11-02
I tried the save graphics mode and nothing changed. I tried it with the memory change and the safe graphics mode and still no change. I have checked the live cd on another computer and it works fine there so it can't be the cd. I have even tried the 64 bit edition and still no change. 
I dread to think of having to install 8.04 and manually updating it when I am not sure if the computer remains bootable after it or if it even gets that far.
How can I post a picture of the error message that I have taken with my digital camera?
Thanks again for any help and any more ideas out there?

---

### Post by fsando on 2008-11-06
I've seen the exact same on a Lenovo T500

Anyone knows something?

---

### Post by johntuck on 2008-11-06
In the meantime I have tried to use Wubi for the dual boot with Vista. It installs fine but when I boot with Grub I get he same black screen and message that I received with the live CD. I have also installed it from the alternate CD and I get the same message when booting.

---

### Post by handydan918 on 2008-11-06
my suspicion is that this is all about the nvidia card. Your system is in fact booting, but the xserver isn't able to start, probably because of the nvidia card.

---

### Post by johntuck on 2008-11-06
I thought about the very same thing. This card and the Nvidia motherboard has been giving me trouble from the start even with Vista which came preinstalled on the system.

---

