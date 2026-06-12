---
title: "IPC shared memory question"
date: 2008-07-20
forum: Programming Talk
---

### Post by Cl0ud9 on 2008-07-20
I haven't done any IPC programming on this machine, but whenever I run ipcs it seems there are numerous shared memory segments marked to be destroyed. I have run the ipcs command upon boot-up and after a few days of continuous operation and they are always there. Shouldn't I have 0 ipcs entries or am I just unfamiliar with Ubuntu?

Here is the result of running ipcs:
```

------ Shared Memory Segments --------
key        shmid      owner      perms      bytes      nattch     status      
0x00000000 32768      jesse     600        393216     2          dest         
0x00000000 65537      jesse     600        393216     2          dest         
0x00000000 98306      jesse     600        393216     2          dest         
0x00000000 131075     jesse     600        393216     2          dest         
0x00000000 163844     jesse     600        393216     2          dest         
0x00000000 196613     jesse     600        393216     2          dest         
0x00000000 229382     jesse     600        393216     2          dest         
0x00000000 262151     jesse     600        393216     2          dest         
0x00000000 294920     jesse     600        393216     2          dest         
0x00000000 327689     jesse     600        393216     2          dest         
0x00000000 360458     jesse     600        393216     2          dest         
0x00000000 393227     jesse     600        393216     2          dest         
0x00000000 425996     jesse     600        393216     2          dest         
0x00000000 458765     jesse     600        393216     2          dest         
0x00000000 491534     jesse     600        393216     2          dest         
0x00000000 524303     jesse     600        393216     2          dest         
0x00000000 557072     jesse     600        393216     2          dest         
0x00000000 589841     jesse     600        393216     2          dest         

------ Semaphore Arrays --------
key        semid      owner      perms      nsems     

------ Message Queues --------
key        msqid      owner      perms      used-bytes   messages 

```

---

### Post by supirman on 2008-07-20
Many applications make use of IPC, so why would you think there should be none on your system?

---

