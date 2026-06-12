---
title: "unable to boot"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by Hypnopirate on 2011-10-18
I must have lost power sometime last night and upon starting this morning .. im unable to get past these following screens 
 
I dont know how to fix this .. and really dont wanna lose data again:(
 
I hope someone can help

---

### Post by oldfred on 2011-10-18
Often after an abnormal shutdown filechecks are required. I might try those first.

#From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by collisionystm on 2011-10-18
> **Hypnopirate said:**
> I must have lost power sometime last night and upon starting this morning .. im unable to get past these following screens 
 
I dont know how to fix this .. and really dont wanna lose data again:(
 
I hope someone can help

reboot

immediately after the bios screen hold the SHIFT key down

At the grub menu, choose system rescue

I believe there is an option in there to run fsck

run it.

---

### Post by Hypnopirate on 2011-10-18
> **oldfred said:**
> Often after an abnormal shutdown filechecks are required. I might try those first.

#From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

I dont know what any of this means .. Im a week new to ubuntu .. :( 



> **collisionystm said:**
> reboot

immediately after the bios screen hold the SHIFT key down

At the grub menu, choose system rescue

I believe there is an option in there to run fsck

run it.

Ive done as stated .. it says grub menu loading .. then comes to the chose which OS screen .. the only options there are load as normal .. or load in recovery < IDK if thats what you mean? ..Or I can load on a 8 gig partion which is what Im using know to connect to this forum ..

so .. Im still @ square one .. but thanx for the support .. Im open to any Ideas you guys have

---

### Post by oldfred on 2011-10-18
Have you tried the recovery mode?

---

### Post by Hypnopirate on 2011-10-18
I was under the impression recovery mode .. dumps you data ?

---

### Post by collisionystm on 2011-10-18
> **Hypnopirate said:**
> I was under the impression recovery mode .. dumps you data ?

Uh... no?

---

### Post by Hypnopirate on 2011-10-18
Awesome.. Ill try that

---

### Post by Hypnopirate on 2011-10-18
I just ran in recovery and it took me back to the same screen as pic one I posted originally ..

---

### Post by kemtnbkr on 2011-10-18
To run the code as shown by oldfred:

1. Boot into your live CD (or USB, what you installed it w/ in the first place)

2. Open up GParted, find your 'swap' partition, right click it, and select 'swapoff'.  Now, your hard drive should be completely unmounted- meaning nothing is using it, so it is just 'sitting there'.

3. Open up the terminal; type in the command(s) exactly as shown by oldfred.

4. If you complete those commands successfully, you hopefully can boot back up.  If not, it's over my head. :)

Just out of curiosity, how do you have it partitioned?  If you have a standalone /home directory, you could do a custom reinstall and not touch your /home directory; you'd keep all your documents, etc., and some settings as well.  I'm guessing you just did the auto-partition though, right?

---

