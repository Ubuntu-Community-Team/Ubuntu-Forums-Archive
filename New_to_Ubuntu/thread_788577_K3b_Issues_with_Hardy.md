---
title: "K3b Issues with Hardy"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by splendid on 2008-05-09
I just did a fresh install of Hardy. When trying to burn a DVD video, I am getting a message "Could not determine size of resulting image file". It will not burn the video to my Kodak DVD-r

Did not have this problem with 7.10.  I am able to burn CD's using Serpentine.  

Anyone have any ideas???

Thanks,

Splendid

---

### Post by crjackson on 2008-05-09
Download a trial version of NERO Linux 3 and see it that works.  I haven't tried K3B under Hardy but I own a copy of NERO Linux.  It works great for me...

---

### Post by splendid on 2008-05-09
Thanks for the advice.  I am downloading it now.  What is the best way to install?

---

### Post by viking_3537 on 2008-06-02
Hi,
I have the same problem.
It seems that mkisofs is not present in Hardy. There's a genisoimage instead and it's not causing any problems. I guess it's just that applications like K3B,Brasero etc. are trying to make an iso image of files that a user wants to burn and issues the command mkisofs ..... etc. and doesn't get what it wants in response because the usage differs.This is just a thought.
I need Your opinion about it. Am I right or not ? And how to make everything work without using Nero (which probably has it's own ways of making iso images) ?
Please help.

---

