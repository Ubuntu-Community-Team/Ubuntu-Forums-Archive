---
title: "Partition &amp; mount point set up during install - now how do I use it?"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by The Bright Side on 2012-04-27
Hey guys!

I installed 12.04 on my laptop yesterday and created a partition on the second hard drive during the installation, which I mounted at /multimedia.

Now, I can see and access that folder from my system, but I cannot read or write to it (obviously, because it's not part of my Home directory). I'd like to use it as a normal folder though in which I store my videos and music. What do I do?

I'm wondering if either of these will work (I'm in the office now so cannot try):

1. Launch Nautilus as root (sudo nautilus), then change the permissions for the folder, then bookmark it for easy future use?
2. Move the mount point from \multimedia to \home\Multimedia? Would you happen to know how I can do that?

Hope you can help me... Sorry for the n00b question.
Thanks!

---

### Post by powder on 2012-04-27
Try this...

```

sudo chown -R yourusername /multimedia/

```

---

### Post by cryptotheslow on 2012-04-27
Hi,

Can you post back the output of the three commands below (wrap it in [ CODE] [ /CODE] tags to keep it readable).

```

sudo mount -l

cat /etc/fstab

ls -al /multimedia

```

Only need the first few lines of the output from that last one.

Should be simple enough to sort out the permissions once we know how it's currently setup.

---

### Post by The Bright Side on 2012-04-27
Thanks so much guys, I will try this tonight when I'm back from the office and post back here. Appreciate your input!

---

### Post by The Bright Side on 2012-04-27
Hey guys, powder's tip worked! I can now have my way with /multimedia :-)

cryptotheslow, I can still get that output if you want...

Thanks so much!
Matt.

---

### Post by cryptotheslow on 2012-04-27
That's good news.

powder's suggestion is fine if you are the only user of the machine and no other user accounts need full access to /multimedia.

In that case - no need for what I asked :)

---

