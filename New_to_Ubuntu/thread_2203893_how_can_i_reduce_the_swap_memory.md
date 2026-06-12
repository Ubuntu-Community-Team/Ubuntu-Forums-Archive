---
title: "how can i reduce the swap memory"
date: 2014-02-05
forum: New to Ubuntu
---

### Post by nick58 on 2014-02-05
and what is the lowest setting i can go down to


thank you

---

### Post by fdrake on 2014-02-05
google will help you [http://ask.slashdot.org/story/08/10/01/221246/how-big-should-my-swap-partition-be](http://ask.slashdot.org/story/08/10/01/221246/how-big-should-my-swap-partition-be)

---

### Post by bc.haynes on 2014-02-05
I have a 4G swap partition which is equal to my RAM. But, I don't do memory-intensive programs. I have had no problems. The rule of thumb, in cases like mine, is use an amount equal to your RAM. The post mentioned above is helpful in explaining different usages (read the Comments).

---

### Post by nick58 on 2014-02-05
thank you very much

---

### Post by deadflowr on 2014-02-05
> **nick58 said:**
> and what is the lowest setting i can go down to


thank you

0(zero)
You can run a system without any swap, if you dare.
(I have, unwittingly, after reformatting my swap partition and then my main system fstab file listed the wrong UUID entry for the partition swap. It took quite a while for me to notice, lol)) 
But if you're meaning the swappiness then this should help explain.
[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

---

### Post by monkeybrain20122 on 2014-02-05
I am not sure what your problem is. If you are not short of hard disk space and just prefer Ubuntu to use ram instead of dropping to swap (it will be faster provided that you don't max out your ram) You can set vm.swappiness to a low value like 10.[ http://askubuntu.com/questions/103915/how-do-i-configure-swappiness]("http://askubuntu.com/questions/103915/how-do-i-configure-swappiness")

You need the swap partition also for hibernation if you are using a laptop. But if you are not going to hibernate and have a lot of ram then yes, you can do without swap.

---

### Post by Herman on 2014-02-06
I agree with setting swappiness to 10, and install Swapspace dynamic swap space manager.  
Swap space manager will create swap files in the hard disk (or flash memory) on demand and only as much as the system needs. 
With swappiness set at 10 your system will hardly ever need to use swap anyway. 
It saves a lot of hard disk space not to need a separate swap partition and if you have an SSD or a flash memory stick, disk space is even more at a premium.  
It's easy to use Swapspace, just install it from the Ubuntu Software Center, or synaptic, or apt-get, and it doesn't need any configuring, just install it. 
If you previously had a swap area, you might want to comment out or delete the entry in /etc/fstab, delete the swap area and grow the Ubuntu partition to fill the free space. You won't be able to hibernate instead of shutting down but you can still suspend to ram.
Link: [Swapspace]("http://pqxx.org/development/swapspace/").

I agree that an operating system can still run okay without swap at all if the computer has enough ram, but in my opinion having the option open for the system to use swap if it needs to somehow seems to improve the performance. Also I think that having a bad swap entry in /etc/stab seems to degrade performance. If I could think of a good way to measure the difference performance exactly I would love to run a series of  experiments and actually prove it. All I can say for now is it seems to me as if having some swap available improves performance even if the system will probably never use it.

---

### Post by Gaweph on 2014-02-06
> **bc.haynes said:**
> I have a 4G swap partition which is equal to my RAM. But, I don't do memory-intensive programs. I have had no problems. The rule of thumb, in cases like mine, is use an amount equal to your RAM. The post mentioned above is helpful in explaining different usages (read the Comments).

This is less important these days.  The average RAM on even laptops is towards 8/16GB now.
Would really don't need much more than 5GB Swap (you probably wont even use that to be honest -- unless you really doing memory intensive work  at the moment you suddenly want to hibernate-- rendering etc...)

---

