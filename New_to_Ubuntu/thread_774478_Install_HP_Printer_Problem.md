---
title: "Install HP Printer Problem"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by digf on 2008-04-29
Hello Forum

I've downloaded ubuntu 7.10 and am in the process of installing a HP PSC 1317
everything was going well until part way through the installation I received the following message "**PyQt init failed reverting to interactive mode**" from that point I couldn't get any further with the installation. 
I've tried googling for info but trying to understand the results is beyond me.
Can anyone advise me please.


Dell Dimension 2400  120 Gig Gard Drive  768 Ram  With a idiot at the controls. At the moment duel booting with XP but hopefully for not too long

---

### Post by Nathan_M on 2008-04-29
How are you going about installing it? Using HPLIP? That's what I would recommend if you're not. $ sudo apt-get install hplip. Then just connect the printer and it should automagically work!

Otherwise, could you point us to the instructions you're following? We can't really help you unless we know what you're trying to do.

---

### Post by digf on 2008-04-29
Hello     I didn't think to include that info but this is the link  [https://help.ubuntu.com/community/HPPrinterInstallation/PSC1210?highlight=%28install%29%7C%28printer%29](https://help.ubuntu.com/community/HPPrinterInstallation/PSC1210?highlight=%28install%29%7C%28printer%29)

Thanks

I got through step No1 ok but when I attempted step No 2 is when the message appeared

---

### Post by eapache on 2008-04-29
What happens if you install it with the System > Administration > Printing tool?

---

### Post by digf on 2008-04-30
> **eapache said:**
> What happens if you install it with the System > Administration > Printing tool?
Thanks for your suggestion. I did that and its working now.

---

