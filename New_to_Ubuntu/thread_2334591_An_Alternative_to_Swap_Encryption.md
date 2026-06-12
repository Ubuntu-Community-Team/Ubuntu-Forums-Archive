---
title: "An Alternative to Swap Encryption?"
date: 2016-08-20
forum: New to Ubuntu
---

### Post by Wadcutter on 2016-08-20
Recently upgraded to Ubuntu 14 LTS from 12.04 and have run afoul of the dev/mapper/cryptswap1 bug that has rendered my swap partition unencrypted. (/home is OK)  Otherwise, the swap functions as it should.

 
 
 Being only an advanced Noob/low-level intermediate user, I’ve been reluctant to tackle this issue with a lot of commands and file edits suggested by others because I don’t know what irreversible damage I might accomplish. Lots of people have lots of suggestions and a lot more have dire warnings about what those suggestions might actually do. I’ve read many, many posts on this issue and am thoroughly immobilized by it all.
 
 
 Since swap seems to work OK, I’m 90% inclined to dispense with encryption. But then I’m 10% concerned that should my computer be stolen (about a 10% chance), someone could glean some very private info from the unencrypted swap partition.
 
 
 Encryption  just appears to be one tool to secure private info should the unlikely scenario of computer theft occur (it’s a big desktop, not a little laptop). What other tools are available to prevent info theft?
 
 
 Here’s where I need opinion, advice, and, I hope, solid info.
 
 
 Would data be just as secure if, at the time of shutdown, I simply shut down the swap partition (with $swapoff -a) to move all of its contents to RAM memory, which would then be erased when the power supply goes cold?  What’s the downside to that strategy?  I have an 8GB swap partition and only 4 GB of physical memory, but my swappiness is set to 10 (and could be lower) and I normally don’t do a lot of memory-intensive activity. At shutdown, wouldn’t there usually be enough available memory to take on the swap partition? I would think that normally there would not be a lot of data in the swap and it would easily move out and be erased when I’m done for the day.
 
 
 I wouldn't mind doing the manual swapoff at shutdown as an alternative to trying to force cryptswap onto my swap partition with a lot of tweaking that I don’t fully understand. As for a learning experience: I don’t really need that in my life right now. What I do need is a functioning computer with reasonable security.
 
 
 Any comments, advice or ??

---

### Post by mook765 on 2016-08-21
I think that it is impossible to prevent theft of your hardware using  software.
I live in touristy place and do translations for the local police.
During high season a lot of things get stolen.
Even modern smart-phones which you are not able to use if you are not the real owner, the phone may get tracked if you switch it on.
The normal thief just sees a nice piece of electronic component and is going to take it whenever there is a good opportunity, in the hope that he can sell it for some small money.
A normal thief is not interested in your data, he is interested in the money he hopes to get.
In the cases of theft i experienced i see a coherence with the behavior of the victims.
To prevent theft you have to take care your belongings very well...
So, for the case of theft you use encryption already.
In addition, you could set up a BIOS-password and enable it for boot. Change the boot-order to your encrypted drive in the first place.
Nobody would be able to boot the machine, even with any kind off live-USB/CD/DVD, To boot the machine or change the boot-order anyone would need to know the BIOS-password.
To obtain any data from your hard-drive one would need to detach the drive from the laptop and attach it to another machine...
For a normal thief this is a no-go, but will not prevent him from stealing the whole laptop, he will not know that your system is secured and he wouldn't be able to use it.
He is not interested in your data, he is interested in the hole piece of hardware for the mentioned reason...
For a high-level hacker nothing will be impossible, he just need time and computing-power to take over what ever he wants...
I run Kubuntu on a machine with 4 GB RAM and like you, i don't have a lot of memory-intensive activity. My swap has never been used so far...
With the hope to give you some useful feedback,
kind regards...

---

### Post by kurt18947 on 2016-08-21
I sometimes don't create a swap partition when doing a fresh install with 4 GB.+ RAM. An alternative would be a swap *file.* I would think - I'm not an expert - that a swap file, being in the / partition would be encrypted if the / partition were encrypted. Here is one method of creating a swap file:

[https://support.rackspace.com/how-to/create-a-linux-swap-file/](https://support.rackspace.com/how-to/create-a-linux-swap-file/)

One limitation of swap file vs. swap partition is that a system with a swap file cannot be hibernated. Suspended sure but not hibernated. I think that hibernation has a checkered history on linux so I don't see that as a major issue.

---

### Post by sudodus on 2016-08-21
I would suggest that you try with 16.04.1 LTS instead of 14.04 LTS.

1. As far as I understand (and I have tested it), cryptswap works in 16.04.1 LTS.

2. But I think it is even better to use LVM with encryption alias 'encrypted disk'. This system has a small unencrypted boot partition, but the rest of the drive will be encrypted (the root partition and the swap partition will be 'inside' the encryption). And the method of encrypted disk works in both 14.04.1 LTS and 16.04.1 LTS.

I think it will be very difficult to upgrade your current system to a system with encrypted disk. Instead ***I suggest that you create a new system*** and transfer your personal files to that system. Gradually, when you need it, you can install program packages and tweak the system.

---

### Post by Wadcutter on 2016-08-23
Thanks to all for your good advice. As far as hibernation goes, I gave up on that in 10.04 when I couldn't get it to work. For a desktop, "suspend" probably works just as well for shutting things down for a while and there's no battery to be frugal about. Your mention of LVM was interesting in that I had never heard of it and was totally unfamiliar with it. I don't like the idea of it, since a failure of one drive will torpedo the whole computer, but I am going to look into it for a friend's computer where there are 3 small HDs and she would prefer to have one large one.  As far as 16.04 goes, my policy is to always stay one or two versions behind the "latest and greatest" until they iron out some of the bugs. In many ways, I wish I were still using 10.04, but of course, there's no light at the end of the tunnel for that idea. I do use Point LInux on a netbook. It's very similar to Lucid and they aren't upgrade-happy developers. I have been following my strategy of swapoff at the end of the day with no apparent damaging side-effects. I think I will call the issue solved for now. Thanks again for your ideas.

---

### Post by sudodus on 2016-08-24
Thanks for sharing your solution :-)

-o-

Finally a comment about "I have been following my strategy of swapoff at the end of the day with no apparent damaging side-effects." Sorry if I have misunderstood it.

If you never swapon at boot, you will not use swap, so there will be no traces of your activity in the swap partition. You can do that by removing the line about swap from your /etc/fstab file.

I don't think it is enough to swapoff at shutdown to wipe the content of the swap partition. You would need to overwrite it too. You can make a shellscript to do that with ***dd*** and re-create it with **[B]*mkswap -U***[/B] (and specify the same UUID as in /etc/fstab).

---

### Post by Wadcutter on 2016-08-24
> **sudodus said:**
> Thanks for sharing your solution :-)

-o-

Finally a comment about "I have been following my strategy of swapoff at the end of the day with no apparent damaging side-effects." Sorry if I have misunderstood it.

If you never swapon at boot, you will not use swap, so there will be no traces of your activity in the swap partition. You can do that by removing the line about swap from your /etc/fstab file.

I don't think it is enough to swapoff at shutdown to wipe the content of the swap partition. You would need to overwrite it too. You can make a shellscript to do that with ***dd*** and re-create it with **[B]*mkswap -U***[/B] (and specify the same UUID as in /etc/fstab).

I had read somewhere that when you "swapoff -a", all of the data in the swap partition is transferred to your available physical memory. And since nothing is saved in that memory when you shutdown, I was guessing that this strategy would effectively delete all data in swap.  But your idea of a script would be a foolproof method, so I think that is exactly the type of info I was looking for. Many thanks.

---

