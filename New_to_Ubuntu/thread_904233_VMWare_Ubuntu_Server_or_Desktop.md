---
title: "VMWare: Ubuntu Server or Desktop?"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by paolino76 on 2008-08-29
Hi, I have decided to install Ubuntu on my laptop (Sempron, 3Gb RAM, 320Gb HD). Yay for that!

All the applications will run inside a virtual environment (VMWare), so the only package that I'll install over a minimal base system will be VMWare (and maybe Rhythmbox, but no Gimp, no OpenOffice, no InkScape etc.) I'm just wondering if in this kind of setup would be better to install Ubuntu server or desktop.

Are there any differences at kernel level to justify the adoption of one edition in place of the other?

Thanks,
Paolo

---

### Post by swoll1980 on 2008-08-29
server if that's all your using it for, and you know your way around a cli terminal(there's no gui on the server edition)

---

### Post by dominiquec on 2008-08-29
Not sure about the wisdom of running everything on VMWare on a laptop, but if that's what you want....it's certainly doable.  Seems to be more work, though, and less efficient from a performance perspective.

Anyway, to answer your actual question: the stock kernel of Ubuntu 8.04 Server requires PAE, which will likely not be present in your Sempron processor.  (You'll need to verify this.)  If there's no PAE, there's no point in running Server.

Try a minimal install using the Alternate Install CD, instead.

---

### Post by paolino76 on 2008-08-29
> **dominiquec said:**
> Not sure about the wisdom of running everything on VMWare on a laptop, but if that's what you want....it's certainly doable.  Seems to be more work, though, and less efficient from a performance perspective.


This is my rationale. I don't care much to have an optimized system if then I can't upgrade it when I need to. That already happened during the upgrade from 7.04 to 7.10 and was not fun. It failed and I lost my applications, settings and data (even if most of them had got backed up). 99,9% my fault, no doubts.

But being perfectly aware that I can fail again, I'm trying to create a "low risk" upgradable working environment.

So I decided to keep a minimal 8.04LTS installation on a dedicated 10Gb all-in-one partition as main OS just to run vmware environments, each located on a separate partition. This way I have two benefits:

1) I can backup my hosted installations (apps, settings and data) in one shot and before the upgrade process begins (I have a large disk with enough space to park vmware images). And then try to upgrade again;
2) I can upgrade the main OS without worries. If the process should fail I don't ruin anything important, I'll just proceed with a new, light and quick installation and I'll be fully functional in no time, with all my virtual installations ready to be used again.

Does it make sense to you?

---

### Post by Vivaldi Gloria on 2008-08-29
> **paolino76 said:**
> Does it make sense to you?

Not really. There is a lot of performance penalty for using a virtual system. I suggest you make another partition for your data so when needed you can install an OS to its own partition without loosing any data. Quick and efficient. Actually make two partitions and install a backup OS in one of them. Then you "can upgrade the main OS without worries".

Also see my sig for different CLI versions of ubuntu.

---

