---
title: "Help needed with multiple OS"
date: 2007-12-28
forum: Other OS Talk
---

### Post by dptxp on 2007-12-28
I got XP and Ubuntu on my laptop. Ubuntu has a separate /home. Now I plan to install Sidux too.Triple boot.

I cannot use the Ubuntu /home as Sidux /home, can I ?

---

### Post by LaRoza on 2007-12-28
you can.

---

### Post by mips on 2007-12-28
> **LaRoza said:**
> you can.

You can but I would not advise it.

---

### Post by LaRoza on 2007-12-28
> **mips said:**
> You can but I would not advise it.

Neither would I.

---

### Post by jken146 on 2007-12-28
You can but the hidden config files that programs put in your home directory can clash if you use the same user name in both distros.

---

### Post by fwojciec on 2007-12-28
Perhaps the best thing to do in this case would be to repartition the disk so you have a separate small /home partition for each distro, or even just use a single partition setup for each without separate /home partitions, and then create an additional partition for sharing between the distros where you could keep your files like documents, music and so on (you could also share this partition with windows as well)...

If you really want to share the /home partition between the distros make sure that you have different default users in each so each distro gets a different user home folder within the /home partition.

---

### Post by dptxp on 2007-12-28
Thanks. I could not create any /home.
I installed sidux Lite on laptop with XP and Ubuntu. Some boot options of Ubuntu from Grub went missing so I reinstalled Ubuntu.

I like it though it is KDE (never liked KDE) , the Lite installed in 8 minutes. 

But my problem of sidux not recognizing the Ubuntu / remains even after enabling automount of the / partition. I do not need to access the root partition from sidux, but I am asked to press Ctrl+D on every boot to skip maintenance. How do I solve this ?

I do not see any packages except a few in meta-packages. No Synaptic, no add/remove. Do I have to install by using apt-get ?

---

