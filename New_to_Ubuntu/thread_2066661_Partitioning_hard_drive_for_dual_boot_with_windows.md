---
title: "Partitioning hard drive for dual boot with windows 7"
date: 2012-10-05
forum: New to Ubuntu
---

### Post by Louis-Philippe on 2012-10-05
Hi everyone

I have just reformatted my computer and I have installed my windows 7 using the factory recovery disks. I have already shrunk the windows 7 partition down to about 100 gb, and now I wanted to create two new partitions using GParted, one 100-gb partition for all things ubuntu and another partition which is used to store files shared by both operating systems (music...) 

However since there are already three primary partitions on my drive I can only create one more:

[https://dl.dropbox.com/u/12349511/Screenshot%20from%202012-10-04%2021%3A12%3A49.png]("https://dl.dropbox.com/u/12349511/Screenshot%20from%202012-10-04%2021%3A12%3A49.png")

Can anyone tell me how I can go about solving this problem? (How would you partition this if it were your computer?) 

Thanks in advance!

LP

---

### Post by puntigamer on 2012-10-05
Sure thing! You should create an extended partition instead of many primaries. (You will be able to have 3 primaries and an extended) For example you can store all your linux stuff on a single extended partition (ext4 / and swap etc). So create an extended partition in GParted and than create more partitions inside it. ;)

---

### Post by Louis-Philippe on 2012-10-05
Thanks for your reply!

How would you do this concretely? Is there a way to merge all the partitions already created by windows into one logical partition, then creating two more logical partitions one of which I split up into the partitions needed for ubuntu? 

Or do I simply create one extended partition and make a logical partition where I store the data used by both ubuntu and windows?

Thanks in advance!

LP

---

### Post by newb85 on 2012-10-05
> **Louis-Philippe said:**
> Or do I simply create one extended partition and make a logical partition where I store the data used by both ubuntu and windows?

Exactly.  Your extended partition should be #4, and then you can put your Ubuntu partition and your shared data partition inside it.

By the way, if no one has said it yet, Welcome to Ubuntu!

---

### Post by Wim Sturkenboom on 2012-10-05
Note that you can only create ONE extended partition. This extended partition however can contain a number of logical partitions.

When you install Ubuntu and use the manual partitioning, you can select between primary and logical partitions. In your case, you should choose logical. The first logical partition that you create will automatically create the exdtended partition as well (the extended partition will be the size of the remaining space after the three primary partitions).

---

### Post by Louis-Philippe on 2012-10-05
Now I understand, I will get to that tonight! 

Thanks, I've been browsing the forum and there is a lot of useful information and lots of people willing to help! 

Thanks again for your help, you have probably saved me from doing it completely wrong and having to start from scratch again!

LP

---

