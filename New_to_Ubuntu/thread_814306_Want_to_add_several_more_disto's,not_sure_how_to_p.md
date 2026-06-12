---
title: "Want to add several more disto's,not sure how to proceed"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by phread59 on 2008-05-31
Not sure if this is where this belongs.  So if it needs moved Mods feel free to place this where it belongs. Here is what I would like to do.  I have currently 32 bit Ubuntu on a 320gig Sata  and xp Pro 64 bit on an 80gig IDE jumpered to master and on master channel.  I have a 320gig IDE on the master channel jumpered to a slave.  Here is what I want to do.

I have both Fedora 9 and Ubuntu 64 bit on CD's ready to go.  They are good and boot to live sessions.  I have the 320gig ATA partitioned as follows:

2 primary partitions of 100 gig each (for Fedora and 64 bit UBuntu)
1 extended partition chopped into 5 25gig logical partitions for later use 
1 5gig swap

I cannot seem to get Fedora to accept 1 of the primarys and take the whole primary and only the primary.  It wants to use the whole disc. I also am not up enough on the manual install of Ubuntu to stick it in the other primary and only the primary.

Any help on how to get these two in just the primarys.  I am sure I want these 2 permanent.  The other 5 are for playing with other distro's just for fun and to learn more.  I am just a little (ok a lot) out of my league here.  So any help would be appreciated.  I will worry about grub settings after I get these 2 in safely.  Thanks in advance.

Mark Shuman

---

### Post by Inxsible on 2008-05-31
I don't think that should be a problem at all. during the installation you can specify where you want to install the OS. However, you will have to choose manual partitioning to be able to achieve that. I would make the partitions first using GParted (System>>Administration>>GParted in Ubuntu). I am not sure where you would have the partitioner in Fedora. Once you have the partitions then you can start installation. Make sure you select the appropriate partitions. 

Also, don't you have a separate partition for the home of each OS? If Fedora 9 and Ubuntu are going to be your permanent OSes, I would advise you to look into having separate home partitions for each.

[www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

[www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by kwacka on 2008-05-31
As long as the user names and UIDs are identical in all distros installed you can share /home.

---

### Post by louieb on 2008-05-31
> **phread59 said:**
> 
2 primary partitions of 100 gig each (for Fedora and 64 bit UBuntu)
1 extended partition chopped into 5 25gig logical partitions for later use 
1 5gig swap


Have fun. I had a similar setup, before settling on Ubuntu. All the distros I tried have a manual partitioning option, where you tell it I want you to install on this partition.   Most give you the option of using the  GRUB or LILO boot loader/mnager.  

GRUB is a great boot loader and manager. You will want to learn the ins and outs of it. Two items will help you keep thing straight learn about the **chainloader** and **configfile** options.  

Another thing you should consider is making a **dedicated GRUB partition**. 50MB or so is plenty. 
[Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/") nice site. The  owner (Herman) is a frequent contributer to this forum.   Its a large site.  I think it would help to go through   [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm").    

Its a great time time waste so have fun and good luck.

---

### Post by enderwig on 2008-05-31
I know it's not exactly what you were asking, but, have you considered virtualizing?  If you are only installing other distros just to try them out and give them a shot, why not load them in VMWare or VirtualBox.  Just a suggestion, that way if your not that into them, no harm no foul!

---

### Post by phread59 on 2008-06-01
Thanks for the responses guys.  Enderwing I have used virtualware in the past.  I originally used a virtual box to try Ubuntu.  I enjoyed it so much I went out and bought a hard drive just to put it in my computer.  I really didn't like the speed penalty and it just was not the same as being permanent.  I want to have at least 1 linux 64 bit op system on board and I want a Red Hat based system as well.  And I want them in permanently so as to get the most out of them.

Loui Thanks for the links I have them saved in faves.  I will give them a look later.  I just have not figured out how to use the manual installation properly yet.  Today I want to try some research on how to use the manual installs.  I'll see where it leads.  Thanks for the help.  If you have any tips on how you got them in please post them here.

Mark Shuman

---

### Post by bumanie on 2008-06-01
I would look here first, a separate grub partition may be what you are looking for. [http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_)

---

