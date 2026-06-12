---
title: "install games on different partition"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by markvandijke on 2008-08-02
I've got a Asus eee pc 900 with eee ubuntu and i want to install (large) games on my 16GB disk or external drive if it's possible. How can i change the default install path -> /usr to another partition?

Now linux isn't using my 16GB disk ast all :(

I've googled alot of hours but i don't get an answer...

---

### Post by RuleMaker on 2008-08-02
You can merge that 16 Gb partition with you ext2 partition using your live CD.
Search on the forum, there are a lot of topics about that.

---

### Post by markvandijke on 2008-08-02
i already installed eee ubuntu from the live cd, can i still merge the partition?

---

### Post by mikewhatever on 2008-08-02
> **markvandijke said:**
> i already installed eee ubuntu from the live cd, can i still merge the partition?

Large games on eee? Can it run games with intensive graphics?

---

### Post by markvandijke on 2008-08-02
Well it doesn't matter :)

I just want to know i i can install on my 16GB disk instead of the 4GB where Ubuntu is installed, because after install i've got 1GB of space left... not a problem if i can use my secondey partition of 16GB

I can't find anything about this..

---

### Post by barkalot on 2008-08-02
After you boot your Ubuntu LiveCD go to the terminal and type
```

gksudo gparted
```

Now you can use the Gnome Partition Editor. Quite a nice tool, in my opinion. Then you can merge your two partitions. Should be self-explanatory.

---

### Post by markvandijke on 2008-08-02
well the 4GB and the 16GB are different drives i think, can i then still merge? I've used an alernative bootable version of gparted and i could't merge this driver together... only seperate options like resize etc

well i will try gparted now with the livecd on usb

---

### Post by markvandijke on 2008-08-02
my primary disk is /dev/sda (4GB)
my secondey disk is /dev/sdb (16GB)


i can't get this together in gparted...

---

### Post by barkalot on 2008-08-02
If they are different drives, it won't work. There is still something you can do, however. Here you go: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by mikewhatever on 2008-08-02
> **markvandijke said:**
> my primary disk is /dev/sda (4GB)
my secondey disk is /dev/sdb (16GB)


i can't get this together in gparted...

No, you can't. Two partitions on the same HDD can be merged, but not two physical HDDs. You don't really get the choice of where to install things, unless it's something like Azureus or GoogleEarth that simply need unpacking. The only option I can think of is reinstalling with Altarnate cd and mounting /usr on the 16GB drive. The down side of that is, it would need to be connected for Ubuntu to run.

---

