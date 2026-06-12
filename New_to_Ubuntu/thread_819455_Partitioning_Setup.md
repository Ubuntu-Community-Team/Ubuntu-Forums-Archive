---
title: "Partitioning Setup"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by Swarley on 2008-06-05
I'm installing ubuntu for a friend, and i'm going to partition his drive. But my brother did my install so i'm not sure what to put for the settings.

**_Options are:_**
Type for the partitioin: Primary or logical (which one?)

Location: beginning or end

Mount point: which selection?

---

### Post by neurostu on 2008-06-05
Create 3 partitions.

(Assuming you have more then 40gb of storage)
1st partition - 10-15 gb:
```

  Format: ext3
  Mount Point: /

```
2nd partition - 512mb - 2 gb (depending on how much ram you have, if you have 512mb of ram make this 512mb if you have 2gb ram make this 2gb)
```

  Format: linux-swap

```
3rd partition - <the rest of the drive>.gb
```

  Format: ext3
  Mount point: /home

```

---

### Post by Duck2006 on 2008-06-05
> **Swarley said:**
> I'm installing ubuntu for a friend, and i'm going to partition his drive. But my brother did my install so i'm not sure what to put for the settings.

**_Options are:_**
Type for the partitioin: Primary or logical (which one?)

Location: beginning or end

Mount point: which selection?

In the install then it comes to partition, do a manual partition. Make one round 10Gb and mount it as / then the next one as swap round 1Gb. If you want a home partition then make that one to what size you want. The / and home (if you have one) partition is ext3, the swap is swap. The first one it at the beginning. This may help.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

installing

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

