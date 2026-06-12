---
title: "Cannot Shut Down on Ubuntu - Ubuntu 16.04 and Win 10 Dual Boot"
date: 2017-06-05
forum: New to Ubuntu
---

### Post by bayeshen on 2017-06-05
I am a total new guy for Ubuntu --I just installed Ubuntu 16.04 on my Windows 10 pre-installed Desktop. Everything looks ok but I cannot shut down on Ubuntu- Every time when I shut it down it freezes with a error like 'end kernel panic: not syncing: fatal exception in interrupt', please see the linked screen shot picture.([https://i.stack.imgur.com/MKMwp.jpg](https://i.stack.imgur.com/MKMwp.jpg)) which I have to force to press power button on PC machine to turn it off.

So currently when I finish using Ubuntu what I can only do  is: either restart and choose to log in on windows OS and shut down normally(since my Windows works fine), or press the physical shutdown button on the machine when I was trying to shut down and got frozen on Ubuntu


FYI: Here are some info about the desktop and system: 
GPU: NVIDIA gtx-1080, 
256 GB SSD, 2T HDD (100GB SSD and 500 GB HDD for Ubuntu) 

Ubuntu disk manage: '/' and 'swap' on SSD, '/home' on HDD


Any help will be extremely appreciated!!

---

### Post by wildmanne39 on 2017-06-05
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

I had that issue with Ubuntu on an usb drive this weekend and it was caused by the drive being corrupted, so I installed on another drive and it worked perfectly, I did also have a message that said there was a corrupt file.

---

### Post by bayeshen on 2017-06-05
Thanks for helping me to edit it, this is the very first post I've ever made, sorry for any inconvenience..

For your mentioned usb issue--actually I dont get it(sorry!), since I am a brand new guy for Ubuntu, but it seems that it works all fine on my Ubuntu-- I can update software, install my needed software(like statistical software R and RStudio) normally, the only issue is I cannot shut it down normally.

Do you mean my USB drive as Ubuntu installation stick has some problem?

---

### Post by wildmanne39 on 2017-06-06
I meant I had the same kernel error message as in your screenshot and it was caused by a corrupt file, I am sure someone will jump in here and maybe they will have a way to fix it.

I did some research and as I thought it is most likely a corrupt file, I am not sure how to fix it without reformatting the drive.

---

### Post by bayeshen on 2017-06-06
Thank you for your info! I just re-installed Ubuntu, and tried to update the softwares/packages before do shutdown action. But this time it just stucks at the Ubuntu splash screen without any info.. 

I did a small survey and it looks like a kernel bug maybe? Looking forward to anyone's support!

Btw I reinstalled it using the installation stick created by Ubuntu(not Windows as previous), not sure this info useful, but just FYI for anyone checking

---

