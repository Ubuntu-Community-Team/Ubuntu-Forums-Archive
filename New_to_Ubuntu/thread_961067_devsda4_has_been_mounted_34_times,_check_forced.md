---
title: "/dev/sda4 has been mounted 34 times, check forced"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by fontanar on 2008-10-28
Hi there,,, 

I have Ubuntu 7.10 on an HP laptop (AMD-64, AthlonX2), which is running Vista on the primary partition. 

I had been using Ubuntu for a few months, but several weeks ago (I haven't fixed it yet, and it's still happening), I started having the following issue: 

I turn the computer on, Grub selects the default boot (which is Ubuntu), I get the graphical logo, and orange bar, and then it goes to an fsck, and eventually gives the following message: 

*/dev/sda4 has been mounted 34 times without being checked, check forced...*

and then it start sscanning, but it gets to a certain percentage, and it hangs there forever. The percentage is never the same. Sometimes does not go over 6%, and the maximum it has reached is 84.4%, but it's never the same number. 

I have even left it running over night (about 20 hours), trying to give it all the time in the world, but it still hangs. There is no way to pass this point of 'fsck'. 

I have seen other threads in here, but in all of them (unless I missed the right one) eventually the scan goes thru, and the boot succeeds. The replies mainly talk about how to change the frequency of the scan. 

That's not my case. In summary, I cannot use Ubuntu, and I had done a lot of work before. I wouldn't like to reinstall since I would lose all my data. 

In addition, I have tried to boot using a live CD for v7.10.  I did this first with the one for Intel-x86 computers, and then with the one for the AMD-64 computers.  The results were identical.  Both of them seem to be working fine, until they get to the point of showing some graphic display, and then it hangs again.


Any help out there??? 

Thanks in advance, 
Roberto

---

### Post by ptn107 on 2008-10-28
Boot from the Live CD and you can turn the check off from there, but that will not solve any *physical* problems that are wrong with /sda4, it will just not check it a boot.

Type the following in a terminal:
```
sudo tune2fs -c -0 /dev/sda4
```

---

### Post by fontanar on 2008-10-28
Thanks ptn107, 

I have tried to boot from the live CD, but I'm not successful either, as I mention in my original message. 

I'm thinking of using the v8.04 live CD, to see if I can get to a prompt.   Is there any specific item from the live CD menu that I should definitely use?   Last night I tried all the possible options in the CD menu, to no avail.  I was using the live CD for v7.10 (for both i386 and AMD-64 CDs). 

Thanks again, 
Roberto

---

