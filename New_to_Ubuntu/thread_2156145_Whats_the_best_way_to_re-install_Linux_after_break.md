---
title: "Whats the best way to re-install Linux after breaking it?"
date: 2013-06-20
forum: New to Ubuntu
---

### Post by Wiking on 2013-06-20
What's the best way of re-installing Linux after say breaking your system with tarballs or if you want to try a new distro?

I usually just delete the partitions and format new ones and install into those. I'm sure there is a more pragmatic way of going about this.

Also, once a distro is deleted and Grub is updated with a new distro is the old distro still in Grub (boot parition) or is it deleted?

---

### Post by Irihapeti on 2013-06-20
You can, as long as you're sure you've got the right partition, just install over the top of it. You need to check the option to format the partition when installing.

Installation of grub during a new install will overwrite whatever is in the boot record.

---

### Post by monkeybrain2012 on 2013-06-20
I clone my installation with fsarchiver. When something goes terribly wrong just restore the image then back in business. It just save my a** yesterday. :)

---

### Post by Paqman on 2013-06-20
If you're messing around experimenting and breaking things you might want to consider using a VM. You can create a snapshot of a running system in Virtualbox, if you mess it up then rolling back to the snapshot is just a couple of mouse clicks.

---

