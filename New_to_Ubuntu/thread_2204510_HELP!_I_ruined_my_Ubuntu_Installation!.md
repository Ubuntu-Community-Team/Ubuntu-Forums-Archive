---
title: "HELP! I ruined my Ubuntu Installation!"
date: 2014-02-08
forum: New to Ubuntu
---

### Post by Nikhi_Bhambra on 2014-02-08
Please Help ASAP!

I tried installing ubuntu on a 50GB Partition on my 1TB drive. I have all my data on my Windows 7 partition. I installed ubuntu on the 50gb partition. When I finished the installation, I rebooted and when I booted I couldnt get into Windows. It booted into the grey and black screen when you boot off of a dvd. I went in to GParted and deleted the partition and tried to reallocate it to the space to windows. I screwed up, and it wouldnt move because there was an error. So I booted back up off of the CD again and when I went back into GParted it says that my Primary Windows Drive is located under /media/ubuntu/. 

Please help me, I really need my Windows Back, and I dont want to loose my data.

HELP ASAP!

---

### Post by deadflowr on 2014-02-08
Could you either post a screenshot of gparted or run this
```
sudo parted -l
```
and post the results.
It'll help us understand the layout of the hard drive now.

---

### Post by tfrue on 2014-02-08
Would you post the boot-info URL here please? Follow the instructions at this site:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

