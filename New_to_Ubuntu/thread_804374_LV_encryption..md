---
title: "LV encryption."
date: 2008-05-23
forum: New to Ubuntu
---

### Post by maxbarjr on 2008-05-23
During the install of Ubuntu 8.04 Server, I selected Encrypt the Logical Volume and asked for a passphrase in which I did.  Now everytime my linux box reboots, I have to enter the passphrase.  Is there a way for my linux box to remember the passphrase during the first initial boot up, or how to get rid of the encryption without re-installing again?

TIA

---

### Post by hyper_ch on 2008-05-23
what use would full encryption be if you don't have to enter the password? Remember, disk encryption is used against physical data theft. If you have a fully encrypted notebook and leave it in the train or restaurant or somewhere, he who finds the notebook can't get access to the data.

There are ways of getting rid of the encryption but it's tedious...

---

### Post by maxbarjr on 2008-05-23
hyper_ch, thanks for the quick turn around.  I know that password and encryption are very important.  But my scenario is this, I am configuring a DNS server on this box and it will be 24/7 operational.  What if there will be power failure or something that will lend the server to reboot, and it will wait for the passphrase to be entered manually before it properly bootup.

---

### Post by hyper_ch on 2008-05-23
that's the case...

---

