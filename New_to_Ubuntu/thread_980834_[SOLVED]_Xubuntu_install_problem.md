---
title: "[SOLVED] Xubuntu install problem"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Charlie Chick on 2008-11-13
Hello Everybody,

I have a curious problem trying to install Xubuntu 8.10 on an older computer. I get the following error message:

Loading, please wait....
Busybox v1.10.2 (ubuntu 1:1.10.2ubuntu6)Built-in shell (ash)

(initrames)

and the installation stops at this point. Can anybody advise me what to do to get this working?

Many thanks,

Charlie

---

### Post by mapes12 on 2008-11-13
Are you using a Live or Alternate CD?

---

### Post by gn2 on 2008-11-13
What are the specs of the computer, what CPU does it have and how much RAM is fitted?

---

### Post by Charlie Chick on 2008-11-13
I'm using the live CD. I don't know what the processor is but it has 512Mb of RAM and an 80Gb hard drive. It originally came with Windoze 98.

---

### Post by mapes12 on 2008-11-13
What version of Ubu are you trying to install?

Can you run a Live CD session without installing it? 

Have you setup your partitions ( [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) ) with GParted or an equivalent tool. GParted can be run from the Live CD.

---

### Post by Bölvaður on 2008-11-13
[http://en.wikipedia.org/wiki/BusyBox]("http://en.wikipedia.org/wiki/BusyBox")

I can understand if BusyBox wont load, xubuntu will fall with it. What I do not understand is it would be pc specific... it shouldn't be hardware dependent. How often have you tried to boot from the cd (it might be flawed or data was incorrectly read from the cd).

I dont know if alternate cd has this utility, but I would go for the alternate cd.. not becaues of RAM because you have enough for even kubuntu live cd.

---

### Post by Charlie Chick on 2008-11-13
I've discovered that I can install 8.04 but if I then upgrade to 8.10 I get the same problem on bootup. So I'm sticking to 8.04. That way, I get a useable computer.

---

### Post by mapes12 on 2008-11-13
> So I'm sticking to 8.04

I also had trouble with 8.10 but for another reason. 8.04 is just fine and has full LTS.

Do you want to mark your thread as SOLVED?

---

### Post by yt_l9 on 2008-11-13
I was thrown into busybox a while back, installing 8.04, and discovered that it is due to a hardware issue.  Mine was with a SATA HDD which was solved by editing the boot parameters.  Your problem could be a video driver (solved with adding "vga=771" or something to that effect, you should double check just to be safe), to your Advanced Configuration and Power Interface (solved with "noacpi")

you should be able to determine what is wrong by just deleting the "quiet splash" parameter to see where the system is stalling on boot.

Hope this helps.

---

### Post by Charlie Chick on 2008-11-14
Thank you to all for your replies. Although I have decided to stick with 8.04, I didn't mark the thread as solved because I hoped that somebody would help me to understand *why* if failed to work. Now that yt 19 has explained that, I'll mark it. 

Thanks again to everybody for your help. This forum is a really great resource!

Charlie

---

