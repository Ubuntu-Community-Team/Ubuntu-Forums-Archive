---
title: "Copying files to USB 3 portable drives very fast with U12.04,  but slow to internal"
date: 2014-04-14
forum: New to Ubuntu
---

### Post by joe_james on 2014-04-14
I've tried and tried to get good file copying speeds to my other internal SATA drive in my desktop PC, created Ext 4 partitions, changed SATA cables, and results have been mixed at best with random slow downs after first 100 mb. etc.
(I am not looking to solve this anymore!)

However, I have found what for me is a wonderful workaround by copying to a portable USB 3.0 hard drive connected to a PCI Express add on card, that gives me two USB 3.0 ports.    I am getting consistent speeds of around 60-70 MB/sec when copying hundreds of photo files, about 80 MB/sec if copying large video files, say around size of 300mb each.   Other large single files such as drive images are copying at 90-95 MB/sec.    I have two portable drives one a Seagate and the other a Transcend (actually Toshiba inside!) and results are very similar.    This is copying onto an Ext 4 partition created on the portable drives using Gparted installed on the PC.    However, I even get good speeds copying onto fat 32.

These speeds are very similar whether I copy from one portable drive to the other, or copy from my main hard drive (Ubuntu 12.04) onto the portable.

Posting this because I have seen lots of posts with people complaining about copy speeds but very few solutions.     I might be lucky but with my particular setup file copying speeds is no longer an issue.     Well, hope this may be of help to someone!

I did find I had to use the chown (change ownership) to be able to write to the drives but I won't go into that because there is plenty of information on this issue & it is easily solved.

---

### Post by Double.J on 2014-04-14
Hi there!

In case it hasn't been said yet, welcome to the forums!

Are these platter drives? (Non-ssd) because what is interesting is that whilst the USB 3.0 card offers a big advantage over USB 2.0, it offers none over SATA 2/3 for platter hard drives - they just can't run that fast anyway.

This is an interesting situation though. Do you know the technical difference between your internal disk vs the external? It could be a faster drive? 

In terms of out and out performance, there are three things that make platter drives faster:
1) Being empty - the more data on the disk, the slower it is.
2) Platter speed - obviously a 7200rpm drive is 30% faster than a 5400 drive
3) Data density - if the head doesn't have to move very far to get the data, it gets it faster.

In terms of user experience a lot of factors can affect drive performance as you say. Extra hard drives can increase performance because the computer can write to two at once. For example if you are running low on RAM, and the machine has started to swap a lot, additional reads/writes to that disk will be slower than to a second drive. Also if it's just one system disk vs a system and data, this in itself causes a reduction in capacity on both disks, increasing performance.

In your example you have also added an extra controller to the mix. However it may be good to run a full on check on the slower disk if it has the same specs as the new one; if it is an older disk, slowing performance can be a warning sign?

Jj

---

### Post by joe_james on 2014-04-14
Hi,

Thanks for the welcome to the forums.    

Yes, these are non ssd drives.    My main drive is a 2 tb Seagate and the other one is another Toshiba pulled out of a Transcend portable.  (They were selling very cheaply!)   However, this issue of transfers starting very quickly for the first 100 mb then slowing to a crawl does not happen when I use Windows 7.   Let's say I have 300 mb of photo files in a folder.    If I copy about 70 mb at a time it works perfectly and real fast.    However, if I try to copy the whole 300 mb at once the first 75 mb will copy real fast then it just slows and then slows some more.    I'd say it would be 10x slower than Windows.   When using Win 7 copying is perfectly fine.      The strange thing is that when copying to the Ext 4 partition on the internal toshiba using Ubuntu it does not always copy slowly - it seems a bit random.     I am 99% certain that the issue is Linux related because of the problem not showing up when using Windows. (To complicate things a bit more the internal Toshiba now has some bad sectors but still passes Disks short test apart from a warning in red about the sectors.)

I am able to compare copying speeds quite easily because I have used Clonzezilla to create Ubuntu and Windows 7 images and can switch from one O.S. to the other in minutes.

I also created an Ext 4 partition on my main 2tb drive and copying to that partition is perfectly o.k. too.    But having a backup on the same physical drive is not the best of course!

However, now that I have found that I can copy files quickly to the two external portable drives I don't care about the internal drive problem any more.   I think I am lucky because I have seen posts about people having trouble with 
very slow copying to external usb drives!

---

