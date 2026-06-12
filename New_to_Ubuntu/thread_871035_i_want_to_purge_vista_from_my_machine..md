---
title: "i want to purge vista from my machine."
date: 2008-07-26
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-26
hello,  I finally have my aircard working,  my confidence level is up steadily now for a few weeks.  I want to at most have Windows gone from my life.  But alas, I feel like I should keep it so I learn how to use it, and abuse it.  I guess my problem is what others refer to as bloatedness.  Windows seems like...too big and clumsy.  so How can I remove it from my machine? Is this the best thing to do?

---

### Post by Joeb454 on 2008-07-26
It's entirely up to you.

I still have Windows around, as the rest of my family aren't the best with PC's, so I need to remember how to use it :p

---

### Post by adamogardner on 2008-07-26
hi joeb, ok ok so I want to do this.  no doubt,  my fears are screwing up my machine in the process.  and getting cut off from the tech support.

---

### Post by sg7791 on 2008-07-26
Well, there isn't much you can "screw up" by simply removing the operating system. But if the machine is under warranty, you may want to check the terms before you go about "purging".

---

### Post by hyper_ch on 2008-07-26
or instead of vista you might want to have an XP still installed....

---

### Post by germanix on 2008-07-26
I too wanted Vista purged from my machine and out of my life altogether. I had no problems making that decission, as a matter of fact I very much enjoyed just sitting back and watching Ubuntu wipe it of my hard drive.
I had Ubuntu installed as a dual boot with Vista. I made a back-up of my personal files, then used the Ubuntu live CD, and chose the option to "use the full hard drive". Ubuntu did the rest. I have not regretted my decission. In all fairness I must add that I am not a gamer, and eveything that I require from my computer, I can get with Ubuntu as my only OS. This may not be the case with everyone.

---

### Post by bumanie on 2008-07-26
> **adamogardner said:**
> hello,  I finally have my aircard working,  my confidence level is up steadily now for a few weeks.  I want to at most have Windows gone from my life.  But alas, I feel like I should keep it so I learn how to use it, and abuse it.  I guess my problem is what others refer to as bloatedness.  Windows seems like...too big and clumsy.  so How can I remove it from my machine? Is this the best thing to do?

It is up to you - unless  gaming is a big part of your computing, there is nothing that can be done on windows that can't be done on ubuntu, other than may be a few 'specialist' win programs. You could always run vista in a vm if you have an install disk, for the odd times you may use it. IMO, you'd not be missing out on anything other than lots of frustation - but that's just my opinion. I have xp running because my kids refuse to use linux.

---

### Post by silent contender on 2008-07-26
I personally keep Windows XP just so other people in family can use the computer.  Since your OS is Vista, there is probably more reason to change.  If you are a gamer, the outlook is not TOO bleak.  Like, others have said use a virtual machine or wine.  Also there are some (not a lot) decent games for linux.

---

### Post by jimmy the saint on 2008-07-26
Holy water + bible + "THE POWER OF CHRIST COMPELLS YOU!!"

More seriously though, if you have a working dual boot system, the easiest way would be to just reformat that partition.  If you have an xp or vista install disk, you can install VirtualBox (a virtual machine manager) and install windows to a virtual machine for emergencies.  One advantage to running windows on a virtual machine is that, should something go very wrong (virii or some other malware) you can simply revert to a prior state that you saved with Virtualbox.  If you are comfortable simply living a healthy MS free lifestyle though, simply reformatting the windows partition to fat or ext3 and using if for extra storage is an effective way.  Just make sure you erase the correct partition!!

---

### Post by oldsoundguy on 2008-07-26
I have an XP machine in my guest room ...  for  .. guests that are too terrified to think of trying Linux of any sort .. and there is a 7.10 box in there also .. both on a KVM switch .. 
in my media room I have a Windows machine .. again XP that is kept for running the plethora of Adobe programs I paid SOOOOOOOOO much money for in the past.  It also works as a media controller and as the main networking print server.  It lives on a KVM with the machine I am using to type this post.

I tried Hasta La Veeeeeesta, Baby a couple of times.  Once in attempting to set up a laptop for my niece, who is handicapped.  To me, it looks like a machine running MAC, and is really hard to figure out where they hid all of the functions that were/are in XP.  And TOTALLY unstable as she crashed it by running Music CD's and DVD videos (Windows Media Player 11)... never going on line with it!!

But you can't tell that to someone that believes that Redmond is responsible for the sunrise and sunset and using anything else but MS is a crime against God and Nature and totally Un-American and contributes to the decline of Western civilization!

---

### Post by adamogardner on 2008-07-26
Ok I'm convinced,  How does one go about erasing the pre-installed vista partition?  will ubuntu expand?  Is it simple to fill the old partition with say another distro, or should ubuntu use all the hardrive and everything else in virtual box?

---

### Post by youthforlinux on 2008-07-26
Well it is possible to just keep your ubuntu installation.  You should definetley back your stuff up somewhere other than the hard drive that you're working on.  Then you can use gparted to delete the Vista partition and then use gparted to expand your ubuntu partition(s) to take up that unallocated space.

Oh and to install gparted:

```
sudo aptitude install gparted
```

Good luck and remember to backup!

---

### Post by jimmy the saint on 2008-07-26
Be aware that gparted can only expand the end of a partition.  If your windows partition is before your Linux partition, you will be unable to grow it back toward the beginning of the drive.  You can install another distro on that partition.  you can also use it as extra storage to store files or virtual machines.

---

### Post by adamogardner on 2008-07-26
this is a bit confusing.  Windows came with the machine, then I installed ubuntu.  windows is taking up most of the disk space.  Are you saying I can't give Ubuntu more room?  I want to install about two other operating systems anyway and adjust partition size at random will.  Is this a practical approach?

---

### Post by oldsoundguy on 2008-07-26
As the guys above pointed out .. using the program gparted should be your first step (after backing up) .. now I did one where the linux partition was last and after I removed the Windows partition, I copied the contents to a new drive and that put the Linux partition FIRST on the drive and left the balance of the drive for other things!

The BEST program I have found for doing a lot of disk work is Easy GigII (that is provided you can find it, as it is not SOLD without hardware in most instances.  The program will work with any platform Window, Linux or MAC or BSD!!

---

### Post by adamogardner on 2008-07-26
I suppose since the "other things" I want to install are Linux operating systems, and I have grub already installed with ubuntu I won't need to move ubuntu to the first partitiion.  Or are you saying this is the only way to give ubuntu more room?

---

### Post by ToySouljah on 2008-07-26
> **Joeb454 said:**
> It's entirely up to you.

I still have Windows around, as the rest of my family aren't the best with PC's, so I need to remember how to use it :p

lmao...yeah...I guess that is one reason I keep it too.  My sister uses my computer, but I usually have Ubuntu booted so she is getting the hang of it.  I do however have Ubuntu set to boot second after Windows in case she needs to use Windows I showed her how to restart with Ubuntu so she can boot into Vista since she is more familiar with Windows and seemed to pick up Vista rather quickly...lol...I'm still trying to get the hang of it myself, but I got spoiled with the ease of use in Ubuntu.

---

### Post by jimmy the saint on 2008-07-26
You can easily expand your Ubuntu partition with gparted, but only toward the back of the disk. Gparted can take the end of the partition, and extend it so that this:
----------------||||||||||||-----------------
Becomes This:
----------------|||||||||||||||||||||||||||||

Gparted cannot extend the other way.  It cannot turn this:
----------------||||||||||||-----------------
into this:
||||||||||||||||||||||||||||-----------------
 
where |||| represents that partition you want to extend and ------- is other partitions or empty space.  If you really plan to install and try multiple operating systems, I highly recomend installing Virtualbox.  There is no need to worry about fancy partitioning and other things.

---

### Post by adamogardner on 2008-07-26
i have virtual box.  I will continue to use it   but if I remove windows I will have a lot of space heeeeeeeeeeeeeeeeeeeeeeeere---------, where ubuntu represents "-----------".  since ubuntu is not in the front of the partition and I can't make it ----------biiiiiiiiiiiiiiiiiiiiiigger, then I shall have operating systems 1111111111112222222222222333333333333333, ubuntu being 33333333333333.  This is plausible?  Windows must go!

---

### Post by jimmy the saint on 2008-07-26
that should work just fine.

---

### Post by youthforlinux on 2008-07-29
you could just use gparted and remove the windows partiton, reformat it and just use it for file storage with ubuntu....

---

