---
title: "Partitioning - separating / and /home after install"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by GoBlue! on 2008-10-28
Back-to-back posts here, different topic.  I've searched, and I'm sure this answer is out there in a million places, but I'm still scratching my head.

I just wiped a hard drive clean and had Ubuntu 8.04 installed on the entire drive, using the installer's default preferences.  I believe this probably made one big partition (it's a 150GB drive) and a 4GB or so swap partition (I have 2GB RAM).

I've since read that it may be smart to make '/' one partition of about 10GB, the swap 4GB, and the rest '/home'

Apparently this would allow future updates to just stick to the '/' partition and not interfere with any of the /home stuff?

If this *is*a smart thing to do, how do I go about repartitioning now that everything's installed?

Thanks,
Jim

---

### Post by zvacet on 2008-10-28
[Here]("http://psychocats.s465.sureserver.com/ubuntu/separatehome")

---

### Post by bumanie on 2008-10-28
Here is a [guide]("http://www.psychocats.net/ubuntu/separatehome") to separate / and /home post installation. Hope it helps.

---

### Post by Paqman on 2008-10-28
> **GoBlue! said:**
> (I have 2GB RAM).

I've since read that it may be smart to make '/' one partition of about 10GB, the swap 4GB, and the rest '/home'


With 2GB of RAM, you won't need a swap any bigger than 2GB. The old 2xRAM rule of thumb went out the window when computers started getting lots of RAM. I have 2GB of RAM myself, and the system never even dips into swap space. You need swap to be as big as your RAM if you want to hibernate the machine, otherwise you could get away with even less if you want.

---

### Post by bumanie on 2008-10-28
> **Paqman said:**
> With 2GB of RAM, you won't need a swap any bigger than 2GB. The old 2xRAM rule of thumb went out the window when computers started getting lots of RAM. I have 2GB of RAM myself, and the system never even dips into swap space. You need swap to be as big as your RAM if you want to hibernate the machine, otherwise you could get away with even less if you want.

+1 - 2gb ram is more than ample for swap under nearly all circumstances.

---

### Post by GoBlue! on 2008-11-02
Excellent.  A quick follow-up question: I'll still have to use microsoft word to remain compatible with people at work (primarily to share Endnote libraries, etc.).  I'd like to bring files over to the Linux desktop at home, however, to print on my laser printer, etc.

So, if I repartition according to the instructions provided, I would make an ext3 partition.  But would it be better for me to make a fat32 partition (this is a 6-yr-old desktop) to make sure I can bring over files from my windows machine?

Thanks
Jim

---

### Post by ugm6hr on 2008-11-02
You can copy files to an ext3 partition just fine.

If you don't have windows on this machine - there is no reason to have a fat partition at all.

---

### Post by ssneff on 2008-11-02
Hey all...
I am a ubuntu virgin.  I am sitting here trying to partition and install 8.10 so I can stop this Vista nightmare that Dell forced on me.  I am using Gparted and I am at the point of choosing a filesystem.  I have no idea what type to choose. I dont want anything else to do with Vista.  How do I handle the partitioning?  For the record, I am not what you would call high speed at any of this, so I kinda need some "spoon feeding" here.

Thanks
Steve

---

