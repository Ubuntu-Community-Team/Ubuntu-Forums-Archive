---
title: "SImple beginner questions"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by Gorgonzolllaa33121 on 2008-08-08
First of all, hello! I`m new on this forum and new to linux. I have 3 simple questions. Now i have a 400 GB WesternDigital hard drive. I currently run WIndows Xp Prof. on it and want to run also Ubuntu. I use 200gb for WIndows and i will use 200gb for Ubuntu. MY first question is how to partition those 200gb? One ext3 partition for root(100gb) and one SWAP partition(100gb)? Please give me some ideas how to partition those 200gb. By the way what is the differences between EXT3 and Swap and other like ext2 for example?
Also, how can i write c programs in Ubuntu linux? What compiler should i use, can you please tell me? Also i`m using a pppoe conection for internet. Can i do something in Ubuntu or is it a program that can help me setup my connection so i don`t have to do in terminal all the time i turn the computer on"sudo pppoeconf". 
THanks very much!

---

### Post by swisscow on 2008-08-08
For partitions, 10-15 GB root for ubuntu is plenty, swap is supposedly about double your ram and the rest can go for home. It's simple and it works because you can reinstall ubuntu without touching your home partition. There are more complex partition schemes though I can't give you the advantages/disadvantages.

Personally with 200GB to play I'd leave space for another partition (maybe 20gb or so) if you want to play around with triple booting - or as I used to do, copying everything to this partition as a simple backup.

As for types, ext3 is (I think, please correct me) better at recovering from crashes than ext2 and swap is just like extra ram, albeit a lot slower.

---

### Post by Gorgonzolllaa33121 on 2008-08-08
OK, so i will make an ext3 partition for root (20gb). But with the rest of 180 gb what should i do? I don`t want to make triple boot, dual boot is enough for me. Should i create to more partitions of 90 gb both SWAP or something else?

---

### Post by bobnutfield on 2008-08-08
I would strongly suggest using a separate partition for your /home directory (where your personal data will go).  Should you ever need to reinstall, you will still have all your data intact as only the root partition will require re-install.  Very much a time saver.

---

### Post by indytim on 2008-08-08
Make one partition /swap =~ 2G (max).  and the balance into another ext3 partition.  When you come to the installation, choose the "manual" install.  Define your "/" with the 20G ext3 partition.  Define the "/swap" with the 2G from above, and the balance of the new ext3 as "/home".

IndyTim

---

### Post by abgemacht on 2008-08-08
If you're familiar at all with the Windows Pagefile, /swap is very similar.  Basically, if you temporarily run out of main memory, you use space on your harddrive.  It's slower than running off main memory, but faster than dumping everything.  As was suggested earlier, doubling your RAM is usually a good approximation for how much /swap to have.

Also, don't feel you need to partition everything right now.  You can leave some space free on your harddrive in case you want to use it for another OS or just for extra space.  You can always partition in further later.

---

### Post by Gorgonzolllaa33121 on 2008-08-08
So i need to make one SWAP with 2gb and then an ext3 of 20gb and then one ext3 where /home will be? And then? 
SOrry but my English is not very good, i`m using google translate so i can`t understand very good.
Can you please writte me this way?
Swap2gb
Ext3-20gb where /home will be
Ext3-90gb..
THanks and sorry for my bad understanding!

---

### Post by abgemacht on 2008-08-08
What is your native language?

/swap  2GB        swap
/      20GB       ext3
/home  20GB-90GB  ext3

---

### Post by bobnutfield on 2008-08-08
My suggestion:

2GB     Swap
15GB    / (root, the system files)
90GB    /home (your personal data)

---

### Post by cdtech on 2008-08-08
Hello Gorgonzolllaa33121 and welcome to the forum.

From my experience, to a new beginner using GNU/Linux, I would suggest reading from the link from my signature below (partitioning). I personally use individual partitions for my setup and eventually you'll probably do the same.

I've found that with everything installed on my setup including a 2G swap partition, I'm using roughly 25G of hard drive space. I decided to use a 60G chunk of my hard drive so that I would have a lot of head room (for unknown future installs).

Start basic and read alot. You'll probably reinstall, repartition several times before its the way you want it.

Just a bit of advice (for what it may be worth), keep documentation on your install and the procedures you took to get it that way. It will pay off.

Good luck.......

---

### Post by Gorgonzolllaa33121 on 2008-08-08
Thanks for the reply, i have managed to partition it.!
Thanks again!
And another question, if i have dual core i need the 64bit version?

---

### Post by abgemacht on 2008-08-08
Maybe.

There are dual core 32bit AND dual core 64bit.

Do you know the name of your processor?

---

### Post by bobnutfield on 2008-08-08
> **Gorgonzolllaa33121 said:**
> Thanks for the reply, i have managed to partition it.!
Thanks again!
And another question, if i have dual core i need the 64bit version?

You are not required to use the 64bit version as 64bit processors will run 32bit just fine.  Many claim that the 64bit version is slightly faster.  I have a dual core 64bit processor and I run 32bit which I prefer.

---

### Post by Gorgonzolllaa33121 on 2008-08-08
THanks

---

