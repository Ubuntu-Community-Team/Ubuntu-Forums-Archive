---
title: "Using Clonezilla to clone Ubuntu 12.04"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by mihnea13 on 2012-12-28
Hello, 

I want to clone my recently installed Ubuntu 12.04 (I`m a new user of Linux and I want to learn more by tinkering and I want a safe net in case I`ll mess it up really bad...I`ve spent a few days installing stuff and making the OS the way I want so I would want to avoid a fresh install). From what I understand the best program to acomplish this is Clonezilla. I`ve read some tutorials but I still don`t understand something: does the image Clonezilla creates need a special partition just for itself, or is it just a file that`s saved somewhere on the partition? (.iso or whatever)
What I want to do is use an external hard drive to store the image, and I have lots of other stuff on it. I`m reluctant to just try using Clonezilla and see what I can do with the image, since I`m afraid that I`ll end up formatting the drive by selecting a wrong option. Can anybody share some light on this?

P.S. sorry for the rusty english!

---

### Post by haqking on 2012-12-28
> **mihnea13 said:**
> Hello, 

I`m interested in cloning my recently installed Ubuntu 12.04 (I`m a new user of Linux and I want to learn more by tinkering and I want a safe net in case I`ll mess it up really bad...I`ve spent a few days installing stuff and making the OS the way I want so I would want to avoid a fresh install). From what I understand the best program to acomplish this is Clonezilla. I`ve read some tutorials but I still don`t understand something: does the image Clonezilla creates need a special partition just for itself, or is it just a file that`s saved somewhere on the partition? (.iso or whatever)
What I want to do is use an external hard drive to store the image, and I have lots of other stuff on it. I`m reluctant to just try using Clonezilla and see what I can do with the image, since I`m afraid that I`ll end up formatting the drive by selecting a wrong option. Can anybody share some light on this?


Clone it to whereever you like, it is a just a folder with some compressed files in it.

Boot to a Clonezilla CD or USB and then clone your disk or partition to a disk or to a partition or to a image saved in a location of your choice.

In your example, create a folder called clones or whatever then when asked where you want to clone to choose that folder on the external drive and it will create a subfolder with the name you give it.

Make sure you understand how to read hardrives and partitions though, such as sda1,sda2,sdb etc etc

Peace

---

### Post by mihnea13 on 2012-12-28
Thanks mate, I know I have to be careful with the drive names. Cheers!

---

### Post by howefield on 2012-12-28
Here's a screenshot of an internal disk where I save my Clonezilla images to, you can see 3 images, one for each of a precise, quantal and raring install.

Each image one is around 1.7 gigs large.

That's all you get, a folder on the destination drive for each image you make.

---

### Post by haqking on 2012-12-28
> **howefield said:**
> Here's a screenshot of an internal disk where I save my Clonezilla images to, you can see 3 images, one for each of a precise, quantal and raring install.

Each image one is around 1.7 gigs large.

That's all you get, a folder on the destination drive for each image you make.

your blackout is transparent ;-)

Peace

---

### Post by howefield on 2012-12-28
> **haqking said:**
> your blackout is transparent ;-)

No worries., :)

---

### Post by mihnea13 on 2012-12-28
> **howefield said:**
> Here's a screenshot of an internal disk where I save my Clonezilla images to, you can see 3 images, one for each of a precise, quantal and raring install.

Each image one is around 1.7 gigs large.

That's all you get, a folder on the destination drive for each image you make.

Thanks, now I`ll do it with no worries.

---

