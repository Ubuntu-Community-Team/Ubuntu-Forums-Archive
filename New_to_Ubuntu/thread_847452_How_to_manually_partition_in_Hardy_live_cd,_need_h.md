---
title: "How to manually partition in Hardy live cd, need help"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by andsmi on 2008-07-02
Hi, I've been using ubuntu since feisty fawn, but now, on hardy heron, I can't manually partition my old xp partition. I would like to use around 30GB from my ntfs xp partition, but I cant because when I click "edit partition" in the installation box from live cd, it doesn't say what size my new partition will be. It only allowes me to change the existing partition to another format like ext3, ext2 etc. How can I change just the size and make 2 other partitions (swap and ext3 for linux) while I still have the old xp partition? I managed to do this in gutsy gibbons and feisty fawn, but not in hardy heron. Thnx.

---

### Post by Matthewslf on 2008-07-02
You could use the gparted live cd separately

---

### Post by andsmi on 2008-07-02
gparted live cd? I'm still a noob when it gets to linux, but I know, well... thought I knew how to edit partitions and installing linux.

---

### Post by hyper_ch on 2008-07-02
install, while you're int he life session, gparted

---

### Post by andsmi on 2008-07-02
Thats what I'm doing, im installing in the live session. but thats where it dosen't allow me to manually size my partition, only the free space partition I can resize, but I can't take 30GB out of ntfs partition, I need to format the whole partition in order to make other partitions, but I don't want to formate mye xp.

---

### Post by hyper_ch on 2008-07-02
it probably autmounted the partitions....

unmount all the partitions first

---

### Post by andsmi on 2008-07-02
I get an error while unmount the partition. "error org.freedesktop.Hal.Device.InterfaceLocked.

Details: The enclosing drive for the volume is locked"

---

### Post by hyper_ch on 2008-07-02
what did you try to unmount?

---

### Post by andsmi on 2008-07-02
Yes. I located my ntfs partition and right clicked, pressed unmount and thats when I got that error.

---

### Post by hyper_ch on 2008-07-02
strange... well, then you probably should use gparted live cd.... if it's VISTA then use the VISTA internal partitioner to resize the partition.

---

### Post by bumanie on 2008-07-02
Whilst on the live cd go to terminal Applications --> Accessories --> terminal and type in sudo apt-get install gparted. You will then find gparted under System --> Adminiistration --> Partition editor. You should be able to shrink you windows partition with it, it may take considerable time as there is a filesystem present. Before shrinking xp partition, defrag xp twice. You could also go and download the [gparted live cd]("http://gparted-livecd.tuxfamily.org/") and use that if you don't feel comfortable with the command line.

---

### Post by andsmi on 2008-07-02
I use xp. Where do I find gparted live cd?

---

### Post by bumanie on 2008-07-02
Click on 'gparted live cd' in the above post. It is linked to the download site.

---

### Post by hyper_ch on 2008-07-02
where have you tried to find it?

---

### Post by andsmi on 2008-07-02
nvm, lol. I found it. But it still wont let me take 30GB from the ntfs partition.

---

### Post by hyper_ch on 2008-07-02
did you download the gparted live cd, burn it and boot from it?

---

### Post by andsmi on 2008-07-02
no. I used the one that was allready in Ubuntu. I managed to unmount the ntfs partition, but not to change the size. I could only make it bigger, and I have only used 25GB and it is 130GB available in the ntfs partition.

---

### Post by hyper_ch on 2008-07-02
did you defrag the windows partition?

And as recommended, try to resize it from gparted live cd

---

### Post by kansasnoob on 2008-07-02
"Thats what I'm doing, im installing in the live session."

Boot into windows, create a restore point, then defrag, then make sure that windows is shut down properly.

After that boot your Ubuntu Live CD and try using Gparted (Partition Editor).

---

