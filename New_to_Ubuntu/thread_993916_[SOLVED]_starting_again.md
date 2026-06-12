---
title: "[SOLVED] starting again"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by Hypo_Mix on 2008-11-26
I screwed up ubuntu in such a way that I can be bothered fixing it. however there is nothing important on that hard drive anyway so it can be wiped.

what's the easiest way to get ubuntu back to like it was when i first installed it?

---

### Post by bruce89 on 2008-11-26
> **Hypo_Mix said:**
> I screwed up ubuntu in such a way that I can be bothered fixing it. however there is nothing important on that hard drive anyway so it can be wiped.

what's the easiest way to get ubuntu back to like it was when i first installed it?

Backup /home, and install with a seperate /home partition.

---

### Post by Hypo_Mix on 2008-11-26
Sorry, would you be able to elaborate on that please?
sorry for newbness

---

### Post by mapes12 on 2008-11-26
Take a look at this link and use the guides to help you on your way: [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by ElderDrake on 2008-11-26
The easiest way would probably be just to reinstall the OS

---

### Post by theozzlives on 2008-11-26
when you install, make a seperate partition for Home so you don't lose your data & settings if you re-install again. here's mine:

150 GB HD:

10 GB root (/)
10 GB tmp (because I rip DVDs, you won't need this)
the rest home
I have 2 GB RAM so I don't need "swap" but normally about 512 MB

Just select  "manual" to partition your HD

---

### Post by icanfly0307 on 2008-11-26
Even though you may have a lot of RAM, I would still recommend having swap space around. If you  use hibernation, swap space is necessary and it won't work around it. My suggestion would be that you create a swap partition that is a little bit more than the amount of RAM that you have.

---

### Post by theozzlives on 2008-11-26
> **icanfly0307 said:**
> Even though you may have a lot of RAM, I would still recommend having swap space around. If you  use hibernation, swap space is necessary and it won't work around it. My suggestion would be that you create a swap partition that is a little bit more than the amount of RAM that you have.

I don't use hibernation and most Ubuntu books say twice the amout of RAM. I'm sorry I'm not wasteing 4 GB of realistate to a swap partition

---

### Post by nynoah on 2008-11-26
I would still keep the swap.  I have 2 gigs of ram and I dip into my swap on a regular basis.

---

