---
title: "Partitioning question"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by pikeman47 on 2008-07-11
Hey guys, new user here...

I recently bought a 250 gig harddrive as a main for my desktop and decided to put ubuntu on it. (I've been a windows guy for years but am making the switch)
I partitioned the hard drive in to four partitions of roughly 60 gigs each. My initial plan was to have a 60 gig partition for ubuntu, a 60 gig partition for xp in virtual box, and a 120 gig partition to be used as a storage drive. I accidentally partitioned my intended 120 gig drive in half, so i now have four 60 gigs.

Is it possible to:
1. take two of the 60's and combine them into one 120
2. leave one 60 gig drive alone for ubuntu
3. set up virtualbox to boot from the last 60 gig partition

assuming these processes are possible, how would i go about doing them?

when i try to setup virtualbox it does not give me any options as to installing on a separate partition/drive, it only allows me to install it in my drive for ubuntu.

i'm pretty confused.

thanks, guys

---

### Post by Bakon Jarser on 2008-07-11
Everything you want to do can be done.  Sounds like you already have Ubuntu up and running.  Have you formatted the other drives?  If so what file system did you use?  Have You already started loading stuff onto your storage partitions?  I think it will be a lot easier to join them together if they are empty.  As for virtualbox, did you install from synaptic or did you install the binaries?  If you installed from synaptic then I suggest you uninstall and follow this guide.

[http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox)

There is a step when creating the .vdi file where it lets you pick a location.

---

### Post by rogier.de.groot on 2008-07-11
1) If there aren't any files on those partitions, yes. Use gparted.
2) Yes, just don't pick that partition as the one you repurpose ;)
3) Yes, virtualbox must be installed on your ubuntu system, but can be configured to use a raw partition (instead of the usual vdi file) for it's virtual harddisk.

---

### Post by pikeman47 on 2008-07-12
Ok, i uninstalled the virtualbox version i had initially installed from synaptic and followed the guide. i still can't find out where to set it to a disk/partition. it only asks me about a .vdi file.

also, when i run gparted to delete my original partitions so i can repartition to my intended partition sizes, i am able to delete one of my 60 gig partitions, but when attempting to delete the others to reallocate, i get an error that says:

Unable to delete dev/sda5!
Please unmount any logical partitions having a number higher than 5

and i'm not quite sure why all of my drives start at sda5

any thoughts?

---

### Post by rogier.de.groot on 2008-07-12
I've only tried on Vista, but you seem to be right about the .vdi files; I probably had VirtualBox and VMWare mixed up - maybe try the free vmware stuff instead?
/dev/sda5 is an "extended partition" or something like that - it contains other partitions but doesn't take up space itself. All partitions with numbers above five are (sda6, sda7, etc) are probably "inside" that partition; you can't delete sda5 while they exist.

Could you post the output of the following command:
sudo fdisk -l /dev/sda
(this will list the parttitons on you system)

---

### Post by dracayr on 2008-07-12
you have to run gparted from a liveCD, because gparted will not apply changes to mounted drives

dracayr

---

### Post by Elfy on 2008-07-12
Possibly also you will need to turn of swap if you use the buntu livecd as it will be in use.

```
sudo swapoff -a
```

> i still can't find out where to set it to a disk/partition. it only asks me about a .vdi file.Try adding it with the Virtual Disk Manager in Vbox - File menu

---

### Post by louieb on 2008-07-12
> **pikeman47 said:**
> .. i'm not quite sure why all of my drives start at sda5

any thoughts?

Sounds like you have 1 extended partition.  Bet its sda1 but could be sda2.3 or 4. The rest of your partitions a logical. In Linux logical partitions start numbering with 5. (1-4 are reserved for primary and extended partitions). BTW nothing wrong with that as long as you stick with Linux as the OS. Some OSs have to be installed on a primary partition Linux is not one of them.
[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

### Post by Bakon Jarser on 2008-07-12
When you're creating a new .vdi file there is a spot where you can select which drive you put the vdi file on (see attached image).  There is a way to install windows the old fashioned way and then make virtual box mount the partition where your windows install is. I haven't tried it myself.

[http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)

[ATTACH]77486[/ATTACH]

---

### Post by pikeman47 on 2008-07-12
Yeah, new idea:
since i just installed ubuntu and haven't really got anything set up or gotten really settled in i think i'll just reformat then start fresh with two 120 partitions, to make things easy on myself. that way i can have my 120 storage and a 120 with 60 reserved for virtualbox.

thanks for the help and also for the warm welcome!

---

### Post by pikeman47 on 2008-07-12
Alright, i reformatted the computer and got my partitions squared away (two 120's) i have ubuntu on one and im reserving half of it for virtualbox (which i'm currently installing)

My new problem is: i dont know where my other 120 gig partition went. before the reformat, my other partitions were represented as 60 gig media under the Places menu. now i only have my filesystem. it says my filesystem is 120 gigs, so i'm not sure where that spare 120 went. any idea how i can find out where it went and get my computer to show it as 120 gig media in the Places menu?

edit: i installed gparted and took a look at my hard drive, it says that i have both partitions but the one that i can't access has 32 gigs used, which is strange because i haven't put anything in it. its formatted ext3, partition /dev/sda2, and the mountpoint is /home, if thats any help

---

