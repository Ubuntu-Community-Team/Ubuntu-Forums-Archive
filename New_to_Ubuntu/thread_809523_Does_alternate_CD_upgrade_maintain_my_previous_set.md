---
title: "Does alternate CD upgrade maintain my previous settings?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by d.kusummmanth@gmail.com on 2008-05-27
I'm using Ubuntu 7.10 and wanna shift to 8.04. 

But, Does alternate CD upgrade maintain my previous settings?

---

### Post by Joeb454 on 2008-05-27
Usually any type of upgrade will preserve your settings, though personally I would recommend doing a backup anyway just in case :)

---

### Post by Majorix on 2008-05-27
A fresh install asks if you want to keep the previous account during the installation process, but I have never used it so I don't know if it would keep your /home folder. Please wait for someone to confirm if it works.

---

### Post by Joeb454 on 2008-05-27
I think that's actually for Users installing over a Windows install ;)

---

### Post by tramir on 2008-05-27
The best thing would be to have a separate partition for /home. You can still do it, even if you already installed Ubuntu. Use the GPartEd LiveCD to create the partition, copy everything from /home into that new partition (don't forget the hidden files), and then when using the installer, just choose that partition to be mounted as /home. And you keep everything. See also [this tutorial]("http://www.psychocats.net/ubuntu/separatehome").

---

### Post by Majorix on 2008-05-27
> **Joeb454 said:**
> I think that's actually for Users installing over a Windows install ;)

Oh, please ignore me then :)

---

### Post by mister_pink on 2008-05-27
Nope, there is a home preservation thing. But can't you also use the alternate CD to do just an upgrade rather than a reinstall? That will certainly keep your settings.

---

### Post by Joeb454 on 2008-05-27
> **mister_pink said:**
> Nope, there is a home preservation thing. But can't you also use the alternate CD to do just an upgrade rather than a reinstall? That will certainly keep your settings.

This is what I suggested :) Though personally - after I had an issue with an upgrade, I backup before upgrading

---

