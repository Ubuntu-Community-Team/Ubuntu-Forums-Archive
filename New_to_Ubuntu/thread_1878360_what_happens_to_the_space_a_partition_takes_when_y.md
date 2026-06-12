---
title: "what happens to the space a partition takes when you delete it?"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by pierreyy on 2011-11-09
thanks

---

### Post by Seb71 on 2011-11-09
Remains unallocated.

---

### Post by pierreyy on 2011-11-09
is there a wat to make it a part of my current os? thanks

---

### Post by cgroza on 2011-11-09
> **pierreyy said:**
> is there a wat to make it a part of my current os? thanks
Yes. You resize your OS partition to take up that unallocated space. The OS partition and the unallocated space must be next to each other.

---

### Post by pierreyy on 2011-11-09
what tool do i use? is there a risk towards my os if i do this? thanks for the help

---

### Post by oldos2er on 2011-11-09
Gparted run from a LiveCD or LiveUSB will suffice.

There's always a risk of data loss when manipulating partitions, so make sure your backups are current.

---

### Post by pierreyy on 2011-11-09
alright thank you!

---

