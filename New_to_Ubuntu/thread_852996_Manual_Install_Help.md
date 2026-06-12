---
title: "Manual Install Help"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by Helical on 2008-07-08
I'm planning on partitioning my HDD like this: [Vista][Linux Files] [Ubuntu OS] [Swap]. And, I understand, I have to do a manual install to do this. Can someone explain this process for me? Vista is already installed.

Also, I'm wondering how I can increase the size of my Vista partition later if I decide I need more space.

Thanks.

---

### Post by Elfy on 2008-07-08
You could use one of many options to resize partitions later.

As far as the manual install goes it is quite simple to do - have you made the partitions yet? If not you can do it in the livecd easily.

To use the manual install option - I'm not certain if you can build partitions inside this option but I think so - if not there is an editor available.

Once you have a swap partition the installer will pick it up and use it so all you actually have to do is pick the partition you wish to install it on and edit the partition to give it the correct mountpoint -/

That's it :)

---

### Post by Sbarton on 2008-07-08
You could have a look here:[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
for dual boot.It is xp & Ubuntu but is worth looking at. I would partition as follows: /(root), Home , swap.
regards

---

### Post by Helical on 2008-07-08
Hm, I didn't realize it was so easy. And no I haven't made the partitions yet, I actually don't have the computer yet...but I wanted to figure out how to do it before hand. Anyways by manual install I really meant the manual *partioning* in G-Parted (I think that's the Ubuntu program).

Another question: my computer has 4GB of RAM so my Swap partition needs to be 4GB as well, correct?

---

### Post by Elfy on 2008-07-08
You might be better of using the vista tool to do the original resizing - you can't obviously use the vista tool to make linux partitions, there used to be problems without - but I couldn't sya whether that is still the case.

Use gparted in the livecd to make you're partitions from the free space - if you want to suspend or hibernate then RAM=swap, if you don't want to do that then I doubt if you would find it necessary to have that much swap, with 1Gb RAM I ver rarely  use more than 256Mb of my swap. You can in any case make mopre without too much trouble.

---

