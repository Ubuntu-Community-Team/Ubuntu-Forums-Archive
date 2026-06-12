---
title: "Install XP to boot FROM linux"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Nyankan on 2008-06-22
*the background*

Okay, Im a first time Linux user, however I have had Ubuntu for a few months so far, and everything went well. After updating to 8.04, I found that my system ran extremely slow, much slower than when under the old 7.10, and attributed this to compiz working instead of metacity, at first, however it doesnt seem to be the case, after turning off compiz, I found Metacity running even slower than the previous display manager. So i decide to reinstall Ubuntu and see if that makes the difference, and decided to use this chance to reinstall XP. However the shared hard drive for Ubuntu and XP is a SATA drive, and the XP disk doesnt like writing to a SATA drive. Even more heartbreaking, although I have the SATA drivers on CD, the windows installation only wants a floppy disk, and I lack a floppy disk drive *sigh*

****The Question!****

Anyway the idea crossed my head to try and install XP through Linux, not as a virtual machine, but as an actual booting from the hard drive OS. Is this possible? If so, how would it be done? Once its done, I will reinstall Ubuntu afterwards, so it doesn't matter if GRUB gets wiped, it'll be fixed when I redo Ubuntu.

---

### Post by Drakkor on 2008-06-22
Have you tried partitioning your hdd into 2 partitions,and then install XP on the first partition,and then Ubuntu on the second,and write grub to the 
mbr,so that you have the option to boot from either ? :)
Edit: I would download and clean install 8.0.4

---

### Post by Nyankan on 2008-06-22
nah, cant even get to the patition screen in XP setup since it doesnt recognize my SATA hard drive, so any installation from scratch is gone. Might give

[http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml](http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml)

a go, it seems to give a solution to my problem.

And yeah, i have a fresh copy of 8.04, so I'll install from that

---

### Post by Paqman on 2008-06-22
Can you borrow a floppy drive from someone and plug it in temporarily? It's not like anybody is using theirs 24/7 these days anyway.

---

### Post by Nyankan on 2008-06-22
Well that link didnt work, so I think its proberly best to go with your idea. I'll see what I can steal from work. If not? I'll just keep XP as it is, laggy and buggy. Dont use it that often, anyway

---

### Post by billgoldberg on 2008-06-22
I had the same issue with an old xp sp1 cd not having sata drivers.

You can do 4 things,

1) slipstream your xp install cd (google it).

2) download xp from the internet (might be illegal)

3) buy an xp cd (expensive)

4) borrow a xp cd from a friend (might be illegal)

About the slow running ubuntu.

If you upgrade instead of installing from a cd, this can happen sometimes.

Do a clean install and the system will run fine.

---

### Post by Nyankan on 2008-06-22
> **billgoldberg said:**
> I had the same issue with an old xp sp1 cd not having sata drivers.

You can do 4 things,

1) slipstream your xp install cd (google it).

2) download xp from the internet (might be illegal)

3) buy an xp cd (expensive)

4) borrow a xp cd from a friend (might be illegal)

About the slow running ubuntu.

If you upgrade instead of installing from a cd, this can happen sometimes.

Do a clean install and the system will run fine.


Yeah. just did a clean install, running smoother than ever. Though Im not going to activate compiz this time till I get a new computer. I think thats what made things go bad last time.

The slipstream method seems to be similar to what I tried earlier. but I'll give it another shot

---

### Post by Drakkor on 2008-06-22
FDDs are about less than $10 bucks these days,lol :)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16821103116](http://www.newegg.com/Product/Product.aspx?Item=N82E16821103116)

---

### Post by Nyankan on 2008-06-22
its even cheaper if I pick one off one of the old computers laying about at work... Its prolly what I will do in the end, seems the simplest way to do things. Thanks, everyone, might as well call this problem solved... sorta. But it would be neat if you could install windows from your Linux desktop...

---

