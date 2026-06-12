---
title: "Installing 32-bit 12.04 Ubuntu on a 64-bit Machine"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by Andavane on 2012-07-23
The Thinkpad I am on at the moment is 64 bit X201i, and I remember when I dual-booted last year with Ubuntu I had to delete a partition (Lenovo Windows Recovery) to enable me to have a partition for the swap file.

Meanwhile, my friend got a Sony Laptop 64 bit Windows Laptop, he also dual-booted it with Ubuntu, but he did it with the 32-bit Ubuntu, so I asked him how he had got on, and he replied it was fine. Also he had the "Install Ubuntu Side by Side" option, which I'm sure I didn't get last time. Privately I wondered if he had done something wrong.

This year it was also time for me to replace my side-kick computer, having passed my former 11.6 incher on to a friend, and got the 64-bit Thinkpad 11.6" X121E. I decided to install Ubuntu 12.04 32-bit  on the new 11.6" from USB key, copying my friend really. I did this last week, and I also got the "Side by Side" option which I used and still have my recovery partition on that one. I did this last week.

I don't know where it put it all, but all seems to be working fine, for what I need. So I fell to wondering what this is about.

I read this article just now[https://help.ubuntu.com/community/32bit_and_64bit]("https://help.ubuntu.com/community/32bit_and_64bit")

but I don't really "Get" this "How to Get It to Work" stuff as it just seems to work. I also get the feeling that the 32-bit runs a bit better.

---

### Post by d.atanasov on 2012-07-23
Hi, 

In principal I use 64-bit operation system because my processor can handle it. I don`t think that if you don`t use your computer for really heavy calculations of what there it is you will not get a feeling for what is better 32 or 64-bit. I also don`t understand what is your question do you want to run 64-bit programs on 32-bit operation system or vice versa ? 

cheers

---

### Post by Andavane on 2012-07-23
> **d.atanasov said:**
> Hi, 

... I also don`t understand what is your question do you want to run 64-bit programs on 32-bit operation system or vice versa ? 

cheers
Hi
I am running 64-bit Ubuntu on my main 64-bit machine,
and running 32-bit Ubuntu on my side-kick machine which is also 64-bit.

---

### Post by d.atanasov on 2012-07-23
> **Andavane said:**
> Hi
I am running 64-bit Ubuntu on my main 64-bit machine,
and running 32-bit Ubuntu on my side-kick machine which is also 64-bit.

Sorry for this but I still don`t see what is your question ? How 64-bit system works or somethings different ? 

cheers

---

### Post by Lupajz on 2012-07-23
Dude you should really work on your way of telling something to other ppl :/ Yack ! 

any way don't you mean like running 32bit apps on 64bit ? 

```
sudo apt-get install ia32-libs
```

---

### Post by Wirephire on 2012-07-23
If I understand correctly your question then your problem is in fact not related with Ubuntu in general or neither with 32 or 64 bit systems.

When you made your first installation (where you had to delete the recovery partition), do you remember how many partitions you had?
If I'm right, they were Recovery, Windows (C: ) and another one for Storage (D: ). Then you created another partition for Ubuntu which made them 4, probably [primary](https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics#Primary_Partition_Rules_and_Conventions). As one HDD can't have more then 4 primary partitions, you weren't able to make SWAP without creating an extended partition. Thats why you had to delete another one. 

Read more about partitioning in [Ubuntu Wiki]("https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics").

[I]
~wph[/I]

---

