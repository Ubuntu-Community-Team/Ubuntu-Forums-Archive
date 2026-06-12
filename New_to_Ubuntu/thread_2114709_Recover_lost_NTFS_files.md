---
title: "Recover lost NTFS files"
date: 2013-02-10
forum: New to Ubuntu
---

### Post by Terry Mc on 2013-02-10
Hey everyone, my first time posting on this site I am having some trouble.

I original had windows 7 on my laptop with 3 different partitions.

C: 
D: Documents
E: Important Files

I decided to install Ubuntu once I was in the set up I clicked the last option about erase everything. ( I though that It would not touch "D, E" partitions like Windows doesn't when you do a install.) 

After setting up I realised that I have lost the most important partitions on my computer. I have spend about 10 hours today trying to figure out how I get my data back. And I found that "TestDisk" would be a good tool to use but to have a change at recovering files I need to have more then one partition on my computer. 

But Ubuntu merged all my partitions in two one and I don't have a clue how I would create another partition was out messing up any files that might still be on the hard disk. 

(Also I do not have accesses to another computer or hard drive)

I really need to restore the data that was in my windows partitions back any help on how I would do this I am new to Ubuntu and don't know much thanks in advance.

---

### Post by CharlesA on 2013-02-10
You are out of luck if you wish to recover data to the same hard drive, because it does not work that way.

You would need either another computer or another hard drive at the very least in order to start recovering what has been lost.

You could try using [Recuva]("http://www.piriform.com/recuva"), but you would need another machine with Windows to use it.

Long story short: In order to recover data from a hard drive, you need to connect that drive to another computer and run the recovery tools from that machine. If you start installing stuff on the drive you want to recover data from, you run the risk of overwriting that data.

In the future, it is a good idea to keep backups of any data you feel is valuable because you never know when something like this will happen. :)

---

### Post by mastablasta on 2013-02-11
> **Terry Mc said:**
> I decided to install Ubuntu once I was in the set up I clicked the last option about erase everything. ( I though that It would not touch "D, E" partitions like Windows doesn't when you do a install.) 
 .
 
it would do it like that if you preformatted one partition to ext4 before doing the linux install. or if you only erased that one partition (delete it) and chose to install to largest empty disk space. it would then install the OS there leaving other partitions as they are. or rather as they were.

---

### Post by Mark Phelps on 2013-02-11
If you CAN get access to a Windows PC, and can connect your drive to that PC, you have a good chance of recovering your stuff if you do the following:
1) Download and burn a CD of the Minitool Partition Wizard Boot CD
2) Boot the Windows PC from that CD
3) Use the option to recover partitions (on your damaged drive -- do not need another drive to do this).

IF this works, when you're done, your old partitions will be back.  Note, this works because Windows actually stores copies of the partition tables several places on the drive -- and utilities like this can find those, and restore the original partition tables.

---

