---
title: "No BTRFS Love in Oneiric?"
date: 2011-07-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by moore.bryan on 2011-07-19
While screwing around with a "sandbox" Oneiric install, I thought I'd use BTRFS as the standard since, according to what seems like many, EXT4 is just "stop-gap" for it, and I ran into an interesting problem. If one chooses BTRFS for / and /home, then GRUB won't install onto one's /dev/sda.

Hmm... is this normal?

---

### Post by teh603 on 2011-07-19
> **moore.bryan said:**
> While screwing around with a "sandbox" Oneiric install, I thought I'd use BTRFS as the standard since, according to what seems like many, EXT4 is just "stop-gap" for it, and I ran into an interesting problem. If one chooses BTRFS for / and /home, then GRUB won't install onto one's /dev/sda.

Hmm... is this normal?I don't think you can boot off BTRFS just yet. You still have to have an EXT2/3/4 partition for booting. There was an announcement about it when they first got support for it, that booting from it was something further down the pipe.

---

### Post by DoeRayMe on 2011-07-19
it will install and boot fine, with btrfs as the whole partition, just really slow at booting because of the fsck issue at the moment

---

### Post by moore.bryan on 2011-07-19
So I just can't specify two partitions?

---

### Post by ratcheer on 2011-07-19
> **moore.bryan said:**
> So I just can't specify two partitions?

Yes, if you specify a small partition as /boot, everything else (as /) can go to a btrfs partition. You can make /boot an ext2 partition of about 300 MB.

Tim

---

### Post by moore.bryan on 2011-07-19
Thanks for that info... what's happening with BTRFS that it's not directly bootable?

---

### Post by ratcheer on 2011-07-19
> **moore.bryan said:**
> Thanks for that info... what's happening with BTRFS that it's not directly bootable?

A question for the ages. They have been talking about it since Maverick, I think. In my opinion, they actually announced it a couple of times, but always backed off.

Tim

---

### Post by moore.bryan on 2011-07-19
Makes me wonder why...

---

