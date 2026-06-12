---
title: "[SOLVED] Partitioning for a gaming machine?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Paraphysicist on 2008-05-21
I'm trying to come up with a good partition plan for my gaming pc.  It will only run Ubuntu, no other distros or windows.  I did some research, but there are a couple of things I'm unclear on.  I have a 320 GB hard drive.  Here's what I have so far:


root:  10 GB
swap:  4 GB
home:  250 GB



Does this plan look ok?  I'm going to install a lot of pc games and play them thru wine, so /usr should be pretty big.  Do I need a separate /opt partition?  Am I missing any other partitions?  Any tips or advice would be greatly appreciated.  Thanks

---

### Post by pytheas22 on 2008-05-21
I'm not positive, but I'm pretty sure that wine installs Windows applications to the home directory of the user installing them--hence the ability to install applications via wine without being root.  /usr is only for native Linux applications.  I would check on this and maybe make /home 200GB and /usr only 50 if I'm correct.  You also might want more than 1GB swap if you're going to be running high-demand games.

Also just to be clear, because I'm not sure how much experience you have with Linux: with the exception of swap, you don't *have* to install all of these things on different partitions.  You can install the whole Linux system on one partition if you want, and this is what most people do.  Sometimes there are advantages to having e.g. /home, /usr and /root on their own partitions, but I'm not sure it would make a difference for you--indeed it might actually harm performance because everything would be farther apart on the hard drive.  Unless you have a compelling reason to want everything so separated, I would only put /home on a separate partition, if I were you (and only this because it would keep your wine configuration and applications separate from the rest of the system, which would allow you to reinstall Ubuntu without having to rebuild all of your wine stuff).

---

### Post by danking12 on 2008-05-21
Generally swap should be twice as large as the amount of RAM in your system. You may want to partition for larger in case you ever upgrade or increase the amount of RAM in your system.

---

### Post by pdtpatrick on 2008-05-21
Have you verified that these games would work under linux? just a start .. thought i'd ask

---

### Post by stchman on 2008-05-21
> **Paraphysicist said:**
> I'm trying to come up with a good partition plan for my gaming pc.  It will only run Ubuntu, no other distros or windows.  I did some research, but there are a couple of things I'm unclear on.  I have a 320 GB hard drive.  Here's what I have so far:


root:  10 GB
boot:  1 GB
swap:  1 GB
tmp:   500 MB
home:  ~50 GB?
usr:   ~200 GB?
opt: needed?



Does this plan look ok?  I'm going to install a lot of pc games and play them thru wine, so /usr should be pretty big.  Do I need a separate /opt partition?  Am I missing any other partitions?  Any tips or advice would be greatly appreciated.  Thanks

If you are going to play lots of Windows games I recommend that you dual boot.  WINE plays some Windows games but not all.  Install XP or Vista first and then Ubuntu.

---

### Post by Paraphysicist on 2008-05-21
Thanks for all the replies.

pytheas, you bring up some really good points.  I'll bump up the swap to 4 GB and check if wine installs games in /home.  

danking, thanks I'll increase the swap to 4 GB (2x my RAM)

pdtpatrick, the games I'm looking at work at least at gold level according to the winehq reports.  Hopefully they'll work ok on 8.04. (If not I can warn others)

stchman, I see where you're coming from, and it would save a some hassle, but I agree with your sig :guitar:

---

