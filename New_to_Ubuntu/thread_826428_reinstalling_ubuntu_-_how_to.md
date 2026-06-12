---
title: "reinstalling ubuntu - how to?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by paker on 2008-06-11
As recommended, I divided the hard drive to 2 partitions. 4 GB and the rest 100+ GB. The latter is the home drive (for data) and the rest of ubuntu is in the first 4 GB partition. 

Now I want to reinstall ubuntu without touching the home drive. How do I do it actually? I can install ubuntu in the 4 GB partition. Will this give me 2 home drives? 
Thanks.

---

### Post by powerpleb on 2008-06-11
> **paker said:**
> As recommended, I divided the hard drive to 2 partitions. 4 GB and the rest 100+ GB. The latter is the home drive (for data) and the rest of ubuntu is in the first 4 GB partition. 

Now I want to reinstall ubuntu without touching the home drive. How do I do it actually? I can install ubuntu in the 4 GB partition. Will this give me 2 home drives? 
Thanks.

You will need more than 4gb most likely. You will also need a swap partition. Luckily all of this can be sorted out through the installer. You have to specify Ubuntu system partition as mount point "/" and home partition as mount point "/home"

when you say you don't want to touch the home partition, do you mean you have data in it already?

---

### Post by paker on 2008-06-11
> **powerpleb said:**
> You will need more than 4gb most likely. You will also need a swap partition. Luckily all of this can be sorted out through the installer. You have to specify Ubuntu system partition as mount point "/" and home partition as mount point "/home"

when you say you don't want to touch the home partition, do you mean you have data in it already?
Yes, I have data in the home partition and don't want to erase it. I will follow your instruction.

PS: Yes, I have a separate swap.

---

### Post by powerpleb on 2008-06-11
> **paker said:**
> Yes, I have data in the home partition and don't want to erase it. I will follow your instruction.


Ok then be careful not to format the drive and you should be fine.

---

