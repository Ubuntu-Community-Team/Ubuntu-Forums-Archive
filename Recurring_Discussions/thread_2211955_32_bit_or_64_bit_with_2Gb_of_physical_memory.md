---
title: "32 bit or 64 bit with 2Gb of physical memory?"
date: 2014-03-18
forum: Recurring Discussions
---

### Post by fangorn2 on 2014-03-18
Hello.

I want to download Ubuntu and I am wondering whether I should download the 64 bit or the 32 bit version.
My computer has 2048 MB (2 x 1024) of physical memory and a 2600 Mhz processor. On the download page it is advised to get Ubuntu 32 bit in case the PC has less than 2 GB of memory, so what should I do? I suppose there are reasons why Ubuntu has chosen the 2 GB threshold, and I am just on it...

---

### Post by slickymaster on 2014-03-18
Hi fangorn2, welcome to the forums.

Here is a thorough answer to your doubt -> [What are the differences between 32-bit and 64-bit, and which should I choose?]("http://askubuntu.com/questions/7034/what-are-the-differences-between-32-bit-and-64-bit-and-which-should-i-choose")

---

### Post by oldfred on 2014-03-18
Moved to recurring discussions. 

You are right on the cusp.

Post by VeeDub on choosing 64 bit:
[http://ubuntuforums.org/showthread.php?t=2133616&p=12594619#post12594619](http://ubuntuforums.org/showthread.php?t=2133616&p=12594619#post12594619)
[http://ubuntuforums.org/showthread.php?t=2028717](http://ubuntuforums.org/showthread.php?t=2028717)
32-bit vs. 64-bit Ubuntu 13.04 Linux Performance with only 1GB of RAM & most tests better with 64bit Mac Mini
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1)

But I run 64 bit on my old Core Duo laptop with 1.5GB of RAM. As long as I load only one larger app and several smaller apps it works well. If I happen to load several larger apps, it turns grey for a second or two and I can tell it is using swap. 
Main reason I loaded 64 bit was my Desktop has 4GB and a 64 bit install and I wanted same install in both.

---

### Post by fangorn2 on 2014-03-18
Thanks for your answer, slikymaster.

I read the post you linked, and I am still undecided about what to do for some reasons.
Shall I take from granted that all the considerations I read are valid for any OS? I have been using windows xp x64 until now and did not have any problem with it, so I might feel safe to install Ubuntu x64 on the ground of this experience.

Being the processor of my pc an AMD Athlon 64, the question is whether it would be convenient to upgrade the RAM to 4 Gb, considering that Ubuntu does not consider 4 Gb as a grey zone but 2 Gb, and that I have been using a different 64 bit operative system until now with no evidence of any problem.

I would like to install both windows 7 and Ubuntu, so I would install the 64 bit version of both, and then, eventually, even if my pc is ancient, I would consider of upgrading the RAM.

---

### Post by grahammechanical on 2014-03-18
The reason why it is suggested that machines with less than 2GB RAM you should choose 32bit Ubuntu has nothing to do with Ubuntu 64bit needing more than 2GB RAM. In the past a 32bit OS was limited in the amount of RAM it could use. Then modifications (PAE) were made to allow it to use (address) more than 4GB RAM. But we needed both a CPU that could run these Physical Address Extensions (PAE) and a 32bit OS that could use them. Well, 32bit Ubuntu does exactly that.

Set against this 64bit operating systems were designed to address more than 4GB RAM from the beginning. So, if the machine has a 64bit CPU it can run 64bit Ubuntu. I find that Ubuntu 64bit runs fine on my 64bit Intel Core 2 Duo 2.40GHz with 1Gb RAM. There are other advantages to using a 64bit OS on a 64bit CPU. Especially if we will have more than 4GB RAM.

Regards.

---

