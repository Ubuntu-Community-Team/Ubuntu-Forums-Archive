---
title: "IDE HDD configuration?"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by andy_blah on 2012-11-01
My current configuration of the HDD are so:

First IDE Channel: -(0) First OS HDD (Master)
                   -(1) Second Data HDD (Slave)
Second IDE Channel: - (2) Optical DVD Drive (Master)
                    - (3) Empty

I've noticed that when I have a torrent with over 1mB/s (1000kB/s)everything in the system slows down to a crawl. I know that it's because torrent clients don't read the files sequencely, but wouldn't it be more logical if only the drive that contains the data is slowed down? I usually keep the things I download on (1), because it's more spacious that (0). If I were to change (1) in (2)'s place (set the HDD as master and the drive as slave ofcourse) would it be faster than this? Also, what difference would make if I were to copy one file from one HDD to another? The fact that they're not on the same channel probably means it's going to be slowed down, right?

Thank you in advance for the answers ^^

---

### Post by grahammechanical on 2012-11-01
I think that the fact that all this work is being done by the CPU is what is slowing it down. I doubt very much if the issue is caused the drive with the OS slowing down.

---

### Post by CharlesA on 2012-11-01
> **andy_blah said:**
> My current configuration of the HDD are so:

First IDE Channel: -(0) First OS HDD (Master)
                   -(1) Second Data HDD (Slave)
Second IDE Channel: - (2) Optical DVD Drive (Master)
                    - (3) Empty

I was told to have an optical drive always set to slave if there is a hard drive on the same bus as the bus slows down to the slowest device in the chain. I haven't touched IDE drives in a long, long while, so I'm not sure if that is still true (but it probably is due to IDE being an ancient technology).

[http://superuser.com/questions/109159/does-it-matter-if-cdrom-is-slave-or-master-when-it-is-on-the-same-ide-cable-with](http://superuser.com/questions/109159/does-it-matter-if-cdrom-is-slave-or-master-when-it-is-on-the-same-ide-cable-with)

---

### Post by wheeze on 2012-11-01
> **andy_blah said:**
> My current configuration of the HDD are so:

First IDE Channel: -(0) First OS HDD (Master)
                   -(1) Second Data HDD (Slave)
Second IDE Channel: - (2) Optical DVD Drive (Master)
                    - (3) Empty

I've noticed that when I have a torrent with over 1mB/s (1000kB/s)everything in the system slows down to a crawl. I know that it's because torrent clients don't read the files sequencely, but wouldn't it be more logical if only the drive that contains the data is slowed down? I usually keep the things I download on (1), because it's more spacious that (0). If I were to change (1) in (2)'s place (set the HDD as master and the drive as slave ofcourse) would it be faster than this? Also, what difference would make if I were to copy one file from one HDD to another? The fact that they're not on the same channel probably means it's going to be slowed down, right?

Thank you in advance for the answers ^^

I would go ahead and swap the 2nd HDD and the optical drive.  That puts your two HDDs on independent controllers. Your assumption about copying files from one drive to the other is backwards. If they're both on the same channel in a master/slave relation, that's when the file transfer would slow down. Your best performance will be with the two drives as masters on different controllers.

---

### Post by CharlesA on 2012-11-01
> **wheeze said:**
> I would go ahead and swap the 2nd HDD and the optical drive.  That puts your two HDDs on independent controllers. Your assumption about copying files from one drive to the other is backwards. If they're both on the same channel in a master/slave relation, that's when the file transfer would slow down. Your best performance will be with the two drives as masters on different controllers.
This too. I just realized I read the entire diagram wrong. :|

Swap the secondary hard drive as master on the second IDE channel with the CD drive as slave.

---

### Post by andy_blah on 2012-11-01
Aha, will do. Thanks for the insight. Will there be any difference though? Perhaps I should try to use a benchmarking tool.

@ grahammechanical I was actually talking about (1) slowing down (0) not the reverse. =D
Also I agree with the CPU doing all the work, I have very little RAM on this machine so it ends up having a bigger disk read rate and the CPU is bottlenecked by this.

---

### Post by CharlesA on 2012-11-01
It probably doesn't help that IDE is a slow bus to begin with. I think there is a benchmark utility in the disk utility.

---

