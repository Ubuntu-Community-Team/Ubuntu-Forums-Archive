---
title: "Damaged WINDOWS Partition"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by turnbub on 2012-11-27
I run WINDOWS XP, I had 3 partitions on my hard drive:-
C: for WINDOWS and basic software,
D: for applications not so important
and
E: for data .... makes it easy to backup data.

I created a new partition, called X: tried to put UBUNTU there but it didn't seem to want to co-operate, so I let it do it's own thing.

UBUNTU created a new partition at the back end of my D: drive and put itself there ...... seems to work well ..... on booting the UBUNTU OS is number one, but if I catch it I can scrole down to WINDOWS and it boots fine also.

My problem is that WINDOWS no longer recognizes my D: drive - it is still there, the PARTION Mgr says it is fine, but apparently the directory is damaged.

I am OK as I did as suggested and backed up my total hard drive before installing UBUNTU, and will continue to try and fix it so as to keep UBUNTU.

MY main purpose in writing this is to put it out there that this can happen ...... I guess we need to be careful WHERE we install UBUNTU.

Any comments will be welcome, both for resolving the WINDOWS problem and for care in installing UBUNTU.

Thanks to all,  Bobby

---

### Post by oldfred on 2012-11-27
Post this from Ubuntu terminal.

sudo fdisk -lu

---

