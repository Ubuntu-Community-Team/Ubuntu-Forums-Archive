---
title: "Can I dual boot two versions of Ubuntu"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Nemo0075 on 2008-05-16
I am currently running 8.04LTS 32 Bit which I upgraded to from 7.10.  I love it and have had very few issues with it.  I have managed to get everything customized to my liking.  

I received my 64 Bit 8.04LTS disc today and tried it live and everything works fine.

I would like to upgrade from the 32 Bit to 64 Bit.  Can I simply put the 64 Bit on a new partition and choose which version to run at startup?  I am hesitant to wipe the hard drive just yet since it took me while to get everything just right.

Lastly, assuming the answer to the above question is yes, can I easily delete the 8.04LTS 32 Bit partition once I am happy with the 8.04LTS 64 Bit install or vice versa if I am unsatisfied with it?

Thanks for all the help in the past, present and future.:KS

---

### Post by overdrank on 2008-05-16
> **Nemo0075 said:**
> I am currently running 8.04LTS 32 Bit which I upgraded to from 7.10.  I love it and have had very few issues with it.  I have managed to get everything customized to my liking.  

I received my 64 Bit 8.04LTS disc today and tried it live and everything works fine.

I would like to upgrade from the 32 Bit to 64 Bit.  Can I simply put the 64 Bit on a new partition and choose which version to run at startup?  I am hesitant to wipe the hard drive just yet since it took me while to get everything just right.

Lastly, assuming the answer to the above question is yes, can I easily delete the 8.04LTS 32 Bit partition once I am happy with the 8.04LTS 64 Bit install or vice versa if I am unsatisfied with it?

Thanks for all the help in the past, present and future.:KS

HI and yes you can create another partition for the 64bit and keep the 32bit until you make your choice.

---

### Post by volkswagner on 2008-05-16
You can create a new partition during the install (manual partitioning).  You can use the same swap partition.  Most people say don't share the home partition.  Either create a new one, or leave it part of the OS partition.  The default setting for grub should be fine (you will find it under advanced prior to finalizing install).

---

