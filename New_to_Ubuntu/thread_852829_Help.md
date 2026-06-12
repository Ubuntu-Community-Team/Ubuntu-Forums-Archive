---
title: "Help"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by fredhernan on 2008-07-08
Hello, first timer here, my question, I have a Sony, notebook, PCG-K23 with a 60 GB hard drive, with 2 partisions, C; 15 GB..D; is 35 GB,,how can I merged partision D; into partision C:??????
Thanks for any suggestions.......

---

### Post by webofunni on 2008-07-08
Hi,

  You can try Gparted 

```
sudo apt-get install gparted
```

  Go to "System >> Administration >> Partition editor" to change the partition table.

---

### Post by bab1 on 2008-07-08
I believe you can NOT MERGE partitions.  You can however put all the data on one partition and delete the empty partition.  You can then expand the partition that holds the data.  Be careful with ID'ing which partition is which.  GParted can only help with the deletion.  You have to move the data first.

BTW -- It helps if you put the problem in the subject line.  ie: I need help with partitioning.

---

### Post by hyper_ch on 2008-07-08
it is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

