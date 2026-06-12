---
title: "Swap: Is having a partition for swap a good idea?"
date: 2017-01-26
forum: New to Ubuntu
---

### Post by martemarziano on 2017-01-26
I read somewhere that having a partition for swap might slow down the system a bit since it tends to use that partition while there is still space left in the RAM. I can see from the memory usage in my system that so is the case. So I just wondered if it is a good idea to have swap at all.

---

### Post by RobGoss on 2017-01-26
Hello and welcome, I think most people have asked this question. If you're the kind of people that use hibernations for your system then I would say sure why not have it in some cases not having it might slow down your machine when your machine hibernates

There maybe more reasons to have one and you can read up it here [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

But as far as slowing down your machine by creating and using a swap partition this is the first I've heard that

They recommend having a 2-GB swap is more them enough to Handel most systems

---

### Post by Impavidus on 2017-01-26
Using some swap isn't necessarily bad. The system might decide to move a page of memory that hasn't been used for a long time to swap (but keep it cached in RAM anyway) at a moment when the system isn't doing much long before you run out of RAM, so that later when you do run out of RAM it can simply drop some cache and make RAM available to an application without first writing some pages to swap. So swapping a bit early may speed things up. The swap system, even with default settings, works quite well.

That said, I haven't seen swap in use since I increased my laptop's memory to 8GiB.

---

### Post by howefield on 2017-01-26
Just for info, Ubuntu is moving to swap files by default as opposed to swap partitions from 17.04.

Could simply be the hardware is on the light side for running Ubuntu Mate, is it a EeeBook ?

---

### Post by leunam12 on 2017-01-26
How can I see that my system is using swap?

---

### Post by howefield on 2017-01-26
> **leunam12 said:**
> How can I see that my system is using swap?

The top command in a terminal or system monitor > processes tab should show you how much swap is being used.

---

### Post by martemarziano on 2017-01-26
> **RobGoss said:**
> 

But as far as slowing down your machine by creating and using a swap partition this is the first I've heard that



Actually, I have already almost 2Gb for the swap and I can't say that I have noticed any particular lagging except for my machine being on the slow side. If I remember correctly, I read an article at makeuseof.com about Linux installation in which they mentioned that swap might cause some slowing down because of extra reading and writing cycles to be performed. I have to admit that I actually notice somewhat better performance since I left Win 10 behind and installed Ubuntu on my machine:)

---

### Post by martemarziano on 2017-01-26
> **howefield said:**
> 

Could simply be the hardware is on the light side for running Ubuntu Mate, is it a EeeBook ?

It is!

](*,)

---

### Post by mastablasta on 2017-01-26
> **howefield said:**
> Just for info, Ubuntu is moving to swap files by default as opposed to swap partitions from 17.04.

 Could simply be the hardware is on the light side for running Ubuntu Mate, is it a EeeBook ?

should be a fun upgrade from 14.04 to 18.04 :)

> **leunam12 said:**
> How can I see that my system is using swap?

additionally from checkign swap the swapiness comand can reduce swapping. i have it set so that it is start using it when the system has 90% ram out of 4 GB occupied. it doesn't realyl get used on the server where ram usage is usually well below 400 MB.

---

### Post by RobGoss on 2017-01-26
> **martemarziano said:**
> Actually, I have already almost 2Gb for the swap and I can't say that I have noticed any particular lagging except for my machine being on the slow side. If I remember correctly, I read an article at makeuseof.com about Linux installation in which they mentioned that swap might cause some slowing down because of extra reading and writing cycles to be performed. I have to admit that I actually notice somewhat better performance since I left Win 10 behind and installed Ubuntu on my machine:)

How much Ram do you currently have on this machine? Ubuntu 16.04 requires more resources these days having the minimal requirements might be pushing it

 I always try and have double that if need in order to have a more efficient running machine

My machines most if not all, have about 8-GB of Ram and Ubuntu is running flawlessly

---

### Post by martemarziano on 2017-01-26
Got only 2 Gb of Ram :(

---

### Post by martemarziano on 2017-01-26
> **mastablasta said:**
> 



additionally from checkign swap the swapiness comand can reduce swapping.

Thank you for your post! I will surely take a look at the swapiness command.

---

### Post by wildmanne39 on 2017-01-26
Please do not post duplicates!

---

### Post by mörgæs on 2017-01-26
If you are interested in swappiness this might be of interest to you:
[https://ubuntuforums.org/showthread.php?t=2130640&p=12580289&viewfull=1#post12580289](https://ubuntuforums.org/showthread.php?t=2130640&p=12580289&viewfull=1#post12580289)

---

### Post by pauljw on 2017-01-26
I recommend using a swap file/partition.  I use 2X RAM up to a 4G swap.  Unless you plan to hibernate more than 4G of RAM you won't need more.  So, if you have 2G RAM, set up a 4G swap.  I also recommend not worrying too much about memory usage with linux.  I've found it to be very good at utilizing RAM efficiently.

---

### Post by martemarziano on 2017-01-28
> **mörgæs said:**
> If you are interested in swappiness this might be of interest to you:
[https://ubuntuforums.org/showthread.php?t=2130640&p=12580289&viewfull=1#post12580289](https://ubuntuforums.org/showthread.php?t=2130640&p=12580289&viewfull=1#post12580289)

Thank you for the link. Very informative.

---

### Post by HermanAB on 2017-01-29
Don't trust hearsay - read the swapon man page.

---

