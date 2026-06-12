---
title: "How do I make a swap partition?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by lostlinuxkiwi on 2008-05-31
Hi 

I bought an acer notebook that came with ubuntu pre-installed and I have just realised it has no swap partition. It never came with a proper ubuntu installation cd but rather with what it calls an e-recovery cd. This basically restores ubuntu to a vanilla install but doesn't give me the option of partitioning. 

I really cant be bothered going through installing it again as i have already done this twice with this computer anyway. is there some way i can setup a partition to use as a swap? I have a 7.04 ubuntu dvd, a 7.10 xubuntu disc and a 8.04 kubuntu disc and the 7.10 recovery disc that i now realise is useless.

help would be greatly apreciated.

thanks

---

### Post by jd65pl on 2008-05-31
You can do it from a live cd, resize your partition using the partition editor, then add a swap partion.

---

### Post by shifty_powers on 2008-05-31
do you have gparted installed?

---

### Post by lostlinuxkiwi on 2008-05-31
I dont have gparted installed but I could install it. The 7.04 dvd works as a live disc and has gparted on it. Can I use that?

---

### Post by jd65pl on 2008-05-31
Use the live cd, If you wont be able to resize partitions which are mounted when running off the hard drive which may cause you problems as you will not be able to unmount a root or home partition.

---

### Post by overdrank on 2008-05-31
> **lostlinuxkiwi said:**
> I dont have gparted installed but I could install it. The 7.04 dvd works as a live disc and has gparted on it. Can I use that?

HI and I believe so and this link may help also
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by lostlinuxkiwi on 2008-05-31
Thanks guys. Actually it looks like just adding a swap file will be easiest. Is this as good as a partition in your opinions?

---

### Post by overdrank on 2008-05-31
> **lostlinuxkiwi said:**
> Thanks guys. Actually it looks like just adding a swap file will be easiest. Is this as good as a partition in your opinions?

Hi, I did it once with the link I provided and I could not tell the difference. :)

---

### Post by lostlinuxkiwi on 2008-05-31
Sweet I'll give that a go. cheers

---

