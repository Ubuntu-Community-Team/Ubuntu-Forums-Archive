---
title: "Quick Question Re: Multiple Installs, Partitions"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Bennett2005 on 2008-04-29
Hey gang,

I have a quick question for you guys.

I currently have Ubuntu and Windows XP set up on separate partitions (XP is basically serving as a glorified gaming platform).

I gave myself a 3rd partition to experiment with other distros.  I was thinking of installing Fedora or even something simple like Kubuntu just to give KDE a go.

The question:  Will I screw up my Grub settings if I start installing and removing other Linux flavors from that 3rd partition?  I know XP is a violent abusive drunkard when it comes to Grub (I had to learn that the hard way; I tried installing XP after Ubuntu first).

Would additional Linux distros leave my Grub alone?  Is there anything I should be aware of before I try?

Ok, that was more like 3 questions.

---

### Post by schauerlich on 2008-04-29
By default, most distros will want to use their own version of grub. There should be an option during the installation to leave the current grub alone.

---

### Post by Bennett2005 on 2008-04-29
> **EDavidBurg said:**
> By default, most distros will want to use their own version of grub. There should be an option during the installation to leave the current grub alone.

Thanks!! :)

---

### Post by iSplicer on 2008-04-29
I strongly suggest you make a seperate /boot partition for t his, since you can write to it and make changes easily.

---

