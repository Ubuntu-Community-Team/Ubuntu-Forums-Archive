---
title: "Hard Disk not recognized on install"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by docusn on 2008-05-02
I am attempting to install Hardy on an old Dell machine so I can evaluate it. When I get to step 4 (partition manager) no disk shows up and all the buttons are greyed out so I can go no further. I had had MEPIS 6 on this machine & all worked just fine. After the Hardy install failed, I deleted all partition information (IE a hdd with no OS or partitions). Still won't recognize that there is a hdd present. I have NO idea how to proceed from here.

The Live CD works just fine.

Dell XPS T600r; Intel Pentium III @600 MHz; 768 MB RAM; Western Digital hdd WDC 800JB.

---

### Post by bjm1904 on 2008-05-02
I'm unsure exactly what you mean when you say "wipe your hard drive" - I recommend you format it to ext3 if you can using a Live Linux distro or the Ultimate Boot CD, then trying again.

If this still fails, then you could always try installing Gutsy and then upgrading (though this isn't ideal). I don't think it's a driver problem - you've probably found a bug in the new hardy installer, so that might be worth reporting.

---

### Post by docusn on 2008-05-02
What I meant is that the HDD has no partitions, nor formatting, just a raw drive.

I tried Gparted from the live CD and it still wont recognize that there is any disk installed. I'm going to try running Gutsy's Live CD and see if I can format that way.

Thanks for your help.

---

