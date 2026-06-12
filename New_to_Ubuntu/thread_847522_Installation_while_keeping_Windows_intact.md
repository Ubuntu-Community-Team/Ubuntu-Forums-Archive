---
title: "Installation while keeping Windows intact"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by harmlessgoat22 on 2008-07-02
I am hoping to install ubuntu on my windows computer, but I want to keep windows as well. I know this is possible, but do I need anything else other than just ubuntu? Can I just pop in the disk, follow the instructions and be able to keep both windows and ubuntu on the same computer, and be able to decide which one to load up when you restart the computer?

Sorry, I'm a complete idiot when it comes to this kinda stuff. Any and all help is appreciated.

---

### Post by sydbat on 2008-07-02
No problem. We all start somewhere. Pop the CD in while in Windows and install it under wubi. This makes it a "program" under Windows and allows dual-booting (of a sort). Just follow the instructions from the CD as they come up. It is a great way of determining if Ubuntu is for you.

---

### Post by harmlessgoat22 on 2008-07-02
Program under windows? So do you still load it at startup, or are you saying that they can be loaded simultaneously?

EDIT: Wait...I dunno if you are understanding what I'm asking right. I want Ubuntu to be installed on the computer, not just loaded from the disk. I wanna be able to use it without the disk in the drive...

---

### Post by munkyboy on 2008-07-02
this give you all the info you need

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Its really easy as long as you do what it says. Any probs ask in these forums, I just did it and it works fine, I dont even use window's

---

### Post by paul101 on 2008-07-02
yes!! it is possable


you will get to a screen where you chop up your hard disk, just dont forget to change the default values, giveing windows more space (the yellow/orange bit)


:-:-:


this is the default and will leave you with **no free space** on your xp partition  (i've learned from my mistakes :lolflag: )
[img]http://www.psychocats.net/ubuntu/images/installinghardyplus10.png[/img]

resized to my preference:
[img]http://www.psychocats.net/ubuntu/images/installinghardyplus11.png[/img]


generally ubuntu only needs about 1/4 of the space in your drive



heres a guide with screenshots:



**[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)**

---

### Post by harmlessgoat22 on 2008-07-02
Thanks so much all of you.

Munkyboy, thanks for the link. I'll check it out.

Paul101, the screenshots really helped. So lets say I have a 160 gig drive, and I give a certain section to Ubuntu, lets say 3 gig. I can't store anything for ubuntu on anything more than that 3 gig (minus the amount needed for the actual OS)???

---

### Post by sydbat on 2008-07-02
We are talking 2 different things here. Let's no confuse the OP.

WUBI runs Ubuntu under Windows, but acts like a fully installed Operating System...you have to choose Windows or Ubuntu when booting. If, for some reason, you do not like Ubuntu, you can remove it via Add/Remove Programs in Windows.

What Paul101 is taking about is a full installation requiring partitioning, etc.

To answer the OP's edit in his second post - you only run Ubuntu from the CD if you are checking it out without making any of the above commitments to install.

---

### Post by eapache on 2008-07-02
Ubuntu can read and write to Windows partitions (via the Places menu which you will see once installed).

---

### Post by paul101 on 2008-07-02
> **harmlessgoat22 said:**
> Paul101, the screenshots really helped. So lets say I have a 160 gig drive, and I give a certain section to Ubuntu, lets say 3 gig. I can't store anything for ubuntu on anything more than that 3 gig (minus the amount needed for the actual OS)???

well 160gb is quite a big hard drive (imo, unless you have allot of software installed)


i'd say give ubuntu partition about 60gigs :)

---

### Post by harmlessgoat22 on 2008-07-02
Ok, it sounds like this is going to work well. I'll read the documentation a few more times, then when I think I've gotten it, I'll try installing Ubuntu for dualboot.

Thanks everyone!

---

### Post by paul101 on 2008-07-02
have you took a looksie at the ubuntu live cd?? (stick the cd in the drive, reboot and select the first option ("try ubuntu without any change to your computer"))...

---

### Post by munkyboy on 2008-07-02
Its alot easier than you think.

I would strongley recommend that you use more than 3 GB for you ubuntu partition. you'll only want to change it later and have to reinstall, I say this cause that what I did.

---

### Post by avtolle on 2008-07-02
I realize that 3 gb was likely used for illustrative purposes, but I'd allocate at least 10 gigs to Ubuntu, likely more; don't forget the /swap as it will be using some space within that part of the HDD allocated to Ubuntu. The installation disk partitioner will likely give you a /swap of 1.5 x RAM by default, BTW.

---

### Post by paul101 on 2008-07-02
well if he / she's got a 160gb hard drive, about 40-50gb imo would be a sensible amount for the ubuntu partition :KS

---

### Post by avtolle on 2008-07-02
> **paul101 said:**
> well if he / she's got a 160gb hard drive, about 40-50gb imo would be a sensible amount for the ubuntu partition :KS
I agree, but didn't want to overwhelm him/her. :)

---

### Post by harmlessgoat22 on 2008-07-02
him.

I tried a couple ubuntu cd's earlier on my old computer, but they didn't work because they were made for 64 bit processor, I think, and that computer was 32, but this one is 64. This computer used to be my brother's, he built it himself, and put ubuntu on it. Then he got a Macbook Pro for college, and we took this computer. My dad wanted to load windows on it because he has various things that need windows (and he doesn't want to go through the hassle of an emulator). So, I have to keep windows there, but I want to use ubuntu.

In a few days, I'll go and try it, and I can always ask my brother for help if I need it...seeing as he did this all in the past.

---

### Post by harmlessgoat22 on 2008-07-05
I'm happy to say that I successfully installed Ubuntu without screwing up any of my windows files.

---

