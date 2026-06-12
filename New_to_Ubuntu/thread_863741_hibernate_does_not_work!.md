---
title: "hibernate does not work!"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by shadowber on 2008-07-18
When I try to hibernate, it goes through the motions, and then gets stuck on a blank screen with 1 dash (-) blinking on the top left corner...
any advice will be very appreciated... thank you.

---

### Post by RealPSL on 2008-07-19
The most common problem I have seen with hibernation is that swap space is not big enough. For it to work I have generally seen that swap space must be 2 times the size of your RAM. When the system hibernates it is storing all the data in memory on your swap device from what I understand which would justify the 2 times RAM size requirement. I had a similar problem myself.

---

### Post by shadowber on 2008-07-19
how do i find out what my swap size is, and what it should be? and how do I change it?

---

### Post by Oldsoldier2003 on 2008-07-19
> **shadowber said:**
> how do i find out what my swap size is, and what it should be? and how do I change it?

```
Free -m
``` will tell you a lot about your memory usage, including the size of your swap file in MB.

You will have to resize your partitions using a tool like gparted in order to enlarge your swap.

---

### Post by nimbis on 2008-07-19
> **shadowber said:**
> how do i find out what my swap size is, and what it should be? and how do I change it?

If you just want to put your computer to sleep, I have always found that "Suspend" works fine. Anyway, to answer your question: 
"Swap size" is referring to a partition on your hard drive that is created by Ubuntu. You can see this partition by going to System > Administration > Partition Editor. You could alternatively type this command in your terminal:```
sudo gparted
```You will see a partition (at the bottom of the list, usually) with a filesystem type of linux-swap. I'm not sure if the size of the partition makes a difference, but REALPSL's remarks seem to make sense.
If you want to increase the size of this partition, it involves using your Ubuntu LiveCD (the CD you installed from). If you still want to try increasing the space, reply to this.

---

### Post by shadowber on 2008-07-19
ok, i ran free -m and the output is this- 
total       used       free     shared    buffers     cached
Mem:          2027       1581        445          0        781        364
-/+ buffers/cache:        434       1592
Swap:        40837          0      40837



my ram size is 2 gig. Do I have to increase the swap size?

---

### Post by nimbis on 2008-07-19
Try the command from my post. This outputs information about partitions in a very user-friendly format: ```
sudo gparted
```

---

### Post by BGFG on 2008-07-19
Hibernate does indeed not work...... yet i suppose. Check this:

[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)

And thanks to Pjotr123

---

### Post by RealPSL on 2008-07-20
You can generally obtain your swap size from the command:

```
swapon -s
```

Your output would look something like:
```
Filename                                Type            Size    Used    Priority
/dev/sda2                               partition       1951888 0       -1
```

The system referenced above has  1.9GB of swap space available to it. In any case using free is perfectly fine and shows you have ample swap for hibernation. As BGFG indicates you could just be running into a bug. Hibernation works for some but not for others depending on the system components. The success rate is higher than suspend though which is even more temper mental. My white box system will hibernate but suspend does not.

---

### Post by ckybam69 on 2008-11-09
i was wondering if i isntalled ibex without using a swap space do i need to reinstall using swap space since my hibernate or suspend does not work? or is there a way to create swap space without reinstalling?

---

