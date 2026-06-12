---
title: "[SOLVED] Ubuntu installation removes NTFS partition?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by greeneemer on 2008-11-03
Hi.
I have the following situation. I dual boot Windows Vista and Ubuntu. I wanted to try the new Intrepid Ibex version with a fresh install. So I want to format my old Ubuntu (8.04) partitions and reinstall 8.10 on that space.
I could not find an easy way to do this in Ubiquity so, from the live session from which I'm currently writing, I fired up GParted and removed my old 8.04 partitions.
Now, I want 8.10 to be placed in the space where 8.04 was previously placed. However, although having 16 GB of available space, and with the option to use the largest continuous free space (which is selected on the attached screenshot), Ubiquity seems to remove my NTFS partition and use the whole disk for 8.10.
This could just be a bug where Ubiquity just shows the wrong representation of the partitions, but I'm really hesitant to try it and see my NTFS partition be removed. (After all, Windows Vista is my everyday OS, mainly thanks to Creative's inability to produce a working Linux driver for my sound card, but that's another thread.)

So, my question is:
Will the option to automatically use the largest continuous free space really wipe my NTFS partition, or can I safely use that option?

[img]http://www.dtek.chalmers.se/~stolpep/ubuntuinstall.png[/img]
(Some text in is in Swedish. but I guess you know what they should mean)

BTW, since I dual booted before and I already removed my previous Ubuntu partitions, GRUB will not be found and I am (I'd guess) locked out from Windows until this matter is solved. So candy and hugs to anyone who helps me :)

---

### Post by eddietours on 2008-11-03
chose the first option it should leave the windows partion

---

### Post by greeneemer on 2008-11-03
It does leave my Windows partition, but it resizes it and also leaves the free space unused. I do not want to neither shrink my Windows partition nor leave hard disk space unused.

[img]http://www.dtek.chalmers.se/~stolpep/ubuntuinstall2.png[/img]

---

### Post by eddietours on 2008-11-03
oh ok l see am not sure my self but someone will help out

---

### Post by greeneemer on 2008-11-03
Thanks for your answers. Anyone else?

---

### Post by Paqman on 2008-11-03
Well, you'll have to shrink your Windows partition to fit Ubuntu. You could install Ubuntu using Wubi, which installs it to a virtual hard drive on your Windows partition, but this will still cost just as much space as the normal install would.

As for the free space, you can use Gparted now or later to expand the adjacent partition to use it.

---

### Post by greeneemer on 2008-11-03
I used to have Ubuntu 8.04 on that free space. It is 16 GB which should be enough for 8.10, shouldn't it? Or maybe 8.10 requires more space than 8.04.
I don't use Ubuntu very much, mainly for testing and gaining some experience of Linux, so I don't need very much space for it.

And you're right about about that last part. Just reallocating space to NTFS post-installation is probably the easiest solution. Thanks.

(still curious as to why "use largest continuous free space does not work though. bug?)

---

### Post by bodhi.zazen on 2008-11-03
Go with the "Manuell" Option.

On that screen it only appears it will use the entire drive, on the next screen you will have the options you need.

---

### Post by bumanie on 2008-11-03
Why not choose to do 'manual' at the partitioning stage, that way you can choose exactly how much space to allocate to ubuntu. If not used often, you should not need a separate /home; so allocate 15gb to / and 1gb to swap. Ensure you format only that space.

---

### Post by greeneemer on 2008-11-03
Thanks for all your answers.
I would definitely say that there is a bug in Ubiquity. I chose to use 4% for Ubuntu. This would leave me with 3% free space which I planned to give to the NTFS partition. However, the resulting partitions looks like on the attached screenshot. Ubuntu now uses around 8% of my hard disk, and no (significant amount of) space is left unallocated.

I guess I could have used the manual partition option, but I don't feel very confident about my knowledge of partition setup in Linux. I would really have preferred if a program did it for me (after my wishes).

[img]http://www.dtek.chalmers.se/~stolpep/ubuntuinstall3.png[/img]

I'm going to call this solved for now. But if anyone ends up in my situation, consider yourself warned. After all, it clearly does not do what it tells you that it will do, and messing with partitions can end up bad. I do not trust Ubiquity very much any more, which is a shame. :(

Big thanks to all who helped me anyway. You can collect your candy and hugs at my place any time.

---

### Post by bodhi.zazen on 2008-11-03
LOL

I agree with the cautionary note about changing your partitions if you do not know what you are doing.

Always back up first :)

FYI, you can manage your partitions with gparted and personally I first manage my partitions, then run the installer.

---

### Post by nggak on 2008-11-20
Good news! I was in the same situation and went ahead and tried it (my system was fully backed up) and it did not blow away the other partitions, despite the ominous-looking image of destruction. So, it did what the writing said (it filled the free space) and not what the picture said. No need to do a manual workaround.

For the record, I was replacing Hardy with Intrepid on my laptop; after deleting Hardy my 100GB drive was split roughly into thirds:
1) Vista, NTFS
2) free space
3) data, NTFS

The installer correctly created an extended partition in the free space, containing an ext3 partition and a swap partition.

I was disappointed that the swap partition was only 1GB, since I have 4GB RAM and frequently hibernate. But as it turns out, both Standby and Hibernate work! (They didn't in Hardy on this same machine.) Apparently in Intrepid hibernation is not dependent on the swap partition.

---

