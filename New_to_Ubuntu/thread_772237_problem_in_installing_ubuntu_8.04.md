---
title: "problem in installing ubuntu 8.04"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by czarnick on 2008-04-28
hi all

i tryin to install ubuntu 8.04 desktop edition on my system which already have windows xp n windows 2003 server installed but facing problem.

i have 250 gb hard disc which have 4 partitioned of 58 gb each approx. n on first partition i have windows xp n on second windows 2003 server n third one i wanted to use for ubuntu n fourth one is jus for data

so i have edited the third partitioned to allocate 30 gb for ubuntu n rest 28 approx as ntfs partition through ubuntu live cd then i got 30 gb as unused space n 28 approx as ntfs n when i selected 30 gb unused space  for use as swap n ext3 then new partition table button become inactive so that i cant change that unused partitioned for ubuntu nor i can reverse the whole process of makin it again as ntfs

so any guru or expert out there to help me in this regard

with regard n thnx
nm

p.s.:1. Apology for bad english
2. I am newbie to linux
3. My system have pentium 4 speed of 2.0 ghz n 512 mb sdram

---

### Post by Tatty on 2008-04-28
Sorry a little confused as to how many partitions you currently have,  could you just clarify that.

You can only have a maximum of four primary partitions on a hard drive.  You will probably want to make one of these an extended partition which you can use to contain your swap and your extra data partition (you can have as many logical partitions as you like under an extended partition).

---

### Post by czarnick on 2008-04-28
hi there 

thnx for reply

currently i have 4 partitioned 
n i wanted to have linux in third partitioned but i cant bcuz when i allocated that partitioned for swap n ext3 it become unused space n i cant partitioned thta usused space bcuz new partitioned tool button inactive so how can i partitioned now

---

