---
title: "USB Partitioning"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by ixtok on 2012-04-29
I did a full install of Ubuntu 12.04 on my 32GB usb and it seems to work ok. I am not very proficient with gparted and did not create a swap. Everything is in one partition. My question is is this a problem. I am using a HP 110 netbook with 2GB ram. I don't mind reinstalling as it is a learning experience. Could a partitioning sceem be recomended. Would other partitions be helpfull?

---

### Post by joetait on 2012-04-29
Do you mean a new install on to the USB? It depends on the ram of the computers you will be using it with. It is generally advised to have twice as much swap space as RAM, but I have read articles of people saying they run okay with no swap space. The more RAM you have, and the less RAM intensive your processes will be, the more likely it is you can get away without a swap partition. Also, with 32GB, you might not want to take up to 8GB out for swap.

On the other hand, if you want to add swap, you should be able to. GParted will let you shrink the current partition by just dragging it. Then you can format it by going to partition -> format -> linux swap.

Then you will need to add the new partition to your Fstab file so it loads it at boot.

edit - for clarification

---

### Post by audiomick on 2012-04-29
> **joetait said:**
>  It is generally advised to have twice as much swap space as RAM, 

This is a rule of thumb that is no longer valid. It dates back to times when 256MB was a real lot of RAM. These days, you only need a swap as big as your RAM if you want the hibernate function to work properly. If you don't, and assuming you don't spend your time doing RAM intensive things like editing four or five films at the same time, you will likely never notice that you have no swap space. Even on my netbook, I rarely get close to using all the RAM. You can look at how much RAM you are really using with the System monitor, or from a terminal with the command
```
top
```
You can see that running in the screen shot, and that I am not currently using any of my swap. The entry "Mem." is the RAM.

In your situation, I would be inclined to not change anything right now, and just observe the system for a while. 

Here is some reading that may help you make an informed choice.
[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

If you create a new swap, I believe you will have to add it to your fstab
[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

If you haven't read through this already, it might be worth it for you.
[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by ixtok on 2012-04-30
Thanks for the replies. So if I do resize my partition and create one for swap (say 2GB) I would have to do something to mount this partition whenever the computer is started, or edit something so it does it automatically. 

Since the hard drive on the computer already has a swap partition on it, Could I defer to that swap partition when running Ubuntu off my USB? What would I have to do to mount it and get it to work?

---

### Post by joetait on 2012-04-30
Thanks to Audiomick for claryfying how much swap space is actually needed.

If you wanted to load it on boot from you memory stick you would need to add the following line to the fstab file in /etc
```

/dev/sda?       none            swap    sw              0       0

```replacing the question mark for whatever partition your swap space is actually on.

With regards to using the swap space from another computer, I am not sure. I do know that if you want to load it at boot you would have to add that to the fstab file too, and then if you mount it on anything else it will have an error (which you can just skip). Whether you can start up Ubuntu then add in some swap space I don't know, sorry.

*edit - the line of code above should go after
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

```
which should already be there.

---

### Post by audiomick on 2012-04-30
> **ixtok said:**
> 
Since the hard drive on the computer already has a swap partition on it, Could I defer to that swap partition when running Ubuntu off my USB? What would I have to do to mount it and get it to work?

I assume that the swap on the hard drive of the computer is a Linux swap partition?

As far as I know, if you boot from a USB device, the system will mount any swap it finds and use it. I'm not exactly sure in your case, but if you boot into the live environment from a USB stick, this does happen. The easiest way to find out is to look at the system monitor and see how much swap it says is there. Since you say your USB drive has none, if there is any there at all, it must be the partition on the hard drive.

To get it to mount automatically, if it isn't being mounted, you would have to include it in the fstab file, i believe. I am hazy on that, but I think that article on automounting that I posted a link to should help there.

---

### Post by ixtok on 2012-04-30
Thanks for the answers, they are pointing me in the desired direction.

---

