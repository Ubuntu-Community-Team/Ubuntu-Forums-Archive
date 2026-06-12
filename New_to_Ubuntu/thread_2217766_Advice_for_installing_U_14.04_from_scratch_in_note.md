---
title: "Advice for installing U 14.04 from scratch in notebook with 2 HDs"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by Catenaccio on 2014-04-18
Hi all,

First of all, I'm sorry in advance if what I'm asking is somewhere else, I couldn't find any specific topic on this, that's why I'm posting a new thread.
I am a beginner user of Linux, who has Linux (Ubuntu 13.10) already installed in notebook. The first time I installed it it was version 12.04, I did not have any problem, and it was in dual boot with Win7 (currently, Win8). 

I've decided to become a "full" Linux user, so I'm going to install U 14.04 on  my main computer, still in dual boot with Win7 just because there are a couple of applications (some of them work-related) that I need to run on Windows, but other than that, I'm planning on have Linux be my "main" OS and Windows just that thing I need from time to time. 

Since this installation is "no test" (as my first one) I want to do things the best way possible. Thus, I have a couple of questions I would like to have some advice on. Just so you know the basic hardware, it's an Asus N73 17" Notebook, with the following specs:

Processor: [FONT=arial]2nd [/FONT][FONT=arial]Gen[/FONT][FONT=arial] Intel Core i7-2630QM, 2.0-2.8GHz,32nm, 6MB, 45W
[/FONT]Graphics Controller: nVidia GeForce GT 540M 1GB GDDR3 with Optimus Technology
RAM: 12GB DDR3 1333 Dual-Channel (4GB x 3)
Primary Hard Drive: 500GB Seagate Momentus XT 7200RPM 32MB, 4GB SSD Hybrid Drive, SATA II 3Gb/s
Secondary Hard Drive: 750GB 7200rpm 2.5-inch 9.5mm 16MB SATA II 3Gb/s

1) Intuitively, I assume that I will have to install Ubuntu along with Windows in the first HD (which currently is half full), so I'll have to create a partition (Linux's one would be an ext3 partition, I understand that is the recommendation). The second HD should remain untouched (so both Windows and Linux would have access to it). Is this right? 
Just for my knowledge, is it possible to have Windows in one HD and Linux in the other HD (perhaps with some partitioning leaving a drive available for sharing data)? Or given that only one of the HD is "primary", both OS have to be there?

2) My understanding is that the "ideal" swap partition should be as big as the RAM memory, so in my case I should have a 12 GB swap, is that right?

3) I don't expect to run into any issues with drivers (none of the components is cutting edge technology), but just in case, any recommendation?

Thanks in advance!

---

### Post by jdeca57 on 2014-04-18
From bottom to top:
Ubuntu works as a live cd/usb and you can test compatibility, then make backups, and only then install
The issue of swap partitions is really one of usage of the computer. 6GB might be enough, see: [http://askubuntu.com/questions/49109/i-have-16gb-ram-do-i-need-32gb-swap](http://askubuntu.com/questions/49109/i-have-16gb-ram-do-i-need-32gb-swap)
And last, it is perfectly possible to put Linux on another drive. On the computer I'm using that's what I'm doing. Of course, an hybrid or SSD drive will be faster to boot, but then again booting is not the real test of an OS.

---

### Post by Catenaccio on 2014-04-18
Thank you very much! I've reading the swap file link, very useful. I'm still doubting if I will be using the hibernation feature (currently, I do, but just because it usually takes so long to windows to boot...); according to the thread, without it I should put 6GB or swap file, with it, it should be 18 GB... At the end of the day, 18gb it's not going to kill me but so I might err on the safe side. Now, having said that, if I were to set up a 6GB swap file, can I later change the partition and enlarge (or reduce) the swapfile without having to re-install the system?

---

