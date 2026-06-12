---
title: "What is this FAT 32 partition for?"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by theDaveTheRave on 2012-04-11
Hi all.

In the attached screenshot you can see the HDD on my new netbook.

On it (this highlighted line) dev/sda2 is formated as FAT 32, and is flagged as hidden.

I am currently running from a Wubi version of ubuntu, but intend to set the install on dev/sda1 permanently and then 'remove'/format the other partitions, with a partition for /root /usr /home etc

My only concern is this FAT32 partition. What is on it (or how can I find out), I removed the 'hidden' flag, but I can't mount the partition and so I can't read it.

What gets me is why it was placed in the middle between the other 2 main partitions and not at the begining of the primary HDD ? I'm guessing it is something to do with the windows 7 home starter that is pre-installed.

Am I safe to remove it?

David

---

### Post by cortman on 2012-04-11
Mount it in GParted and explore the contents in Nautilus. It could be some sort of system restore or recovery partition.

---

### Post by westie457 on 2012-04-11
Hi, that hidden partition is the manufacturers recovery partition which wipes the hard drive to reinstall Windows and any utilities the manufacturer thinks you need.

Only get rid of that after you have made a backup of it to DVDs. If you ever decide to sell the computer that is probably the only legal version of Windows you can pass on to the buyer.

---

### Post by lisati on 2012-04-11
> **westie457 said:**
> Hi, that hidden partition is the manufacturers recovery partition which wipes the hard drive to reinstall Windows and any utilities the manufacturer thinks you need.

Only get rid of that after you have made a backup of it to DVDs. If you ever decide to sell the computer that is probably the only legal version of Windows you can pass on to the buyer.

+1.

Many new systems come with software installed that helps automate the task of creating bootable CD or DVD based backups of recovery partitions. 

Although not universally the case, some manufacturers (including Compaq/HP) arrange for things so that you can only run the software once, which can be a major pain in the posterior if something goes wrong with the backup, so make sure that the computer is running off mains power and not battery.

---

### Post by theDaveTheRave on 2012-04-11
> **cortman said:**
> Mount it in GParted and explore the contents in Nautilus. It could be some sort of system restore or recovery partition.

That was in fact my first port of call. I could remove the 'hidden' flag but even if I mounted it in GParted I still couldn't navigate to it with Nautilus (or thunar in my case).

@ Westie457 and lisati

Thanks that is the info I was needing. I'll now be appy to copy it to an external drive and then transfer it to a CD / DVD.

I can now happily get rid of the rest of the windows install.

David

---

