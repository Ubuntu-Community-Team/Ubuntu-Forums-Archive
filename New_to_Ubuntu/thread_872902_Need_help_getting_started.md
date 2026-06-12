---
title: "Need help getting started"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by DKCorey on 2008-07-28
I've burned the CD and recieve the option at startup to boot from 
either windows or ubuntu.  After selecting ubuntu,. I get a splash 
screen, then I get a screen with a message that begins: 

[155.147076]ata2.00 exception Emask 0x0 Sact 0x0 Serr............. 

Thanks

---

### Post by Walter Melon on 2008-07-28
> **DKCorey said:**
> I've burned the CD and recieve the option at startup to boot from 
either windows or ubuntu.  After selecting ubuntu,.

So...did you install ubuntu or are you running off the live cd? Could you give some more information?

---

### Post by gjoellee on 2008-07-28
if this happened with the live CD the easiest thing to do is actually to burn a new CD

---

### Post by jamesrfla on 2008-07-28
Good questions. Don't know the answer.

---

### Post by Bodsda on 2008-07-28
hi, i think you may be talking about grub for the selection, if so when you see the choices move to ubuntu and press 'e' then find the boot line (the long one) and highlight and press 'e', remove the word 'quiet' from the line and press 'esc'. then go grab a piece of paper and a pen, then with the boot line highlighted press 'b'. When you see the splash screen there should be writing underneath it, please write down everything you see. Also this is a confirmed bug no. 223014 [https://bugs.launchpad.net/ubuntu/+bug/223014](https://bugs.launchpad.net/ubuntu/+bug/223014)

Thanks 

Bodsda

---

### Post by DKCorey on 2008-07-28
Thanks, folks - here is some more info.

I downloaded the iso file and did the md5sum check.

I then burned two separate CDs, both of which display the same behavior.

The machine is a dell inspiron 530 with a p4 dual core processor

---

### Post by cprofitt on 2008-07-28
To be honest I have not seen that error before, but you might want to burn a CD on another computer if you have the option...

---

### Post by Bodsda on 2008-07-28
DKcorey -- have you actually installed ubuntu? if so was it a wubi(windows) install or a live cd install?

Thanks 

Bodsda

---

