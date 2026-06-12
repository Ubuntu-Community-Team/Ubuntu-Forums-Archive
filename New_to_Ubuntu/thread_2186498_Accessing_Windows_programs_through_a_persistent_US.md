---
title: "Accessing Windows programs through a persistent USB install"
date: 2013-11-07
forum: New to Ubuntu
---

### Post by lupus9478 on 2013-11-07
Hey everyone - it's been a long while since I've been on this forum, long enough that I had to create a new account because of Ubuntu One. A while ago, I ran a dual boot to try and get myself acquainted with the Linux world, but I didn't get very far (so bear with my ignorance).

So at work I have an older Dell computer that is slowly dying. It **is** usable, it's just painfully slow. So I plan on creating a persistent installation of Ubuntu on a USB flash drive and using Linux for most tasks - web browsing, word processing, general procrastinating...

What I'm not sure how to do is access the Windows programs that I use for work through the Linux environment. These are expensive programs, so I can't just buy the Linux version. I know about Wine, and I know about VirtualBox, but what I'm trying to do is access the programs and files on an existing Windows installation rather than create a new one.

So, what's the simplest way of doing this? Is it even possible?

For some background that may help you relate to my problem: I'm a student. I conduct research in a microbiology lab. I use DNA-sequencing programs that are paid for by my department, and I don't think they'd be willing to buy the Linux version of these programs. As far as I know, there's no free alternative.

Thanks in advance!

---

### Post by Bucky Ball on 2013-11-07
Welcome (back).

You install Wine in Ubuntu and then install the Windows programs using Wine. There is no way of running the Windows programs on the Windows partition while you are running Ubuntu.

Your only other option is to install Windows in Ubuntu as a virtual machine (make sure you have plenty of RAM) or dual-boot.

See here and check if your programs will work in Wine (use the search bar, top right):

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by lupus9478 on 2013-11-07
Thanks! I may have found a workaround. Going to close this thread and start another.

---

