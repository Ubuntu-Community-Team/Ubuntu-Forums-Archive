---
title: "Installing???? but not working!!!!!"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by frankjeffries on 2012-05-01
I have used and installed ubuntu before but I have been trying for last 4 days to install ubuntu 12.04 it installs ok and then asks me to reboot but when I do I cannot find it. I am trying to Dual boot with Windows 7 ultimate. I have tried all 3 options that you get to install even manually setting up the partitions. I was lucky when I did this because when it asked me to reboot It said error loading operating system and everything had been wiped from my hard drives even the Bios. Here I was lucky because I had just setup a new PC with a gigabyte H77M-D3H motherboard which has a Dual Bios and was able to put in a windows 7 rescue disc and the Bios was copied across and so my windows 7 system was saved. It seems like the partitioning part of ubuntu 12.04 does not work. I have seen other people posting a similar thing happening to them here. The other thing I'm thinking is I have 32 gig of ram and maybe its installing into the ram so when it reboots it wipes the ubuntu 12.04 files. Just not good enough to know.

---

### Post by jtarin on 2012-05-01
Why let Ubuntu partition? Partition it yourself then you can indicate during install where you want it .
Look to my sig for the link to EasyBCD.

---

### Post by souravc83 on 2012-05-01
Yes. Most tried and tested way is use Windows 7 to shrink the primary partition, and create an unformatted space.
Google "shrink parition in Windows 7" to see how to do that.
Then you can install Ubuntu in this unformatted space. Ubuntu in general recognizes this automatically.
But if you are concerned it installs into the RAM, you can just specify it.

---

### Post by frankjeffries on 2012-05-01
> **jtarin said:**
> Why let Ubuntu partition? Partition it yourself then you can indicate during install where you want it .
Look to my sig for the link to EasyBCD.

I partitioned it myself and it was an empty 200gig sata drive!!!

---

### Post by frankjeffries on 2012-05-01
> **souravc83 said:**
> Yes. Most tried and tested way is use Windows 7 to shrink the primary partition, and create an unformatted space.
Google "shrink parition in Windows 7" to see how to do that.
Then you can install Ubuntu in this unformatted space. Ubuntu in general recognizes this automatically.
But if you are concerned it installs into the RAM, you can just specify it.I cannot specify because it does not give me that option just says delete windows 7!!! install alongside windows 7!!! or partition hard drive which I did!!!!other ubuntu's have said they will put a starter under windows on screen but 12.04 does not ask to do this???so does not give option to boot but its installing i can see by the space it uses in hard drive.

---

### Post by Toadmund on 2012-05-01
I am also having this problem, a whole hard-drive I put 12.04 on, on the other HD is 11.10.
12.04 does not load, says something about kernal not loading.

I tried setting the boot order on my BIOS, but it won't let me?

---

### Post by Toadmund on 2012-05-01
Someone posted this:
```
sudo dpkg-reconfigure grub
```

And it solved my problem.

---

### Post by frankjeffries on 2012-05-02
> **Toadmund said:**
> Someone posted this:
```
sudo dpkg-reconfigure grub
```

And it solved my problem.Not much good telling us a code to put in when it does not start????

---

### Post by Toadmund on 2012-05-03
Try it from the live CD perhaps?

---

