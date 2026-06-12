---
title: "Raid problem?"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by cthulhuxxx on 2008-11-23
Ok, here is my problem....

...I am desperately wanting to change over to Linux (ubuntu) and dual boot for a while until I am completely weened off of Window$. So I had tried to install Ultimate Edition a few months ago. All it did was lose ALL my partitions and never even wound up installing. Now I just tried the new Ultimate Edition since it says I can install it inside of Windows, and it still doesn't install anything except I guess what's called a "boot loader". But when I choose to boot into Ubuntu, it just hangs there forever at a prompt.

My setup is this:
When I have to re-format, I use the Alien Respawn disk that came with my rig. It's just my XP on a Norton Ghost image as it was setup originally from Alienware. Now I do know that I have RAID 0, and I *think* that when I use the image, it automatically takes care of the RAID for me.

So I guess my question is:
Could the RAID be preventing me from installing another OS, or using another partition?

I really do want to break away from Window$, and Ubuntu really makes it attractive for total newbs like me.

---

### Post by talsemgeest on 2008-11-24
Yeah, unfortunately wubi (the thing you are using to install ubuntu inside windows) doesn't play nicely with RAID partitions. However, the new Ubuntu 8.10 [alternate install cd](http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate) does have support for RAID.

The only problem is, dual booting Ubuntu and Windows on RAID can be VERY dangerous, your data is at serious risk if you try anything with RAID, so I would strongly suggest backing up everything that you don't mond losing. My suggestion would be to turn off RAID0, install windows on one Hard drive, and ubuntu on the other, that is the best option in your case (and mine, I wanted RAID0 but it was more trouble than it was worth.)

So good luck, and if you need any further help or explainations, please feel free to ask.

---

### Post by cthulhuxxx on 2008-11-24
Ok, I don't mind looking newbish here. Noone knows me. :)

Here's the thing. I have RAID. RAID 0 I *believe*. I remember configuring the computer when I was buying it. I came to the RAID option, and I remember one option gave you the hard drive split in two, so you only got to take advantage of half the space actually there (RAID 1 I think). So I thought "I want the whole thing available to me". So that's the only reason I chose one over the other. I don't even know why else it would benefit me or not.

So, if I were willing to wipe everything out and start over, which really isn't an option. Could I add Ubuntu first, and then run my rescue disk on the remaining partition? Would the RAID stay in that partition, or would it mow down all partitions?

Uhg! I just want to be in Ubuntu. But I need Window$ for my job. They require it, along with using IE.

Am I doomed?

---

### Post by talsemgeest on 2008-11-24
The thing about RAID is that it makes disk access twice as fast by splitting every file in half and putting each half on a different hard drive. This is fine if you have the right drivers for it, but almost no manufacturer makes drivers for Linux. To ubuntu you only have two blank hard drives, instead of the one with data on it, since it can not use the raid drives. However, the new ubuntu disc that I linked to above has support for RAID, meaning it should be able to install to your hard drive without too much trouble. The problem when I tried it was that the boot-loader for Ubuntu, called the "grub", couldn't load my windows partiton, and neither could the windows bootloader see my ubuntu partiton. So it is basically up to you whether you want to risk it, since that problem can be reversed back to just booting windows.

But if you have a DVD burner or flash drive that you could use to back up your data, then turn off RAID, install the two operating systems onto the two drives and put all your data back on. That way you should have no problems.

Yet another alternative if all else fails and if your PC is good enough, you could run ubuntu in a virtual machine, so it is like having ubuntu in a window on your windows desktop. I wouldn' recommend it, but it is possible. The best program for this is [virtualbox](http://www.virtualbox.org/).

---

### Post by psusi on 2008-11-24
There isn't anything risky about it.  It used to be a pain to set up, but with Intrepid it couldn't be easier.  You just need to do a normal install rather than try that Wubi business.  See [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto).

---

### Post by talsemgeest on 2008-11-24
It is when you want to dual boot. When I tried under intrepid it locked me out of windows.

---

### Post by cthulhuxxx on 2008-11-24
I have no idea what this "Wubi" thing is.

I went to that link, and wow...it seems like it's something for me. But there are terms that are new to me, and then there's the commands...
ex.:
```
From a terminal, run sudo apt-get install dmraid
```
*ducks head*
Wow! I haven't got a clue. It actually does seem doable at first glance, but I think I need to FULLY grasp everything before I risk losing all of my data. 

I guess I just want to know that anything it says in that article doesn't look like it will knock down existing partitions and wipe me out.

By the way, I REALLY do appreciate this help from all.

---

### Post by cthulhuxxx on 2008-11-24
> **talsemgeest said:**
> It is when you want to dual boot. When I tried under intrepid it locked me out of windows.

And I *DO* want/need to dual boot.

Now I'm torn. :(

:confused:

---

### Post by talsemgeest on 2008-11-24
Oh, no, you don't have to do the second part of that page, with all the commands. Just download the cd that I linked to in my first post and all of that is done for you. Just beware of the caveats I mentioned in my other posts.

---

### Post by HittingSmoke on 2008-11-24
Due to the nature of recovery disks, you probably wont be able to install XP with it next to Ubuntu. I'm not sure how Intrepid's RAID support works, but you'll probably have to recover using your Alienware disk, then use the Intrepid Live CD to resize your Windows partition and install Ubuntu.

---

