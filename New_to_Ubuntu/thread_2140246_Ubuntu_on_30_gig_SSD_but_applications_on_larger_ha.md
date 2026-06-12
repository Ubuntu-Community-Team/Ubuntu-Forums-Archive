---
title: "Ubuntu on 30 gig SSD but applications on larger hard drive"
date: 2013-04-29
forum: New to Ubuntu
---

### Post by Ikith on 2013-04-29
On Saturday I won an ultrabook/netbook at Linuxfest Northwest, they installed OpenSUSE on it which I prefer Ubuntu, so I did a general install of Ubuntu with everything to the SSD, looking back on that decision I regret it, but at this point there is no data on here that I would be hurt losing. I need suggestions partitioning this ultrabook/netbook to keep the speed of the SSD but utilize the large hard drive for everything else (Like new applications).

TLDR: Won ultrabook at Linuxfest Northwest, installed Ubuntu with non optimal partions, looking to correct my mistake and set it up so I can keep the speed of the SSD but use the larger hard drive for new applications/updates.

---

### Post by fantab on 2013-04-29
Congratulations on your Win!

30GB SSD is perfect. Install Ubuntu on it with only "/" mountpoint. I have only 20GB "/" and after installing everything I need I have more than 10GB to spare.

When we don't use separate "/home", Home folder will be created within "/". I don't use "/home". Instead to save my DATA I use just ext4 formatted partition. Which I mount manually when I want to read from it or write to it.

You can use your SSD to install ubuntu with "/" and the HDD as ext4 formatted DATA partition and save your Data on it. Also make a SWAP on HDD.

---

### Post by mastablasta on 2013-04-29
applicaitons should be on SSD. data can be elsewhere (for exmaple since this is notebook) this will likely be external disk unelss you have a hybrid disk or if the normal HDD is inside. 
if you have it inside you can just put home on that disk. or you can move it there. for example: [http://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/](http://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/)

home keeps user datat and users settings.

---

